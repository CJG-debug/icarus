---
title: javascript如何定义函数
date: 2015-02-06 11:19:16
toc: true
categories:
- 大前端
- javascript
tags:
- javascript
- function
- 定义
---
## javascript函数是一种特殊的对象。

## 函数在内存中是以键值对的形式存储的。

{% asset_img 1-1.jpg %}

<!-- more -->

## 函数的定义方式有如下三种。

### 第一种方式

{% codeblock lang:javascript %}
function fn1(){
		alert("fn1");
	}
{% endcodeblock %}

### 第二种方式

{% codeblock lang:javascript %}
var fn2=function(){
	alert("fn2");
}
{% endcodeblock %}

### 第三种方式(不常见)

{% codeblock lang:javascript %}
var fn3=new Function("num1","num2","alert(num1+num2)");
fn3(1,2);
{% endcodeblock %}

### 源码下载:{% asset_link function_define.txt function_define.txt %}
