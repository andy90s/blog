---
title: "iOS中的只读属性"
subtitle: ""
date: 2023-02-01T09:21:27+08:00
# lastmod: 2023-02-01T09:21:27+08:00
draft: false
author: "andy90s"
authorLink: ""
description: "Swift中的只读属性,像OC一样隐藏set方法"
license: ""
images: []

tags: [iOS只读,Swift,OC]
categories: [移动端]
featuredImage: "/images/fengmian.jpg"
featuredImagePreview: "/images/fengmian.jpg"




---
<!--more-->
## OC只读,Swift设置set私有`private(set)`
```swift
public private(set) var someKey: String
```
当外部调用set方法时的报错信息:
```
Cannot assign to property: 'somekey' setter is inaccessible
```
OC表示只读`readonly`:
```Objective-C
@property (nonatomic, strong, readonly) NSString *someKey;
```
