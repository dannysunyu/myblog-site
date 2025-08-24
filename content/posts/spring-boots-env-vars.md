+++
title = 'Spring Boot的环境变量'
date = 2025-07-08T17:28:00+07:00
draft = false
+++

在Spring Boot中，环境变量的定义，可以诸如在application.properties中：
```
server.port=${PORT}
```

这里的$PORT是一个自定义的环境变量，它将绑定系统预设的server.port，就是服务的端口号。

但是如果要自定义一个环境变量，而没有系统的某个key对应，那就不要在application.properties中绑定？
