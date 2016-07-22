---
layout: post
title: windows服务开发
date: 2015-12-27 10:00
comments: true
categories: [服务器]
---
 
安装window服务

安装命令：InstallUtil.exe MyServiceLog.exe

InstallUtil存在路径为：C:\WINDOWS\Microsoft.NET\Framework\.NET版本号

复制C:\WINDOWS\Microsoft.NET\Framework\版本号  路径中的InstallUtil.exe 到bin/debug或bin/release文件夹中，在命令行窗口中直接运行命令

Timer不执行Elapsed事件的解决办法

Timer.Start() 了但只执行了一次Elapsed事件就停止不执行了，原因是您在设置Timer控件属性的时候没有设置AutoReset 为 true

如果将 Enabled 设置为 true 并将 AutoReset 设置为 false，则 Timer 在第一次达到间隔时仅引发一次 Elapsed 事件。当 Enabled 为 true 并且 AutoReset 为 true 时，Timer 继续按指定的间隔引发 Elapsed 事件。

参考：http://blog.csdn.net/angle860123/article/details/17375895