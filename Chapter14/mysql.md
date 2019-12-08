# 第1节：SQL存储引擎 Mysql

# Python PyMsql

## PyMysql

PyMysql 是一个让 Python 可以访问操作 Mysql 数据库软件的第三方库，它非常的好用，但仅支持 Python 3，使用前需要安装 `pip install pymysql`。

------

## 查找数据

主要是 `select语句` 的相关操作。

```
import pymysql

# 连接 Mysql 服务器
conn = pymysql.connect(host='localhost', user='root', passwd='', port=3306, db='dbname')

# 游标 （具体操作数据库的对象）
cursor = conn.cursor(cursor=pymysql.cursors.DictCursor)

cursor.execute('select * from tbname') # 获取数据到缓冲区
cursor.fetchone() # 从缓冲区获取一条数据
cursor.fetchmany(3) # 指定获取几条数据
cursor.fetchall() # 获取所有数据

# 销毁游标
cursor.close()

# 断开服务器链接
conn.close()
```

------

## 改变状态



主要是 `insert、update、detele语句` 的相关操作。



```
import pymysql

# 连接 Mysql 服务器
conn = pymysql.connect(host='localhost', user='root', passwd='', port=3306, db='dbname')

# 游标 | 数据缓冲区
cursor = conn.cursor(cursor=pymysql.cursors.DictCursor)

cursor.execute('insert into test (name) values (%s)', ['...']) # 数据提交到缓冲区

cursor.rowcount # 影响行数
cursor.lastrowid # 自增ID

# conn.rollback() 回滚 | 如果你发现数据异常可以清空 cursor 的数据

conn.commit() # 确认提交到数据库

# 关闭
cursor.close()
conn.close()
```

# [PyMySQL的基本使用](https://www.cnblogs.com/xfxing/p/9322199.html)

昨天在李哥帮忙检验我学习效果的时候
我使用pymysql出现了以下的错误

```
`python-module ``'pymysql'` `has no attribute ``'connect'`
```

一出错 我本能的想去看下是不是我没连接成功 然后 pip3 install pymysql
不要起import的包名作为文件名啊！！！

因此，我总结了下pymysql的基本使用

一、PyMySQL介绍
PyMySQL是在 Python3.x 版本中用于连接 MySQL 服务器的一个库，Python2中是使用mysqldb。

PyMySQL安装

```
`pip3 install pymysql`
```

创建链接的基本使用　

```
`# 导入pymysql模块``import pymysql` `# 连接database``conn = pymysql.connect(``  ``host=“你的数据库地址”,``  ``user=“用户名”,password=“密码”,``  ``database=“数据库名”,``  ``charset=“utf8”)` `# 得到一个可以执行SQL语句的光标对象``cursor = conn.cursor() # 执行完毕返回的结果集默认以元组显示``# 得到一个可以执行SQL语句并且将结果作为字典返回的游标``#cursor = conn.cursor(cursor=pymysql.cursors.DictCursor)` `# 定义要执行的SQL语句``sql = ``""``"``CREATE TABLE USER1 (``id INT auto_increment PRIMARY KEY ,``name CHAR(10) NOT NULL UNIQUE,``age TINYINT NOT NULL``)ENGINE=innodb DEFAULT CHARSET=utf8; #注意：charset=``'utf8'` `不能写成utf-8``""``"` `# 执行SQL语句``cursor.execute(sql)` `# 关闭光标对象``cursor.close()` `# 关闭数据库连接``conn.close()`
```

 

在建链接之前，我们需要做好一些前期工作：建库建表

下面例子中 我将使用我建好的库：db= 'xing'

建好的userinfo表

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717153525399-63943329.png)

 

简单验证功能

[+ View Code](https://www.cnblogs.com/xfxing/p/9322199.html#)

　　

输出结果：

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717154037549-1155366096.png)

但是会有以下问题：输入的SQL 语句被注释了

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717154152569-1613302466.png)

或者是

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717154318501-1965568199.png)

 

这个时候之后 我们可以这样解决

```
`execute帮我们做字符串拼接` `# 将以下代码``sql=``"select * from userinfo where name='%s' and password='%s'"` `%(user,pwd)``res=cursor.execute(sql)``# 改为``sql=``"select * from userinfo where name=%s and password=%s"` `#%s需要去掉引号，pymysql会自动加上` `res=cursor.execute(sql,[user,pwd])`
```

 输出结果：

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717155137020-45013445.png)

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717155151260-1616861087.png)

 

二、增删改查操作

添加多条数据

```
`import pymysql` `conn = pymysql.connect(``  ``host=``'192.168.0.103'``,``  ``port=3306,``  ``user=``'root'``,``  ``password=``'123'``,``  ``database=``'xing'``,``  ``charset=``'utf8'``)``# 获取一个光标``cursor = conn.cursor()` `# 定义要执行的sql语句``sql = ``'insert into userinfo(user,pwd) values(%s,%s);'``data = [``  ``(``'july'``, ``'147'``),``  ``(``'june'``, ``'258'``),``  ``(``'marin'``, ``'369'``)``]``# 拼接并执行sql语句``cursor.executemany(sql, data)` `# 涉及写操作要注意提交``conn.commit()` `# 关闭连接``cursor.close()``conn.close()`
```

输出结果：

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717160847020-1135038350.png)

```
插入单条数据
import pymysql``conn =pymysql.connect(``  ``host =``'192.168.0.103'``,``  ``port = 3306,``  ``user = ``'root'``,``  ``password =``'123'``,``  ``database =``'xing'``,``  ``charset =``'utf8'``)``cursor =conn.cursor() #获取一个光标``sql =``'insert into userinfo (user,pwd) values (%s,%s);'` `name = ``'wuli'``pwd = ``'123456789'``cursor.execute(sql, [name, pwd])``conn.commit()``cursor.close()``conn.close()
```

　输出结果：

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717161406701-2002469455.png)　

 

获取最新插入数据 （最后一条）

```
`import pymysql` `# 建立连接``conn = pymysql.connect(``  ``host=``"192.168.0.103"``,``  ``port=3306,``  ``user=``"root"``,``  ``password=``"123"``,``  ``database=``"xing"``,``  ``charset=``"utf8"``)``# 获取一个光标``cursor = conn.cursor()``# 定义将要执行的SQL语句``sql = ``"insert into userinfo (user, pwd) values (%s, %s);"``name = ``"wuli"``pwd = ``"123456789"``# 并执行SQL语句``cursor.execute(sql, [name, pwd])``# 涉及写操作注意要提交``conn.commit()``# 关闭连接` `# 获取最新的那一条数据的ID``last_id = cursor.lastrowid``print(``"最后一条数据的ID是:"``, last_id)` `cursor.close()``conn.close()`
```

输出结果为：（因为我之前插入多条记录时，多运行了两次，所有结果下面的这个）

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717161949020-1010555122.png)

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717161959685-786416707.png)

 

 删除操作

```
`import pymysql` `# 建立连接``conn = pymysql.connect(``  ``host=``"192.168.0.103"``,``  ``port=3306,``  ``user=``"root"``,``  ``password=``"123"``,``  ``database=``"xing"``,``  ``charset=``"utf8"``)``# 获取一个光标``cursor = conn.cursor()``# 定义将要执行的SQL语句``sql = ``"delete from userinfo where user=%s;"``name = ``"june"``# 拼接并执行SQL语句``cursor.execute(sql, [name])``# 涉及写操作注意要提交``conn.commit()``# 关闭连接` `cursor.close()``conn.close()`
```

输出结果是：

![img](https://images2018.cnblogs.com/blog/899590/201807/899590-20180717162429727-1780572982.png)

```
更改数据
import pymysql` `# 建立连接``conn = pymysql.connect(``  ``host=``"192.168.0.103"``,``  ``port=3306,``  ``user=``"root"``,``  ``password=``"123"``,``  ``database=``"xing"``,``  ``charset=``"utf8"``)``# 获取一个光标``cursor = conn.cursor()``# 定义将要执行的SQL语句``sql = ``"update userinfo set pwd=%s where user=%s;"``# 拼接并执行SQL语句``cursor.execute(sql, [``"july"``, ``"july"``])` `# 涉及写操作注意要提交``conn.commit()` `# 关闭连接``cursor.close ()``conn.close ()
查询数据
fetch数据
import pymysql` `conn = pymysql.connect (``  ``host=``'192.168.0.103'``,``  ``port=3306,``  ``user=``'root'``,``  ``password=``'123'``,``  ``database=``'xing'``,``  ``charset=``'utf8'``)``# 获取一个光标``cursor = conn.cursor(cursor=pymysql.cursors.DictCursor) # 返回字典数据类型` `# 定义将要执行的sql语句``sql = ``'select user,pwd from userinfo;'``# 拼接并执行sql语句``cursor.execute(sql)` `# 取到查询结果``ret1 = cursor.fetchone() # 取一条``ret2 = cursor.fetchmany(3) # 取三条``ret3 = cursor.fetchone() # 取一条` `cursor.close()``conn.close()` `print(ret1)``print(ret2)``print(ret3)　　

# 可以获取指定数量的数据``cursor.fetchmany(3)``# 光标按绝对位置移动1``cursor.scroll(1, mode=``"absolute"``)``# 光标按照相对位置(当前位置)移动1``cursor.scroll(1, mode=``"relative"``)

 
数据回滚
import pymysql` `# 建立连接``conn = pymysql.connect(``  ``host=``"192.168.0.103"``,``  ``port=3306,``  ``user=``"root"``,``  ``password=``"123"``,``  ``database=``"xing"``,``  ``charset=``"utf8"``)``# 获取一个光标``cursor = conn.cursor()``# 定义将要执行的SQL语句``sql1 = ``"insert into userinfo (user, pwd) values (%s, %s);"``sql2 = ``"insert into hobby (id, hobby) values (%s,%s);"``user = ``"july1"``pwd = ``"july1"``id = ``"我是错误的id"` `#id = ``"3"``hobby = ``"打游戏"``try``:``  ``# 拼接并执行SQL语句``  ``cursor.execute(sql1, [user, pwd])``  ``print(sql1)``  ``cursor.execute(sql2, [id, hobby]) # 报错的SQL语句``  ``# 涉及写操作注意要提交``  ``conn.commit()``except Exception ``as` `e:``  ``print(str(e))``  ``# 有异常就回滚``  ``conn.rollback()` `# 关闭连接``cursor.close()``conn.close()
```