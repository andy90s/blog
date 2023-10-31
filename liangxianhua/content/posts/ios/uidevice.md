---
title: "UIDevice"
subtitle: ""
date: 2023-10-30T17:29:49+08:00
# lastmod: 2023-10-30T17:29:49+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [iOS]
categories: [移动端]
keywords: [UIDevice,ios,刘海屏,设备信息]
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
关于设备信息,苹果提供的API并不多,但是我们可以通过一些开源库来获取更多的信息,比如设备型号,屏幕尺寸,系统版本等等.比如获取当前设备是否是刘海屏,如果用安全距离来判断,因为window有可能是nil,可能会导致判断错误
## DeviceKit
### 地址
{{<link href="https://github.com/devicekit/DeviceKit" content="【DeviceKit】">}}
### 使用
比如判断是否是刘海屏等:<br>

```swift
import DeviceKit

let device = Device.current
// 判断是否是iphone
if device.isPhone {
    // 判断是否是刘海屏
    if device.hasRoundedDisplayCorners {
        // 判断是否是iphoneX
        if device == .iPhoneX {
            // ...
        }
    }
}
```
