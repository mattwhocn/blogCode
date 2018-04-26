---
title: js页面重定向的方法梳理
date: 2018-04-25 14:54:23
tags:
---

### 前言
项目中页面需要根据权限重定向到不同的页面，用了window.location.href = "eucation.html" 来做的重定向，但是极少数情况下会出现偶现的bug，页面没有跳转，不知道是什么原因，但是由此激发我总结一下都有哪些方法可以实现页面重定向的跳转，以及他们的区别


目前在开发中经常用到的几种形式
```
self.location.href = "www.baidu.com";   //当前页面打开URL页面
window.location.href = "www.baidu.com"; //当前页面打开URL页面
this.location.href = "www.baidu.com";   //当前页面打开URL页面
location.href = "www.baidu.com";        //当前页面打开URL页面
parent.location.href = "www.baidu.com"; //在父页面打开新页面
top.location.href = "www.baidu.com";    //在顶层页面打开新页面 
```

- window.location.href = "www.baidu.com";
- window.location.replace("www.baidu.com");
- window.open("www.baidu.com")  // 第二个参数代表是否在当前页面打开 '_blank' '_self';
- window.location.reload();     // 重新加载当前页面，入股参数为true 代表绕过缓存重新加载页面


### location对象的属性和方法
##### Location 对象属性
属性 |	描述
---  | ---
hash |	设置或返回从井号 (#) 开始的 URL（锚）。
host |	设置或返回主机名和当前 URL 的端口号。
hostname |	设置或返回当前 URL 的主机名。
href |	设置或返回完整的 URL。
pathname |	设置或返回当前 URL 的路径部分。
port |	设置或返回当前 URL 的端口号。
protocol |	设置或返回当前 URL 的协议。
search |	设置或返回从问号 (?) 开始的 URL（查询部分）。

##### Location 对象方法
属性 |	描述
---  | ---
assign() |	加载新的文档。
reload() |	重新加载当前文档。
replace() |	用新的文档替换当前文档。

