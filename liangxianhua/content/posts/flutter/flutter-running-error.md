---
title: "Flutter运行问题"
subtitle: ""
date: 2023-10-31T10:12:39+08:00
# lastmod: 2023-10-31T10:12:39+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [flutter]
categories: [移动端]
keywords: [flutter]
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
记录flutter运行遇到的问题
## 无法打开`iproxy`
### 问题描述
<center>
{{<image src="https://cdn.jsdelivr.net/gh/andy90s/blog-image@master/blog/images/无法打开iproxy.png" title="" width="50%">}}
<div style="color:#717171;font-size:14px;font-weight:normal"> <b> 无法打开`iproxy` </b>  </div>
</center>


### 解决方案
```zsh
sudo xattr -d com.apple.quarantine /Users/xxx/flutter/bin/cache/artifacts/usbmuxd/iproxy
```
{{< admonition tip "注意">}}
其中`/Users/xxx/flutter/bin` 替换自己的flutter安装目录 <br>
终端输入```which flutter```查看目录
{{< /admonition >}}
