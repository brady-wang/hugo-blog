---

date: "2020-10-18T10:05:06+08:00"
title: "ssh防御暴力破解"
tags: ["ssh"]
categories: ["ssh"]

---



托管在阿里云的机器我们通常都用SSH方式来远程管理.但是经常可以发现log-watch的日志中有大量试探登录的

信息,为了我们的主机安全,有必要想个方法来阻挡这些可恨的"HACKER"

有很多办法来阻挡这些密码尝试

1. 修改端口
2. 健壮的密码
3. RSA公钥认证

 

##  vi /etc/ssh/sshd_config
#Port 22
默认端口为22,为了避免被扫描,去掉#,改成一个其他的端口,比如45632
保存后重启sshd服务.service sshd restart

## 增加密码复杂
没什么可说的,密码的复杂性可以增加破解的难度,大小写混合加上数字并且有足够的密码长度就比较安全了,唯一的问题就是要牢记密码. 

 
## 使用公钥登录 
默认的登录方式是password,如果需要用RSA公钥登录,需要先创建RSA Key
\#ssh-keygen -t rsa -b 1024
会生成私钥/home/username/.ssh/id_rsa
同时生成公钥/home/username/.ssh/id_rsa.pub
输入一个加密短语(也可省略)

修改sshd 设置,编辑/etc/ssh/sshd_config
'PasswordAuthentication no'
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile   .ssh/id_rsa.pub
 
将公钥下载到本地计算机,然后在ssh客户端软件Secure CRT中设置好,就可以登录了

