---
title: linux中安装nodejs
date: 2015-01-30 16:47:26
toc: true
categories:
- 大前端
- nodejs
tags:
- linux
- nodejs
- 安装
- install
---

## 下载{% link nodejs http://pan.baidu.com/s/1o6SgGLc %}(密码：fre8）

## 放在共享文件Install中

## 拷贝node-v0.10.36-linux-x86.tar.gz到/tmp

{% codeblock lang:base %}
cp /mnt/hgfs/Install/node-v0.10.36-linux-x86.tar.gz /tmp
{% endcodeblock %}

<!-- more -->

## 解压文件，并放置到/opt目录下

{% codeblock lang:base %}
tar -zxvf node-v0.10.36-linux-x86.tar.gz
mv /tmp/node-v0.10.36-linux-x86 /opt
{% endcodeblock %}

## 配置环境变量（对全部用户有效）

{% codeblock lang:base %}
vi /etc/profile
#加入如下信息
NODEJS_HOME=/opt/node-v0.10.36-linux-x86
export NODEJS_HOME
PATH=$PATH:$NODEJS_HOME/bin
export PATH
{% endcodeblock %}

## 不用重启，使环境变量起效

{% codeblock lang:base %}
source /etc/profile
{% endcodeblock %}

## 安装是否成功
{% codeblock lang:base %}
node -v
{% endcodeblock %}

