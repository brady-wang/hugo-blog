---
date: "2020-10-18T10:02:01+08:00"
title: "ssh修改默认端口"
tags: ["ssh"]
categories: ["ssh"]
---



## 修改ssh端口

vi /etc/ssh/sshd_config

#Port 22

默认端口为22,为了避免被扫描,去掉#,改成一个其他的端口,比如45632
保存后重启sshd服务

service sshd restart