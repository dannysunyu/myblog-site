+++
title = 'Book Troubleshooting Java'
date = 2024-08-16T19:35:23+08:00
draft = false
+++

最近在读一本Larentiu Spilca写的关于Java的调试和性能刨析的书。

{{< figure src="https://m.media-amazon.com/images/I/61BaCofsSyL._SL1500_.jpg" width="400px" height="720px" >}}

# 第六章：Identifying resource consumption problems using profiling techniques

>I consider learning to use a profiler a must for all developers, as it can be a compass to guide you to the cause of a
> seemingly hopeless problem.

作者推荐[VisualVM](https://visualvm.github.io/index.html)，一款免费的profiler。此外还可以选：
* [Java Mission Control](https://jdk.java.net/jmc/8/)
* [JProfiler](https://www.ej-technologies.com/jprofiler)

A memory leak is when an app stores and keeps references to unused objects.

[LeakCanary](https://square.github.io/leakcanary/)