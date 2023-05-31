---
title: "Text组件显示链接文本超出组件"
subtitle: ""
date: 2023-05-31T13:16:40+08:00
# lastmod: 2023-05-31T13:16:40+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: []
categories: []
featuredImage: "/images/fengmian1.jpg"
featuredImagePreview: "/images/fengmian1.jpg"

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
## 问题
当文本是链接时候,会超出组件显示,如下图,红色为`text`组件:
<center>
{{<image src="https://raw.githubusercontent.com/andy90s/blog-image/master/blog/images/202305311318757.png" title="超出组件" width="50%">}}
<div style="color:#717171;font-size:14px;font-weight:normal"> <b> 超出组件 </b>  </div>
</center>

## 解决
```css
/* 单词换行 */
word-break: break-all;
```