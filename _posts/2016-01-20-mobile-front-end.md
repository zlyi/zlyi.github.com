---
layout: post
title: 移动前端性能优化点
date: 2016-01-20 10:00
comments: true
categories: [前端]
---
 
尽可能多的利用硬件能力，如使用3D变形来开启GPU加速。
```ruby
-webkit-transform: translate3d(0, 0, 0);
-moz-transform: translate3d(0, 0, 0);
-ms-transform: translate3d(0, 0, 0);
transform: translate3d(0, 0, 0);
```
如动画过程有闪烁（通常发生在动画开始的时候），可以尝试下面的Hack：
```ruby
-webkit-backface-visibility: hidden;
-moz-backface-visibility: hidden;
-ms-backface-visibility: hidden;
backface-visibility: hidden;

-webkit-perspective: 1000;
-moz-perspective: 1000;
-ms-perspective: 1000;
perspective: 1000;
```
尽可能少的使用box-shadows与gradients
box-shadows与gradients往往都是页面的性能杀手，尤其是在一个元素同时都使用了它们。

尽可能的让动画元素不在文档流中，以减少重排
 
懒加载

dom操作

dns-prefetch DNS预解析机制