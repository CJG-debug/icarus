---
title: chrome80与cookie的二三事
date: 2020-03-23 14:16:02
toc: true
categories:
- 浏览器
- chrome
tags:
- chrome
- 80
- cookie
- 安全
---

## 前生今世

https://blog.chromium.org/2019/10/developers-get-ready-for-new.html

## 暗渡陈仓

**注：仅针对跨域问题**

### 暴力法（简单）

- 打开浏览器，在地址栏中输入chrome://flags

- 修改设置

{% asset_img chrome-samesite.png %}

<!-- more -->

### 推荐法（复杂）

**主要是后台服务进行修改**

- cookie 修改

```
在cookie值中加入; SameSite=None; Secure=true
```

- http改为https

### 半残法（不确定）

**主要是后台服务进行修改**

- cookie 修改

```
在cookie值中加入; SameSite=None
```

**经测试，部分版本的80浏览器可以起效，不推荐使用**

