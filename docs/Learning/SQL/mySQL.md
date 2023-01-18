---
# MYSQL 笔记

---

# 计算机语言

## 机器语言
## 汇编语言
## 高级语言
# sql 语言基础
## 语法特点
- sql 对关键字的大小写不敏感
- sql语句可以以单行或者多行书写，以分行结束
- sql的注释
```
-- 单行注， -- 后面一定要加空格
#单行注释，#后面可加空格可不加空格
SELECT * FROM emp; -- 这里是注释
```
/*
多行注释
多行注释
*/



# 数据库系统简介
## 关系型数据库（RDBMS）
Oracle 数据库
Mysql数据库
SQL server数据库
PostgreSQL
SQLite

## 非关系数据库（NoSQL）
Redis
MongoDB
Elasticserach
Cassandra
HBase

# sql和数据库管理系统的关系
- SQL是一种用于操作数据库的语言，SQL适用于所有关系型数据库。
- MySQL, Oracle ,SQLServer 是一个数据库软件，这些数据库软件支持SQL，也就是通过SQL可以使用这些软件，不过每一个数据库系统会在标准SQL的基础上扩展自己的SQL语法。
- 大部分的NoSQL有自己的语言，对SQL的支持并不好


# MySQL版本
## MySQL Community Server 
社区版，免费
## MySQL Enterprise Edition
## MySQL Cluster
## ......等


# 数据库操作指令
## 数据库相关操作
### 终端执行
```
mysql -u root -p
```
### 退出数据库
```
quit;
```
### 查询所有数据库
```
show databases;
```
### 创建数据库：
```
create database 数据库名称;
```
### 查看数据库详情：
```
show create database 数据库名称
```
### 创建数据库（指定字符集）：
```
create database 数据库名称 character set gbk/utf8;
```
### 删除数据库：
```
drop database 数据库名称;
```

### 使用数据库：
```
use 数据库名称;
```

# mysql
## 常用图形工具
### Navicat
### SQLyog
### MySQL Workbench
## 常用工具
### DataGrip
### phpMyAdmin
### MySQLDumper