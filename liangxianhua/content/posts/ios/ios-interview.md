---
title: "Ios Interview"
subtitle: ""
date: 2023-11-01T09:55:35+08:00
# lastmod: 2023-11-01T09:55:35+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: []
categories: []
keywords: []
featuredImage: ""
featuredImagePreview: ""

hiddenFromHomePage: false
hiddenFromSearch: false
twemoji: false
lightgallery: true
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: false
rssFullText: false

toc:
  enable: true
  auto: true
code:
  copy: true
  # ...
math:
  enable: true
  # ...
mapbox:
  accessToken: ""
  # ...
share:
  enable: true
  # ...
comment:
  enable: true
  # ...
library:
  css:
    # someCSS = "some.css"
    # 位于 "assets/"
    # 或者
    # someCSS = "https://cdn.example.com/some.css"
  js:
    # someJS = "some.js"
    # 位于 "assets/"
    # 或者
    # someJS = "https://cdn.example.com/some.js"
seo:
  images: []
  # ...
---
<!--more-->
## 前言
整理一些ios面试题，方便复习
## 基础
### 1. 说一下OC的内存管理
- 1.1. 什么是引用计数

{{< details summary="参考答案">}}
引用计数是一种内存管理方式，当一个对象被创建时，它的引用计数为1，当有一个对象引用它时，它的引用计数就会加1，当引用它的对象被销毁时，它的引用计数就会减1，当它的引用计数为0时，它就会被销毁。
{{< /details >}}

- 1.2. 说一下引用计数的优缺点

{{< details summary="参考答案">}}
优点：引用计数是一种轻量级的内存管理方式，它的实现简单，效率高，不会产生内存碎片。<br>
缺点：引用计数无法解决循环引用的问题，当两个对象相互引用时，它们的引用计数都不会为0，所以它们都无法被销毁，这就会导致内存泄漏。
{{< /details >}}

- 1.3. 都有哪些方法会使引用计数加1

{{< details summary="参考答案">}}
- alloc/new/copy/mutableCopy方法创建的对象，它们的引用计数都为1<br>
- 通过retain方法使对象的引用计数加1<br>
- 当一个对象作为另一个对象的属性时，它的引用计数会加1<br>
- 当一个对象被添加到集合中时，它的引用计数会加1<br>
- 当一个对象被添加到自动释放池中时，它的引用计数会加1<br>
- 当一个对象被赋值给__strong修饰的变量时，它的引用计数会加1
{{< /details >}}

- 1.4. 都有哪些方法会使引用计数减1

{{< details summary="参考答案">}}
- 通过release方法使对象的引用计数减1<br>
- 当一个对象从集合中移除时，它的引用计数会减1<br>
- 当一个对象从自动释放池中移除时，它的引用计数会减1<br>
- 当一个对象的__strong修饰的变量被赋值为nil时，它的引用计数会减1
{{< /details >}}

- 1.5. 说一下自动释放池

{{< details summary="参考答案">}}
自动释放池是一种内存管理方式，它可以将一些对象添加到自动释放池中，当自动释放池被销毁时，它会向池中的每个对象发送一条release消息，从而使这些对象的引用计数减1，当这些对象的引用计数为0时，它们就会被销毁。
{{< /details >}}

- 1.6. 说一下自动释放池的实现原理

{{< details summary="参考答案">}}
自动释放池是一个栈结构，当一个对象被添加到自动释放池中时，它会被添加到栈顶，当自动释放池被销毁时，它会向栈中的每个对象发送一条release消息，从而使这些对象的引用计数减1，当这些对象的引用计数为0时，它们就会被销毁。
{{< /details >}}

- 1.7. 说一下ARC

{{< details summary="参考答案">}}
ARC是一种内存管理方式，它可以自动在合适的地方插入retain/release/autorelease方法，从而使对象的引用计数正确，从而避免内存泄漏。
{{< /details >}}

- 1.8. 说一下全局区、栈区、堆区

{{< details summary="参考答案">}}
全局区：存储全局变量、静态变量、常量字符串等，它的内存是在程序运行时就分配好的，当程序结束时，它才会被销毁。<br>
栈区：存储局部变量、函数参数等，它的内存是在函数调用时分配的，当函数调用完毕时，它就会被销毁。<br>
堆区：存储OC对象、C结构体等，它的内存是在程序运行时分配的，当它被赋值给__strong修饰的变量时，它的引用计数会加1，当它的引用计数为0时，它就会被销毁。
{{< /details >}}

### 2. 说一下Block
- 2.1. 什么是Block

{{< details summary="参考答案">}}
Block是一种数据类型，它可以用来封装一段代码，它可以作为参数传递，也可以作为返回值返回。
{{< /details >}}

- 2.2. 说一下Block的实现原理

{{< details summary="参考答案">}}
Block是一个结构体，它的内部有三个成员，分别是isa指针、flags、invoke指针，其中isa指针指向Block的类，flags用来记录Block的一些信息，invoke指针指向Block的实现代码。
{{< /details >}}

- 2.3. 说一下Block的类型

{{< details summary="参考答案">}}
Block有三种类型，分别是全局Block、栈Block、堆Block。
{{< /details >}}

- 2.4. 说一下这三种Block的区别

{{< details summary="参考答案">}}
全局Block：它的内存是存储在全局区的，它的生命周期和程序的生命周期一样长，当程序结束时，它才会被销毁。<br>
栈Block：它的内存是存储在栈区的，它的生命周期和它所在的函数一样长，当函数执行完毕时，它就会被销毁。<br>
堆Block：它的内存是存储在堆区的，它的生命周期和它所在的函数不一样长，当它被赋值给__strong修饰的变量时，它的引用计数会加1，当它的引用计数为0时，它就会被销毁。
{{< /details >}}

- 2.5. 那我们平时使用的Block是什么类型的

{{< details summary="参考答案">}}
我们平时使用的Block是堆Block，因为它可以在多个函数中使用，如果是栈Block，那么它只能在它所在的函数中使用。
{{< /details >}}

- 2.6. 说一下Block的循环引用

{{< details summary="参考答案">}}
当Block内部使用了外部的局部变量时，Block会对这个局部变量进行强引用，当Block被赋值给__strong修饰的变量时，这个局部变量的引用计数会加1，当这个局部变量被赋值为nil时，它的引用计数会减1，但是Block对这个局部变量的引用计数不会减1，所以这就会导致循环引用。
{{< /details >}}