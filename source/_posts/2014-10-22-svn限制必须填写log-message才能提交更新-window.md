---
title: svn限制必须填写log message才能提交更新(window)
date: 2014-10-22 09:55:17
toc: true
categories:
- 团队协作
- svn
tags:
- svn
- commit
- message
---
## 在svn服务端的仓库的hook目录下添加pre-commit.bat文件，内容如下
{% codeblock lang:bash %}
@echo off
setlocal
set REPOS=%1
set REV=%2
set svnlook="D:\Program Files\VisualSVN Server\bin\svnlook.exe"(改为自己的目录)
rem check that logmessage contains at least 10 characters
%svnlook% log "%REPOS%" -t "%REV%" | findstr ".........." > nul
if %errorlevel% gtr 0 goto err
echo 提交的log信息要大于10个字符，请重新提交！1>&2
exit 0
:err
echo 提交被阻止，请填写关于此次修改的log信息（需大于10个字符），然后再重新提交! 1>&2
exit 1
{% endcodeblock %}
