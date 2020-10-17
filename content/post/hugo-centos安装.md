+++
date="2020-10-16T02:00:00+08:00"
title="Hugo-Linux下安装"
tags=["Hugo"]
categories=["Hugo"]
+++

>   主题地址 :  https://github.com/flysnow-org/maupassant-hugo


1. **下载安装**

```
cd /usr/local/src
wget https://github.com/gohugoio/hugo/releases/download/v0.76.5/hugo_0.76.5_Linux-64bit.tar.gz
tar -zxvf hugo_0.76.5_Linux-64bit.tar.gz
mv ./hugo /usr/local/bin/

# 查看版本
[root@brady src]# hugo version
Hugo Static Site Generator v0.76.5-60F0725B linux/amd64 BuildDate: 2020-10-14T15:15:49Z
```

2. **新建网站**

```
[root@brady hugo]# hugo new site blog
Congratulations! Your new Hugo site is created in /phpwww/hugo/mysite.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.

```

3. 下载主题 

```
cd blog;\
git init;\
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke;\

# Edit your config.toml configuration file
# and add the Ananke theme.
echo 'theme = "ananke"' >> config.toml
```

4. **添加一篇文章**

```hugo new posts/my-first-post.md
hugo new posts/my-first-post.md 
```

5. **运行查看效果**
    `hugo server -D`

6. **使用新的Hugo maupassant主题**

    ```
      cd blog
      git clone https://github.com/rujews/maupassant-hugo themes/maupassant
    ```

 	 然后在Hugo的配置文件里config.toml(yaml,json)中进行如下配置，即可使用。

  	`theme = "maupassant"`

  	记得把你的MD文章放在content/post目录下。

7. **Hugo maupassant 主题配置**

    Hugo maupassant 主题配置也不难，是否熟悉Hugo都可以快速配置，并生成自己的网站。
    我博客的配置如下，大家可以参考。

    *config.toml*

    ```
    baseURL = "http://www.flysnow.org"
    languageCode = "zh-CN"
    title = "飞雪无情的博客"
    theme = "maupassant"
    
    [author]
      name = "飞雪无情"
    
    [params]
      author = "飞雪无情"
      subtitle = "专注于Android、Java、Go语言(golang)、移动互联网、项目管理、软件架构"
      keywords = "golang,go语言,go语言笔记,飞雪无情,java,android,博客,项目管理,python,软件架构,公众号,小程序"
      description = "专注于IT互联网，包括但不限于Go语言(golang)、Java、Android、Python、项目管理、抖音分析、软件架构等"
    ```

    

8. **Hugo maupassant 自定义菜单**

    原作者的菜单是基于Content Type实现的，扩展性很差。Hugo本身有菜单的支持，扩展性更好，所以我改为基于Hugo原生菜单的方式实现，可以无限级扩展、支持菜单排序。

    *config.toml*

    ```
    [menu]
      [[menu.main]]
        identifier = "books"
        name = "新书"
        url = "/books/"
        weight = 2
      [[menu.main]]
        identifier = "archives"
        name = "归档"
        url = "/archives/"
        weight = 3
      [[menu.main]]
        identifier = "about"
        name = "关于"
        url = "/about/"
        weight = 4
    ```

    `identifier`标志符必须是唯一的，不能重复；`weight`用于排序，值越小越靠前。

9. Hugo maupassant 友情链接

    友情链接的实现也是遵循Hugo原生的方式，参考配置如下：

    *config.toml*

    ```
    [[params.links]]
      title = "Android Gradle权威指南"
      name = "Android Gradle权威指南"
      url = "http://yuedu.baidu.com/ebook/14a722970740be1e640e9a3e"
    [[params.links]]
      title = "常用开发工具CDN镜像"
      name = "常用开发工具CDN镜像"
      url = "http://mirrors.flysnow.org/"
    ```

    >   params.links`是一个数组，所以我们可以自定义很多友情链接。`name`表示显示的链接文本，`title`表示鼠标悬停在友情链接时，显示的文本。

    

10. **Hugo maupassant 文章归档支持**

    hugo默认是不支持生成归档文件的，需要自己实现。新主题已经实现了文章归档，只需要在新建`content/archives/index.md`文件，文件内容为：


        ```title: "归档"
         description: Android资深工程师 ，Go和Java打杂师，《Android Gradle权威指南》作者，Android官方技术文档译者
         type: archives ```


​        
​    
​    > `title`和`description`都可以换成你自己的，但是`type`必须是`archives`。
​    
​    >   content/archives/index.md`表示在`content/archives/`目录下的`index.md`文件
​    
    > 这样Hugo就会自动生成`/archives/index.html`归档页面，通过类似`http://www.flysnow.org/archives/`的URL进行访问，目前的归档是按照年份进行归档， 后面可以扩展更多的归档方式。
    >
    > 

11. **其他静态文件**

      `有些不需要我们转化的静态文件，比如`robots.txt`、我们上传的附件等，这些不需要Hugo进行处理，可以直接放在`static`目录下，Hugo会原封不动的拷贝`

12. 原文地址 

      ` https://segmentfault.com/a/1190000016679032?utm_source=tag-newest `

13.  运行

     `hugo`

     会生成public目录  配置public目录到nginx 即可访问 
     
     hugo server -w 热启动 

     