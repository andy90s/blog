---
title: "Uni Popup组件底部安全区域问题"
subtitle: ""
date: 2023-05-18T15:43:20+08:00
# lastmod: 2023-05-18T15:43:20+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [uniapp,vue]
categories: [uniapp]
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
## uni-popup 带圆角的情况下，底部安全区域问题
官方自带了一个popup组件，但是在ios手机上，如果popup组件带圆角，会出现底部安全区域问题，如下图所示：
<center>
{{<image src="https://cdn.jsdelivr.net/gh/andy90s/blog-image@master/blog/images/202305181545761.png" title="底部安全区域问题" width="50%">}}
<div style="color:#717171;font-size:14px;font-weight:normal"> <b> 底部安全区域问题 </b>  </div>
</center>

## 解决方案 `:safeArea=false`
```js
<uni-popup type="bottom" :safeArea=false>
    <view class="content">
        <view>标题</view>
        <view>内容</view>
    </view>
</uni-popup>

.content {
    background-color: #fff;
    border-radius: 20upx 20upx 0 0;
    /*兼容 IOS<11.2*/
		padding-bottom: constant(safe-area-inset-bottom);
		/*兼容 IOS>11.2*/
		padding-bottom: env(safe-area-inset-bottom);
}
```