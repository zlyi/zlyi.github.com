---
layout: post
title: Tomcat学习笔记
date: 2014-05-13 10:00
comments: true
categories: [Java,学习纪录]
---

1. Tomcat下载链接：http://tomcat.apache.org/

2. 各文件目录功能
	1.bin：存放各种不同平台开启与关闭Tomcat的脚本文件。
	
    2.lib：存tomcat与web应用的Jar包

    3.conf：存放tomcat的配置文件

    4.webapps：web应用的发布目录

    5.work：tomcat把由各种jsp生成的servlet文件存放的地方

    6.logs：tomcat存放日志文件的地方

    7.temp：tomcat存放临时文件的地方
  
3. 配置环境变量：JAVA_HOME，指向JDK安装目录。
 
4. 配置控制台访问密码：conf\tomcat-users.xml  <user username="admin" password="" roles="manager-gui"/>
