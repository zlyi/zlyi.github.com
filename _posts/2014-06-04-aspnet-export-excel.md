---
layout: post
title: asp.net 导出数据至Excel
date: 2014-06-04 10:00
comments: true
categories: [后端技术]
---
 
 **在Asp.Net中导出数据至Excel有多种方法，其中比较典型的就是利用epplus.dll来进行开发。它可以在服务器中未按照Office的情况下也能正常使用。**
  
  **EPPlus简介**

　　EPPlus就是一个通过Open XML方式来读写Office文件的开源.NET类库，所以使用它生成Office文件完全不需要Microsoft Office（当然如果你需需要查看生成的文件就需要Office了）。它的官方网址是：http://epplus.codeplex.com/。如果需要体验本文中提到的效果，需要从这个网址下载最新版本的类库，我现在使用的这个名为EPPlus.dll类库仅658K，非常方便部署。

**参考网址：**

- http://epplus.codeplex.com/
- http://blog.csdn.net/jimmy2248/article/details/8363697
- http://zhoufoxcn.blog.51cto.com/792419/1319741/