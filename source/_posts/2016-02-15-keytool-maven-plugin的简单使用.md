---
title: keytool-maven-plugin的简单使用
date: 2016-02-15 13:36:09
toc: true
categories: 
- 构建
- maven
tags:
- maven
- keytool-maven-plugin
---

## 在pom文件的plugin节点中加入如下内容

{% codeblock lang:xml %}
<plugin>
	<groupId>org.codehaus.mojo</groupId>
	<artifactId>keytool-maven-plugin</artifactId>
	<version>1.4</version>
	<configuration>
		<keystore>${basedir}/src/main/resources/yands.keystore</keystore>
		<dname>cn=localhost</dname>
		<keypass>changeit</keypass>
		<storepass>changeit</storepass>
		<alias>yands</alias>
		<keyalg>RSA</keyalg>
		<file>${basedir}/src/main/resources/yands.cer</file>
	</configuration>
</plugin>
{% endcodeblock %}

## 解释如下

{% asset_img 1-1.jpg %}

<!-- more -->

## 步骤如下

### 删除已经存在的keystore文件

{% codeblock lang:bash %}
keytool:clean
{% endcodeblock %}

### 生成keystore文件

{% codeblock lang:bash %}
keytool:generateKeyPair
{% endcodeblock %}

### 生成客户端使用cer文件

{% codeblock lang:bash %}
keytool:exportCertificate
{% endcodeblock %}