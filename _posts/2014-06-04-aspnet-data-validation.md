---
layout: post
title: Asp.Net中进行数据验证方式
date: 2014-06-04 10:00
comments: true
categories: [后端技术]
---
 
**1. 利用传统的调用方法进行验证。**

优点：结构清晰，容易开发和理解
缺点：增加代码量，不好扩展和维护。
实例代码：
 ```C# 
   if ( string.IsNullOrEmpty(subItemID))
            {
                return 0;
            }
            else
            {
            }
  ```
**2.利用C#提供Attribute(特性)进行验证。**

优点：结构清晰，代码简洁。
缺点：开发较复杂。
参考网址： http://www.cnblogs.com/zhouqianhua/archive/2010/10/15/1852559.html
实例代码：

```C# 

public class OrderRequest{ 
          /// <summary>
          /// 订单号
          /// </summary>
          [Validate(ValidateType.IsEmpty)]
          public string OrderNo { get; set; }
           /// <summary>
          /// 商品名称
          /// </summary>
                                               [Validate(ValidateType.IsEmpty|ValidateType.MaxLength,MaxLength = 50)]
         public string CommodityName { get; set; }
``` 

**3.利用FluentValidation空间进行验证。**
优点：利用表达式语法链式编程，使得验证组件与实体分开，更便于组建开发。
缺点：增加前期学习成本。
官方网址：http://fluentvalidation.codeplex.com/
实例代码：

```  C#

using FluentValidation;

public class CustomerValidator: AbstractValidator<Customer> {
  public CustomerValidator() {
    RuleFor(customer => customer.Surname).NotEmpty();
    RuleFor(customer => customer.Forename).NotEmpty().WithMessage("Please specify a first name");
    RuleFor(customer => customer.Discount).NotEqual(0).When(customer => customer.HasDiscount);
    RuleFor(customer => customer.Address).Length(20, 250);
    RuleFor(customer => customer.Postcode).Must(BeAValidPostcode).WithMessage("Please specify a valid postcode");
  }

  private bool BeAValidPostcode(string postcode) {
    // custom postcode validating logic goes here
  }
}

Customer customer = new Customer();
CustomerValidator validator = new CustomerValidator();
ValidationResult results = validator.Validate(customer);

bool validationSucceeded = results.IsValid;
IList<ValidationFailure> failures = results.Errors;
``` 