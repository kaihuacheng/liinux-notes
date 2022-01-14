# Python概述、环境搭建

![image-20220113120844438](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113120844438.png)

 ![image-20220113120924153](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113120924153.png)

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113120946202.png" alt="image-20220113120946202" style="zoom:67%;" />

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113121110221.png" alt="image-20220113121110221" style="zoom:67%;" />

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/fkBHkP.png" alt="fkBHkP" style="zoom:67%;" />

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/GNX4GK.png" alt="GNX4GK" style="zoom:67%;" />

**或者使用如下方式安装：**

1.下载pyenv源码

```
git clone https://gitee.com/krypln/pyenv.git  ~/.pyenv
```

2.将pyenv 的路径写入配置文件

```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc 
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n eval "$(pyenv init -)"\nfi' >> ~/.bashrc 
exec $SHELL
```

3.安装完成

```
pyenv versions
```

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/Dr5no6.png" alt="Dr5no6" style="zoom:67%;" />

pyenv install -l

pyenv install 3.5.3

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/PprCBL.png" alt="PprCBL" style="zoom:67%;" />

```
或者使用如下方法安装python：
cd ./~.pyenv/cache
wget https://mirrors.huaweicloud.com/python/3.8.6/Python-3.8.6.tar.xz
 
#安装python编译所需第三方库
sudo yum install zlib-devel bzip2 bzip2-devel readline-devel sqlite sqlite-devel openssl-devel xz xz-devel libffi-devel git wget
 
#编译安装
pyenv install 3.8.6<br><br>#全局使用3.8.6<br>pyenv global 3.8.6</em></em>
```



<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/s7cU4S.png" alt="s7cU4S" style="zoom:67%;" />

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/d3RgrZ.png" alt="d3RgrZ" style="zoom:67%;" />

c

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/warRPg.png" alt="warRPg" style="zoom:67%;" />

![6uheBS](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/6uheBS.png)

```
安装 pyenv-virtualenv 插件：
git clone https://gitee.com/krypln/pyenv-virtualenv.git  $(pyenv root)/plugins/pyenv-virtualenv
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
exec $SHELL
```

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/Eycwo6.png" alt="Eycwo6" style="zoom:67%;" />

在 虚拟空间中安装redis：pip install redis

/在 home/python/.pyenv/versions/mysql01/lib/python3.6/site-packages 中可以看到redis目录

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/eDsQNK.png" alt="eDsQNK" style="zoom:67%;" />

 <img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/bYb5b2.png" alt="bYb5b2" style="zoom:67%;" />

```
jupyter安装后测试：
jupyter notebook password 设置一个密码
jupyter notebook --ip=0.0.0.0 --no-browser
```

![Yt0Z9i](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/Yt0Z9i.png)

**如果出现"ModuleNotFoundError: No module named '_ctypes'"的错误。**

Python3中有个内置模块叫ctypes，它是Python3的外部函数库模块，它提供兼容C语言的数据类型，并通过它调用Linux系统下的共享库(Shared library)，此模块需要使用CentOS7系统中外部函数库(Foreign function library)的开发链接库(头文件和链接库)。
由于在CentOS7系统中没有安装外部函数库(libffi)的开发链接库软件包，所以在安装pip的时候就报了"ModuleNotFoundError: No module named '_ctypes'"的错误。

####  步骤

1. 安装外部函数库(libffi)

	`yum install libffi-devel -y`

2. 重新安装python

	`pyenv install 3.8.6`

3. 用pip3 Install 安装需要的包

	`pip3 install jupyter`

![LvlYXq](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/LvlYXq.png)

![RwQmMf](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/RwQmMf.png)

![WSwHGI](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/WSwHGI.png)

![KA1ofZ](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/KA1ofZ.png)

![vsyoae](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/vsyoae.png)

![szt1je](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/szt1je.png)

![image-20220113151047404](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113151047404.png)

![image-20220113151442216](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113151442216.png)

