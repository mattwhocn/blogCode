---
title: bower包管理器的使用命令
date: 2018-04-10 18:25:44
tags:
---


#### 1，自定义包安装目录
新建名为  .bowerrc的文件，指定包安装路径
```
{
    "directory":"app/lib"
}
```

#### 2，bower init  自动生成bower.json文件
```
$ bower init
```
```
{
  "name": "bb_boot",
  "version": "0.0.1",
  "authors": "",
  "moduleType": [
    "amd"
  ],
  "license": "MIT",
  "ignore": [
    "**/.*",
    "node_modules",
    "bower_components",
    "js/lib",
    "test",
    "tests"
  ],
  "dependencies": {
  }
}
```

#### 3，包的安装
```
$ bower install jquery --save			// save 保存配置到bower.json中
```

#### 4，包的信息
```
$ bower info jquery
```

#### 5，更新包版本（更新和下载）
```
$ bower update
```

#### 6，包的查找 （查找关于jquery的包）
```
$ bower search jquery
```

#### 7，包的卸载 
```
$ bower uninstall jquery
```