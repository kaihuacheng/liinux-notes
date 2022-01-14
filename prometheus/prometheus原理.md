<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/jUR4r4.png" alt="jUR4r4" style="zoom:50%;" />

## 监控体系

![image-20220112111837030](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112111837030.png)

## 著名的监控方法论

![image-20220112095705047](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112095705047.png)

![Tdgu24](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/Tdgu24.png)

### USE方法

![t9ogHM](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/t9ogHM.png)

### RED方法

![jHEs7p](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/jHEs7p.png)

## prometheus是什么？

![image-20220112100041441](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112100041441.png)

## 时序数据简介

![sFP7Ui](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/sFP7Ui.png)

## prometheus如何工作

![iAF7xa](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/iAF7xa.png)

![KPc5YO](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/KPc5YO.png)

Exporters：主机将采集的数据格式化为prometheus兼容的格式

instrumentation：主机内置了的本身就兼容prometheus格式的数据

Pushgateway：监控的目标中有些是短期任务或批处理任务，这些任务本身不可能暴露任何指标也很难通过exporters去监控它的指标的，这时候就只好基于pushgateway的方式来进行工作，借助于pushgateway的机制让这些短期任务能够送给我们的pushgateway，pushgateway暂存下来以后可以基于prometheus的pull拉取的方式来采集数据



## pull and push

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/yaJ0u3.png" alt="yaJ0u3" style="zoom:50%;" />



## Prometheus的生态组件

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/OMMNS9.png" alt="OMMNS9" style="zoom:50%;" />

promethesu：prometheus server

alertmanager：外部的组件，实现告警信息

application：客户端库，可以直接输出prometheus支持的指标格式的，不支持的就靠exporters组件来实现

exporters：

UI：promql 表达式展示，但是丑爆了

dashboard：外置的第三方的组件来作为展示界面，比如 grafana



prometheus 四个主要组件：

scaping：主机数据的采集是由主机自己完成的，这个组件叫scaping，定期的去采集数据

storage：内置的tsdb，自我开发的，开源

rules and alerts接口：promql语言来记录规则

service discovery：内置了基于dns的，基于文件的，基于kubernetes的等市面上各种服务发现和注册总线的工具

![9IHQne](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/9IHQne.png)

## prometheus数据模型

![IP6NHp](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/IP6NHp.png)

## 指标类型（Metric Type）

![image-20220112103209203](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112103209203.png)

## 作业（job）和实例（instance）

![image-20220112103345480](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112103345480.png)

## PromQL

![image-20220112103436063](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112103436063.png)

## Instrumentation (程序仪表)

![GKR26c](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/GKR26c.png)

## Exporters

![9ysI6X](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/9ysI6X.png)

## Alerts

![image-20220112103716419](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112103716419.png)

## prometheus	 architecture

![ZRpk4x](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/ZRpk4x.png)

## node_exporter安装完以后运行于后台

![BT0kyZ](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/BT0kyZ.png)

















