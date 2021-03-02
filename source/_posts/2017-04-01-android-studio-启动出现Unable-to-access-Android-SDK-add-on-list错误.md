---
title: android studio 启动出现Unable to access Android SDK add-on list错误
date: 2017-04-01 15:43:35
toc: true
categories:
- 移动开发
- android
tags:
- android
- studio
- 启动错误
---

{% asset_img 1-1.png %}

<!-- more -->

**在bin/idea.properties文件最后加入如下内容**

{% codeblock lang:properties %}
disable.android.first.run=true
{% endcodeblock %}
