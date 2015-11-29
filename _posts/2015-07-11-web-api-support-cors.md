---
layout: post
title: webapi支持Cors
date: 2015-07-11 10:00
comments: true
categories: [后端技术]
---
 
##可使用Ms 官方提供的组件##

1.Install-Package Microsoft.AspNet.WebApi.Cors

2.在Web.config中设置
```C#
    < httpProtocol>
      < customHeaders>
        < add name ="Access-Control-Allow-Origin " value ="* " />
        < add name ="Access-Control-Allow-Credentials " value ="true " />
        < add name ="Access-Control-Allow-Headers " value ="x-requested-with, content-type, accept, origin, authorization, bearer_token, ETag, Last-Modified, IF_MODIFIED_SINCE, location, version, platform, zip_code" />
        < add name ="Access-Control-Allow-Methods " value ="GET, POST, PUT, PATCH, DELETE, OPTIONS " />
        < add name ="Access-Control-Max-Age " value ="8400 " />
      </ customHeaders>
    </ httpProtocol>
```


**注意点**
    1. 因为IIS默认会过滤OPE请求，所以在跨域之前，一定要检查web.config里是否有<remove name=" OPTIONSVerbHandler" />，他会过滤OPTIONS请求，删除即可。
     2.Access-Control-Allow-Origin一定要设置在所有属性之前，不然不能访问


 
　　---- 
　　 