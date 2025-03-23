+++
title = '本地安装MongoDB 8.0+'
date = 2025-03-05T15:13:15-07:00
draft = false
+++

https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-os-x/#std-label-install-mdb-community-macos

### mongosh
The MongoDB Shell, mongosh, is a JavaScript and Node.js REPL environment for interacting with MongoDB deployments.

### MongoDB Compass



### 用命令行启动MongoDB服务器
MongoDB needs a folder/directory to store the database.    

启动mongod，需要带上存储路径
```zsh
% mongod --dbpath /opt/homebrew/var/mongodb
```

`--dbpath`参数：Directory for datafiles - defaults to `/data/db`

```zsh
% mongod --config /opt/homebrew/etc/mongod.conf
```

`/opt/homebrew/etc/mongod.conf`是MongoDB的配置文件

```textmate
systemLog:
destination: file
path: /opt/homebrew/var/log/mongodb/mongo.log
logAppend: true
storage:
dbPath: /opt/homebrew/var/mongodb
net:
bindIp: 127.0.0.1, ::1
ipv6: true
```

如果是用homebrew安装的MongoDB，可以这样启动和关闭：
```zsh
% brew services start mongodb-community
```

```zsh
% brew services stop mongodb-community
```

you should be able to directly interact with the MongoDB database by running the command:
```
% mongosh
```

### 参考
https://web.stanford.edu/class/cs142/install.html


