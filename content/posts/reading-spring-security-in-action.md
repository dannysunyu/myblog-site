+++
title = '「Spring Security in Action」读书笔记'
date = 2024-03-14T14:27:10+08:00
draft = false
+++

Java专家Laurentiu Spilca于2020年出版了「Spring Security in Action」一书。

根据Manning Publications官方和Amazon上的讯息，他将于2024年4月出版本书第二版。

{{< figure src="https://images.manning.com/360/480/resize/book/6/e751b54-0e51-4676-b05f-c0f023d152b9/Spilca-Spring-HI.png" title="Spring Security in Action" width="300px" height="480px" >}}

虽然我没有第二版的书，但是读一下2020年版的应该不会太过时。

这篇博文记录书中的摘录、我的笔记和感想。

> _**Spring Security** is a framework that belongs to **application-level security**._

> _**Application-level security** refers to everything that an application should do to protect the environment it executes in, as well as the data it processes and stores. Mind that this isn’t only about the data affected and used by the application. An application might contain vulnerabilities that allow a malicious individual to affect the entire system!_

> _Through **authentication**, an application identifies a user (a person or another application). The purpose of identifying these is to be able to decide afterward what they should be allowed to do—that’s **authorization**._
