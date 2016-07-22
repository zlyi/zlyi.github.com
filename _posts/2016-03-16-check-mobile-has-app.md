---
layout: post
title: 网页中判断手机里是否包含APP
date: 2016-03-16 10:00
comments: true
categories: [前端]
---
 
在浏览器中验证是否安装App，可以在浏览器中打开对于环境App的url schemes，然后根据相应时间判断是否安装，如果500毫秒之内打开，则正常调整到App，如果超时未响应，则可以断定为未安装App
具体的实现代码可参考：
```ruby
<script language="javascript">
  if (navigator.userAgent.match(/(iPhone|iPod|iPad);?/i)) {
    var loadDateTime = new Date();
    window.setTimeout(function() {
      var timeOutDateTime = new Date();
      if (timeOutDateTime - loadDateTime < 5000) {
        window.location = "要跳转的页面URL";
      } else {
        window.close();
      }
    },
    25);
    window.location = " apps custom url schemes ";
  } else if (navigator.userAgent.match(/android/i)) {
    var state = null;
    try {
      state = window.open("apps custom url schemes ", '_blank');
    } catch(e) {}
    if (state) {
      window.close();
    } else {
      window.location = "要跳转的页面URL";
    }
  }
</script> 
```
还可参考这个链接：http://blog.woodbunny.com/post-140.html
 
 