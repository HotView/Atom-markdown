## Web服务器
严格意义上只负责处理HTTP协议，只能发送静态页面的内容。
而JSP，ASP，PHP等动态内容需要CGI，FastCGI，ISAPI等接口交给其他程序处理。这个其他应用程序就是应用服务器。

比如Web服务器包括Nginx，Apache，IIS等。

## Python
==动态内容需要通过WSGI接口交给应用程序去处理。==
#### Python框架
框架包含一系列库和一个主要的处理器（handler），这样你能构建自己的代码来实现web应用。包含以下功能：
1. URL路由：输入的HTTP请求匹配到特定的python代码中去  
2. 请求和响应对象：封装来自或发送给用户浏览器的信息。 
3. 模板引擎：将python逻辑代码和HTML分离开

分类：
1. django
2. flask
3. tornado等
#### Nginx：
是一个web服务器，并是HTTP，SMTP和其他协议的反向代理。

####  WSGI服务器：
==是一种在web服务器和python应用程序或框架之间的标准。==
	1. Gunicorn
	2. uWSGI
	3. Waitress等WSGI容器。
	
>一般应用服务器都集成了web服务器，主要是为了调试方便，出于性能和稳定性考虑，并不能在生产环境中使用。

>在python中，其实最终为应用服务的最后是WSGI服务器，而==WSGI==是在web服务器和Web应用程序或框架之间提出的一个简单通用的标准接口。
>使得框架的选择与Web服务器的选择分开，使得用户选择适合他们的配对。
>同时也使得框架和服务器人员可以专注于他们喜欢的专业领域。

## Java
应用服务器一般也支持HTTP协议，因此界限没那么清晰。但是应用服务器的HTTP协议部分仅仅是支持，一般不会优化，所以很少暴露给外面，而是和Nginx，Apache等配合，只让Tomcat处理JSP和Servlet部分。
> 尽管Java拥有尽可能多的Web应用程序框架，但是Java的“servlet”API使得任何Java Web应用程序框架编写的应用程序可以在支持servletAPI的任何Web服务器中运行。（这种思想在python中被应用和广泛使用。）
#### 应用服务器
- WebLogic：Oracle，大型收费，javaEE
- JBoss：
- websphere：IBM，大型收费，javaEE
- Tomcat：Apache，开源免费，javaEE中的servlet和jsp规范。



> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDYwODYyNzU1LDQzMzA4NjE2OSw5Nzc4MD
kyNzZdfQ==
-->