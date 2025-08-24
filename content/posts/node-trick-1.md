+++
title = 'Node Trick 1'
date = 2025-06-26T17:32:47+07:00
draft = false
+++

在Node项目中，要运行npm install，必须要存在package.json。

如果是手动从零新建一个项目，新建package.json后，加入个空的对象。

```json 
// package.json

{}
```

否则，运行npm install foo会报错。

或是用npm init -y来创建，参数-y避免在创建创木时需要回答的一些交互问题。
