---

date: "2020-10-18T09:32:01+08:00"

title: "vim新手节约时间十个技巧"

tags: ["vim"]

categories: ["vim"]

toc: true 

---



**Vim 是很多开发者的首选编辑器，通过设置正确的命令和快捷方式，它可以帮你更快的完成工作。这篇文章我们为 Vim 新手提供一些快捷键等方面的小技巧，帮你提升工作效率。**

 

## 配置 vimrc

当我最初使用 vim 的时候，我浪费了好多时间来缩进代码，我不知道通过修改 Vim 的 .vimrc 配置文件来实现代码缩进、语法高亮、显示行号等功能。

在你的 Home 目录下创建一个 .vimrc 文件，添加下面的代码来设置行号、代码缩进等。

``` shell
	set number       # 显示行号 
	set autoindent     # 自动缩进 
	set nowrap       # 不换行
```


在.vimrc中添加以下代码后，重启vim即可实现按TAB产生4个空格：
```set ts=4 (注：ts是tabstop的缩写，设TAB宽4个空格)
set expandtab
```

对于已保存的文件，可以使用下面的方法进行空格和TAB的替换：
**TAB替换为空格：**
```:set ts=4
:set expandtab
:%retab!
```

**空格替换为TAB：**

``` shell 
:set ts=4
:set noexpandtab
:%retab!
```

**加!是用于处理非空白字符之后的TAB，即所有的TAB，若不加!，则只处理行首的TAB。**



## 不关闭终端退出编辑器

使用 Vim 编辑器保存并退出编辑状态是一件轻而易举的事，你只需记住按 ESC 键切换到正常模式，然后输入冒号(:)，之后输入 wq 即可实现保存并退出。

``` shell 
	: wq
```

如果不想保存，则按 ESC 键切换到正常模式，然后输入冒号(:)，之后输入 q! 即可。

``` shell 
: q!
```



## 粘贴进vim 不让格式错乱

经常需要粘贴一段代码到vim ,但是进去后换行完全乱了 
非插入模式下 输入下面,后面粘贴的就不会错乱了
```
:paste
```



## 删除一行或多行

通过退格键(Backspace)来删除一行代码显然是太麻烦了。可以通过切换到正常模式(编辑模式下按 ESC 键)来进行操作：

dd ： (输入两次 d，下同)删除当前行；5dd ：删除当前行开始的5行； 

dG ：(先输入d，然后按 shift 键输入 g)删除当前行至最后一行的所以行。



## 复制粘贴一块代码

你可能经常需要复制一行或一大块代码，使用 Vim 快捷键来实现此功能是非常简单的：

 按 Esc 切换到正常模式；
 把光标移到你需要复制的代码行首； 
 按 V 选择整行，可移动光标选择多行； 
 按 d 剪切或按 y 复制选择的代码； 
 移动光标到你需要粘贴的位置，按 p 粘贴代码到光标后的位置，或按 P 粘贴到光标前。



## 撤销与重做


在使用 Vim 或其他编辑器的时候，你可能经常需要对某些修改进行撤销或重做。在 Vim 中，你可以切换到正常模式，按 u 来撤销操作，按 Ctrl+r 来重做。



## 代码注释

**代码注释：**

- 按 Ctrl+v 切换到可视化模式； 

- 移动光标(j 或 k)选中需要注释的行的开头； 

- 按大写 I，然后输入注释符，如 #； 最后按 Esc。

**取消注释：**

- 按 Ctrl+v 切换到可视化模式； 

- 按 j 或 k 选择要删除的注释符； 

- 按 d 或 x 删除注释符

 

如果使用 // 符号注释，则取消注释时需进行两遍操作。



## 搜索

搜索在很多时候都是一个非常重要的功能。在文件中搜索一个特定的词，可以切换到正常模式，然后输入斜线( / )，之后跟上要搜索的词，回车即可。

`/word-to-be-searched`

按 n 显示下一个搜索结果，按 N 显示上一个搜索结果。

从最后开始搜索 按下 Shift+g 

 ?word-to-be-search



## 把外部文件读入 Vim

我开始使用 Vim 的时候，经常会打开一个文件、复制内容、关闭文件、打开另一个文件、然后粘贴进去复制到内容。其实 Vim 中读取另一个文件的内容非常方便。切换到正常模式，然后按 :read。使用此快捷键你不需要手动打开文件来复制内容。

``` shell 
:read readme.md
```



## 把命令的结果读入 Vim

有时候你需要把某个命令的结果复制到 Vim 中，这在 Vim 也非常简单。切换到正常模式，然后输入 :read !command 即可把 command 的结果输入到 vim 中。
``` shell 
:read !ls -l
```



## 切换到上次修改的位置

想知道你在文件中做的最后一次修改是在什么位置？切换到正常模式，输入 g; 来即可切换到上次修改的位置。



## 移动到文件顶部或底部

当需要移动到文件顶部或底部时，通过 j 或 k 来一行行的移动显得有点麻烦。Vim 提供了一个快捷键可直接实现此功能。切换到正常模式，输入 gg 返回文件顶部，输入 G 返回文件底部。

