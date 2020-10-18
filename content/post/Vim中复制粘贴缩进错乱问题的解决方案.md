---
date: "2020-10-18T09:54:16+08:00"
title: "Vim中复制粘贴缩进错乱问题"
tags: ["vim"]
categories: ["vim"]
---



这是一则记录贴，防止小技巧遗忘。

不知道大家是否会有这种困扰，例如在Android Studio有一段缩进优美的代码实现，例如：

```java
public void sayHello() {
    String msg = "Hello Vim Paste Mode";
    System.out.println(msg);
}
```

当你把这段缩进优美的代码直接ctrl+c，ctrl+v到Vim的时候，就会出现代码丢失和缩进错乱等情况。



# **解决方案**

vim进入paste模式，命令如下：

```bash
:set paste1
```

进入paste模式之后，再按i进入插入模式，进行复制、粘贴就很正常了。 

命令模式下，输入

```bash
:set nopaste1
```

解除paste模式。

paste模式主要帮我们做了如下事情：

- textwidth设置为0
- wrapmargin设置为0
- set noai
- set nosi
- softtabstop设置为0
- revins重置
- ruler重置
- showmatch重置
- formatoptions使用空值