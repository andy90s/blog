---
title: "UITableView使用记录"
date: 2023-01-06T11:20:37+08:00
draft: false
categories: [移动端]
tags: [iOS]
keywords: [UITableView]
featuredImage: "/images/fengmian4.jpg"
featuredImagePreview: "/images/fengmian4.jpg"
description: "UITableView使过程中遇到的一些问题记录"
lightgallery: true
---
<!--more-->
## UITableView的`type`
### UITableView的类型(type)
```swift
public enum Style : Int, @unchecked Sendable {

    case plain = 0 // 通用类

    case grouped = 1 // 分组模式

    @available(iOS 13.0, *)
    case insetGrouped = 2 // iOS13以后支持的API,给组加圆角,效果如下
}
```

<center>
{{<image src="https://cdn.jsdelivr.net/gh/andy90s/blog-image@master/blog/images/202301062145544.png" title="insetGrouped"width="50%">}}
<div style="color:black;"> <b> insetGrouped </b>  </div>
</center>

### iOS15系统之后type为`grouped`时,头部有间距
```swift
if #available(iOS 15.0, *) {
    tableView.sectionHeaderTopPadding = 0
}
```
```objc
if (@available(iOS 15.0, *)) {
    _tableView.sectionHeaderTopPadding = 0;
}
```

### type为`grouped`时,组间距问题
```swift
func tableView(_ tableView: UITableView, heightForFooterInSection section: Int) -> CGFloat {
    return 0
}
    
func tableView(_ tableView: UITableView, viewForFooterInSection section: Int) -> UIView? {
    return UIView()
}
```

### 去除诡异动画
```objc
[UIView setAnimationsEnabled:false];
        [CATransaction begin];
        [CATransaction setCompletionBlock:^{
            [UIView setAnimationsEnabled:true];
        }];
        [self.tableView beginUpdates];
        [self.tableView insertRowsAtIndexPaths:addIndexPathes
                              withRowAnimation:UITableViewRowAnimationNone];
        [self.tableView endUpdates];
        [CATransaction commit];
```




