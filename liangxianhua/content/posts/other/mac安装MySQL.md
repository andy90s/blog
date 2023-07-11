---
title: "Mac安装MySQL"
subtitle: ""
date: 2023-07-11T17:30:23+08:00
# lastmod: 2023-07-11T17:30:23+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [mysql]
categories: [mysql]
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
最近在学习MySQL，需要在Mac上安装MySQL，记录一下安装使用过程。

## 安装
### 1.通过brew安装
```shell
brew install mysql
```
### 2.启动MySQL
```shell
brew services start mysql
```
### 3.设置密码
```shell
mysql_secure_installation
```
### 4.登录MySQL
```shell
mysql -uroot -p
```
### 5.修改密码
```shell
ALTER USER 'root'@'localhost' IDENTIFIED BY 'new password';
```
### 6.退出MySQL
```shell
exit
```
### 7.重启MySQL
```shell
brew services restart mysql
```
### 8.登录MySQL
```shell
mysql -uroot -p
```
### 9.创建数据库
```shell
create database test;
```
### 10.查看数据库
```shell
show databases;
```
### 11.删除数据库
```shell
drop database test;
```

## 参考
{{<link href="https://www.sjkjc.com/mysql/install-on-macos/" content="【Mac安装MySQL】">}}