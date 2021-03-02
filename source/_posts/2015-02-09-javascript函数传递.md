---
title: javascript函数传递
date: 2015-02-09 14:52:34
toc: true
categories:
- 大前端
- javascript
tags:
- javascript
- function
- 传递
---

## 由于函数是对象，所以可以通过参数传递进来。

{% codeblock lang:javascript %}
function callFun(fun,arg){
	return fun(arg);
}

function say(str){
	alert("hello "+str);
}

function sum(num){
	return num+100;
}
callFun(say,"John");

alert(callFun(sum,10));
{% endcodeblock %}

<!-- more -->

## 函数作为返回值返回

{% codeblock lang:javascript %}
function fn1(arg){
	var rel=function(num){
		return arg+num;
	}
	return rel;
}
//返回函数对象
var f=fn1(20);
alert(f(11));
{% endcodeblock %}

## 感觉arg的变量域扩大了一样。

## 源码下载:{% asset_link function_transfer.txt function_transfer.txt %}

