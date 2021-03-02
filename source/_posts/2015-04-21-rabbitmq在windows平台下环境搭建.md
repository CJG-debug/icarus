---
title: rabbitmq在windows平台下环境搭建
date: 2015-04-21 21:38:27
toc: true
categories:
- 消息中间件
- rabbitmq
tags:
- rabbitmq
- erlang
- install
---
## 下载{% link erlang http://pan.baidu.com/s/1i4uHp45 %}（密码：7s0g）

## 安装

## 配置环境变量

{% asset_img 1-1.jpg %}

<!-- more -->

## 下载{% link rabbitmq http://pan.baidu.com/s/1mh4K5Nq %}（密码：bj2r）

## 安装

## 配置环境变量

{% asset_img 1-2.jpg %}

{% asset_img 1-3.jpg %}

## 安装web监控，在命令提示符中输入如下代码（记得重启命令提示符和管理权限）

{% codeblock lang:bash%}
rabbitmq-plugins enable rabbitmq_management
{% endcodeblock %}

## 重启服务

{% codeblock lang:bash%}
rabbitmq-service stop
rabbitmq-service start
{% endcodeblock %}

## 打开浏览器，输入http://localhost:15672<br/>
默认用户及密码：guest/guest（仅在本机访问，一般重新创建用户）

