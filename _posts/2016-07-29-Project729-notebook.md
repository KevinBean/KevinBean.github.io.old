---
layout:     post
title:     随手记
subtitle:   Project 729
header-img: ""
categories: [blog ]
tags: [project,learn ]
 
---

## 转换时间字符串为数字时间戳
	import datetime,time
	dt = datetime.datetime.strptime('2010-01-01 18','%Y-%m-%d %H')

输出：datetime.datetime(2010, 1, 1, 18, 0)

	time_tuple = dt.timetuple()
	ts = time.mktime(time_tuple) 
	ts

输出：1262340000.0

## 这条排序没看懂
	sims=sorted(enumerate(sims),key=lambda item: item[1],reverse=True)


D3.js

## pandoc
pandoc可以很方便的转换文档格式，但是不知为何，“doc/SL331C-A-01.docx”文件转换时会丢失数字和字母数据。