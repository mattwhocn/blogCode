---
title: oh my zsh
date: 2018-04-28 15:21:14
tags: tool zsh terminal1
---

## shell
> shell处理计算机内核的外层，是用户和Linux内核之间的接口程序。提示符下输入的命令由shell先解释然后传给Linux内核。
shell(壳) core(内核)。

> linx中的shell 有很多的版本,不同的shell具备不同的功能,比如 Bourne Again shell (bash), 就是大部分linux系统或 类linux系统默认的 shell。
流行的shell有ash、bash、ksh、csh、zsh等，不同的shell都有自己的特点以及用途。

### bash
bash shell 是 Bourne shell 的一个免费版本，全称Bourne Again shell (bash)，它是最早的 Unix shell，bash还有一个特点，可以通过help命令来查看帮助。包含的功能几乎可以涵盖shell所具有的功能，所以一般的shell脚本都会指定它为执行路径。

### 其他的shell
csh ksh tcsh sh 

### zsh
zsh 是一款功能强大的 shell 软件，它可以兼容 bash，并且提供了很多高效的改进：
- 更好的自动补全
- 更好的文件名展开
- 强大的定制性

### 查看电脑安装的shell
```
$ cat /etc/shells
$ /bin/bash
$ /bin/csh
$ /bin/ksh
$ /bin/sh
$ /bin/tcsh
$ /bin/zsh
```

### 安装zsh
```
$ sudo yum install zsh
$ sudo apt-get install zsh
```

### 切换shell
```
$ chsh -s /bin/zsh          // 将终端shell切换为zsh
$ chsh -s /bin/bash         // 将终端shell切换为bash
```

### 什么是 oh-my-zsh
> 由于zsh的功能比bash强大很多，使得其使用起来也比较困难，因此 有组织开发了 zsh的插件集合 oh-my-zsh，
```
Oh-My-Zsh is an open source, community-driven framework for managing your ZSH configuration. It comes bundled with a ton of helpful functions, helpers, plugins, themes, and a few things that make you shout
```
从官方的介绍中可以得知 它是一个开源的管理 zsh 配置框架,它内置了非常多的插件、主题、functions等等。

### 安装 oh-my-zsh
```
// 使用curl安装
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
// 使用wget安装 （wget是一款下载工具，详见之前的博客）
$ sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

zsh的github地址 https://raw.github.com/robbyrussell/oh-my-zsh

### Zsh 配置

##### 插件
oh-my-zsh安装时自动下载的大量的有用的插件 ，通过编辑```~/.zshrc```文件，启用相应的插件/主题
zsh的github 插件介绍地址 https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins

##### 主题
zsh主题介绍地址： https://github.com/robbyrussell/oh-my-zsh/wiki/Themes

