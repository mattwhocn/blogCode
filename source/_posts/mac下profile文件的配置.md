---
title: mac下profile文件的配置
date: 2018-05-02 18:30:54
tags: mac
---

### mac下配置环境的文件 /etc/profile、/etc/bashrc、~/.bashrc的区别

> 需要给terminal中显示的git分支显示彩色区分，百度了一下如何配置,结果 不同的文章讲解的配置的方法不太一样，发现有些是在 /etc/profile 文件配置，有些是在 ~/.bashrc 配置；对这些的区别不是特别清楚，特此查阅了相关资料，整理下来，供以后查阅。如有错误之处，还望各位朋友批评指正。 

#### ①/etc/profile: 
> 该文件登录操作系统时，为每个用户设置环境信息，当用户第一次登录时,该文件被执行。也就是说这个文件对每个shell都有效，用于获取系统的环境信息。

```
# /etc/profile

# System wide environment and startup programs, for login setup
# Functions and aliases go in /etc/bashrc

# It's NOT a good idea to change this file unless you know what you
# are doing. It's much better to create a custom.sh shell script in
# /etc/profile.d/ to make custom changes to your environment, as this
# will prevent the need for merging in future updates.
```

#### ②/etc/bashrc： 
> 为每一个运行bash shell的用户执行此文件，当bash shell被打开时,该文件被读取。也就是说，当用户shell执行了bash时，运行这个文件。

```
# /etc/bashrc

# System wide functions and aliases
# Environment stuff goes in /etc/profile

# It's NOT a good idea to change this file unless you know what you
# are doing. It's much better to create a custom.sh shell script in
# /etc/profile.d/ to make custom changes to your environment, as this
# will prevent the need for merging in future updates.
```

#### ③~/.bashrc 
> 该文件存储的是专属于个人bash shell的信息，当登录时以及每次打开一个新的shell时,执行这个文件。在这个文件里可以自定义用户专属的个人信息。

那么在用户登录系统时候，相关的文件执行顺序是什么呢。 
在刚登录Linux时，首先启动 /etc/profile 文件，然后再启动用户目录下的 ~/.bash_profile、 ~/.bash_login或 ~/.profile文件中的其中一个，执行的顺序为：~/.bash_profile、 ~/.bash_login、 ~/.profile。如果 ~/.bash_profile文件存在的话，一般还会执行 ~/.bashrc文件。

#### 区别与联系
> - /etc/profile: 此文件为系统的每个用户设置环境信息,当用户第一次登录时,该文件被执行.并从/etc/profile.d目录的配- 置文件中搜集shell的设置.
- /etc/bashrc:  为每一个运行bash shell的用户执行此文件.当bash shell被打开时,该文件被读取.
- ~/.bash_profile: 每个用户都可使用该文件输入专用于自己使用的shell信息,当用户登录时,该文件仅仅执行一次!默认情况- - 下,他设置一些环境变量,执行用户的.bashrc文件.
- ~/.bashrc: 该文件包含专用于你的bash shell的bash信息,当登录时以及每次打开新的shell时,该该文件被读取.
- ~/.bash_logout: 当每次退出系统(退出bash shell)时,执行该文件.
 
另外,/etc/profile中设定的变量(全局)的可以作用于任何用户,而~/.bashrc等中设定的变量(局部)只能继承/etc/profile中的变量,他们是"父子"关系.

### 如何给终端中git分支显示颜色
> 知道了以上profile 文件的区别之后，就可以编辑文件了，这里假设电脑上有多个用户，而只想给当前用户配置的话，就编辑~/.bash_profile 文件。

```
# git目录显示当前分支 2
function git_branch {
  branch="`git branch 2>/dev/null | grep "^\*" | sed -e "s/^\*\ //"`"
  if [ "${branch}" != "" ];then
      if [ "${branch}" = "(no branch)" ];then
          branch="(`git rev-parse --short HEAD`...)"
      fi
      echo " ($branch)"
  fi
}
export PS1='\u@\h \[\033[01;36m\]\W\[\033[01;32m\]$(git_branch)\[\033[00m\] \$ '
```

> 注：Mac 下面启动的 shell 是 login shell，所以加载的配置文件是.bash_profile，不会加载.bashrc。如果是编辑在.bashrc 文件内，需要再执行下面的命令，这样每次开机后才会自动生效：
```
echo "[ -r ~/.bashrc ] && source ~/.bashrc" >> .bash_profile
```