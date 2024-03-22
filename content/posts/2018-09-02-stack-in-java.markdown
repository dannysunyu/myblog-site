---
layout: post
title: "Stack in Java"
date: 2018-09-02 20:17:01 +0800
comments: true
categories: algorithms
---

##前言
堆栈作为最基础的数据结构之一，在Java的最初版本就有了纯粹的标准实现：`java.util.Stack`。只可惜该实现存在性能缺陷，主要是由于主要的操作都加上了synchronized线程安全保护机制，导致无法被应用于对性能要求颇高的生产环境。

>A more complete and consistent set of LIFO stack operations is provided by the Deque interface and its implementations, which should be used in preference to this class.  For example: Deque<Integer> stack = new ArrayDeque<Integer>();

在Java Collections类发布后就和`java.util.Vector`类被一起被废弃了，取代之的是`java.util.Deque`接口。之所以设计成接口，是不想与某一个`Deque`的实现绑定。Java提供了`LinkedList`和`ArrayDeque`即可按照使用场景不同，采纳基于数组或是链表的`Deque`实现，提供了灵活性。

>Deques can also be used as LIFO (Last-In-First-Out) stacks. This interface should be used in preference to the legacy Stack class. When a deque is used as a stack, elements are pushed and popped from the beginning of the deque.
