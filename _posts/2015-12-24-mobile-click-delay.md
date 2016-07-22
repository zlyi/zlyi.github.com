---
layout: post
title: 解决移动端Click时间300毫秒延迟问题
date: 2015-12-24 10:00
comments: true
categories: [前端]
---
 
在移动端，对性能，相应速度有要求的情况下，使用Click事件，可能会有卡顿延迟的现象，特别是android的一些浏览器下，问题更明显，引起原因据说是因为浏览器区分双击和单击操

作，需要300ms时间区分单击还是双击.

以下为移动端各个事件的集合，以及触发的时间：

touchstart 0ms
touchend 53ms
mouseover 353ms
mousemove 354ms
mousedown 355ms
mouseup 356ms
click 356ms

一般的解决方案为：

在touchstart、touchend时记录时间、手指位置，在touchend时进行比较，如果手指位置为同一位置（或允许移动一个非常小的位移值）且时间间隔较短（一般认为是200ms），且过程中未曾触发过touchmove，即可认为触发了手持设备上的“click”，一般称它为“tap”   