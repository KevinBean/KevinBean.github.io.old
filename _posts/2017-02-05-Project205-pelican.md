---
layout:     post
title:     pelican学习
subtitle:   Project 205
header-img: ""
categories: [blog ]
tags: [project,learn ]
 
---
## 项目进度
### 用来收集工作信息
- 质量信息 ok
- OA ok
- 工作记录 待办
- 规程规范 待办
- 文章自动打标签 意义不大
- 解决文章附件／图片链接的问题 待办 不急迫
## pelican为每个类别创建页面
- 首先要求category.html模板
- DIRECT_TEMPLATES = (('index', 'tags', 'categories','archives', 'search', '404’)）中要包含category
- CATEGORY_URL = 'category/{slug}.html'
- 设置CATEGORY_SAVE_AS setting (Default: category/{category_name}.html). If pagination is active, subsequent pages will by default reside at category/{category_name}{number}.html.

## 解决pelican搜索结果undefined的问题 Tipue search return undefined url · Issue #147 · talha131/pelican-elegant
Another idea/hack/work-around is to edit the pelican-plugins/tipue_search/tipue_search.py to add (twice)  'loc': page_url  to the  node =  dicts in both  def create_tpage_node  and  def create_json_node . 
The resulting URLs are fully-qualified and seem to ignore the pelicanconf.py RELATIVE_URLS setting, but that too can be recognised in the init settings parameter. That's probably not a new thing though. 

## 处理txt去除转义字符，常用的转义字符及其含义：
　　\‘　　单引号
　　\“　　双引号
　　\\　　反斜杠
　　\0　　空
　　\a　　警告(产生蜂鸣)
　　\b　　退格
　　\f　　换页
　　\n　　换行
　　\r　　回车
　　\t　　水平制表符
　　\v　　垂直制表符
## plugins
### events 通过增加markdown元信息标签，可以生成events list页面，以及ical文件
### ical 显示ical calendar文件
列表模式 不是日历模式
### pin_to_top 置顶
### Pelican Comment System 评论系统，存储评论在本身文件中
### series 多篇文章集合到一篇文章

## 渲染page时，不用在DIRECT_TEMPLATES = ('index', 'tags', 'categories', 'archives', 'search', '404’)中增加page



