+++
date="2020-11-15T10:31:08+08:00"
title="HAproxy连接Mycat集群docker-compose版"
tags=["HAproxy"]
categories=["HAproxy"]
toc=true

+++



# 1. 前言

> 设置一个统一的入口来控制`mycat`集群，在这里我们使用到了`HAproxy`来做负载均衡和请求转发。

# 2. 架构图

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200211153601387.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxOTY3ODk5,size_16,color_FFFFFF,t_70#pic_center)

# 3. 配置HAproxy

```bash
# 创建文件夹
cd /usr/local/docker
mkdir haproxy/etc/haproxy -p
# 创建配置文件
cd /usr/local/docker/haproxy/etc/haproxy
vim haproxy.cfg
## 输入下列内容 
1234567
global
	#工作目录
	chroot /usr/local/etc/haproxy
	#日志文件，使用rsyslog服务中local5日志设备（/var/log/local5），等级info
	log 127.0.0.1 local5 info
	#守护进程运行
	daemon

defaults
	log	global
	mode	http
	#日志格式
	option	httplog
	#日志中不记录负载均衡的心跳检测记录
	option	dontlognull
    #连接超时（毫秒）
	timeout connect 5000
    #客户端超时（毫秒）
	timeout client  50000
	#服务器超时（毫秒）
    timeout server  50000

#监控界面	
listen  admin_stats
	#监控界面的访问的IP和端口(对应前端页面的端口访问，可以修改)
	bind  0.0.0.0:8888
	#访问协议
    mode        http
	#URI相对地址
    stats uri   /dbs
	#统计报告格式
    stats realm     Global\ statistics
	#登陆帐户信息
    stats auth  admin:123456
#数据库负载均衡
listen  proxy-mysql
	#访问的IP和端口
	bind  0.0.0.0:8889  
    #网络协议
	mode  tcp
	#负载均衡算法（轮询算法）
	#轮询算法：roundrobin
	#权重算法：static-rr
	#最少连接算法：leastconn
	#请求源IP算法：source 
    balance  roundrobin
	#日志格式
    option  tcplog
    #对mycat节点进行负载均衡

    server  mycat_1 mycat:8066 check port  8066 weight 1 maxconn 2000
    server  mycat_2 mycat02:8066 check port 8066  weight 1 maxconn 2000
	#使用keepalive检测死链
    option  tcpka
123456789101112131415161718192021222324252627282930313233343536373839404142434445464748495051525354
```

# 4. docker-compose.yml

```
cd /usr/local/docker/haproxy`
`vim docker-compose.yml
version: '3'
services:
  haproxy:
    restart: always
    image: haproxy:2.1.2
    container_name: haproxy
    ports:
      - 8888:8888 # 端口来源于haproxy.cfg里面配置
      - 8889:8889 # 统一的端口对mycat， haproxy.cfg里面配置
    volumes:
      - ./etc/haproxy:/usr/local/etc/haproxy:ro #ro 表示仅仅只能读

networks:
  default:
    external:
      name: mysql_network
12345678910111213141516
```

# 5. 效果图

## 5.1 容器效果

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200211154807172.png#pic_center)

## 5.2 节点安全图

ip:port/dbs
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200211155209744.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxOTY3ODk5,size_16,color_FFFFFF,t_70#pic_center)

## 5.3 navicat连接图

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200211155326851.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxOTY3ODk5,size_16,color_FFFFFF,t_70)

# 6. 补充说明

到现在你会发现。我们出现了一个新的负载均衡软件。
那么我们来简单说说两者的区别。

1. `nginx`是一个`HTTP`服务器/反向代理服务器及电子邮件（`IMAP/POP3`）代理服务器。
2. `Nginx`跟 `HAproxy`其实他们两个的定位是有所不同的，`Nginx`的定位是一个`server`，`HAproxy`的定位是一个`load balancer`.
3. `HAproxy`负载均衡性能比`nginx`好，有一个状态统计页面，官方支持会话保持、健康检查等