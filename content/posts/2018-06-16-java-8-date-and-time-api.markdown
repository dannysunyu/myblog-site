---
layout: post
title: "Java 8 Date & Time API"
date: 2018-06-16 22:43:02 +0700
comments: true
categories:
---

[Android官方文档里](https://developer.android.com/reference/java/time/package-summary)

`java.time.temporal`: lower level access to the fields.        
`java.time.format`: customization options.    

<!-- more -->

>The offset-based date-time types OffsetTime and OffsetDateTime, are intended primarily for use with network protocols and database access. For example, most databases cannot automatically store a time-zone like 'Europe/Paris', but they can store an offset like '+02:00'.

## 获取当前月份
```java
Month.from(Instant.now().atZone(ZoneId.of("Asia/Bangkok"));
```    

## Instant
An Instant represents a specific moment in time using GMT.

## Daylight Saving Time
The United States observes daylight savings time on March 12, 2017, by moving the clocks forward an hour at 2 a.m.

In the United States, daylight savings time ends on November 5th, 2017 at 02:00 a.m. and we repeat the previous hour.

实验如下：
```java
LocalDate localDate = LocalDate.of(2017, Month.NOVEMBER, 5);
LocalTime localTime = LocalTime.of(1, 0);
ZoneId zone = ZoneId.of("America/New_York");
ZonedDateTime z = ZonedDateTime.of(localDate, localTime, zone);
for (int i = 0; i < 6; i++) {
    System.out.println(z.plusHours(i));
}
```
输出如下：
```
2017-11-05T01:00-04:00[America/New_York]
2017-11-05T01:00-05:00[America/New_York]
2017-11-05T02:00-05:00[America/New_York]
2017-11-05T03:00-05:00[America/New_York]
2017-11-05T04:00-05:00[America/New_York]
2017-11-05T05:00-05:00[America/New_York]
```
