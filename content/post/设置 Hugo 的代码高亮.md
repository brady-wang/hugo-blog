+++
date="2020-10-17T08:00:22+08:00"
title="设置Hugo的代码高亮"
tags=["hugo"]
categories=["Hugo"]
toc=true
+++

## 前提条件

首先我们要保证 `Hugo` 的版本是高于 `v0.65.0` 的，查询方法如下

```shell
$ hugo version
Hugo Static Site Generator v0.70.0-7F47B99E windows/amd64 BuildDate: 2020-05-06T11:17:50Z
```

上面查询，我的版本是 `v0.70.0` 如果你的版本低于 `v0.65.0` 则不支持我们今天要设置的代码高亮，请先升级版本。

`Hugo` 在 `v0.65.0` 版本之后使用了 [Chroma](https://github.com/alecthomas/chroma) 代码高亮插件，它是一个 Go 语言实现的非常漂亮并能快速生成的代码高亮工具。

## 如何配置

默认的代码高亮配置文件如下，你可以复制到你的配置文件内进行修改：

yaml 格式的配置文件：

``` yaml
markup:
  highlight:
    codeFences: true
    guessSyntax: false
    hl_Lines: ""
    lineNoStart: 1
    lineNos: false
    lineNumbersInTable: true
    noClasses: true
    style: monokai
    tabWidth: 4
```

toml 格式的配置文件：

``` toml
[markup]
  [markup.highlight]
    anchorLineNos = false
    codeFences = true
    guessSyntax = true
    hl_Lines = ""
    lineAnchors = ""
    lineNoStart =1
    lineNos = true
    lineNumbersInTable = true
    noClasses = true
    style = "monokai"
    tabWidth = 4
```

json 格式的配置文件：

``` json
{
    "markup":{
        "highlight":{
            "codeFences":true,
            "guessSyntax":false,
            "hl_Lines":"",
            "lineNoStart":1,
            "lineNos":false,
            "lineNumbersInTable":true,
            "noClasses":true,
            "style":"monokai",
            "tabWidth":4
        }
    }
}
```

配置文件中各个设置项的含义如下：

- codeFences：代码围栏功能，这个功能一般都要设为 true 的，不然很难看，就是干巴巴的-代码文字，没有颜色。
- guessSyntax：猜测语法，这个功能建议设置为 true, 如果你没有设置要显示的语言则会自动匹配。
- hl_Lines：高亮的行号，一般这个不设置，因为每个代码块我们可能希望让高亮的地方不一样。
- lineNoStart：行号从编号几开始，一般从 1 开始。
- lineNos：是否显示行号，我比较喜欢显示，所以我设置的为 true.
- lineNumbersInTable：使用表来格式化行号和代码,而不是 标签。这个属性一般设置为 true.
- noClasses：使用 class 标签，而不是内嵌的内联样式