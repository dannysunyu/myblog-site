+++
title = '在中国，使用npm需要替换registry'
date = 2024-01-02T21:10:24+08:00
draft = false
+++

是在国外开始把玩Node.js，回国后发现npm install速度很慢...

这又是一个解决别的制度不存在的问题…

总之，npm默认的registry是 https://registry.npmjs.org 。可是在中国，这个源似乎访问速度很慢。

```
npm config get registry
```
可以返回当前源设置

设置淘宝源：
```
npm config set registry https://registry.npmmirror.com
```

