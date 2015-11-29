---
layout: post
title: ionic页面中页面切换问题
date: 2015-10-20 10:00
comments: true
categories: [前端]
---
 

在ionic页面中，不要使用a标签默认的href跳转，以及$state.go不然会导致页面变形，可使用  Angular-UI-Router ui-sref 指令。
   
在一些特殊情况下，ui-sref的state参数是动态的，怎么办呢，我们知道官方是不支持动态传参的，在百思不得其解的时候，在github上发现了有人向官方提过这个问题，并引起了很大的讨论，很多人都遇到过这个问题。[传送门](https://github.com/angular-ui/ui-router/issues/395)，我是参照@crisbeto 提供的指令方法实现的。实现方法如下：
template:
<div page-state state='{{pageState}}' id="123">

js:
    dir.directive('pageState', function () {
            return {
                restrict: 'EAC',
                template: function (elem, attr) {
                  
                    var template='<a ui-sref="'+attr.state+'({Id:'+attr.id+'})"></a>';
                                   
                    return template;
                }
        };
    })

指令具体使用方法可参考：angularjs 指令详解 - template, restrict, replace
  
---- 

　　 