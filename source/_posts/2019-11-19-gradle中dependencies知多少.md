---
title: gradle中dependencies知多少
date: 2019-11-19 08:38:09
toc: true
categories:
- 构建
- gradle
tags:
- gradel
- dependencies
---

## [术语](https://docs.gradle.org/current/userguide/dependency_management_terminology.html)


## scope 

**[java plugin参考文档](https://docs.gradle.org/current/userguide/java_plugin.html#sec:java_plugin_and_dependency_management)**

- implementation
- compile/api
- compileOnly/provided
- runtimeOnly

## 关系

- A<--compile--B<--**--C

**B、C模块都可使用A模块**

- A<--implementation--B<--**--C

**B模块可以使用A模块，C模块不可使用A模块**

- A<--compileOnly--B<--**--C

**B模块可以使用A模块，C模块不可使用A模块**