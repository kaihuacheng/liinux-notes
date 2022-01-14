#  

Nginx 背景简介

## 背景介绍

![image-20220112144124427](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112144124427.png)





## 名词解释

![ldJHt1](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/ldJHt1.png)

![XggL1n](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/XggL1n.png)

![x1fUyR](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/x1fUyR.png)

正向代理：服务端禁止掉客户端访问的某些类数据，那么客户端想继续访问怎么办，那么就通过代理，由代理去想服务端请求，服务端响应给代理，再由代理响应给客户端，这样客户端就能访问到数据了。

## 常见服务器对比

![T0Wy8r](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/T0Wy8r.png)

nginx官网点击about中的链接可以浏览到

![image-20220112145458332](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112145458332.png)

![wpPqTL](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/wpPqTL.png)

一台空载的tomcat最高并发访问是 200到300左右

nginx单台服务器官网公布的数据显示可以达到5万甚至更多的并发。

![image-20220112145740790](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112145740790.png)

![DuEWhv](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/DuEWhv.png)

![u7RAkN](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/u7RAkN.png)

Google Servers现在是闭源的，所以市面上很少看到有使用的



## Nginx的优点

![ZFUwd5](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/ZFUwd5.png)

![image-20220112150322056](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112150322056.png)

![rt5kta](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/rt5kta.png)

![seWy67](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/seWy67.png)



## Nginx的功能特性及常用功能

![S2qtn2](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/S2qtn2.png)

![mhxdU5](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/mhxdU5.png)

![aDqhuW](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/aDqhuW.png)

![image-20220112151147149](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112151147149.png)

![II0AQw](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/II0AQw.png)

## Nginx 的官方简介

![image-20220112151419483](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112151419483.png)

更老版本nginx还有一个下载路径：nginx.org/download/

![NQaiRL](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/NQaiRL.png)

![RXOM6w](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/RXOM6w.png)

![Cc1pBB](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/Cc1pBB.png)

## Nginx系统环境准备

![nYcn2D](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/nYcn2D.png)

xsheel和SecureCRT需要收取一定的费用，MobaXterm有免费版的

![image-20220112152715431](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112152715431.png)

![image-20220112153210947](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112153210947.png)

![image-20220112153226582](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112153226582.png)

![image-20220112153340665](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112153340665.png)

![V3v19c](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/V3v19c.png)

## Nginx安装方式介绍及源码安装的准备工作

![ebKk1l](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/ebKk1l.png)

![xF8VZ4](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/xF8VZ4.png)

![3WsSeo](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/3WsSeo.png)

![image-20220112161941567](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112161941567.png)

## 通过 Nginx 源码简单安装

![image-20220112162518391](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112162518391.png)

![JKml0F](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/JKml0F.png)

## 通过 yum 安装 nginx

![jJc1ES](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/jJc1ES.png)

![lX0qAY](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/lX0qAY.png)

![f6yrq3](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/f6yrq3.png)

## 简单源码安装和yum安装的区别

![image-20220112163431615](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112163431615.png)



## 通过 Nginx 源码复杂安装

![image-20220112164443985](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112164443985.png)

![I6LUOE](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/I6LUOE.png)

![itFgPT](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/itFgPT.png)

![2y145k](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/2y145k.png)

![EaLl3Z](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/EaLl3Z.png)



## Nginx的目录结构分析

![image-20220112170643740](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112170643740.png)

![image-20220112170919956](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112170919956.png)

![image-20220112171745646](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112171745646.png)

![oj5RW7](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/oj5RW7.png)



## Nginx服务器启停方式介绍

![image-20220112171901253](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112171901253.png)



## Nginx 服务的信号控制

















