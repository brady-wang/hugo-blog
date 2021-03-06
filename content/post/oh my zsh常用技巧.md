---
date:  "2020-10-18T12:36:00+08:00"

title: "oh my zsh 常用插件"

tags: ["zsh","oh my zsh"]

categories: ["shell"]

---

目前已经有的自带插件在官网Github中可以看到，https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins
 凡是这里有的，都可以立刻生效。

## autojump

安装地址 https://blog.csdn.net/shenhonglei1234/article/details/106674554

https://blog.csdn.net/java_road_far/article/details/101324677

autojump和z插件关系 

autojump 需要单独安装，之后在 zshrc 文件启用，才能使用。

Z 是 oh-my-zsh 内置的插件，不需要再安装其他的软件。直接在zshrc 文件启用即可。



## Zsh命令语法高亮插件 [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)

将插件下载到oh my zsh的插件目录下的该新建插件同名文件夹中



```shell
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

编辑`~/.zshrc`文件将然后将插件引用命令写入该文件最后一行（必须）



## wd插件

wd 插件是我比较喜欢的一个，它的作用就是能够快速的切换到常用的目录。我们用命令行时经常会遇到这样一种情况，我们常用的目录就那么几个，而这些目录有时候会再很深的层级中。使用 cd 命令在这些深层级目录中切换就比较耗费时间了。

wd 插件正是为了解决这个问题，比如我们有一个常用的目录 /usr/nginx/www/html，我们首先进入到这个目录中，然后输入

```
wd add web
```

这个命令相当于给当前目录做了一个标识，标识名叫做 `web` ，我们下次如果再想进入这个目录，只需输入： 

```
wd web
```

这样就可以完成目录切换了，非常方便。

它的原理并不复杂，它维护了一个标识和实际路径的映射表，我们使用 wd add 命令可以添加新的映射，可以使用 wd rm 命令删除已有的映射，还可以使用 wd show 命令查看现有的映射。

这个简单的插件解决了一个很实际的问题，推荐使用。 wd 插件的更多内容可以查看它的 github 主页： https://github.com/mfaerevaag/wd



## web-search插件 

它能让我们在命令行中使用搜索引擎进行搜索。比如 `google swift` 这个命令就可以使用 Google 搜索 swift 关键字。 

web-search 插件在默认情况下没有开启，所以我们需要做一点小工作把它打开。

1. 打开 ~/.zshrc 文件。
2. 找到 `plugins=(git)` 这行定义。 
3. 把它修改成 `plugins=(git web-search)`

然后重新开启一个命令行窗口我们就可以使用 web-content 的功能了。

我们可以使用 google 搜索：

```
google 你好
```

这样会打开 google 搜索 “swift 学习” 这个关键字。

web-content 同样集成了 baidu, bing 这些搜索引擎：

```shell
baidu 你好
bing 你好
```

只需在命令行中输入要搜索的关键字和搜索引擎，就可以进行搜索了，还是很方便的。



## last-working-dir

last-working-dir 插件，可以记录上一次退出命令行时候的所在路径，并且在下一次启动命令行的时候自动恢复到上一次所在的路径。这一切不需要我们进行任何操作，全部都是自动完成的。只需要在 .zshrc 文件中将插件开启即可。



## catimg

catimg 这个命令将图片文件的内容输出到命令行, 比如：

## zsh-syntax-highlighting 

语法高亮插件

github地址: https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting 



## Zsh命令自动补全插件 zsh-autosuggestions

github地址: https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md#oh-my-zsh

这里利用Oh my zsh的方法安装。直接一句话命令行里下载并移动到oh my zsh目录中：

git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions 

然后在~/.zshrc文件中找到plugins数组，加入zsh-autosuggestions名字，重新打开终端即可。



### extract

功能强大的解压插件，所有类型的文件解压一个命令`x`全搞定，再也不需要去记`tar`后面到底是哪几个参数了。

## z

这个和autojump 功能基本一样,感觉按j比z舒服,强大的目录自动跳转命令，会记忆你曾经进入过的目录，用模糊匹配快速进入你想要的目录。

## sublime

平时使用sublime比较多，该插件可以使用命令行打开sublime。
常用命令如下：

```bash
st          # 直接打开sublime
st file_a   # 用sublime打开文件 file
st dir_a    # 用sublime打开目录 dir
stt         # 在sublime打开当前目录，相当于 st .
```



## 我的配置

vim ~/.zshrc

```zsh
ZSH_THEME="crunch" # cloud bira 

plugins=(
    git
    navi 
    wd
    incr
    autojump
    web-search
    last-working-dir
    zsh-syntax-highlighting
    sublime
    extract
    z
    docker
    docker-compose
    zsh-autosuggestions
)
```



## 其他插件文章

https://hufangyun.com/2017/zsh-plugin/



### powerlevel10k 插件安装

```
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Users in mainland China can use the official mirror on gitee.com for faster download.
中国大陆用户可以使用 gitee.com 上的官方镜像加速下载.

```
git clone --depth=1 https://gitee.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`.

​	 修改样式: p10k configure

## centos7 下安装

```shell
plugins=(
        git
        autojump
        last-working-dir
        extract
        docker
        docker-compose
        zsh-autosuggestions
        zsh-navigation-tools
        wd
)
```

### centos7下 zsh-autosuggestions 要安装

git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions 

### autojump也要自己安装

wget https://github.com/downloads/joelthelion/autojump/autojump_v21.1.2.tar.gz 

解压

python install.py

安装提示复制 东西到zshrc文件最后

```
Please add the line to ~/.zshrc :

[[ -s ~/.autojump/etc/profile.d/autojump.sh ]] && . ~/.autojump/etc/profile.d/autojump.sh

You need to run 'source ~/.zshrc' before you can start using autojump. To remove autojump, run './uninstall.sh'
```

生效 

```shell
source ~/.zshrc
```

## centos8 bash- chsh command not found

安装oh-my-zsh 修改bash发现

usr/bin下没有chsh

dnf新的包管理工具,类似yum

sudo dnf update 

```bash
$ sudo dnf -q provides '*/chsh'



util-linux-user-2.32.1-17.el8.x86_64 : libuser based util-linux utilities
```

可知chsh在package util-linux-user中

dnf install:

```bash
sudo dnf install util-linux-user
```

