---
title: Gradle控制台乱码解决方法
date: 2020-05-13 11:01:08
comments: false
---

## Gradle编译时，Idea控制台输出中文乱码
<!--more-->
```
项目编码已经是utf-8
网上搜索得到的结果大部分已经过期

最后按以下方案尝试修改：

IDEA -> Help -> Edit Custom VM Options  

在最后一行添加

-Dfile.encoding=utf-8

保存重启IDEA后解决
```
