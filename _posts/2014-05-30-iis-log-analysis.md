---
layout: post
title: IIS日志分析例子
date: 2014-05-30 10:00
comments: true
categories: [服务器]
---
 
**IIS日志的格式：**
 
date time s-sitename s-computername s-ip cs-method cs-uri-stem cs-uri-query s-port cs-username c-ip cs-version cs(User-Agent) cs(Cookie) cs(Referer) cs-host sc-status sc-substatus sc-win32-status sc-bytes cs-bytes time-taken
 
**实例1：**

awk '{print $11}' u_ex13082715.log|sort |uniq -c|sort -nr|head -200
说明：功能是对各个ip的访问情况做一个统计。(第一个sort是把相同的ip排在一起，uniq –c是把相邻的同一ip进行数量统计，如果没有前一个sort，则隔开的同一个ip会被分开统计，第二个sort –nr是把这些ip按数字进行反向排序)

**实例2：**

awk '{if (($2<"02:00:03")&&($2>="02:00:00"))print $11}' u_ex14030610.SH02SVR3631.log|sort |uniq -c|sort -nr|head -200
说明：为了筛选出从10:00:00~10:00:03之间的ip访问情况。注意这里if条件的使用。
 
**实例3：**

awk '{if($6=="OUTLOOK.EXE") print $6,$7}' u_ex14030610.SH02SVR3631.log|sort |uniq -c|sort –nr
说明：同上，可以print出不同的内容。

**实例4：**

awk 'BEGIN{sum=0;num=0}{if($7=="/Flight.Product.Webservice/ProductService.asmx"){sum+=$22;num+=1}} END{printf"avr:%f\n",sum/num}' fltws_baking.log
 cat u_ex13122410.log |awk '{if($11=="113.106.91.189") print $11,$17}'|sort |uniq -c|sort -nr
说明：这是为了计算url“/Flight.Product.Webservice/ProductService.asmx”的平均响应时间，BEGIN{}里面执行赋值，{}执行运算，END{}里面打出来。当然，可能会有更简洁的写法。
 
**实例5：正则表达式匹配：xxx-xxx-day-1**

awk '{if($7 ~ /\/booking\/[a-zA-Z]{3}-[a-zA-Z]{3}-day-1.html/)print $7,$22}' u_ex14030610.SH02SVR3631.log
说明：awk正则是比较高级的应用，也在进一步摸索和学习中。这个是用来匹配cs-uri-stem 字段模式为“/booking/xxx-xxx-day-1”这样的url，并返回结果的一个语句。