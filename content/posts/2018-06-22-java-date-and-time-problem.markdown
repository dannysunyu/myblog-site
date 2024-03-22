---
layout: post
title: "Java Date and Time Problem"
date: 2018-06-22 22:08:32 +0700
comments: true
categories:
---

https://www.hackerrank.com/challenges/java-date-and-time/problem

<!-- more -->

这道算法题使用Java 8的Date & Time API很容易解决了。

```java
public class Solution {
    private static String getDay(String day, String month, String year) {
        int d = Integer.parseInt(day);
        int m = Integer.parseInt(month);
        int y = Integer.parseInt(year);

        LocalDate date = LocalDate.of(y, m, d);
        return date.getDayOfWeek().toString();
    }

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        String month = in.next();
        String day = in.next();
        String year = in.next();

        System.out.println(getDay(day, month, year));
    }
}
```
