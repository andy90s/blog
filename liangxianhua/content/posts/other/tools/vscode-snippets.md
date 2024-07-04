---
title: "vscode snippets对于markdown不生效"
subtitle: ""
date: 2023-12-09T20:26:55+08:00
# lastmod: 2023-12-09T20:26:55+08:00
draft: false
author: "andy90s"
authorLink: ""
description: ""
license: ""
images: []

tags: [vscode, markdown]
categories: [other]
keywords: [vscode, markdown, snippets]


---
<!--more-->
## vscode snippets对于MARKDOWN不生效
默认情况下，vscode 没有支持 markdown 的 snippets。
## 解决
打开 vscode 的 settings.json 文件，添加如下配置：
```json
"[markdown]": {
    "editor.unicodeHighlight.ambiguousCharacters": false,
    "editor.unicodeHighlight.invisibleCharacters": false,
    "diffEditor.ignoreTrimWhitespace": false,
    "editor.wordWrap": "on",
    "editor.quickSuggestions": {
        "comments": "on",
        "strings": "on",
        "other": "on"
    }
}
```

