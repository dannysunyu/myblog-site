+++
title = '安装PostgreSQL'
date = 2025-03-03T15:54:57-07:00
draft = false
+++
>Postgres似乎是比PostgreSQL更cool的称呼。

上一份工作一直在和Postgres打交道。本地Mac开发环境里，Postgres跑在了Docker容器中，非侵入式地安装。然后使用DataGrip提供的可视化界面进行数据查询。

而侵入式地安装Postgres，会把本地文件系统搞得乱糟糟。安装容易卸载难啊。

如果想geek一些的，推荐[在Docker中运行Postgres](/posts/run-postgres-on-docker/)。

### 本地安装
然而在大学课堂里，大部分教授都不懂Docker，所以课堂上要求侵入式地安装Postgres —— 我也老老实实地照做了。

一种简单的安装方式是直接从Postgres官网下载，在[下载页面](https://www.postgresql.org/download/)可找到各平台的Installer安装包。目前最新的版本是17。

初始安装后，界面只会显示默认的postgres数据库。

>注意，这里是指在Postgres中的一个叫postgres的数据库。

{{< figure src="/images/postgres-ui.png" width="480px" height="360px" >}}

直接安装Postgres也是有好处的，有一个操作Postgres的极简用户界面。界面上会列出了一个个本地创建的数据库。此外，可以用界面启动、暂停Postgres服务器。

### 设置PATH环境变量
此外，安装目录带了许多原生的命令行工具，其中有重要的**psql**命令。它的所在位置如下： 

```zsh
/Applications/Postgres.app/Contents/Versions/17/bin/psql
```

为了在Terminal运行这条命令，要把Postgres的bin目录放入PATH环境变量中。

```zsh
export PATH=$PATH:/Applications/Postgres.app/Contents/Versions/17/bin
```

这样就能运行psql命令了：
```zsh
% psql --version
psql (PostgreSQL) 17.4 (Postgres.app)
```

安装完毕后，与Postgres交互可以从psql命令行开始。需要掌握[psql的常用命令](/posts/essential-psql-commands)。

_请我喝杯咖啡吧！_

[<img src="https://tinyurl.com/57dkxa4f" width="120"/>](https://www.buymeacoffee.com/danielsun)

完毕
