---
title: "MAC Terminal 443"
subtitle: ""
date: 2024-01-31T17:23:53+08:00
# lastmod: 2024-01-31T17:23:53+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: []
categories: []
keywords: []
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

平时在mac上使用终端的时候,访问一些资源报错,提示443错误,例如访问github资源:

```shell
fatal: unable to access 'https://github.com/ReactiveX/RxSwift.git/':
LibreSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443
```

这时我们需要配置终端的代理,以便于正常访问资源.(终端和你网页走的并不是一个网络环境,我理解的是terminal走的网络权限比app的权限更高)
## 配置

### 1.检查当前环境

终端输入:

```shell
curl ipinfo.io
```

返回:<br>

```shell
{
  "ip": "xxx.xxx.xxx.xxx",
  "city": "Shanghai",
  "region": "Shanghai",
  "country": "CN",
  "loc": "1111,1111",
  "org": "AS17621 China Unicom Shanghai network",
  "timezone": "Asia/Shanghai",
  "readme": "https://ipinfo.io/missingauth"
}
```

### 2.配置终端代理

根据代理工具查看自己的代理模式和代理地址端口,例如一般为`127.0.0.1:1082`<br>

```shell
export http_proxy="http://127.0.0.1:1082"
export https_proxy="http://127.0.0.1:1082"
```

然后你的软件代理开启全局模式,进行测试:<br>

```shell
curl ipinfo.io
```

返回:<br>

```shell
{
  "ip": "111.111.111.111",
  "city": "Urayasu",
  "region": "Tokyo",
  "country": "JP",
  "loc": "35.6609,139.7717",
  "org": "AS199524 G-Core Labs S.A.",
  "postal": "135-0061",
  "timezone": "Asia/Tokyo",
  "readme": "https://ipinfo.io/missingauth"
}%
```

说明代理成功,可以正常访问资源了.

{{< admonition tip "注意">}}
上面的全局模式只是为了测试,记得改回规则模式,按需代理.
{{< /admonition >}}
