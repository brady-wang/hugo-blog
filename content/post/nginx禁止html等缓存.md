+++
date="2020-10-17T10:21:00+08:00"
title="Nginx禁止html等缓存"
tags=["nginx"]
categories=["Nginx"]
+++

1. 在本地开发的时候，经常会碰到缓存引起的莫名其妙的问题，最暴力的方式就是清掉浏览器的缓存，或者使用Ctrl + F5，Shift + F5强制刷新页面。 有时候按了好几下，缓存还是清不掉，只能暂时禁用浏览器静态资源缓存了，配置如下：

    ```
    location ~.*\.(js|css|html|png|jpg)$
    {
        add_header Cache-Control no-cache;
    }   
    ```
