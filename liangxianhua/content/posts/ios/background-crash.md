---
title: "退到后台通知引起的崩溃"
subtitle: ""
date: 2023-05-17T21:40:52+08:00
# lastmod: 2023-05-17T21:40:52+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [iOS]
categories: [移动端]


---
<!--more-->
## 退到后台通知引起的崩溃
不排除是特定版本的iOS系统bug
## 解决
```swift
@objc func appDidEnterBackground() {
    // 要判断当前应用程序状态是否为后台状态
    guard UIApplication.shared.applicationState == .background else { return }
    // todo something
}
```