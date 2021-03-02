---
title: spring aop概述
date: 2015-03-05 08:47:51
toc: ture
categories:
- spring
- aop
tags:
- spring
- aop
- 概述
---

## 概述

```
AOP:Aspect oriented programing(面向切面编程),它的应用场合是受限的，一般适用于具有横向切面逻辑的应用场合，比如
性能检测、访问控制、事务管理及日志记录（很难使用aop编写出实用的程序日志）等。
```
### 按照重构的思想，多个类中出现重复的代码，可以考虑定义一个共同的抽象类，将重复代码提取的抽象类中。

<!-- more -->

### 场景重现，如下的Horse、Cow对象都拥有eat()、run()方法。

{% codeblock lang:java %}
public class Cow {
    public void eat() {
        System.out.println(this.getClass().getName() + " eat!");
    }

    public void run() {
        System.out.println(this.getClass().getName() + " run!");
    }
}
public class Horse {
    public void eat() {
        System.out.println(this.getClass().getName() + " eat!");
    }

    public void run() {
        System.out.println(this.getClass().getName() + " run!");
    }
}
{% endcodeblock %}

### 通过引入一个包含eat()和run()方法的抽象的Animal父类，可以消除重复的代码。

{% codeblock lang:java %}
public abstract class Animal {
    public void eat() {
        System.out.println(this.getClass().getName() + " eat!");
    }

    public void run() {
        System.out.println(this.getClass().getName() + " run!");
    }
}
{% endcodeblock %}

### 一般情况下，通过引入父类消除重复的代码是可行的，但事情并非我们想象的那么简单！如以下论坛管理业务类的代码。

{% codeblock lang:java %}
public class ForumService {
    private TransactionManager transactionManager;
    private PerformanceMonitor performanceMonitor;
    private ForumDao forumDao;
    private TopicDao topicDao;

    public void removeTopic(int topicId) {
        performanceMonitor.start();
        transactionManager.beginTransaction();
        topicDao.removeTopic(topicId);
        transactionManager.commit();
        performanceMonitor.end();
    }

    public void create(Forum forum) {
        performanceMonitor.start();
        transactionManager.beginTransaction();
        forumDao.create(forum);
        transactionManager.commit();
        performanceMonitor.end();
    }
}
{% endcodeblock %}

### 可以看到业务逻辑代码被重复的非业务逻辑代码（性能检测、事务管理）所包围。如下图所示，我们可以将ForumService业务类看成一段圆木，将removeTopic()和create()方法分别看出圆木的一截。此时，业务代码就类似圆木的树心，性能监视和事务管理就好像一个年轮。

{% asset_img 1-1.jpg %}

## 因为这些横向逻辑依附在业务类方法的流程中，不能转移到其他地方去。

## AOP通过横向抽取机制为重复性代码（无法通过纵向继承体系进行抽象的）提供解决方案。

{% asset_img 1-2.jpg %}

### AOP希望将这些分散在各个业务逻辑代码中的相同代码，通过横向切割的方式抽取到一个独立的模块中，还业务逻辑类一个清新的世界。

## 需要解决的问题

```
如何将这些独立的逻辑融合到业务逻辑中完成和原来一样的业务操作。
```
