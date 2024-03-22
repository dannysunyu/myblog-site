---
layout: post
title: "Priority Queue in Java"
date: 2018-09-03 11:30:01 +0800
comments: true
categories: algorithms
---

In the queue abstraction presented in this chapter, new items are always added at the end of the queue and wait their turn in line. For some programming applications, it is useful to extend the simple queue abstraction into a priority queue, in which the order of the items is determined by a numeric priority value. When an item is enqueued in a priority queue, it is inserted in the list ahead of any lower priority items. If two items in a queue have the same priority, they are processed in the standard first-in/first-out order.
Using the linked-list implementation of queues as a model, design and implement a pqueue.h interface that exports a class called PriorityQueue, which exports the same methods as the traditional Queue class with the exception of the enqueue method, which now takes an additional argument, as follows:
           void enqueue(ValueType value, double priority);
The parameter value is the same as for the traditional versions of enqueue; the priority argument is a numeric value representing the priority. As in conventional English usage, smaller integers correspond to higher priorities, so that priority 1 comes before priority 2, and so forth.
