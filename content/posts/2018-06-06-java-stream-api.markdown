---
layout: post
title: "Java Stream API"
date: 2018-06-06 18:02:25 +0700
comments: true
categories: Java
keywords: 孙昱, octopress
---
Java 8引入了Stream的概念，掌握这个概念的最佳方式是阅读Java官方文档。

<!-- more -->

可以浏览一下Oracle Java文档或是[Android官方文档](https://developer.android.com/reference/java/util/stream/package-summary)。

有些关键的概念需要掌握：stream、source、stream pipeline、stream operations、intermediate operations、terminal operation。

```java
/**
 * Returns a sequential {@code Stream} with this collection as its source.
 *
 * <p>This method should be overridden when the {@link #spliterator()}
 * method cannot return a spliterator that is {@code IMMUTABLE},
 * {@code CONCURRENT}, or <em>late-binding</em>. (See {@link #spliterator()}
 * for details.)
 *
 * @implSpec
 * The default implementation creates a sequential {@code Stream} from the
 * collection's {@code Spliterator}.
 *
 * @return a sequential {@code Stream} over the elements in this collection
 * @since 1.8
 */
default Stream<E> stream() {
    return StreamSupport.stream(spliterator(), false);
}
```

Stream实例只能被使用一次，否则会抛出Runtime Exception：
```
java.lang.IllegalStateException: stream has already been operated upon or closed
```

The right and most convenient way to use streams are by a stream pipeline, which is a chain of stream source, intermediate operations, and a terminal operation.    


## 将`Stream`转换为`int`、`long`或`double`流

```java
abstract DoubleStream	mapToDouble(ToDoubleFunction<? super T> mapper)

abstract IntStream mapToInt(ToIntFunction<? super T> mapper)

abstract LongStream mapToLong(ToLongFunction<? super T> mapper)
```

## allMatch，anyMatch和noneMatch方法

```java
abstract boolean allMatch(Predicate<? super T> predicate)

abstract boolean anyMatch(Predicate<? super T> predicate)

abstract boolean noneMatch(Predicate<? super T> predicate)
```
