---
title: TortoiseGit如何通过ssh连接github
date: 2015-02-04 16:25:05
toc: true
categories:
- 团队协作
- git
tags:
- TortoiseGit
- ssh
- github
---

## 打开PuTTYgen。

{% asset_img 1-1.jpg %}

<!-- more -->

## 点击Generate,生成密钥对(可以点击其他位置，加快生成速度)。

{% asset_img 1-2.jpg %}

## 拷贝公钥。

{% asset_img 1-3.jpg %}

## 进入github,将上面的公钥加入ssh中。

## 点击保存私钥，my.ppk文件。

{% asset_img 1-4.jpg %}

## 在tortoisegit中配置ssh。

{% asset_img 1-5.jpg %}

## 若在第3步忘记拷贝公钥，可以打开PuTTYgen，加载第5步保存的ppk文件，重复3~6步骤即可。

{% asset_img 1-6.jpg %}
