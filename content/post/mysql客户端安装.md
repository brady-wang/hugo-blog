+++
date="2020-11-14T23:17:34+08:00"
title="mysql客户端连接"
tags=["mysql"]
categories=["mysql"]

+++

## 客户端安装

```
安装mysql客户端
yum install mysql  -y
 
连接目标主机mysql
mysql -h192.168.43.119 -uroot -p1234
 
查看数据库
show databases;
 
使用test数据库
use test
 
查询dept表
select * fom dept ;
 
退出连接
exit;
```



## 远程连接

本人在远程机器101.200.152.192，利用docker创建两个数据库，端口号分别为3307,3308, 如要在本地机器上远程登陆3307的mysql,

则命令如下：

`mysql -u root -P 3307 -h 101.200.152.192 -p`

