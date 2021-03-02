---
title: javascript函数传递巧解排序
date: 2015-02-12 16:07:57
toc: true
categories:
- 大前端
- javascript
tags:
- javascript
- function
- 传递
- 排序
---

## 对下面数组进行排序（按数字大小）

{% codeblock lang:javascript %}
var arr=[1,22,13,4,101];
arr.sort();
alert(arr);
{% endcodeblock %}

<!-- more -->

### 运行后，可以看出默认安装字符串排序。

### 可以在sort函数中传入函数，改变排序规则。

{% codeblock lang:javascript %}
var arr=[1,22,13,4,101];
function sortByNum(pre,next){
	if(pre>next) return 1;
	else if(pre==next) return 0;
	else return -1;
}
arr.sort(sortByNum);
alert(arr);
{% endcodeblock %}

## 对下面对象进行排序

{% codeblock lang:javascript %}
function Person(name,age){
	this.name=name;
	this.age=age;
}

var p1=new Person('Tom',22);
var p2=new Person('Ada',16);
var p3=new Person('John',14);

var p=[p1,p2,p3];

p.sort();
var show=document.getElementById("show");
for(var v in p){
	show.innerHTML+=p[v].name+" "+p[v].age+"<br/>";
}
{% endcodeblock %}

### 结果没有改变，因为不知道根据什么进行排序。
### 根据姓名排序。

{% codeblock lang:javascript %}
function sortByName(pre,next){
	if(pre.name>next.name) return 1;
	else if(pre.name==next.name) return 0;
	else return -1;
}

p.sort(sortByName)
{% endcodeblock %}

### 根据年龄排序。

{% codeblock lang:javascript %}
function sortByAge(pre,next){
	if(pre.age>next.age) return 1;
	else if(pre.age==next.age) return 0;
	else return -1;
}

p.sort(sortByAge);
{% endcodeblock %}

## 思考：如果该对象有100属性，按照上面的逻辑，我们不是得写100个sortByXX才能实现所有的排序，这样代码不就像老太婆的裹脚布又臭又长了。此时利用返回函数的方法就能轻松解决该问题。

{% codeblock lang:javascript %}
function sortByProperty(prop){
	var rel=function(pre,next){
		if(pre[prop]>next[prop]) return 1;
		else if(pre[prop]==next[prop]) return 0;
		else return -1;
	}
	return rel;
}
p.sort(sortByProperty("age"));
{% endcodeblock %}

## 源码下载:{% asset_link function_sort.txt function_sort.txt %}

