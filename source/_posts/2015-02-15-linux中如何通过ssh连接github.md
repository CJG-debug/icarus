---
title: linux中如何通过ssh连接github
date: 2015-02-15 10:03:28
toc: true
categories:
- 团队协作
- git
tags:
- github
- linux
- git
- ssh
---

## 生成新的ssh，放置在/data/.ssh/目录下

{% codeblock lang:bash %}
ssh-keygen -t rsa -C "821192673@qq.com"
#为邮箱地址
{% endcodeblock %}

## 将生成的私钥加入ssh-agent中

{% codeblock lang:bash %}
#判断ssh-agent是否启动
eval "$(ssh-agent -s)"
ssh-add /data/.ssh/id_rsa
{% endcodeblock %}

<!-- more -->

## 拷贝id_rsa.pub公钥内容，并加入github的ssh中

## 测试是否成功

{% codeblock %}
ssh -T git@github.com
{% endcodeblock %}

