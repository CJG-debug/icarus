---
title: vmware中linux与window文件共享
date: 2015-01-29 17:01:16
toc: true
categories:
- 虚拟机
- vmware
tags:
- vmware
- linux
- window
- 文件共享
---
## 安装vmware tools

{% asset_img 1-1.jpg %}

<!-- more -->

## 拷贝VMwareTools-9.9.0-2304977.tar.gz到/tmp

{% codeblock lang:bash %}
mount /dev/cdrom /mnt
cp /mnt/VMwareTools-9.9.0-2304977.tar.gz /tmp
{% endcodeblock %}

## 安装vmware tools

{% codeblock lang:bash %}
tar -zxvf VMwareTools-9.9.0-2304977.tar.gz
cd /tmp/vmware-tools-distrib
./vmware-install.pl
{% endcodeblock %}

## 重启系统

{% codeblock lang:bash %}
reboot
{% endcodeblock %}

## 重新安装vmware tools

{% codeblock lang:bash %}
cd /usr/bin
./vmware-config-tools.pl
{% endcodeblock %}

## 共享文件

{% asset_img 1-2.jpg %}
{% asset_img 1-3.jpg %}

## 访问共享文件

{% codeblock lang:bash %}
cd /mnt/hgfs
{% endcodeblock %}

