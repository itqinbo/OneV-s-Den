---
layout: post
title: "python学习---------之与java数据结构异同"
date: 2018-04-08 10:20:24
tags: python

---
## python和java数据类型的区别
　　	有梦想的人是幸福的，每一个it人都有一个危机意识，所以最近半夜下班回来一直在学习Python。由于我目前主要编程语言还是Java，所以针对Python 的学习我主要是通过与Java 进行对比。希望可以帮助那些要转python或者有兴趣学习的人，
我使用的是Python3，因此语法上也会遵循Python3 的规则。以前的博客放在阿里云上，由于服务器到期自己又懒得去续费了，所以还是继续用github吧，虽然访问速度慢，但好在免费。以前的那些播客闲了自己会慢慢恢复。
学习这一段时间的收获近期大概来总结一下：
##### 数据类型的区别
　　	对于java分为数据类型从大的方向分为基本数据类型和引用数据类型。而基本数据类型包含byte、short、int、long
float、double、char、boolean八种，引用型数据类型包含数组array、接口interface、类class（就是自己定义的数据结构，还有一些java类库中的：包括string，date等）三种
　　	从类型上说，Java是静态类型语言，Python是动态类型语言。所谓静态类型就是变量需要先声明再使用，动态类型是不需要事先声明变量的类型。
对于python来说，由于python认为万物皆对象，它的的语法要比Java更为灵活。python的数据类型基本上不像java分的那么细腻。大体上分为：
Number（数字）、String（字符串）、List（列表）、Tuple（元组）、Sets（集合）、Dictionary（字典）六种。这其中Number（数字）、String（字符串）、Tuple（元组）、Sets（集合）四个是不可变数据；
List（列表）、Dictionary（字典）是可变数据。
　　	对于有java过来的人来说，应该大部分都认识，有些陌生的就是tuple和dictionary了。下面会一一介绍.
###### Number（数字）
~~~
　　	对于python3现在已经没有long类型了，python是有长整型long类型的。对于3来说数字类型包含int、float、bool（java中对应boolean）、complex（复数）
复数这个概念在java中是不存在的，什么是复数？就是a+bi。。。。好像是大学还是高中学的吧，a对应实部，b对应虚部，当b为零时候这个数就是实数。。大学力学什么的应该用到好多吧，不懂得自己再脑部一下吧
　　	对于数字类型之间的转换，并不是大多数情况像java中强转一下就好。具体怎么转换如下：

              int(x [,base]) 将x转换为一个整数 
              float(x ) 将x转换到一个浮点数 
              complex(real [,imag]) 创建一个复数 
              str(x) 将对象x转换为字符串 
              repr(x) 将对象x转换为表达式字符串 
              eval(str) 用来计算在字符串中的有效Python表达式,并返回一个对象 
              tuple(s) 将序列s转换为一个元组 
              list(s) 将序列s转换为一个列表 
              chr(x) 将一个整数转换为一个字符 
              unichr(x) 将一个整数转换为Unicode字符 
              ord(x) 将一个字符转换为它的整数值 
              hex(x) 将一个整数转换为一个十六进制字符串 
              oct(x) 将一个整数转换为一个八进制字符串
~~~

###### Java list与Python list相比较
~~~

　　	对于list和java中并无太大区别但是没有java中ArrayList，LinkedList，vector三种分类，这个玩意在java中就用的很多，所以在Python中是使用最频繁的数据类型
~~~
###### Python 元组概念
~~~
　　	元组，对于元组概念java中并没有，到底什么是元组，简单点讲元组就是一个不可变的list，但是它又不仅仅是一个不可变list，最大区别就是元组的元素不能修改，元组写在小括号 () 里。
如a = [1, 'aaaa', 'bbbb', 4.22, 5, 6]这是一个列表,而tuple = ( 'abcd', 786 , 2.23, 'runoob', 70.2  )这是一个元组，list中提供一些列函数如append()、pop()等等在元组中是不存在的
~~~
###### Java Set与Python set相比较
~~~
　　	java中Set里存放的对象是无序，不能重复的，集合中的对象不按特定的方式排序，只是简单地把对象加入集合中，
　　	主要分为
	　　	--HashSet:底层使用哈希表，线程不安全，保证对象唯一的方式:重写hashcode(),equals(Object obj).使用哈希算法导致无序
		---TreeSet:底层使用二叉树，线程不安全，保证对象唯一的方式:1 实现Comparable<E>接口，实现compareTo()方法的返回值是0，则不能加入。2 创建一个类，实现Comparator<T>，实现compare()方法。
　　	对于python：无分类，就是一种无序集合
~~~
###### Java Map与Python dict相比较
~~~
　　	对于java中的map在python叫做Dictionary
　　	Java Map分类：
		--- HashMap:底层使用的数据结构是哈希表
			    保持键的唯一性同HashSet相同。
		--- TreeMap:底层使用的数据结构是二叉树     
			    保持键的唯一性同TreeSet相同。
　　	Python 字典无分类，dict是Python的基本数据结构
~~~