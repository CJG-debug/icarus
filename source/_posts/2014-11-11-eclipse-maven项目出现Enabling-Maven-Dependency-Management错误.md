---
title: eclipse maven项目出现Enabling Maven Dependency Management错误
date: 2014-11-11 17:24:18
toc: true
categories:
- IDE
- eclipse
tags:
- eclipse
- maven
- Enabling Maven Dependency Management
---
## 背景

```
eclipse maven项目出现如下错误，怎么办？
```

{% asset_img 1-1.jpg %}
<!-- more -->

## 右键选中你的项目，maven<<disable maven naure

## cmd  在doc界面进入到你的项目目录，执行如下代码

{% codeblock lang:bash %}
mvn eclipse:clean
{% endcodeblock %}

## 再次进去到eclipse中，右键选中你的项目，Configure << Convert into Maven Projec

