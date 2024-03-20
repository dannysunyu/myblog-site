+++
title = 'Hands on Learning Postgresql'
date = 2024-03-11T21:22:44+08:00
draft = false
tags = ["sql"]
+++

这是记录我学习的Open Full Stack上的一门小课程[**Part 13 - Using relational databases**](https://fullstackopen.com/en/part13)。

这本课程是用[**PostgreSQL**](https://www.postgresql.org/)。

类似Mongoose，这门课程用到了[**Sequelize**](https://sequelize.org/)。官网的描述是：

> _**Sequelize** is a modern TypeScript and Node.js ORM for Oracle, Postgres, MySQL, MariaDB, SQLite and SQL Server, and more. Featuring solid transaction support, relations, eager and lazy loading, read replication and more._

{{< figure src="https://sequelize.org/img/logo.svg" title="Spring Security in Action" width="200px" height="360px" >}}

这里首先讲到之前课程用到的MongoDB。

> Mongo is a document database and one of its most characteristic features is that it is schemaless, i.e. the database has only a very limited awareness of what kind of data is stored in its collections. The schema of the database exists only in the program code, which interprets the data in a specific way, e.g. by identifying that some of the fields are references to objects in another collection.

The `\d` command, which tells us what tables are in the database.

```
postgres=# \d
            List of relations
 Schema |     Name     |   Type   |  Owner
--------+--------------+----------+----------
 public | notes        | table    | username
 public | notes_id_seq | sequence | username
(2 rows)
```

With the command `\d` notes, we can see how the notes table is defined:

```
postgres=# \d notes
                                     Table "public.notes"
  Column   |          Type          | Collation | Nullable |              Default
-----------+------------------------+-----------+----------+-----------------------------------
 id        | integer                |           | not null | nextval('notes_id_seq'::regclass)
 content   | text                   |           | not null |
 important | boolean                |           |          |
 date      | time without time zone |           |          |
Indexes:
    "notes_pkey" PRIMARY KEY, btree (id)
```

> _In practice, a *migration* is a single JavaScript file that describes some modification to a database. A separate migration file is created for each single or multiple changes at once._
