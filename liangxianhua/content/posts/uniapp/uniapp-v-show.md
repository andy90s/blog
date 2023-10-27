---
title: "v-show在微信小程序中不生效"
subtitle: ""
date: 2023-05-08T10:23:24+08:00
# lastmod: 2023-05-08T10:23:24+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [uniapp,vue]
categories: ["前端"]
featuredImage: "/images/fengmian3.jpg"
featuredImagePreview: "/images/fengmian3.jpg"

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
## v-show在微信小程序中不生效
```css
<style lang="scss" scoped>
/* #ifdef MP-WEIXIN */
view[hidden] {
  display: none !important;
}
/* #endif */
</style>
```
{{<link href="https://liguoyou.gitee.io/your/2020/08/20/uni-app-display-flex-v-show-invalid/" content="【具体原因】">}}