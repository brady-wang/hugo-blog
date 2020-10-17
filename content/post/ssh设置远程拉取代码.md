---

date: "2020-10-17T13:54:44+08:00"

title: "ssh设置远程拉取代码"

tags: ["ssh"]

categories: ["ssh"]

---



## 原因

hugo本地代码提交到github  

服务器再拉取,然后线上网站页面才会生效  每次都要ssh -p 22 root@xx.xx.xxx.xx 到阿里云服务器,然后cd /www/blog   git pull 而且阿里云服务器,隔一段时间不动,就会自己退出 有没有什么方式快速让远程服务器拉取到代码,

-  一种方式jenkins搭建 太麻烦

## 我的解决方式

首先设置免密登录  ssh root 就能登录,然后 编辑ssh文件

**vim pull.sh** 

``` shell
#/bin/bash

cd /phpwww/hugo-blog
git pull origin master
```

*chmod +x pull.sh*



**本地执行命令** 

``` ssh
ssh root "sh pull.sh"
```

即可自动拉取代码 一条就执行完了,而且不用远程登录进去