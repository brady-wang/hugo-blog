+++

date="2020-10-16"
title="linux常用命令"
tags=["linux"]
categories=["运维"]
toc=true
+++



## linux
- 查看ip占用
    - netstat -tlunp|grep 80
- 杀死指定ip占用端口
    `sudo kill -9 $(lsof -i:18309 -t)`
- 查看程序是否启动
    `ps -ef|grep redis`

---

## soft 
- 根据表生成实体 
    - `php bin/swoft entity:gen table=area_agent`


## git
- 生成ssh 
    - ssh-keygen -t rsa