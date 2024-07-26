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