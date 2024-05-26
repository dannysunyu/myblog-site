+++
title = 'Beyond Java8'
date = 2024-03-25T17:43:54+08:00
draft = false
+++

在入职Grab后就开始专注Kotlin，我就没碰过Java了，所以Java 8之后语言的新变化知之甚少。但有点是肯定的，这门语言变得越来越复杂。

当时我甚至觉得Kotlin这样新的JVM语言优于Java。Java已经不再是一门值得关注的语言。甚至我觉得我以后不太可能用Java了。

Compiler bugs
All software has bugs, and sometimes the JVM, the Java compiler, or both have bugs. When you are using a 10-year-old version of the JVM and Java compiler, you run a much greater risk of compiler bugs, especially around features introduced near to that release.

There were many compilation problems around lambdas which were introduced in Java 8. If you are using the Java compiler from JDK 8 to target Java 8 JVMs you can still run into those bugs. Even if you are keeping your JDK 8 up-to-date many fixes are not backported. You can find ones on the issue tracker without much effort.

Now is the Java compiler in JDK 22 completely bug-free? No. But is using the Java compiler from JDK 22 on sources targeting Java 8 using only Java 8 language features much safer than using one from JDK 8? Absolutely.




