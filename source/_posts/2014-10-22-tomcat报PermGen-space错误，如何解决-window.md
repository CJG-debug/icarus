---
title: tomcat报PermGen space错误，如何解决(window)
date: 2014-10-22 17:40:03
toc: true
categories:
- 服务器
- tomcat
tags:
- tomcat
- PermGen space
---
修改TOMCAT_HOME/bin/catalina.bat，在“echo "Using CATALINA_BASE:   $CATALINA_BASE"”上面加入以下行
{% codeblock lang:init %}
@set JAVA_OPTS=%JAVA_OPTS% -server -XX:PermSize=128M -XX:MaxPermSize=512M
{% endcodeblock %}
