---
layout: post
title: gulp 安装
date: 2015-08-01 10:00
comments: true
categories: [前端]
---
 
注意权限问题

更新镜像：

```ruby
$ gem sources --remove https://rubygems.org/$ gem sources -a https://ruby.taobao.org/$ gem sources -l *** CURRENT SOURCES *** https://ruby.taobao.org# 请确保只有 ruby.taobao.org $ gem install sass
```

**sass文件编译**

转译.scss文件，我们主要使用的是sass命令。其操作非常简单，首先进入到对应的项目中，比如这里，先要进入mySass项目中：


$ cd ~/Sites/mySass

然后输入转译命令：

$ sass sass/style.scss css/style.css

http://www.w3cplus.com/preprocessor/sass-compile.html

[在线编辑sass](http://sassmeister.com/)


 
　　---- 
　　 