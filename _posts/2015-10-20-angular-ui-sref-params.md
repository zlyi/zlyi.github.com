---
layout: post
title: 解决ui-sref不支持动态参数问题
date: 2015-10-20 10:00
comments: true
categories: [前端]
---
 

**[参考地址](https://github.com/angular-ui/ui-router/issues/395)**

I solved it like this:
I'm using Angular 1.2.9 and UI-Router 0.2.10

 
```C#

angular.directive('someDirective', [function(){
    return {
        restrict:'EA',
        scope:{
            itemType: "=",
            itemId: "=",
            state: "@"
        },
        template:'\            <a ui-sref="{{ state }}({type: type, id: id})">\            </a>',
        replace:true,
        link: function(scope){}
    }

}]);
  
---- 
　　 