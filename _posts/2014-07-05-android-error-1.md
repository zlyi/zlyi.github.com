---
layout: post
title: Android SDK 中的 SDK Manager.exe 无法启动、一闪而过的解决办法
date: 2014-07-05 10:00
comments: true
categories: [Android]
---

**【故障描述】**
做 Android 开发就要下载 Android SDK，其中的 SDK Manager.exe 无法启动，一闪而过。
尝试重装 JDK、重新从官网下载 Android SDK、添加环境变量等等均无效。
而且，有些版本的没事，有些版本的就不行。下载的 android-sdk_r14 可以正常执行 SDK Manager.exe，但是 android-sdk_r18 就不能执行，闪了一下就退出了。
 
**【问题所在】**
SDK Manager.exe 通过调用 android-sdk-windows\tools\lib\find_java.bat 确认 java.exe 的路径。
启用 cmd.exe，命令行切换路径到 android-sdk-windows\tools\lib，执行 find_java.bat，看到输出：
C:\Windows\system32\java.exe
虽然该路径下存在 java.exe，但是这并不是 jre 的安装路径。估计是由于某些需要 java 的软件在安装时，将 java.exe、javaw.exe、javaws.exe 复制到了 c:\windows\system32 下，导致 SDK Manager.exe 调用了错误位置的 java.exe 所致。
 
**【解决办法】**
 知道了问题所在，解决起来就很容易了，删掉 C:\Windows\system32\ 下的 java.exe、javaw.exe、javaws.exe 即可解决。不放心的话，可以进入 cmd 再切换路径执行 find_java.bat 检查一下，输出：C:\Program Files\Java\jre7\bin\java.exe 就没问题了。