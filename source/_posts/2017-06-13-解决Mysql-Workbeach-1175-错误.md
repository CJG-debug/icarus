---
title: 解决Mysql Workbeach 1175 错误
date: 2017-06-13 11:10:52
toc: true
categories:
- 数据库
- MySQL Workbench
tags:
- mysql
- workbeach
- 1175
---

## 背景

```
使用MySQL Workbench进行批量更新时，报如下错误
Error Code: 1175
You are using safe...without a WHERE that uses a KEY column
```

## 打开Workbench的菜单[Edit]->[Preferences...]

## 切换到[SQL Editor]页面

## 把[Forbid UPDATE and DELETE statements without a WHERE clause (safe updates)]之前的对勾去掉

## 点击[OK]按钮

## 最后记得要重启一下sql editor,建立一个新的连接就可以了
