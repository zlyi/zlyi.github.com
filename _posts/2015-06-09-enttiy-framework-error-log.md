---
layout: post
title: Entity fromework 踩过的坑
date: 2015-06-09 10:00
comments: true
categories: [后端技术]
--- 

**EF Code First Fluent Mapping: 0-1 to Many: HasOptional() WithMany()**


In order to make the relationship optional you need a nullable foreign key property in your TruckPartentitiy (plus the mapping with HasOptional):

``` public int? PartId { get; set; }

**Entity Framework 4.1 : The navigation property 'BusinessUser' declared on type 'Login' has been configured with conflicting multiplicities**


Your BusinessUser must have relation configured as:

this.HasOptional(bu => bu.LoginInfo)
    .WithRequired(l => l.BusinessUser);

Both configuration must be same (actually only one is needed) and the first configuration is incorrect because it is trying to define 0..1 - 0..1 relation.



　　---- 
　　 