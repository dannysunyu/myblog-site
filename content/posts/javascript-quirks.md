---
title: "JavaScript怪癖"
date: 2022-04-15T21:52:20+08:00
draft: false
---

### 1. `JavaScript`里的空指针异常其实是一种`TypeError`

```javascript
null.toString();
```
回显
```textmate
"TypeError: Cannot read property 'toString' of null"
```
