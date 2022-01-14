# Nginx 架构

## nginx 请求处理流程

nginx 运行在企业内网的最外层，也就是边缘节点，它处理的流量是其他应用服务器流量的数倍甚至几个数量级。

任何一个问题在不同数量级下处理的方案是完全不同的。nginx 它所处理的应用场景中所有的问题都会被放大。所以我们要了解 nginx 为什么要采用 master/worker 这样的架构；为什么 worker 进程的数量 和 cpu 核心数相匹配；当我们在多个 worker 进程间共享数据的时候，为什么在 tls 或一些限流限速的场景中它们的共享方式是不同的。这些都需要我们对 nginx 架构清晰的了解。

### nginx请求处理流程

![image-20220110203944511](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110203944511.png)

大致有三种流量：WEB，EMAIL，TCP流量

流量进入 nginx 以后，nginx 有三个大的状态机，为什么叫状态机呢，因为外面大的绿色的框用的是非阻塞的事件驱动处理引擎，也就是 epoll 模型。一旦我们用这种异步处理引擎之后，一般都需要用状态机来把请求正确的识别和处理的。

基于这样的事件驱动处理引擎，我们在解析出请求需要访问静态资源的时候，它就走左下方的静态资源。

如果我们做反向代理的时候，那么对反向代理的内容可以做磁盘缓存。

但是我们在处理静态资源的时候，会有一个问题：当内存不足以完全的缓存所有的文件时，sendfile 这样的调用或 AIO 会退化成阻塞的磁盘调用，所以我们需要一个线程池来处理。

对于每一个完成的请求，我们会记录 access 日志和 error 日志，这里也是记录在磁盘中的。当然我们可以通过 rsyslog 记录到远程的机器上。

更多的时候，nginx是作为负载均衡或反向代理使用的。这个时候，将请求通过协议级传输到后面的服务器。也可以通过应用层的协议（fastcgi，uwsgi，scgi）代理到相应的服务器。



## nginx 进程结构

nginx 有两种进程结构：

- 单进程结构：不适合生成环境，只适合开发调试用
- 多进程结构：生产环境必须保持 nginx 足够健壮；利用 cpu多核心 的特性

### nginx 的多进程结构

![image-20220110204840826](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110204840826.png)

一个父进程 master 进程它会有很多的子进程，这些子进程分为两类：一类是 worker 进程，一类是 cache 相关的进程

**为什么nginx采用的是多进程结构而不是多线程结构呢？**
**这就要从 nginx 最核心的一个目的来说：nginx 要保持它的高可用性和高可靠性。如果 nginx 是多线程结构，因为线程间是共享同一个地址空间，当某一个第三方模块引发了一个地址空间导致的段错误时，在地址越界出现时，会导致整个 nginx 进程全部挂掉。**
**当我们采用多进程结构时，往往不会出现这样的问题。**

通常第三方模块是不会在 master进程中 加入自己的功能代码的，因为 master 进程设计的目的是：做 worker进程的管理的，所有的worker进程是处理真正的请求的。

master 进程：负责监控每个 worker 进程是不是在正常的工作，需不需要重新载入配置文件，需不需要热部署等。
缓存是要在多个worker 进程间共享的，而且缓存不光要被 worker 进程使用，还要被 cache manager  和 cache loader 进程使用。

cache manager 和 cache loader 也是为反向代理时后端发来的动态请求做缓存所使用的，cache loader 用来做缓存的载入，cache manager 用来做缓存的管理。实际上，每一个请求处理时使用到缓存还是由 worker 进程来进行的。

这些进程间的通信都是使用共享内存来解决的。

**为什么 worker 进程有很多？**
**因为 nginx 采用了事件驱动模型以后，他希望每一个 worker 进程从头到尾占用一颗 cpu，所以往往我们不光要配置 worker进程的数量与服务器上的 cpu 核心数要一致，还需要把每一个 worker 进程与某一颗 cpu 核心 绑定在一起，这样可以更好的使用每一颗 cpu 核上的 cpu缓存，来减少缓存失效的命中率。**



## nginx 进程结构实例演示

nginx 进程父子之间是通过==信号==管理的。

下面我们通过一个实例来了解 nginx 进程之间如何通过信号进行管理。

我们启动了一个父进程 和 两个 worker 进程  ![img](https://img2020.cnblogs.com/blog/597917/202201/597917-20220110114745184-1291057760.png)

worker进程和cache进程都是由 9170 这个父进程生成的。

当我们 reload nginx 时，worker 进程和 cache 进程会优雅的退出，而后使用新的配置项去启动新的 worker 进程。

![img](https://img2020.cnblogs.com/blog/597917/202201/597917-20220110115215250-1291144832.png)

reload 和 发送 SIGHUP 信号是一样的，会重新生成两个worker进程 

![img](https://img2020.cnblogs.com/blog/597917/202201/597917-20220110115433770-195889907.png)

stop 和 quit 也有相应的信号，当向 worker 进程发送退出信号后，那么这个 worker 进程就会退出，但是在退出时会自动向它的父进程发送一个 CHLD 信号，这样 master 进程就会知道它的 worker 进程退出了，然后它会新起一个 worker 进程来维持总共两个 worker 进程这样的配置。

![img](https://img2020.cnblogs.com/blog/597917/202201/597917-20220110120023536-312495930.png)

 

## 使用信号管理 Nginx 的父子进程

nginx 是一个多进程的程序，多进程之间进行通讯可以使用共享内存、信号等。但我们做进程间的管理时，通常只是用信号。

下面我们来看一下nginx的信号是怎么样使用的。

### Nginx进程管理：信号

![image-20220110210442724](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110210442724.png)

能够发送和处理信号的有 master 进程、worker 进程、还有我们使用nginx命令行。

因为master进程会启动worker进程，所有它管理worker进程的方式：首先是监控worker进程有没有发送CHLD信号。因为nginx中规定，当子进程终止的时候会向父进程发送CHLD信号，所以worker进程由于一些模块出现bug导致worker进程以外的终止掉，那么master进程可以立即通过CHLD发现这个事件，重新把worker进程拉起。

master进程还会接收一些信号来管理worker进程。可以接收的信号比如：TERM,INT（立刻停止nginx的进程），QUIT（优雅的停止nginx进程）,HUP（重载配置文件），USR1（重新打开日志文件，做日志文件的切割）；这里把 USR2 和 WINCH 单独拿了出来，因为上面4个信号可以通过nginx命令行加特定的命令直接向master进程发送的，而最后两个信号只能通过kill命令向master进程发送信号，比如热部署时使用。

通常我们不直接向worker进程发送信号，因为worker进程由master进程进行管理。

nginx命令行中的信号是通过向 PID文件中的master进程号 发送信号的。



## reload重载配置文件的真相

我们向master进程发送 SIGHUP 信号 或 使用nginx -s 命令来重新读取配置文件，这时候我们会发现有时候worker进程变多了，尤其是四层代理的时候更为常见，这是因为老的worker进程没有及时退出导致的，这就涉及到立即退出和优雅的退出的区别。

### reload流程

![auqW4h](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/auqW4h.png)

![image-20220110212834103](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110212834103.png)



## 热升级的完整流程

### 热升级流程

![image-20220110213335281](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110213335281.png)

1 只替换 binary 文件是因为大部分场景下，我们新编译的nginx文件所指定的相应的配置选项，比如配置文件的目录在哪里，log的目录在哪里等必须保持和老的nginx是一致的。我们要保证配置文件能够复用。另外 binary 文件在替换时要备份。如果只覆盖 binary 文件要使用 "cp -f"命令才能替换掉。

2 向老的master进程发送USR2信号，这时候我们是没有办法通过nginx -s 来处理就是因为nginx到目前为止还没有支持这样的信号。

3 发送完USR2信号后，老的master进程会去做这样几件事：1 修改pid文件名加.oldbin后缀，这是要给新的master进程让路。2 老的master进程会用新的二进制文件启动新的master进程，此时会出现两个master进程和老的worker进程。然后新的master进程会去启动新的worker进程。

5 我们要向老的master进程发送WINCH信号，可以通过ps命令查看到老的master进程号或者自pid.oldbin文件中可以查看到老的master进程。老的master进程会优雅的关闭老worker进程。

这样热升级已经结束了，但是老的master进程一直是保存下来的，这是为了方便回滚。也就是发现新的nginx程序有问题了，因为老的master进程还在，所以通过向它发送HUP信号，相当于执行了一次reload，它会启新的worker进程，然后我们向新的master发送QUIT信号。

### 热升级具体的流程图

![T5cl87](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/T5cl87.png)



## 优雅的关闭worker进程

所谓优雅的退出指的是nginx的worker进程能够识别出当前的进程有没有在处理请求。那么nginx能不能做到这一点呢，nginx在反向代理websocket协议时，nginx是不解析它的帧的，所以这个时候nginx是没有办法识别的。nginx在做udp层的反向代理的时候，它也没有办法识别一个请求需要经历多少报文才算是结束。

不过对于http请求，nginx是可以做到的。	

## worker进程：优雅的关闭

![image-20220110215801828](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110215801828.png)

当处理的时间超过第一步中设定的worker_shutdown_timeout的时间时，进程会立即关闭。



## 网络收发与Nginx事件间的对应关系

nginx是一个事件驱动的框架。所谓事件主要指的是网络事件。

nginx每一个连接会对应两个网络事件，一个读事件，一个写事件。

**什么是网络事件？**

### 网络传输

![image-20220110221118447](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110221118447.png)

主机A --> 主机B 经历了哪些网络事件呢？

应用层里发送了一个GET请求。

到了传输层，它主要做一件事，比如我的浏览器打开了一个端口，可以从任务管理器看到。然后它会把这个端口记下来，并且把nginx打开的端口比如80也记录到传输层。

在网络层会记录下我的主机所在的IP和nginx所在服务器的公网IP

然后到链路层以后，经过以太网，到达路由器，路由器里会记录下运营商的下一端的IP，

经过广域网以后，最终跳转到主机B所在的机器中。

在这里边，**网络报文扮演了什么样的角色呢？**

### TCP流与报文

![image-20220110221831904](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110221831904.png)

我们发送的http协议报文会被切割成很多小的报文，在网络层会切掉MTU，在TCP层会考虑中间每个环节中最大的MTU值，这时候，每个报文往往只有几百字节。这个报文大小叫 MSS。**每收到一个小于MSS大小的报文时其实就是一个网络事件**。

**网络事件和日常调用接口是怎么关联呢？**

### TCP协议与非阻塞接口

![image-20220110222529912](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110222529912.png)

请求建立TCP连接事件：事实上是发送了一个TCP报文。对于NGINX来说：它是一个读事件

nginx服务器向客户端浏览器响应的时候，这是一个读事件。



## Nginx网络事件实例演示

网络报文的发送对应着Nginx的网络事件。比如Accept建立新连接其实是收到了一条读事件。

比如：访问 116.62.160.193:8080时，wireshark进行抓包：

![7LfGnd](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/7LfGnd.png)

![IRFFjm](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/IRFFjm.png)

当三次握手建立之后，linux才会去通知nginx收到了一个读事件。这个读事件对应着建立了一个新连接。所以此时，nginx调用Accept()这个方法去建立一个新的连接。



## Nginx的事件驱动模型

nginx是如何处理事件的？

### Nginx事件循环

![image-20220110224318082](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220110224318082.png)

nginx刚刚启动时，也就是打开了80端口，等待新的事件进来，这样一步往往对应着epoll中的 epoll_wait() 方法，此时nginx是出于 sleep 状态的。

当操作系统收到了一个tcp的建立连接的报文并且处理完握手流程以后，操作系统就会通知 epoll_wait() 这个阻塞方法，告诉它你可以往下走了。同时唤醒nginx的worker进程。

nginx往下走完以后就会去向操作系统要事件。操作系统会把它准备好的事件放在事件队列中，从事件队列中可以一个一个获取到我们要处理的事件。比如建立连接。

取出来以后就会处理这个事件，右边这张图就是处理事件的循环。我们发现事件队列中不为空，就把事件取出来处理。

处理事件过程中又会生成新的事件，比如我发现一个连接新建立了，我可能要添加一个超时时间，比如默认60s，60s之内浏览器没有向我请求的话，我就把这个连接关掉。生成的新的事件会放在另一个队列中，等待下一次来处理。

当所有的事件都处理完成以后，又会返回到 WAIT FOR EVENTS ON CONNECTIONS。

**知道了nginx事件循环有什么好处呢？**

**有时候我们使用第三方模块时，第三方模块可能会做大量的cpu运算，这样的计算任务会导致我处理一个事件的时间非常的长。那它就会导致后续队列中大量的事件长时间得不到处理，从而引发恶性循环，也就是它们的超时时间可能到了，大量的连接会不正常的断开。所以nginx不能容忍有些第三方模块长时间的消耗大量的cpu进行计算任务。我们可以看到，向gzip这些模块，它们都是不会一次使用大量的cpu，而是分段使用的。**



## epoll 的优劣及原理





































