+++
title = '学习Kotlin'
date = 2024-05-24T18:05:54+08:00
draft = false
+++

Kotlin的杀手锏是与Java的互操作性。

**Kotlinx** — a set of optional, first-party libraries provided by JetBrains that extend on the base functionality in the 
Kotlin language and standard library. The **Coroutines** library is also part of Kotlinx.

**CIO** — coroutine-based I/O.

**Structured Concurrency** — A paradigm for managing batches of coroutines and handling them collectively as resources.

**async** — A coroutine builder that can be used as an alternative to launch. Much like launch, async accepts a lambda
expression as an argument, which is where you can call other code that suspends. The big difference between these two
functions is their return types: 

# Coroutines

>Unlike threads, coroutines can execute and wait for the completion of other work without blocking the thread they are 
> launched on – thanks to the magic of suspending functions.


>Kotlin 1.3 introduced stable support for coroutines, but coroutines are not new or exclusive to Kotlin. The concept of 
a coroutine dates back to the 1950s, and they have been implemented in many programming languages.

>Coroutines are based on the idea of functions being able to suspend, meaning that a function can be paused until a 
long-running operation completes.

>Coroutines provide a high-level and safer set of tools to help you build asynchronous code. Under the hood, Kotlin’s 
coroutines use threads to perform work in parallel, but you often do not have to worry about this detail.

>Kotlin does not ship with support for coroutines. 

