## 本节话题

![image-20220112130105230](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112130105230.png)

## Prommetheus时间序列

![image-20220112130151603](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112130151603.png)

tsdb 默认只保存数据一个月

## PromQL简介

![image-20220112130346754](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112130346754.png)

示例：标签过滤器

node_cpu_seconds_total{mode=~"s.*"}

node_cpu_seconds_total{mode!~"s.*"}

## Prometheus数据模型

![6ORAuf](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/6ORAuf.png)

## 样本数据格式

![fCCrZd](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/fCCrZd.png)

## 指标名称及标签使用注意事项

![7cPYSd](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/7cPYSd.png)

## PromQL的数据类型

![UYw5WO](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/UYw5WO.png)

## 时间序列选择器（Time series Selectors）

![WhLLHf](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/WhLLHf.png)



## 向量表达式使用要点

![f3rqey](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/f3rqey.png)

## 即时向量选择器

![DfTV2X](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/DfTV2X.png)

## 匹配器（Matcher）

![NGdRt6](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/NGdRt6.png)

匹配器示例：

 node_cpu_seconds_total{cpu="0"}

 node_cpu_seconds_total{cpu="0",mode=~"i.*"}

{cpu="0",mode=~"i.*"}

**{cpu=""}  : 这是不允许的**

## 范围向量选择器

![9jdAEl](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/9jdAEl.png)





































