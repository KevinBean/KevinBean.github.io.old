---
layout:     post
title:     XML文件生成的两种方法
subtitle:   ""
header-img: ""
categories: [blog ]
tags: [log, program]
 
---

## 第一种：直接写入文件
	def writetoaiml(aimlfile,cat):
	    out = open(aimlfile,'w')
	    out.write('<?xml version="1.0" encoding="utf-8"?>\n')
	    out.write('< aiml version = "1.0" >\n')
	    out.write("  <category>\n")
	    out.write("    <pattern>")
	    pat = cat.pattern.encode("utf-8")
	    if not pat.strip():
	        return
	    else:
	        pat = pat.replace("&", "&amp;")
	        pat = pat.replace("<", "&lt;")
	        pat = pat.replace(">", "&gt;")
	        pat = pat.replace("'", "&apos;")
	        pat = pat.replace('"', "&quot;")
	        out.write(pat)
	    out.write("</pattern>\n")
	    out.write("    <template>\n")
	    print cat.pattern
	    if len(cat.tempaltes) > 1:
	        out.write("      <random>\n")
	        for template in cat.tempaltes:
	            print template
	            out.write("        <li>")
	            temp = template.encode("utf-8").replace("&", "&amp;")
	            temp = temp.replace("<", "&lt;")
	            temp = temp.replace(">", "&gt;")
	            temp = temp.replace("'", "&apos;")
	            temp = temp.replace('"', "&quot;")
	            out.write(temp)
	            out.write("</li>\n")
	            # count += 1
	            out.write("      </random>\n")
	    else:
	        template = cat.tempaltes("utf-8")
	        print template
	        temp = template.replace("&", "&amp;")
	        temp = temp.replace("<", "&lt;")
	        temp = temp.replace(">", "&gt;")
	        temp = temp.replace("'", "&apos;")
	        temp = temp.replace('"', "&quot;")
	        # charset=chardet.detect(words)["encoding"]
	        out.write(temp + '\n')
	    out.write("    </template>\n")
	    out.write("  </category>\n")
	    out.write('< /aiml >\n')
	    out.flush()
## 第二种：根据一个给定的XML Schema，使用DOM树的形式从空白文件生成一个XML。
	from xml.dom import minidom
	import traceback

	try:
	    f = open("xmlstuff.aiml", "w")

	    try:
	        doc = minidom.Document()

	        aimlNode = doc.createElement("aiml")
	        aimlNode.setAttribute('version', "1.0")
	        doc.appendChild(aimlNode)

	        metaNode = doc.createElement("meta")
	        metaNode.setAttribute("author","KevinBean")
	        metaNode.setAttribute("language", "zh")
	        aimlNode.appendChild(metaNode)

	        categoryNode = doc.createElement("category")
	        aimlNode.appendChild(categoryNode)

	        patternNode = doc.createElement("pattern")
	        pattern_text = doc.createTextNode("问题")
	        patternNode.appendChild(pattern_text)
	        categoryNode.appendChild(patternNode)

	        templateNode = doc.createElement("template")
	        template_text = doc.createTextNode("回答")
	        templateNode.appendChild(template_text)
	        categoryNode.appendChild(templateNode)



	        doc.writexml(f, "\t", "\t", "\n", "utf-8")
	    except:
	        traceback.print_exc()
	    finally:
	        f.close()

	except IOError:
	    print "open file failed"

