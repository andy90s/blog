---
title: "异步函数调用this找不到方法"
subtitle: ""
date: 2023-05-10T16:29:56+08:00
# lastmod: 2023-05-10T16:29:56+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [uniapp,vue]
categories: ["前端"]


---
<!--more-->
## 异步函数调用this找不到方法
that 一下;
```js
const that = this;

promise {
  then(res => {
    that.xxx();
  })
}
```