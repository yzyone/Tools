# mongoose做轻量级http service+client

mongoose开源http服务器项目：https://github.com/cesanta/mongoose

源码下载后，只需要使用mongoose.c和mongoose.h两个文件
examples有事例代码

mongoose OS开源物联网系统：https://github.com/cesanta/mongoose-os
开源代码工程：https://github.com/cesanta

参考文章：
https://blog.csdn.net/yi412/article/details/45840413
https://cloud.tencent.com/developer/article/1350885
https://www.wandianshenme.com/play/javascript-os-mongoose-os-esp8266-build-iot-projects/

http服务器：
```
Apache
Apache Tomcat
Nginx
Lighttpd
Cherokee
Appweb
Node.js
```

轻巧的http服务器：

1、micro_httpd - really small HTTP server
特点：
支持安全的 … 上级目录过滤
支持通用的MIME类型
支持简单的目录
支持目录列表
支持使用 index.html 作为首页
Trailing-slash redirection
程序总共代码才200多行
这个httpd适合学习简单的Web Server编写学习，因为它只有一个简单的框架，只能够处理简单的静态页，可以考虑用来放静态页。
官方地址：http://www.acme.com/software/micro_httpd/
下载地址：http://www.acme.com/software/micro_httpd/micro_httpd_12dec2005.tar.gz

2、mini_httpd - small HTTP server

特点：

```
支持GET、HEAD、POST方法
支持CGI功能
支持基本的验证功能
支持安全 … 上级目录功能
支持通用的MIME类型
支持目录列表功能
支持使用 index.html, index.htm, index.cgi 作为首页
支持多个根目录的虚拟主机
支持标准日志记录
支持自定义错误页
Trailing-slash redirection
mini_httpd 也是相对比较适合学习使用，大体实现了一个Web Server的功能，支持静态页和CGI，能够用来放置一些个人简单的东西，不适宜投入生产使用。
官方地址：http://www.acme.com/software/thttpd/
下载地址：http://www.acme.com/software/mini_httpd/mini_httpd-1.19.tar.gz
```

3、thttpd - tiny/turbo/throttling HTTP server

```
thttpd中是一个简单,小型,轻便,快速和安全的http服务器：
简单：它能够支持HTTP/1.1协议标准，或者超过了最低水平
小巧：它具有非常少的运行时间，因为它不fork子进程来接受新请求，并且非常谨慎的分配内存（性能对比表：http://www.acme.com/software/thttpd/benchmarks.html）
便携：它能够在大部分的类Unix系统上运行，包括FreeBSD, SunOS 4, Solaris 2, BSD/OS, Linux, OSF等等
快速：它的速度要超过主流的Web服务器（Apache, NCSA, Netscape），在高负载情况下，它要快的多
安全：它努力的保护主机不受到攻击，不中断服务器
```

thttpd 类似于lighttpd，对于并发请求不使用fork()来派生子进程处理，而是采用多路复用(Multiplex)技术来实现。因此效能很好。同时它还有一个特点就是基于URL的文件流量限制，这对于下载的流量控制而言是非常方便的。象Apache就必须使用插件实现，效率较thttpd低。

thttpd跟lighttpd类似，适合静态资源类的服务，比如图片、资源文件、静态HTML等等的应用，性能应该比较好，同时也适合简单的CGI应用的场合。

```
官方地址：http://www.acme.com/software/thttpd/
下载地址：http://www.acme.com/software/thttpd/thttpd-2.25b.tar.gz
```

4、lighttpd - light footprint + httpd = LightTPD

Lighttpd是一个德国人领导的开源软件，其根本的目的是提供一个专门针对高性能网站，安全、快速、兼容性好并且灵活的web server环境。具有非常低的内存开销，cpu占用率低，效能好，以及丰富的模块等特点。

lighttpd 是众多OpenSource轻量级的web server中较为优秀的一个。支持FastCGI, CGI, Auth, 输出压缩(output compress), URL重写, Alias等重要功能，而Apache之所以流行，很大程度也是因为功能丰富，在lighttpd上很多功能都有相应的实现了，这点对于apache的用户是非常重要的，因为迁移到lighttpd就必须面对这些问题。

实用起来lighttpd确实非常不错，apache主要的问题是密集并发下，不断的fork()和切换，以及较高（相对于 lighttpd而言）的内存占用，使系统的资源几尽枯竭。而lighttpd采用了Multiplex技术，代码经过优化，体积非常小，资源占用很低，而且反应速度相当快。

利用apache的rewrite技术，将繁重的cgi/fastcgi任务交给lighttpd来完成，充分利用两者的优点，现在那台服务器的负载下降了一个数量级，而且反应速度也提高了一个甚至是2个数量级！
lighttpd 适合静态资源类的服务，比如图片、资源文件、静态HTML等等的应用，性能应该比较好，同时也适合简单的CGI应用的场合。

```
官方地址：http://www.lighttpd.net/
下载地址：http://www.lighttpd.net/download/lighttpd-1.4.16.tar.gz
```

5、SHTTPD - Simple HTTPD

Shttpd是另一个轻量级的web server，具有比thttpd更丰富的功能特性，支持CGI, SSL, cookie, MD5认证, 还能嵌入(embedded)到现有的软件里。最有意思的是不需要配置文件！由于shttpd可以嵌入其他软件，因此可以非常容易的开发嵌入式系统的web server，官方网站上称shttpd如果使用uclibc/dielibc(libc的简化子集)则开销将非常非常低。

特点：

```
小巧、快速、不膨胀、无需安装、简单的40KB的exe文件，随意运行
支持GET, POST, HEAD, PUT, DELETE 等方法
支持CGI, SSL, SSI, MD5验证, resumed download, aliases, inetd模式运行
标准日志格式
非常简单整洁的嵌入式API
dietlibc friendly. NOT that friendly to the uClibc (*)
容易定制运行在任意平台：Windows, QNX, RTEMS, UNIX (*BSD, Solaris, Linux)
由于shttpd可以轻松嵌入其他程序里，因此shttpd是较为理想的web server开发原形，开发人员可以基于shttpd开发出自己的webserver！
官方网站：http://shttpd.sourceforge.net/
下载地址：http://jaist.dl.sourceforge.net/sourceforge/shttpd/shttpd-1.38.tar.gz
```

6、tinyhttpd

————————————————

版权声明：本文为CSDN博主「大漠不死鸟」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。

原文链接：https://blog.csdn.net/rxs0011/article/details/90260330