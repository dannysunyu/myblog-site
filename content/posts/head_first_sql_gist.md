+++
title = 'Head First SQL的精要'
date = 2024-02-17T22:30:10+08:00
draft = false
tags = ["sql", "mysql"]
+++

第一章

SQL is case-insensitive. But it's considered a good programming practice in SQL.

```sql
CREATE DATABASE gregs_list;
```

The **semicolon** is there to indicate that the command has ended.

**TIMESTAMP** is usually used to capture the current time. **DATETIME** is best used to store a future event.

# DESC命令
To see how *my_contacts* table you created looks, you can use the **DESC** command to view it:
```sql
DESC my_contacts;
```
**DESC** is short for *DESCRIBE*.

# INSERT语句
```sql
INSERT INTO your_table (column_name1, column_name2,...) VALUES ('value1', 'value2',...);
```
IMPORTANT: the values need to be in the same order as the column names.

Any value that goes into a VARCHAR, CHAR, DATE, or BLOB column has single quotes around it.

NULL相当于undefined。

> You can’t compare one NULL to another. A value can be NULL, but it never equals NULL because NULL is an undefined value!

# 第四章

**LIKE** isn’t specific enough to target precise data.

> _... consider how much room on your hard drive it will take up when your database grows to an enormous size._

# Cartesian join（亦称Cross join或Cartesian product）

A Cartesian join is a type of inner join. An inner join is basically just a Cartesian join where some results rows are removed by a condition in the query.

An <b>outer joins</b> returns all rows from one of the tables, along with matching information from another table.
