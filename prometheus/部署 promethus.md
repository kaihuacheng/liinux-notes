prometheus官方站点：prometheus.io

下载prometheus：prometheus.io/download

## 在 CentOS上使用rpm包

![image-20220112104611219](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112104611219.png)

prometheus下载路径：https://github.com/prometheus/prometheus/releases/download/v2.32.1/prometheus-2.32.1.linux-amd64.tar.gz

alertmanager下载路径：https://github.com/prometheus/alertmanager/releases/download/v0.23.0/alertmanager-0.23.0.linux-amd64.tar.gz

mysqld_exporter下载路径：https://github.com/prometheus/mysqld_exporter/releases/download/v0.13.0/mysqld_exporter-0.13.0.linux-amd64.tar.gz

node_exporter下载路径：https://github.com/prometheus/node_exporter/releases/download/v1.3.1/node_exporter-1.3.1.linux-amd64.tar.gz



prometheus内置的采集指标查看：

- 启动prometheus：./prometheus
- 访问：http://192.168.2.15:9090/metrics

![image-20220112110645909](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112110645909.png)



内建的UI界面：

直接访问：http://192.168.2.15:9090/

![image-20220112111053167](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112111053167.png)

采集指标示例：

![czxN8X](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/czxN8X.png)



指标过滤器：加上响应码是302的指标：

![k3vzFz](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/k3vzFz.png)

## 客户端库

![UFG4vU](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/UFG4vU.png)

## Exporter 基础

![DRFCCy](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/DRFCCy.png)



## Exporter 的Unit 文件示例

![3Gh4vr](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/3Gh4vr.png)

## Node Exporter 的指标

![image-20220112124941475](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112124941475.png)

## 适用于主机监控的USE方法

![image-20220112125502264](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112125502264.png)

监控自身指标：比如 cpu利用率

```
tar xf node_exporters...
cd node_exporters
cp node_exporter /usr/local/bin
./node_exporter
```

node_exporter默认监听在 9100 端口上

重启 prometheus 服务，可以看到 两个 nodes 显示在 UI 中了：

![image-20220112122351522](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112122351522.png)

现在我们可以过滤节点级的数据：

比如监控 CPU 空闲比例：

![DTFRtu](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/DTFRtu.png)

## CPU 使用率

![hKZqyC](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/hKZqyC.png)

irate：灵敏度非常高的速率计算函数

## CPU 的饱和度

![image-20220112123941442](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112123941442.png)



## 内存使用率

![ks7Cgg](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/ks7Cgg.png)



## MySQL exporter

![image-20220112124625143](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112124625143.png)



