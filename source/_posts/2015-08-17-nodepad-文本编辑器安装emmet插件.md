---
title: nodepad++文本编辑器安装emmet插件
date: 2015-08-17 09:21:10
toc: true
categories:
- emmet
tags:
- emmet
- nodepad++
- install
---

## 安装{% link nodepad++ https://notepad-plus-plus.org %}

## 安装emmet插件

{% asset_img 1-1.jpg %}

<!-- more -->

{% asset_img 1-2.jpg %}

## 修改快捷方式为TAB

{% asset_img 1-3.jpg %}

{% asset_img 1-4.jpg %}

{% asset_img 1-5.jpg %}

## 测试安装是否成功

### 新建文档，输入html:5，按TAB键。神奇的事情发生了。

### 原始代码

{% codeblock lang:html %}
html:5
{% endcodeblock %}

### 变化后的代码

{% codeblock lang:html %}
<!doctype html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	
</body>
</html>
{% endcodeblock %}

### 如出现Unknown exception和python script plugin did not accept the script错误提示，不要惊慌。
重新安装{% link "python script" http://sourceforge.net/projects/npppythonscript/?source=typ_redirect %}就行了。

