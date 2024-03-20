+++
title = 'Head First SQL的精要'
date = 2024-02-17T22:30:10+08:00
draft = false
tags = ["sql", "mysql"]
+++

第一章
NULL相当于undefined。

> You can’t compare one NULL to another. A value can be NULL, but it never equals NULL because NULL is an undefined value!

# Cartesian join（亦称Cross join或Cartesian product）

A Cartesian join is a type of inner join. An inner join is basically just a Cartesian join where some results rows are removed by a condition in the query.

An <b>outer joins</b> returns all rows from one of the tables, along with matching information from another table.
