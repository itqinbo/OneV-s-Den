---
layout: post
title: "Oracle和Mysql自增长流水号生成"
date: 2017-06-19 16:19:24.000000000 +09:00
tags: 数据库函数

---
## Oracle日期格式流水号生成
    
　　最近项目中遇到业务需要生成自增长日期格式流水号,并使其每天凌晨可以从零增长
	
　　　　　　　　　　　　　　![](http://i.imgur.com/T00Wd6B.png) 

　　如上图的格式,每天早上从0开始,以当天的日期进行拼接,当然日期不能用前端页面上日期,最终决定用oracle的函数,每次向数据库插入数据时先查询这个最大值,只需调用这个函数即可,具体函数如下
``` javascript
create or replace function f_troq(tableName varchar2)
RETURN varchar2
as
/**
  tableName : 表名称
*/
/*自动生成序列号
序列号格式：日期+数字（固定是4位）
数字是一次累加，每天从1开始

//如果使用函数,只需替换tro_no即可,tro_no为你传入表里需要生成该格式字符串的列名,其他或者改个函数名称即可
调用仅需 	select f_contq('xxxx')   from dual 即可
*/
vi_seq number;
vi_date varchar2(8);
vi_ret varchar2(20);

v_sql varchar2(1000);

begin


  v_sql :=' select max(to_number(substr(t.tro_no,1,8))) ,max(to_number(substr(t.tro_no,9,4)))
    from '||tableName||' t where substr(t.tro_no,1,8) = to_char(sysdate,''yyyymmdd'')';

  dbms_output.put_line(v_sql);

  execute immediate v_sql into vi_date,vi_seq ;

  if vi_date<>to_char(trunc(sysdate),'yyyymmdd') or vi_date is null then

  vi_ret:=to_char(trunc(sysdate),'yyyymmdd')||'0001';

  else

  vi_ret:=to_char(trunc(sysdate),'yyyymmdd')||lpad(vi_seq+1,4,0);

  end if;

   RETURN (vi_ret);


end;
```
### 函数的调用
``` javascript
//f_contq为你保存函数时的名字,
select f_contq('T_EVENT_DEAL_CONTRADICT')  from dual
```
![](http://i.imgur.com/H28ECHc.png)
由于此次需要每次只要添加了都需要对应值加1,因此只需要在触发添加保存按钮事件时候调用该sql去数据库查寻即可,
###前台页面调用
![](http://i.imgur.com/M95QtmL.png)
### 对应的mapper文件(函数调用方式:dual:相当于一张伪表, f_contq:函数名称 T_EVENT_DEAL_CONTRADICT 表名 )
![](http://i.imgur.com/EQGD9Uk.png)

　　	

## Mysql格式
	(需要用到navicat premium,当然只要工具可以支持mysql函数即可:该函数没有实现日期拼接,仅实现每天清0,想实现的自己拼接)
　　mysql由于sqlyog不支持函数,所以在navicat premium里 点击[函数-新建函数-函数-输入这个历程参数可以不填-完成-然后复制declare---return c 替换RETURN 0 即可]
  　　
``` javascript
/*
uesr:表名
b:字段名,注意类型必须为datetime
v:字段名,类型必须为int:
*/
BEGIN
	#Routine body goes here...
declare  c int;

select max(t.v) into c
   from `user` t
  where date_format(b,'%y-%m-%d')=date_format(now(),'%y-%m-%d');

if c >0 then 
 set c=c+1;
ELSE
 set c=1;
end if;

	RETURN c;
END

```
　　
### 函数的调用
　　
``` javascript
//fn为你保存函数时的名字,
select fn();
```
![](http://i.imgur.com/DElXmu6.png)
