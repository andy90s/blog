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

tags: [uni-app,vue]
categories: []
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