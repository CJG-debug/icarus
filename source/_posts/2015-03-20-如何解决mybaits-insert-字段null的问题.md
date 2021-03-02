---
title: 如何解决mybaits insert 字段null的问题
date: 2015-03-20 08:34:17
toc: true
categories:
- mybatis
tags:
- mybatis
- insert
- 字段
- null
---

## 可在mybatis配置文件settings节点中，加入如下内容

{% codeblock lang:xml %}
<settings>
	<setting name="jdbcTypeForNull" value="NULL"/>
</settings>
{% endcodeblock %}

