---
layout:     post
title:     数据科学课学习
subtitle:   “project 716”
header-img: ""
categories: [blog ]
tags: [learn,project ]
 
---

## 开始读《数据科学实战》

## 数据科学竞赛
- 注册了天池大数据竞赛
- 注册了DataCastle竞赛
\- 
## 笔记

## 开始学习EDX上的Data Science课程
课程来自Microsoft，地址：[https://courses.edx.org/courses/course-v1:Microsoft+DAT101x+5T2016/info][1]

### 课程介绍
- 课程内容。
- 工具 Excel powerBI R Python spark
- 要及时听课，过期不候。
- 什么是数据科学家，需要什么技能。
- 统计学、数学、编程、python
- 主要工作:收集数据，清理数据，分析数据。
- 数据科学家可以来自不同领域，不需要一份相关的工作，可以自己寻找感兴趣的领域，开始做，并且分享，吸引注意。

### 数据基础
Getting Started with Data：
主要是微软的夹带私货，Excel实现基本的筛选、可视化、数据透视表功能

### 统计学基础
1. 拿到一组数据，可以先从平均值mean、中位数median、高频数mode入手，画出这三个值后，连线得到分布曲线，最理想的是这三个值完全相同，或者接近。否则分布左偏或者右偏。
2. 方差Variance 标准差Standard Deviation 67%的数据集都在＋1到－1之间 ，95%的数据集都在＋2到－2之间 ，99%的数据集都在＋3到－3之间。 标准误差Standard Error 数据集越大，越小. 67%的数据集都在＋1到－1之间 ，95%的数据集都在＋2到－2之间。
3. 描述统计学descriptive statistics：Excel的数据分析工具（2013以后版本）。快捷分析。正态分布的峰值kurtosis和偏态（skewness），＋2到－2之间说明是正常的数据集。
4. Associative statistics：correlation相关性
5. T-test or Z-test平均值差异性检验的方法: 样本大，方差已知，则z test更好。t test在样本量大的时候很接近z test, 但是样本方差会有很大的浮动，这就是为什么建议使用z test if n\>30.ZTEST(一组数据，200)，得出的值表示平均值相对于200的偏离程度？ **P值小于0.05为显著数据，有统计学意义。**
6. Comparing Multiple Variables in a Dataset。T－test two samples t－test比较两组数据
7. ANOVA方差分析 变异数分析 一次进行多组t－test

[1]:	https://courses.edx.org/courses/course-v1:Microsoft+DAT101x+5T2016/info