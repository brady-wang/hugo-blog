---

date: "2020-10-17T13:43:31+08:00"

title: "ssh免密登录"

tags: ["ssh"]

categories: ["ssh"]

---


## 原因

每次登录都要ssh -p wang@xx.xx.xx.xx 

虽然做了公钥验证 https://www.cnblogs.com/php-linux/p/10795913.html

不需要输入密码，但是每次还是要输入域名，有点麻烦



## 设置方式 

进入到.ssh目录 也是就是 id_rsa.pub目录

 

vim config

```
Host wang  这个是个标识 不是远程用户
    HostName  ip地址
    Port 22
    User wang
    IdentityFile ~/.ssh/id_rsa
```

ssh wang 即可登录

　

如果还想要快速用root登录

```shell
Host wang
    HostName 120.79.xx.xx
    Port 22
    User wang
    IdentityFile ~/.ssh/id_rsa
 
Host root
    HostName 120.79.xx.xx
    Port 22
    User root
    IdentityFile ~/.ssh/id_rsa         
```

 

## 效果 

执行 ssh root 即可直接登录到服务器