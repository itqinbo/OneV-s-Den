---
layout: post
title: "Maven版本jeecg快速开发平台环境的搭建"
date: 2017-04-11 10:34:24.000000000 +09:00
tags: jeecg

---
### 开发工具

  　　Eclipse、JDK1.7、Tomcat７、Maven项目构建、JEECG提供私服仓库、SQLyog。

　　关于maven环境的搭建以及在eclipse中集成maven此处不再进行详细介绍，请翻看前期关于如何搭建本地maven仓库

### 导入jeecg-maven项目

　　jeecg-maven项目可自行在[论坛](http://www.jeecg.org/forum.php?mod=viewthread&tid=1229&extra=page%3D1)下载对应版本，由于maven版本相对于非maven版本要求开发者需要熟悉maven，所以推荐大家使用maven版的。
  　　 1:选择导入maven项目-![](http://i.imgur.com/78XgMsW.png)
 　　　2：配置maven setting文件​
　　　 3：设置工程编码UTF-8，
　　　 4：​右键选择项目-properties-validation设置disabled all （可选），去除不必要的验证。
　　　 5：打包：右键-run as-maven install  ​
　　　 如果没有出错说明已经执行成功。
### 执行sql脚本并修改数据库连接地址和密码
##### 执行sql脚本
　　打开数据库连接工具，我使用的是sqlyog，建立数据库：jeecg（注意要保持和dbconfig.properties里面名字保持一致，没有修改的的话就是和我的一样）![](http://i.imgur.com/cXVXPjV.png)
　　将本地下载下来的sql语句执行，建表。
##### 修改数据库连接地址和密码

　　和上图相同，修改和自己数据库密码相同即可

### 运行服务器
	
　　运行服务器前首先要对服务器进行配置。
　　第一步：点击windows-showview-servers，出来界面如图：![](http://i.imgur.com/JDfOTed.png)
　　第二步：点击create a new server：出来界面如图：选择apache![](http://i.imgur.com/n6vc62h.png)
　　第三步：选择apache下面对应的tomcat，由于我此次用的是tomcat7，所以我选择的是7，大家具体的按照自己版本走，按照我的图步骤走，2处点击add配置自己本地的tomcat，3处就是本地tomcat地址，4处请选择自己本地的jre，不要用自带的![](http://i.imgur.com/W8oe814.png)
　　第五步：点击next-add将自己项目加配置到服务器中，接下来我们就可以运行服务器，访问http://localhost:8080/jeecg 访问配置好的jeecg开发平台输入admin-密码123456进行快速操作了
		![](http://i.imgur.com/AjYMvyI.png) 
	 	![](http://i.imgur.com/C0Fd0By.png)
