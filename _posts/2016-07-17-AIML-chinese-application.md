---
layout:     post
title:     Python下两种曲线救国实现AIML中文聊天机器人功能的方法
subtitle:   “”
header-img: ""
categories: [blog ]
tags: [总结,post ]
 
---
![][image-1]
## Python下两种曲线救国实现AIML中文聊天机器人功能的方法
AIML，全称Artificial Intelligence Markup Language，是一种XML模式，用做自然语言聊天机器人的规则库。
最简单的AIML规则如下：

	<?xml version="1.0" encoding="GB2312"?>
	<aiml>
	<category>
	    <pattern>* bye</pattern>
	    <template>byebye</template>
	</category>
	</aiml>

\<pattern\>中的“\* bye”为模式。比如输入“mike,bye”就可以匹配该模式（\*表示任意字符），然后AIML解释器就会根据规则库返回“byebye”作为回复。

更复杂的aiml规则可参考：[Alicebot][1] 或 [AIML介绍][2]

应用实例可参考：[基于Python如何使用AIML搭建聊天机器人][3]

Aiml可以用来实现对话机器人，但是用于中文有以下问题：
1. 中文规则库较少。规则库相当于对话机器人的“大脑”，一般来说，规则库越丰富，对话机器人的应对就更像人。目前英文的规则库已经很丰富，涵盖面很广，而且是公开可获取的。但公开的中文规则库就基本没有。
2. AIML解释器对中文支持不好。实际上，Python下的Pyaiml模块（解析器）已经能比较好的支持中文，但是也存在以下问题：
	英文单词间一般都有空格或标点区分，因此具备一种“自然分词”特性，
	比如模式“\* BYE”很自然的就和“mike,bye”匹配，而且一般也不会写成无空格的"\*BYE"；
	但是中文的“*再见”（无空格），与“* 再见”（有空格）匹配的就是不同的模式，
	分别匹配"迈克,再见”和“迈克, 再见”（再见前必须有空格）。

由于中文输入没有以空格分隔的习惯，以上会在实践中造成一些不便。比如要实现有/无空格的输入匹配，就需要在规则库中同时包含这两种模式。

这种情况下，很多中文aiml规则库在实现时，就采取了在每个单字间人为增加空格的方法；同样，进行输入匹配的时候，也需要对输入添加空格来进行匹配。

针对上述问题，提出两种曲线救国的思路：
1. 通过翻译工具解决AIML对中文的处理,比如输入内容先经过翻译处理后变成英文内容,英文内容经AIML处理后输出,输出再翻译成中文显示。  
	输入中文-\>翻译为英文-\>AIML处理-\>英文结果-\>翻译成中文  

	好处是可以直接利用现有的英文规则库

经测,可实现。  
  
但因为要用到翻译api,实现效果跟翻译api的质量有关，另外在没有网络的情况下,较难实现。  
  
参考代码如下:  

 
	import aiml
	from translate import Translator
	# 创建Kernel()和 AIML 学习文件
	kernel = aiml.Kernel()
	kernel.learn("std-startup.xml")
	kernel.respond("load aiml b")
	# 按组合键 CTRL-C 停止循环
	while True:
	    translator = Translator(to_lang='en', from_lang='zh')
	    backtranslator = Translator(to_lang='zh',from_lang='en')
	    original = raw_input(u"请输入信息 >> ")
	    print original
	    message = translator.translate(original)
	    print message
	    response = kernel.respond(message)
	    print backtranslator.translate(response)



2. 利用中文分词工具（如jieba）进行分词，而不是每个单字间添加空格。  
	为了实现中文输入与模式的对应关系。建立规则库时，用分词工具对匹配模式进行预处理；在处理输入信息时，使用相同的分词工具进行处理。

	基本思路和逐字添加空格类似。但是分词工具能同时兼顾中文的语义表达性。
本文采用ulysses写作。
耗时：50分钟

[1]:	www.alicebot.org/aiml.html
[2]:	http://www.w3ii.com/aiml/aiml_introduction.html
[3]:	http://www.lai18.com/content/5447412.html

[image-1]:	http://git.writelab.cn/images/alicebot.jpg