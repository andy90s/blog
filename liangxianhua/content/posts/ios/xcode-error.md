---
title: "Xcode运行项目报错"
subtitle: ""
date: 2023-07-12T19:30:20+08:00
# lastmod: 2023-07-12T19:30:20+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: []
categories: [移动端]
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

## M系列电脑运行`MAC(Designed for iPad)`或者`MAC(Designed for iPhone)`项目报错
### 报错信息
```error
The app's bundle identifier "com.xxx.xxx.xxx" is being used by another running app. 
macOS does not support running iOS or Mac Catalyst apps concurrently with other apps using the same bundle identifier. 
Please try again after terminating all other processes using the same bundle identifier or changing the bundle identifier of your app.
```
### 分析原因
- 电脑上有同名应用
### 解决方案
- 检查当前电脑应用是否有同名应用，如果有，关闭同名应用
- 重启Xcode
- 上面不行直接施展重启大法: **重启电脑**
   