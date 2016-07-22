---
layout: post
title: angular开发经验
date: 2015-12-07 10:00
comments: true
categories: [前端]
---
 
- 只监听必要的变量(例如：在进行实时通讯时，不要在每次接收到消息时触发 $digest loop)

- 对于那些只初始化一次并不再改变的内容, 使用一次性 watcher bindonce 对于早期的 AngularJS 或者一次性 bindings 对于 AngularJS >=1.3.0.

- 尽可能使 $watch 中的运算简单。在单个 $watch 中进行繁杂的运算将使得整个应用延缓(由于JavaScript的单线程特性，$digest loop 只能在单一线程进行)

- 当监听集合时, 如果不是必要的话不要深度监听. 最好使用 $watchCollection, 对监听的表达和之前表达的估值进行浅层的检测.

- 在 $timeout 设置第三方参数为 false 来跳过 $digest 循环 当没有变量被 $timeout 回调函数所影响.

- 当面对超大不太改变的集合, 使用 immutable data structures.

- 不要使用全局。通过依赖注入解决所有依赖。