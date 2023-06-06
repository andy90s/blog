---
title: "Uni页面撑满整个view"
subtitle: ""
date: 2023-05-08T13:45:46+08:00
# lastmod: 2023-05-08T13:45:46+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [uni-app,vue]
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
## Uni页面撑满整个view
设置了父元素高度100%后,没有撑满整个view,如下图所示:
<center>
{{<image src="https://raw.githubusercontent.com/andy90s/blog-image/master/blog/images/202305081351874.png" title="示例" width="40%">}}
<div style="color:#717171;font-size:14px;font-weight:normal"> <b> 示例 </b>  </div>
</center>

## 解决方法

增加如下样式代码,**uni-page-body,html,body{height:100%}**:
```css
<style lang="scss" scoped>
uni-page-body,html,body{height:100%}
.page {
	display: flex;
	background-color: #FFFFFF;
	height: 100%;
}
</style>
```

## 效果

<center>
{{<image src="https://raw.githubusercontent.com/andy90s/blog-image/master/blog/images/202305081356147.png" title="效果" width="40%">}}
<div style="color:#717171;font-size:14px;font-weight:normal"> <b> 效果 </b>  </div>
</center>
