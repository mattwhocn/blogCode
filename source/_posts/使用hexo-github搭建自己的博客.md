---
title: 使用hexo + github搭建自己的博客
date: 2018-01-24 14:10:58
tags: hexo
---

##### 前言：
经常会在有道云笔记中用markdown写一些自己的总结
跟着官方文档搭建了之后，还是有必要做一个记录，方便自己查阅，下面上教程

##### 简介：（抄自官方网站→_→）
Hexo 是一个快速、简洁且高效的博客框架[hexo github地址](https://github.com/hexojs/hexo)。Hexo 使用 Markdown 语法，使用起来很简单。

### 配置环境
> 要求电脑安装环境环境
- node 6.0+ ， npm 3.10+
- git
- github 账号
本文章假设你已经安装好了node 6.0+ 并且拥有自己的github账号，如果有继续下一步，如果没有先安装必要的依赖

### 安装步骤

#### 1,安装hexo-cli脚手架工具
> hexo 使用npm来管理包，直接使用命令:
```
$ npm install hexo-cli -g
```
> 将hexo-cli脚手架全局安装到你的电脑上

#### 2,初始化项目
> hexo-cli 在电脑全局添加了hexo命令，使用 hexo -help 能够查看hexo提供的全部命令以及说明
在工作目录打开终端，执行：
```
$ hexo init <文件夹名>
```
就会自动下载文件，生成一个<文件夹名>的项目，并把项目代码clone进去

#### 3,本地运行调试
> hexo init命令生成的项目可以直接运行，使用命令：
```
# 生成静态资源
$ hexo generate
# 启动本地服务在浏览器预览调试
$ hexo server
```

#### 4,与github链接
> 打开你自己的github，新建一个以你的github账户开头的仓库，固定格式： 【your_user_name.github.io】比如我的仓库名为：mattwhocn.github.io
然后打开_config.yml 文件将github仓库地址配置到项目中，
```
deploy:
    type: git
    repo: https://github.com/mattwhocn/mattwhocn.github.io.git
    branch: master
```

#### 5,发布
> 使用hexo deploy命令发布你的代码：
```
$ hexo deploy
```
> 等一下------报错了 -_-!!!
需要安装一个包来执行deploy的命令:
```
$ npm install hexo-deployer-git --save
```
> 包安装完成之后再执行上面的hexo deploy命令，hexo deploy命令会直接将上面用hexo generate命令生成的资源文件发布到github仓库。在浏览器地址栏打开your_user_name.github.io就可以访问啦

#### 6，更新博客
> 使用命令：
```
$ hexo new "第一篇博客"
```
> 就能新建一篇博客，博客源码存放在source/_posts/ 文件夹下，打开 <b>第一篇博客.md</b> 编辑你的博客然后使用：
```
$ hexo clean            # 清除上次生成的文件
$ hexo generate         # 构建生成新资源文件
$ hexo deploy           # 发布文件到github
```


***
### 后记
为了写这篇，删掉了之前搭好的内容，重新搭了一遍，亲测一切顺利的话5分钟搞定，

#### 仓库的关系
> github 仓库 地址是 https://github.com/mattwhocn/mattwhocn.github.io.git 本地项目链接了远程这个仓库，但是我执行了hexo deploy之后就无法往这个仓库中push代码了，其实由于在_config.yml文件中配置了git仓库地址，hexo deploy命令就是替你把打包之后的（public文件下）的代码push到这个远程仓库，远程仓库存储的不是整个项目，而是打包之后的文件，所以不能将整个项目的remote地址指向这个仓库。如果想要把整个项目代码提交到github，可以另建一个仓库来保存代码。

#### 项目目录解析
```
├── .deploy_git             // 
├── node_modules            // node依赖包
├── public                  // 打包之后的文件
├── scaffolds               
├── source                  // 博客源文件
│   └── _posts              // 博客存放文件夹
├── themes                  // 主题文件夹
│   ├── landscape           // 默认landscape主题
│   └── yilia               // yillia主题子仓库 
├── _config.yml             // 配置文件
├── .gitignore              // git仓库忽略的文件和文件夹
├── db.json
├── package.json            // package.json
└── README.md               // 说明文件
```

