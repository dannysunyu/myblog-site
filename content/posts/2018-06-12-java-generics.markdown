---
layout: post
title: "Java泛型中一些难点解析"
date: 2018-06-12 11:44:52 +0700
comments: true
categories:
---

Joshua Bloch：

<!-- more -->

>For maximum flexibility, use wildcard types on input parameters that represent producers or consumers. If an input parameter is both a producer and a consumer, then wildcard types will do you no good: you
need an exact type match, which is what you get without any wildcards. Here is a mnemonic to help you remember which wildcard type to use:
PECS stands for producer-extends, consumer-super.

参考Stackoverflow上这个[问答](https://stackoverflow.com/questions/4343202/difference-between-super-t-and-extends-t-in-java)或是参考这个[Java Generics FAQs](http://www.angelikalanger.com/GenericsFAQ/FAQSections/TypeArguments.html#FAQ103)    

### What is a bounded wildcard?
A wildcard with either an upper or a lower bound.
A wildcard with an upper bound looks like " ? extends Type " and stands for the family of all types that are subtypes of Type , type Type being included.  Type is called the upper bound .
A wildcard with a lower bound looks like " ? super Type " and stands for the family of all types that are supertypes of Type , type Type being included. Type is called the lower bound .

Bounded wildcards are used as arguments for instantiation of generic types.  Bounded wildcards are useful in situations where only partial knowledge about the type argument of a parameterized type is needed, but where unbounded wildcards carry too little type information.

Example:
```java
public class Collections {
  // bounded wildcard parameterized types
  public static <T> void copy(List<? super T> dest, List<? extends T> src) {  
      for (int i = 0; i < src.size(); i++)
        dest.set(i, src.get(i));
  }
}
```
The copy method copies elements from a source list into a destination list.  The destination list must be capable of holding the elements from the source list.  We express this by means of bounded wildcards: the output list is required to have an element type with a lower bound T and the input list must have an element type with an upper bound T .  
