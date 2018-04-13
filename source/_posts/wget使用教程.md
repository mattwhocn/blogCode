---
title: wget使用教程
date: 2018-04-10 18:34:30
tags:
---

## 起源
> wget是一个命令工具，通过执行wget 命令用来从指定的url下载文件。它的优点是稳定，支持断点下载，脱离下载工具的限制。   
安装和使用wget需要先执行前面的环境的配置

#### 一，安装ruby
> mac 自带 ruby

#### 二，利用 ruby 安装 brew
> 如果已经安装ruby直接进入下一步
> brew 全称Homebrew  是Mac OSX上的软件包管理工具
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
> brew 中文官网：https://brew.sh/index_zh-cn.html

> 在安装了brew之后就能通过brew来安装各种有用的插件包

为什么要使用Homebrew
> - Mac OS X是基于Unix的，它可以使用非常多Linux平台上开源的优秀工具，比如wget，比如dos2unix脚本工具等。
> - 但是OS X系统本身却缺少Linux下得包管理器。比如Fedora的yum与dnf，比如Ubuntu的apt-get，比如ArchLinux的Pacman等。
> - 于是这些优秀的开源软件在Mac上的安装只能通过下载源码，编译，安装，配置环境变量的步骤来完成安装。对于大部分的软件，在安装过程中是需要很多的依赖库的，手动去解决这些依赖库是十分痛苦的事情。包管理器干的就是这样的事情：解决软件安装过程中的依赖关系。
> - 有一个开源的项目叫Homebrew，完美解决了Mac OS X上没有包管理器的尴尬。
> - brew的包管理是基于git的


#### 三，使用brew安装wget
科普brew的基本命令：
1，安装软件
brew安装软件的命令：
``` 
$ brew install <软件包名>    
// brew install wget 就可以安装wget
```
2，搜索软件
brew搜索软件的命令：
```
$ brew search <软件包名>     
// brew search wget 就可以搜索包管理器，列出所有相关的软件包，
```
3，查看软件信息
brew 查看信息的命令：
```
$ brew info <软件包名>   
如：brew Info wget 可以查看软件 wget的信息
```
4，卸载软件
```
uninstall
```

#### 四，wget命令		 
参考链接： http://man.linuxde.net/wget
wget 命令用来从指定的url下载文件。稳定，支持断点下载。
wget <选项:可选> <参数>
基本用法：
- wget <文件的URL地址>
    > 将地址指向的文件下载到终端打开的位置    
    如：wget http://i3.mifile.cn/a4/pms_1478510064.36397738.jpg
- wget -i <文件路径/文件名>    
    > 从指定文件获取要下载的url可以有多个url进行批量下载   
    如： wget -i miimg.txt
- wget -nc <url>             
    > 文件存在时不覆盖原有文件


#### 五，试验
下面就随便找一个网站试验，这里拿小米商城为例：   
1，进入小米商城官网：右键->存储为  把网页源码保存到本地    
2，打开html文件（这里使用sublime）  
3，command + f 搜索，使用正则表达式搜索功能 -> find all 搜索所有匹配的结果
搜：
```
<img[\s]+src[\s]*=[\s]*((['"](?<src>[^'"]*)[\'"])|(?<src>[^\s]*))
```
用来匹配img标签中的url  
4，command + c 复制所有搜索的结果 command + n 新建一个文本文件，把复制的链接粘贴进去    

5， 再搜索一次：把
```
<img src="./小米商城 - 小米6、红米Note 5A、小米5X、小米笔记本官方网站_files/
替换为
http://i3.mifile.cn/a4/ 
保存
```
6，打开终端 执行 wget -i <url文件路径名> 既可以把文件中合法的url链接下载到打开终端的当前目录，不正确的url会被忽略

7，另外一种正则：
```
(http:)?//[\w./-]*
```
匹配所有的http://开头的链接 同样不可下载的文件或者不正确的URL链接不会被下载

 



