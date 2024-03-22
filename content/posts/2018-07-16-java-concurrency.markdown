---
layout: post
title: "Java Concurrency"
date: 2018-07-16 12:28:47 +0700
comments: true
categories:
---
##  为何要同步线程？
>Since all threads run in the same address space, they all have access to the same data and variables. If two threads simultaneously attempt to update a global counter variable, it is possible for their operations to interleave in such way that the global state is not correctly modified. Although such a case may only arise only one time out of thousands, a concurrent program needs to coordinate the activities of multiple threads using something more reliable that just depending on the fact that such interference is rare.

`Executor`: An object that executes submitted `Runnable` tasks.    
`ExecutorService`: A more extensive interface.    
`ThreadPoolExecutor`: Provides an extensible thread pool implementation.    
`Executors`: Provides convenient factory methods for these Executors.    

`AbstractExecutorService`: Provides default implementations of ExecutorService execution methods.    
`ScheduledExecutorService`: An ExecutorService that can schedule commands to run after a given delay, or to execute periodically.

## `ExecutorService`的生命周期
* Active
* Shutting Down
* Shutdown

## Synchronizers (synchronization aids)
* CyclicBarrier循环屏障: A synchronization aid that allows a set of threads to all wait for each other to reach a common barrier point.
* Phaser
* CountDownLatch: 当counter为1时为被用作start signal，为N时为complete signal。
* Exchanger
* Semaphore
* SynchronousQueue

## Potential threading problems
* Deadlock
* Starvation
* Livelock
* Race conditions

## Concurrent Collections
