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