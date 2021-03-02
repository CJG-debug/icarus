---
title: 如何将ubuntu打造成mac
date: 2017-03-29 15:01:45
toc: true
categories:
- 操作系统
- linux
tags:
- ubuntu
- mac
- style
---

{% asset_img 1-1.png %}

## 添加macbuntu源

{% codeblock lang:bash %}
sudo add-apt-repository ppa:noobslab/macbuntu 
{% endcodeblock %}

## 更新

{% codeblock lang:bash %}
sudo apt-get update
{% endcodeblock %}

<!-- more -->

## 安装相关包

{% codeblock lang:bash %}
sudo apt-get install macbuntu-os-icons-lts-v8 macbuntu-os-ithemes-lts-v8 slingscold albert macbuntu-os-plank-theme-lts-v8					
{% endcodeblock %}

## 安装unity-tweak-tool

{% codeblock lang:bash %}
sudo apt-get install unity-tweak-tool 
{% endcodeblock %}

## 打开unity-tweak-tool

## 设置主题

{% asset_img 1-2.png %}
{% asset_img 1-3.png %}

## 设置图标

{% asset_img 1-4.png %}
{% asset_img 1-5.png %}

## 设置指针

{% asset_img 1-6.png %}
{% asset_img 1-7.png %}

## 替换Ubuntu Desktop为Mac(需重启)

{% codeblock lang:bash %}
cd && wget -O Mac.po http://drive.noobslab.com/data/Mac/change-name-on-panel/mac.po
cd /usr/share/locale/zh_CN/LC_MESSAGES; sudo msgfmt -o unity.mo ~/Mac.po;rm ~/Mac.po;cd
{% endcodeblock %}

**其中 /zh_CN/需替换为本机的locale**

**修改前**

{% asset_img 1-8.png %}

**修改后**

{% asset_img 1-9.png %}

## 修改启动器(需重启)

{% codeblock lang:bash %}
wget -O launcher_bfb.png http://drive.noobslab.com/data/Mac/launcher-logo/apple/launcher_bfb.png
sudo mv launcher_bfb.png /usr/share/unity/icons/
{% endcodeblock %}

**修改前**

{% asset_img 1-10.png %}

**修改后**

{% asset_img 1-11.png %}

## 修复libreoffice样式

{% codeblock lang:bash %}
sudo apt-get install libreoffice-style-sifr
{% endcodeblock %}

**打开任意一个libreoffice软件，以writer为例**

{% asset_img 1-14.png %}

{% asset_img 1-15.png %}

## 更改Plank

**打开Plank**

{% asset_img 1-16.png %}

**在Plank Ctrl+鼠标右击，弹出菜单**

{% asset_img 1-17.png %}

{% asset_img 1-18.png %}

## 设置Alert

**打开alert**

{% asset_img 1-19.png %}

**设置hot key**

{% asset_img 1-20.png %}

{% asset_img 1-21.png %}

## 隐藏侧边栏

**打开unity-tweak-tool**

{% asset_img 1-22.png %}

{% asset_img 1-23.png %}