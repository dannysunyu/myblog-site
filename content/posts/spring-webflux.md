+++
title = 'Spring Webflux'
date = 2024-03-28T13:17:41+08:00
draft = false
+++

先来梳理一下关系。

Reactive Streams是一个规范，定义了处理异步数据流的标准，包括了发布者(Publisher)、订阅者(Subscriber)、订阅(Subscription)、处理器(Processor)等核心接口和规则。
它为异步编程提供了一个统一的基础，解决了背压(Back Pressure)等问题。

而Project Reactor则是这个规范的一种具体实现。它提供了Reactive Streams规范接口的不同实现，以及一组符合规范的操作符，从而让开发者能够方便地进行响应式编程。