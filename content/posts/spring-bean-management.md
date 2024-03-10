+++
title = 'Spring的容器中获取Bean'
date = 2024-02-14T12:40:18+08:00
draft = false
+++

默认情况下，Spring项目启动时，会把Beans都创建好放在IOC容器中。如果想要主动获取这些Beans，可以通过如下方式：

## 根据name获取Bean

```java
Object getBean(String name);
```

## 根据类型获取Bean

```java
<T> T getBean(Class<T> requiredType);
```

## 根据name获取Bean（带类型转换）

```java
<T> T getBean(String name, Class<T> requiredType);
```
