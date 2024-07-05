+++
title = '聊聊Spring WebFlux'
date = 2024-03-28T13:17:41+08:00
draft = false
+++

先来梳理一下关系。

# Reactive Streams
[Reactive Streams](http://www.reactive-streams.org/)是一个规范，定义了处理异步数据流的标准，包括了发布者(Publisher)、订阅者(Subscriber)、订阅(Subscription)、处理
器(Processor)等核心接口和规则。
它为异步编程提供了一个统一的基础，解决了背压(Back Pressure)等问题。

详细见：https://github.com/reactive-streams/reactive-streams-jvm/blob/v1.0.4/README.md

# Java 9 Flow API
此外，Java 9引入的java.util.concurrent.Flow与Reactive Streams在语义上是1：1等价的。

*JDK9 java.util.concurrent.Flow*
> The interfaces available in JDK >= 9 java.util.concurrent.Flow, are 1:1 semantically equivalent to their respective
> Reactive Streams counterparts. This means that there will be a migratory period, while libraries move to adopt the new
> types in the JDK, however this period is expected to be short - due to the full semantic equivalence of the libraries,
> as well as the Reactive Streams <-> Flow adapter library as well as a TCK compatible directly with the JDK Flow types.

# Project Reactor
而[Project Reactor](https://projectreactor.io/)则是这个规范的一种具体实现。它提供了Reactive Streams规范接口的不同实现，以及一组符合
规范的操作符，从而让开发者能够方便地进行响应式编程。

有关Project Reactor的书很少，分享一本免费的[在线电子书](https://eherrera.net/project-reactor-course/)。
{{< figure src="https://d2sofvawe08yqg.cloudfront.net/unraveling-project-reactor/s_hero2x?1682559252" 
    title="Unraveling Project Reactor"
    width="200px" 
    height="360px" >}}


# RxJava
[RxJava 3](https://github.com/ReactiveX/RxJava)是一个基于观察者模式的Java编程库，用于实现异步、基于事件的程序。作为Reactive Streams规范的实现之一，RxJava 3遵循了
Reactive Streams的接口和协议。

# Spring WebFlux