---
title: "在Big Sur上安装Ruby的经历"
date: 2022-04-01T18:19:07+08:00
draft: false
---
**TL;DR**: macOS Big Sur貌似对安装Ruby不太友好。不推荐`rvm`；推荐`rbenv`...

我是在macOS Big Sur上安装Ruby的，从来没有那么折腾过，花费了大半天时间。最后虽然安装成功，但却有很多点值得记录。
这是是要安装`2.7.5`版本，LTS版本。输入`ruby -v`后会发现Mac是自带Ruby的，只是版本滞后，满足不了灵活需要。

最好不要直接安装Ruby，而是通过Ruby版本管理工具。

## 藉rvm安装Ruby
首先尝试安装[rvm](https://rvm.io/)，用rvm管理不同的本地Ruby版本应该很简单，然而却不然。rvm很容易安装，但要手动设置环境变量。
具体步骤可以参考RVM官网。

YouTube上有个很好的[视频讲解](https://www.youtube.com/watch?v=SL64tWlpwSE)    

安装某个Ruby版本只要`rvm install 2.7.5`；安装后设置成默认是用`rvm --default use 2.7.5 `，但是却报错。

## 藉rbenv安装Ruby
rbenv似乎没有官方主页，只有[Github项目地址](https://github.com/rbenv/rbenv#installing-ruby-versions)
```shell
brew install rbenv
```
然后
```shell
rbenv install 2.7.5
```
这条命令居然也失败了...

参考了[这篇Github Gist](https://gist.github.com/Neutrollized/37841827940b28b27ec2e54abbbcc408)，找到了解决方法。
```shell
RUBY_CONFIGURE_OPTS="--with-openssl-dir=$(brew --prefix openssl@1.1)" RUBY_CFLAGS="-w" rbenv install 2.7.5
```
然后
```shell
rbenv global 2.7.5
```
关闭Terminal后，`ruby -v`还是输出老版本，设置一下环境变量
```shell
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"
```

