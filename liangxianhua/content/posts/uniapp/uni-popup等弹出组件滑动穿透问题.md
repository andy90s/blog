---
title: "Uni Popup等弹出组件滑动穿透问题"
subtitle: ""
date: 2023-05-18T16:44:37+08:00
# lastmod: 2023-05-18T16:44:37+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [uniapp,vue]
categories: ["前端"]
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
## uni小程序弹出组件滑动穿透问题解决方案
**示例:** `@touchmove.stop.prevent="moveStop"`
```js
<view @touchmove.stop.prevent="moveStop">
			<u-popup :show="show"  class="approval-popup" mode="bottom" :round="18" @close="close">
      </u-popup>
</view>

const moveStop = (e) => {
		e.stopPropagation();
};
```