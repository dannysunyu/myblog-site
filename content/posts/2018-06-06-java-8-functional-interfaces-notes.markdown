+++
title = 'Java 8 Functional Interfaces笔记'
date = 2018-06-06T17:15:33+07:00
draft = false
tags = ["java"]
+++

最近在准备OCJP 8考试，需要熟悉一下Java 8引入的函数式编程的概念。具体包括了Functional Interfaces、Lambda表达式、Stream API等新知识。

<!-- more -->

最值得阅读的文档一般都是官方文档。[Oracle](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html)和[Android](https://developer.android.com/reference/java/util/function/package-summary)都有文档的链接。

## 4个内建(Built-in)的Functional interfaces
Functional Interfaces，或称为函数式接口，主要是指列于`java.util.function`包下的所有新的接口。它们被设计出来以满足通用的需求。乍看下共有43个接口，会觉得很吓人。其实它们都是从4个最典型的接口派生而来，为了某个specialization的、更具体化的场景而设计的，说白了就是为了让程序员能够根据需求选择出最具体化的接口。        

### 1. Function接口    
```java
@FunctionalInterface
public interface Function<T, R> {
    /**
     * Applies this function to the given argument.
     *
     * @param t the function argument
     * @return the function result
     */
    R apply(T t);
```

### 2. Supplier接口    
```java
@FunctionalInterface
public interface Supplier<T> {
    /**
     * Gets a result.
     *
     * @return a result
     */
    T get();
```
### 3. Predicate接口    
```java
@FunctionalInterface
public interface Predicate<T> {
    /**
     * Evaluates this predicate on the given argument.
     *
     * @param t the input argument
     * @return {@code true} if the input argument matches the predicate,
     * otherwise {@code false}
     */
    boolean test(T t);
```

### 4. Consumer接口    
```java
@FunctionalInterface
public interface Consumer<T> {
    /**
     * Performs this operation on the given argument.
     *
     * @param t the input argument
     */
    void accept(T t);
```

Lambda表达式和函数式接口并不是一一对应的关系，一个Lambda表达式可以与多个Functional Interfaces兼容（compatible）。

## Primitive Functional Interfaces
Primitive Functional Interfaces只包含`double`、`int`和`long`类型，而不包含`char`、`float`和`short`类型，所以`java.util.function`包下就不存在类似`CharSupplier`的接口。


## 补充
arity的解释是"元数"，就是参数数目的意思。
