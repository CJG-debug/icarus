---
title: git历史commit用户名密码修改
date: 2018-09-06 16:15:33
toc: true
categories:
- 团队协作
- git
tags:
- git
- commit
- 历史
- 邮箱
- 密码
---

```
git filter-branch -f --env-filter "GIT_AUTHOR_NAME='SimilarSu'; GIT_AUTHOR_EMAIL='similarsu@qq.com'; GIT_COMMITTER_NAME='sutong'; GIT_COMMITTER_EMAIL='821192673@qq.com';" HEAD
```

**其中GIT_AUTHOR为新的，GIT_COMMITTER为老的**
