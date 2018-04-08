---
layout: post
title: "python基础2---------之与java常用函数异同"
date: 2018-04-08 15:33:24.000000000 +09:00
tags: linux

---
## python基础之与java常用函数异同
##### 1.条件语句
　　	python的if语句流程什么的和java大同小异，只是格式有所不同，python中省去了写括号的繁琐，由于 python 并不支持 switch 语句，所以多个条件判断，只能用 elif 来实现
　　1.java中的if与python的if
~~~
			if 判断条件：
			    执行语句……
			else：
			    执行语句……
~~~
　　2.java中的elseif与python的elif
~~~
			if 判断条件1:
			    执行语句1……
			elif 判断条件2:
			    执行语句2……
			elif 判断条件3:
			    执行语句3……
			else:
			    执行语句4……
~~~
　　3.java中的&&与python中and
~~~
			num = 9
			if num >= 6 and num <= 10:    # 判断值是否在0~10之间
			    print 'hello python'             # 输出结果: hello
~~~
　　	4.java中的||与python中or
~~~
				um = 8
				
				if (num >= 0 and num <= 5) or (num >= 10 and num <= 15):    # 判断值是否在0~5或者10~15之间
				    print 'hello java'
				else:
				    print 'hello python'	# 输出结果: undefine

~~~
　　	5.在Java中，判断字符串是否相等要用equals(str)方法，而不能直接用==。equals判断的是值是否相同，==判断的是引用是否相同。内容相同的两个字符串其引用可能是不同的。对于在python是怎么判断字符串的值呢？python并没有这个用法，在python中用 ***is 比较比较引用是否相同，==比较内容是否相同***
　　	python中is 主要是判断 2 个变量是否引用的是同一个对象，如果是的话，则返回 true，否则返回 false。[判断数字相等不要用 is 操作符]:http://onlypython.group.iteye.com/group/wiki/852-%E6%93%8D%E4%BD%9C%E7%AC%A6is%E7%9A%841%E4%B8%AA%E8%AF%A1%E5%BC%82%E9%97%AE%E9%A2%98 为什么最好不要用字符串，我们自己可以实际操作一下看一下


##### 2.Python 循环语句
　　	Python提供了for循环和while循环（在Python中没有java的do..while循环），对于循环嵌套和java基本逻辑处理是一致的，只是语法问题，这里不做解释
	1.Python的for循环语法格式：![](https://i.imgur.com/vg6Vpfy.png)
~~~
	for iterating_var in sequence:
  			 statements(s)
~~~
	2.Python的while循环语法格式：![](https://i.imgur.com/Gwws3H9.png)
~~~
	while 判断条件：
    	执行语句……
~~~
	3.结束循环
　　python结束循环和java一样都是用continue和break，continue 语句跳出本次循环，而break跳出整个循环
此外python还提供pass语法，但是pass这个并没有什么卵用，它不做任何事情，一般用做占位语句。如图![](https://i.imgur.com/3jp3iNz.png)
##### 3.Python 导包
　　导包引用其它类中的函数java中可以通过import导包，那么python呢，python可以通过以下方导包，具体什么意思懂java的一看便知。
	1.from modname import name1[, name2[, ... nameN]]（相当于java 从modname类导入函数name1）
	2.from…import* 
	3.import xxx

	