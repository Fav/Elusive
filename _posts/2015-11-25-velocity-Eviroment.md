---
layout: default
title: velocity环境搭建
---

直接来步骤了：

1. 到[官网](http://velocity.apache.org/download.cgi)下载安装包（目前最新包链接如下）

	[velocity-1.7.zip](http://mirror.bit.edu.cn/apache//velocity/engine/1.7/velocity-1.7.zip)

	[velocity-tools-2.0.zip](http://mirror.bit.edu.cn/apache//velocity/tools/2.0/velocity-tools-2.0.zip)

2. 在Eclipse里面创建动态web工程
3. 要添加的jar包有两部分，将以下内容拷贝到新工程的WebContent\WEB-INF\lib
	1. velocity-1.7.zip包中的 velocity-1.7-dep.jar 和 velocity-1.7.jar
	2. velocity-tools-2.0.zip 包里面 lib下所有jar包
	
4. 在WebContent目录下添加 index.vm,内容如下：

			#set($hello="Velocity")
			<html>
			   <head>
			     <title>Hello</title>
			   </head>
			   <body>
		
			     Hello $hello World !
			   </body>
			</html>

5. 修改web.xml

		<servlet>
		 <servlet-name>velocityView</servlet-name>
		 <servlet-class>org.apache.velocity.tools.view.servlet.VelocityViewServlet</servlet-class>
		</servlet>
		<servlet-mapping>
		 <servlet-name>velocityView</servlet-name>
		 <url-pattern>*.vm</url-pattern>
		</servlet-mapping>
		
		<welcome-file-list>
				<welcome-file>index.vm</welcome-file>
		</welcome-file-list>

运行程序，能看到

![成功]({{ site.imgPath }}/velocity-hello.jpg)

说明运行成功 

注意：
1. 添加velocity-tools-2.0.zip 包里面 lib下所有jar包而不是velocity-1.7.zip包lib下的所有jar包
2. 在WebContent目录下添加 index.vm，层级有时候容易看错，比如你加到WEB-INF文件夹下的话，就会一直报错说找不到index。

