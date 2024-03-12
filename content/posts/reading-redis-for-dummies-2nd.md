+++
title = '「Redis for Dummies」第二版读书摘要'
date = 2024-03-11T17:30:24+08:00
draft = false
+++

**Redis** is a popular multi-model database server.

NoSQL数据库有四个主要的类型：key/value、column、document和graph。

有两个易混淆的术语：

**Data Store**是专门的数据库系统，提供高效的数据组织和访问能力。

**Data Storage**是通用的数据存储介质和设备，为Data Store等上层系统提供存储容量。

**Durability** is the ability to ensure that data is available in the event of a failure of a database component.

# 第三章

> There is no formal database creation step with Redis. There isn’t a formal table creation step with Redis either. The SET command is used to create data within the current database.

> Those familiar with formalized database creation and definition may be uncomfortable with the seemingly informal process of Redis database creation and data handling. However, it’s through this flexibility that the true power of Redis is found.
