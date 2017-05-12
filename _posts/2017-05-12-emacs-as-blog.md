---
layout:     post
title:     使用emacs写博客
subtitle:   " 使用emacs写博客"
header-img: ""
categories: [blog, emacs ]
tags: [test,emacs,jekyll,markdown ]
 
---

## 不成功的尝试
使用以下方法,均未成功搞定org到jekyll的转换
  学习:       DONE [Using org to Blog with Jekyll](http://orgmode.org/worg/org-tutorials/org-jekyll.html)             :emacs:学习:org::没看懂:
  学习:       DONE 直接使用org-jekyll失败                    :emacs:学习:org:没看懂::
  学习:       CANCELLED [bmaland/happyblogger: Write your blog posts in org-mode and let Jekyll take care of the rest.](https://github.com/bmaland/happyblogger) :emacs:学习:org::
  学习:       [metajack.im - Manage Jekyll From Emacs](https://metajack.im/2009/01/02/manage-jekyll-from-emacs/)             :emacs:学习:org::
  学习:       [jekyll/jekyll.el at master · metajack/jekyll](https://github.com/metajack/jekyll/blob/master/emacs/jekyll.el)       :emacs:学习:org::
  学习:       hyde 使用 org 发布 jekyll 博客[the website of noufal ibrahim | hyde : an emacs mode for jekyll blogs](http://nibrahim.net.in/2010/11/11/hyde_:_an_emacs_mode_for_jekyll_blogs.html) :emacs:学习:org::
  学习:       waiting [#a] 使用 ox-jekyll                        :emacs:学习:org::
  学习:       TODO 使用org2jekyll[ardumont/org2jekyll: blogging with org-mode and jekyll without alien yaml headers.](https://github.com/ardumont/org2jekyll) :emacs:学习:org::blog素材:
  学习:       TODO 安装[org-octopress/ox-jekyll.el at master · yoshinari-nomura/org-octopress](https://github.com/yoshinari-nomura/org-octopress/blob/master/ox-jekyll.el) :emacs:学习:org:blog素材::
  学习:       TODO 参考 [Malabarba/ox-jekyll-subtree: Extension to ox-jexkyll for better export of subtrees](https://github.com/Malabarba/ox-jekyll-subtree)q :emacs:学习:org:blog素材::

## 最终解决方案
使用projectile管理_post文件夹,仍然使用md进行写作.
