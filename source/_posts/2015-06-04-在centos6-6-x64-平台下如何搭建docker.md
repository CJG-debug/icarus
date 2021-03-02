---
title: 在centos6.6(x64)平台下如何搭建docker
date: 2015-06-04 19:17:51
toc: true
categories:
- docker
tags:
- docker
- centos6.6
- install
---

## 安装epel源

{% codeblock lang:bash %}
yum install http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
{% endcodeblock %}

## 安装docker

{% codeblock lang:bash %}
yum install docker-io
{% endcodeblock %}

<!-- more -->

## 启动docker

{% codeblock lang:bash %}
service docker start
chkconfig docker on#设置开机启动
{% endcodeblock %}

## 验证是否启动成功

{% codeblock lang:bash %}
docker info
{% endcodeblock %}
