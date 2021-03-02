---
title: javascript函数的重载
date: 2015-02-09 15:07:59
toc: true
categories:
- 大前端
- javascript
tags:
- javascript
- function
- 重载
---

## javascript函数不存在重载的概念。函数的参数与调用没有关系，后面会覆盖前面的定义。如果函数有一个参数，但传入两个参数，仅仅会匹配一个。

{% codeblock lang:javascript %}
function sum(num1,num2){
	return num1+num2;
}


function sum(num1){
	return num1+100;
}

alert(sum(5));
alert(sum(5,10));
{% endcodeblock %}

<!-- more -->

## 结果都是105，即调用最后一个sum函数。

## 换一种方法，相信大家会容易明白点。

{% codeblock lang:javascript %}
var sum=function(num1,num2){
	return num1+num2;
};

var sum=function(num1){
	return num1+100;
};

alert(sum(5));
alert(sum(5,10));
{% endcodeblock %}

## 源码下载:{% asset_link function_reload.txt function_reload.txt %}

