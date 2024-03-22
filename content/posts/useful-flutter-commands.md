---
title: "超有用的Flutter命令行"
date: 2022-04-14T13:51:33+08:00
draft: false
---

## 自动生成的代码
```shell
flutter packages pub run build_runner build --delete-conflicting-outputs
```

## 获取依赖
```shell
flutter pub get
```

## 静态分析
```shell
flutter analyze
```

## 格式化
```shell
flutter format -n --set-exit-if-changed path/to/project --line-length 140
```


