---
layout: post
title: 采集股票数据记录
date: 2014-05-06 10:00
comments: true
categories: [学习纪录]
---

**采集历史数据**

雅虎：
[雅虎采集地址](http://table.finance.yahoo.com/table.txt?a=3&b=29&c=2014&d=4&e=6&f=2014&s=CTRP)

**参数说明**

-  s – 股票名称
-  a – 起始时间，月
* b – 起始时间，日
* c – 起始时间，年
* d – 结束时间，月
*  e – 结束时间，日
* f – 结束时间，年
* g – 时间周期。Example: g=w, 表示周期是’周’。d-&gt;’日’(day),
* w-- ’周’(week)，m-&gt;’月’(mouth)，v-&gt;’dividends
* Date Open High Low Close Volume Adj Close
      分别是：日期、开盘价、最高价、最低价、收盘价、成交量、复权收盘价 

雅虎股票API 参数对照表 http://blog.t41.cn/index.php/archives/256  

新浪：
http://hq.sinajs.cn/list=gb_ctrp

参考链接：http://blog.sina.com.cn/s/blog_7ed3ed3d010146ti.html