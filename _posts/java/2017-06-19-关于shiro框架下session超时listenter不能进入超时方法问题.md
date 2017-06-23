---
layout: post
title: "关于shiro框架下session超时问题"
date: 2017-06-23 11:10:24.000000000 +09:00
tags: 错误谨记

---
## shiro框架SessionListener的onExpiration方法失效
    
##### shiro框架HttpSessionListener不起作用以及SessionListener的onExpiration方法进不去原因分析
　　项目中为解决session超时,在用监听器配置HttpSessionListener后发现怎么都进入不了重写后的创建,销毁方法等,经过查找,发现是shiro框架的影响,由于shiro重新封装了原有的session，所以不能再使用原来的session监听方法了,配置后发现重写SessionListener监听器的onStart,onStop都可以执行,但是onExpiration超时怎么配置都没作用,找了好久才发现在spring中 shiro会话管理器中少配置 deleteInvalidSessions这个属性,
~~~
	　　<property name="deleteInvalidSessions" value="true"/>
~~~
　![](http://i.imgur.com/cI2xG12.png)
　　这个属性决定是否删除无效的session，默认也是开启,当然你不配置的话.,,默认是开不起的,,所以你要配置 
