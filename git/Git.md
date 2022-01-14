# 	Git分布式版本控制工具

## 目标

![Ouwyz8](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/Ouwyz8.png)

## 概述	

![image-20220112185732014](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112185732014.png)

![image-20220112191544848](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112191544848.png)

![4tDcUh](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/4tDcUh.png)

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112191822063.png" alt="image-20220112191822063" style="zoom:67%;" />

<img src="https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/GChGUh.png" alt="GChGUh" style="zoom: 67%;" />

![image-20220112192906293](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112192906293.png)

## Git安装与常用命令

![image-20220112193109076](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112193109076.png)

![28d3gg](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/28d3gg.png)

![image-20220112193450370](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112193450370.png)

![1m75RQ](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/1m75RQ.png)

![yPnu0v](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/yPnu0v.png)

![image-20220112203146690](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112203146690.png)

![kvcd0l](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/kvcd0l.png)

![HJtM0P](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/HJtM0P.png)

如果是 linux 系统直接 yum 安装 git 即可

```
yum install git -y
cd git
git init
git config --global user.name "node5.ckh.com"
git config --global user.email "2098485895@qq.com"
```

```
[root@node1 git]# git config --global user.name
node5.ckh.com
[root@node1 git]# git config --global user.email
2098485895@qq.com
```

![image-20220112203643144](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112203643144.png)

![image-20220112204813058](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112204813058.png)

![8Rp3B0](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/8Rp3B0.png)

![image-20220112205442810](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112205442810.png)

```
git reflog   查看以前的记录
```

![vZAFsD](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/vZAFsD.png)

```
添加 .gitignore 文件，里面添加文件就会忽略管理
```

![2RQwkN](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/2RQwkN.png)

 ![OVp9xS](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/OVp9xS.png)

![image-20220112214349557](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112214349557.png)

![image-20220112214528931](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112214528931.png)

![image-20220112215122855](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112215122855.png)



## Git 远程仓库

![image-20220112221042250](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112221042250.png)

![image-20220112222333116](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112222333116.png)

![image-20220112221750585](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112221750585.png)

![FWNM1J](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/FWNM1J.png)



```
[root@node1 git]# git remote add origin git@gitee.com:chengkaihua/testgit.git
[root@node1 git]# git remote
origin
[root@node1 git]# git push origin master
Counting objects: 14, done.
Compressing objects: 100% (6/6), done.
Writing objects: 100% (14/14), 1017 bytes | 0 bytes/s, done.
Total 14 (delta 1), reused 0 (delta 0)
remote: Powered by GITEE.COM [GNK-6.2]
To git@gitee.com:chengkaihua/testgit.git
 * [new branch]      master -> master
```

![image-20220112225031807](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220112225031807.png)

![bBUN5X](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/bBUN5X.png)



![P9exyC](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/P9exyC.png)

![image-20220113084734543](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113084734543.png)



![2b1077](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/2b1077.png)

## 在 Idea中使用Git

![image-20220113090327300](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113090327300.png)

![image-20220113090516536](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113090516536.png)

.ignore文件

![t30TZj](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/t30TZj.png)

![wQzCpO](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/wQzCpO.png)

![C4RV4a](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/C4RV4a.png)

![image-20220113092631458](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113092631458.png)

![image-20220113092647442](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113092647442.png)

![vECdsG](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/vECdsG.png)





![image-20220113092234008](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113092234008.png)

![image-20220113092441948](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/image-20220113092441948.png)



![XaPa7E](https://cdn.jsdelivr.net/gh/kaihuacheng/images@master/uPic/XaPa7E.png)





























