---
title: "如何去除IDE中对Dart代码行超长的警告"
date: 2021-05-27T17:32:07+08:00
draft: true
---

如果在IDE中的Dart文件单行字符数如果超过设定的长度，会遇到：
```
AVOID lines longer than 80 characters
```    

这种警告非常恼人，解决的方法是打开`analysis_options.yaml`文件。

注释掉这两行
```
lines_longer_than_80_chars: error
- lines_longer_than_80_chars
```

