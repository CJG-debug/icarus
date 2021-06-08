---
title: vim编辑模式下backspace按键失效
date: 2021-04-30 13:57:42
toc: true
categories:
- 文本编辑器
- vim
tags:
- vim
- backspace
- 失效
---

## 背景

```
vim编辑模式下backspace按键失效
```

## 配置

**修改~/.vimrc或/etc/vim/vimrc**

```bash
……
set nocompatible
set backspace=2
……
```

- nocompatible
  
  设置是否兼容

- backspace
  
  设置可以删除字节
