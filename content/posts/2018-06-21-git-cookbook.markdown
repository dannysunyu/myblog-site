---
layout: post
title: "Git Cookbook"
date: 2018-06-21 12:07:45 +0700
categories:
---
这个博客包含了在日常开发中经常会使用，但是却不太容易记住的Git命令和用法。

<!-- more -->

### 如何重命名本地和远程分支

### 如何删除本地和远程分支

### 如何撤销已被push到远程Git仓库的最新的commit
```
git revert HEAD
git push
```

### 如何从某个分支cherry-pick一个commit，并生成patch文件

### 如何stash当前分支本地的修改
```
git stash
```

### 如何unstash本地修改
```
git stash pop
```
