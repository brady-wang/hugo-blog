---

date:  "2020-10-18T12:36:00+08:00"

title: "oh my zsh 安装"

tags: ["zsh","oh my zsh"]

categories: ["shell"]

---



# 官网地址

oh my zsh:  https://ohmyz.sh/

oh my zsh github 地址:   https://github.com/ohmyzsh/ohmyzsh/wiki

zsh github地址:  https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH

oh my zsh 主题: https://github.com/ohmyzsh/ohmyzsh/wiki/Themes

oh my zsh 插件: https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins

## 安装zsh

mac系统

```mac
zsh --version 
brew install zsh zsh-completions
```

centos 

```
sudo yum update && sudo yum -y install zsh
```

ubuntu 

```
apt install zsh
```

https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH



## 安装 oh my zsh

curl 方式安装

**sh -c“ $（curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh）”**

wget 方式安装

**sh -c“ $（wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O-）”**



## 切换为zsh

查看系统支持的shell

```
cat /etc/shells
```

查看当前shell

```
echo $SHELL
```

**chsh -s /usr/local/bin/zsh**
或者
**chsh -s /bin/zsh**

切换后要新打开terminal才会生效



---

## 配置主题和插件

**题外话，由于clear每次打的很麻烦，可以直接使用ctrl+L清屏，和clear等效。**

**First：**

安装好zsh和oh-my-zsh

**Second：**

接下来就可以开始享受了

主题:cloud  这个云朵看上去挺舒服的～～



另外一个主题就是 c,bira，也是我目前在用的一个主题

设置方法：vim ~/.zshrc， 找到**ZSH_THEME=“”，**这句话，在双引号里面写上cloud就可以啦！

如果你在里面写的是random，每次开启终端的主题将是随机的！

当然你也可以自己找主题，oh-my-zsh里面带有主题了，主题都在以下这个文件夹里，可以进去找自己喜欢的

```
~/.oh-my-zsh/themes
```

插件：

1、git
2、pip

这两个没什么讲的

3、sudo

当我们输入命令需要管理员身份时，不必让光标回到开始打一个sudo，可以直接按两次ESC，就会自动帮你加上sudo

4、thefuck

当我们输入命令错误时，输入fuck，终端就会乖乖的给我们正确的指令选择了！（这个插件需要自己下

5、autojump

在终端输入d，可以显示刚刚走过的路径，然后按数字选择进入哪一个目录。（这个插件需要自己下



6、web-search

直接在终端使用浏览器搜索，可以百度 谷歌

7、last-working-dir

可以记录我退出终端时所在的路径，再次打开时还在这个路径

8、zsh-syntax-highlighting

shell下的语法高亮，（这个也要自己下，命令如下`）`

```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

除了以上的两个插件需要自己下载，其他都不需要的。

设置方法：vim ~/.zshrc 在里面找到**plugins=()**

然后在括号里加上想要的插件就可以了。

```
plugins=(
    git
    pip
    sudo
    thefuck
    autojump
    web-search
    last-working-dir
    zsh-syntax-highlighting
)
```

以上步骤操作完后，重启终端，输入source .zshrc，就ok了！

注意每次添加插件以后，都要进行source .zshrc一下，让这些插件运行起来。

另外，我的截图软件的scrot，查看图片是用gwenview

scrot -s：可以自己选择截图的范围

一下是我的 **.zshrc** 配置文件

```
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
  export ZSH="/home/jiaaaaaaaqi/.oh-my-zsh"

# Set name of the theme to load --- if set to "random", it will
# load a random theme each time oh-my-zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/robbyrussell/oh-my-zsh/wiki/Themes
ZSH_THEME="cloud"

# Set list of themes to pick from when loading at random
# Setting this variable when ZSH_THEME=random will cause zsh to load
# a theme from this variable instead of looking in ~/.oh-my-zsh/themes/
# If set to an empty array, this variable will have no effect.
# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment the following line to disable bi-weekly auto-update checks.
# DISABLE_AUTO_UPDATE="true"

# Uncomment the following line to change how often to auto-update (in days).
# export UPDATE_ZSH_DAYS=13

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in ~/.oh-my-zsh/plugins/*
# Custom plugins may be added to ~/.oh-my-zsh/custom/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(
    git
    pip
    sudo
    thefuck
    autojump
    web-search
    last-working-dir
    zsh-syntax-highlighting
)

source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# ssh
# export SSH_KEY_PATH="~/.ssh/rsa_id"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"
```

 



