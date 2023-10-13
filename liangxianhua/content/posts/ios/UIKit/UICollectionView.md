---
title: "UICollectionView"
subtitle: ""
date: 2023-10-13T14:42:52+08:00
# lastmod: 2023-10-13T14:42:52+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: []
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
## 布局从右到左
```swift
if #available(iOS 9.0, *) {
    collectionView.semanticContentAttribute = .forceRightToLeft
}
```
```objc
if (@available(iOS 9.0, *)) {
    _collectionView.semanticContentAttribute = UISemanticContentAttributeForceRightToLeft;
}
```
