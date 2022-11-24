# pandoc——文档转换神器 #

pandoc是一款开源转换工具，可以实现常见的格式转换。支持全平台操作，以命令行的方式进行转换。

[下载地址](http://www.pandoc.org/installing.html)，根据系统的不同选择不同的安装方式。

使用

```
# 打开终端窗口，windows下打开cmd
# 小试牛刀，将input.txt文件转换为output.html文件。-o参数表示输出文件
pandoc -o output.html input.txt

-f: 指定输入格式，比如docx、epub、md、html等
-t: 指定输出格式，比如docx、epub、md、html等
-o: 输出到file文件
--verbost: 显示详细调试信息
--log： 指定输出日志信息

--list-input-formats：列出支持的输入格式。
--list-output-formats：列出支持的输出格式。
--list-extensions：列表支持Markdown扩展，后面跟一个+或者-说明是否在pandoc的Markdown中默认启用。
--list-highlight-languages:列出语法突出显示支持的语言。
--list-highlight-styles:列出支持语法高亮的样式。。
-v: 打印版本信息。
-h：显示语法帮助
```

更多详细命令，参看[官方文档](http://pandoc.org/MANUAL.html)

```
# 一些例子
# 获取网页内容，并将其转换为markdown格式（感觉可以用来写简易爬虫）
pandoc -f html -t markdown http://www.fsf.org

# 将input.txt文件作为markdown输入，转换为latex
pandoc -f markdown -t latex input.txt

# 如果未指定-f、-t，pandoc则会根据输入文件输出文件的后缀来转换
pandoc input.txt -o output.pdf

# pandoc要求输入输出使用utf8编码，可以使用iconv命令进行编码转换
iconv -t utf-8 input.txt | pandoc | iconv -f utf-8

# 如果需要使用tex生成pdf文件，则需要下载latex编译器    
```

[latex官网](https://www.latex-project.org/get/)

关于latex是什么的问题，可以从官网上获取答案，百度亦可。简单来说是最强大的排版软件。

————————————————

版权声明：本文为CSDN博主「wnma3mz」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。

原文链接：https://blog.csdn.net/wnma3mz/article/details/78824614

