---
title: mysql全文检索
date: 2020-04-09 09:40:42
toc: true
categories:
- 数据库
- mysql
tags:
- mysql
- 全文检索
---

**以base_person为例，基于InnoDB**

```
CREATE TABLE `base_person` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `address` text,
  `bp_attention` tinyint(4) NOT NULL DEFAULT '0',
  `birthday` varchar(10) DEFAULT NULL,
  `t_create_time` datetime NOT NULL,
  `t_creator` bigint(20) NOT NULL,
  `t_deleted` bit(1) NOT NULL,
  `domicile` text,
  `family_relation` varchar(2) DEFAULT NULL,
  `bp_foreign` tinyint(4) NOT NULL DEFAULT '0',
  `id_card` varchar(30) NOT NULL,
  `bp_id_card_image` longtext,
  `id_type` varchar(2) NOT NULL,
  `bp_image` longtext,
  `marital_status` varchar(2) DEFAULT NULL,
  `t_modifier` bigint(20) NOT NULL,
  `t_modify_time` datetime NOT NULL,
  `name` varchar(50) NOT NULL,
  `nation` varchar(16) DEFAULT NULL,
  `occupation` varchar(30) DEFAULT NULL,
  `phone` varchar(20) NOT NULL,
  `political_status` varchar(2) DEFAULT NULL,
  `province_id` bigint(20) DEFAULT NULL,
  `sex` varchar(2) DEFAULT NULL,
  `age` int(11) NOT NULL,
  `company_address` varchar(255) NOT NULL,
  `company_name` varchar(255) NOT NULL,
  `culture` varchar(255) NOT NULL,
  `id_card_validity` varchar(255) DEFAULT NULL,
  `nationality` varchar(255) NOT NULL,
  `position` varchar(255) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `base_person_uindex` (`id_card`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

```

<!-- more -->

## 创建/删除

- 创建

**创建表的同时创建全文索引**

```
CREATE TABLE `base_person` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `address` text,
  ……
  PRIMARY KEY (`id`),
  ……
  fulltext ft_base_person2 (address,domicile,name,phone) WITH PARSER ngram
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

**通过alter方式**

```
alter table base_person add fulltext index ft_base_person (address,domicile,name,phone) WITH PARSER ngram;
```

**通过create方式**
```
create fulltext index ft_base_person on base_person (address,domicile,name,phone) with parser ngram;
```

- 删除

**通过alter方式**

```
alter table base_person drop index ft_base_person;
```
**通过drop方式**

```
drop index ft_base_person on base_person;
```

## 使用

- 自然语言

**查出含有黑龙江和138577的记录，默认已排序**

```
SELECT address,domicile,name,phone FROM base_person where match(address,domicile,name,phone) against('黑龙江 138577');
```
{% asset_img 1.png %}

**展示关联分值**

```
SELECT address,domicile,name,phone,match(address,domicile,name,phone) against('黑龙江 138577') as score FROM base_person;
```
{% asset_img 2.png %}

**查出含有黑龙江和138577的记录和分值，并排序**

```
SELECT address,domicile,name,phone,match(address,domicile,name,phone) against('黑龙江 138577') as score FROM base_person where match(address,domicile,name,phone) against('黑龙江 138577')
```
{% asset_img 3.png %}

- BOOLEAN模式

**TODO**

- explain模式

**TODO**

## 注意点

https://dev.mysql.com/doc/refman/5.7/en/fulltext-restrictions.html

## 优化

- [ngram_token_size][5]

如果需要搜索单字，就要把ngram_token_size设置为1

**通过mysqld**

```
mysqld --ngram_token_size=1
```

**通过my.cnf**

```
[mysqld] 
ngram_token_size=1
```

****须重建索引****

## 扩展
[1]:https://dev.mysql.com/doc/refman/5.7/en/fulltext-search.html

[2]:https://www.jianshu.com/p/c48106149b6a/

[3]:https://wpdatatables.com/mysql-best-practices/

[4]:https://dev.mysql.com/doc/refman/5.7/en/writing-full-text-plugins.html

[5]:https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_ngram_token_size

[6]:https://blog.csdn.net/sweeper_freedoman/article/details/82847754

[7]: https://dev.mysql.com/doc/internals/en/full-text-search.html