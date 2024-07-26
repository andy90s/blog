---
title: "项目使用 Swift Package Manager"
subtitle: ""
date: 2024-07-22T17:57:59+08:00
draft: false
authors: [andy90s]
description: ""

tags: []
categories: []
series: []
keywords: []

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: true
license: ""
---

## Swift Package Manager

优势:

- 项目使用spm的方式,主工程文件不会有冲突
- 依赖管理更加方便
- 越来越新的swift相关的库不再支持cocoapods,只支持spm

缺点:

- 太依赖网络了,如果远程库是github上的库,一旦DNS被污染你就暂时性的访问不了

## 使用

工程 - 右键 - Add Package Dependency
