---
layout: post
title: "Java中的assert断言"
date: 2018-06-29 15:52:18 +0700
comments: true
categories: Java
---
使用Java已经有了10个年头，难以想象居然很少使用assert关键字。

[Oracle官方指南](https://docs.oracle.com/javase/8/docs/technotes/guides/language/assert.html)中详细介绍了assert的用法。

<!-- more -->

>An assertion is a statement in the Java programming language that enables you to test your assumptions about your program. For example, if you write a method that calculates the speed of a particle, you might assert that the calculated speed is less than the speed of light.

>Each assertion contains a boolean expression that you believe will be true when the assertion executes. If it is not true, the system will throw an error. By verifying that the boolean expression is indeed true, the assertion confirms your assumptions about the behavior of your program, increasing your confidence that the program is free of errors.

>Experience has shown that writing assertions while programming is one of the quickest and most effective ways to detect and correct bugs. As an added benefit, assertions serve to document the inner workings of your program, enhancing maintainability.
