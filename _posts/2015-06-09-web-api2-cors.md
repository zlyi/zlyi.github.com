---
layout: post
title: web api2 cors 無法put和delete的解決方法
date: 2015-06-09 10:00
comments: true
categories: [后端技术]
---

我是參考Bruce的此篇文章
發現如果連架在iis上面的web api，put和delete會有問題，想說到底是專案上還是iis或者是client寫法錯誤，最後google大神終於發現問題出在web.config上面。

 ```C#
<system.webServer>
<modules> 
      <remove name="WebDAVModule" /> 
   </modules> 
   <handlers> 
      <remove name="WebDAV" /> 
   </handlers> 
</system.webServer>
```


     ---- 
　　 