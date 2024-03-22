---
layout: post
title: "Java 8 Optional类的要点分析"
date: 2018-06-11 21:15:02 +0700
comments: true
categories:
---

首先仔细浏览[Oracle](https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html)和[Android](https://developer.android.com/reference/java/util/Optional)官方API文档。

<!-- more -->

然后仔细浏览Urma所著的Oracle的Java官方[Tutorial](http://www.oracle.com/technetwork/articles/java/java8-optional-2175753.html)。

Urma关于空指针的一段话：
>I will argue in this article that using null to represent the absence of a value is a wrong approach. What we need is a better way to model the absence and presence of a value.

关于引入`java.util.Optional`类的初衷：
>It is important to note that the intention of the Optional class is not to replace every single null reference. Instead, its purpose is to help design more-comprehensible APIs so that by just reading the signature of a method, you can tell whether you can expect an optional value. This forces you to actively unwrap an Optional to deal with the absence of a value.

## Optional.map和Optional.flatMap的区别
其实只要仔细读读Optional类的源码就明白两者的区别了：
```java
/**
 * If a value is present, apply the provided mapping function to it,
 * and if the result is non-null, return an {@code Optional} describing the
 * result.  Otherwise return an empty {@code Optional}.
 *
 * @apiNote This method supports post-processing on optional values, without
 * the need to explicitly check for a return status.  For example, the
 * following code traverses a stream of file names, selects one that has
 * not yet been processed, and then opens that file, returning an
 * {@code Optional<FileInputStream>}:
 *
 * <pre>{@code
 *     Optional<FileInputStream> fis =
 *         names.stream().filter(name -> !isProcessedYet(name))
 *                       .findFirst()
 *                       .map(name -> new FileInputStream(name));
 * }</pre>
 *
 * Here, {@code findFirst} returns an {@code Optional<String>}, and then
 * {@code map} returns an {@code Optional<FileInputStream>} for the desired
 * file if one exists.
 *
 * @param <U> The type of the result of the mapping function
 * @param mapper a mapping function to apply to the value, if present
 * @return an {@code Optional} describing the result of applying a mapping
 * function to the value of this {@code Optional}, if a value is present,
 * otherwise an empty {@code Optional}
 * @throws NullPointerException if the mapping function is null
 */
public<U> Optional<U> map(Function<? super T, ? extends U> mapper) {
    Objects.requireNonNull(mapper);
    if (!isPresent())
        return empty();
    else {
        return Optional.ofNullable(mapper.apply(value));
    }
}

/**
 * If a value is present, apply the provided {@code Optional}-bearing
 * mapping function to it, return that result, otherwise return an empty
 * {@code Optional}.  This method is similar to {@link #map(Function)},
 * but the provided mapper is one whose result is already an {@code Optional},
 * and if invoked, {@code flatMap} does not wrap it with an additional
 * {@code Optional}.
 *
 * @param <U> The type parameter to the {@code Optional} returned by
 * @param mapper a mapping function to apply to the value, if present
 *           the mapping function
 * @return the result of applying an {@code Optional}-bearing mapping
 * function to the value of this {@code Optional}, if a value is present,
 * otherwise an empty {@code Optional}
 * @throws NullPointerException if the mapping function is null or returns
 * a null result
 */
public<U> Optional<U> flatMap(Function<? super T, Optional<U>> mapper) {
    Objects.requireNonNull(mapper);
    if (!isPresent())
        return empty();
    else {
        return Objects.requireNonNull(mapper.apply(value));
    }
}
```

可见两者唯一的区别就是map方法在最后用 `Optional.ofNullable` 包装了返回值，而flatMap没有。

## Optional类的primitive版本
`OptionalInt`、`OptionalLong`、`OptionalDouble`，它们的对应`get`方法签名变成了`getAsInt`、`getAsLong`、`getAsDouble`。
