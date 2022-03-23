# Sqli-labs

### 第一关

1.判断当前表的字段个数

![](C:\Users\wanghaoyu\Desktop\order by3.png)

![](C:\Users\wanghaoyu\Desktop\order by4.png)

说明表有3列

2.判断显示位

![](C:\Users\wanghaoyu\Desktop\显示位3.png)

![](C:\Users\wanghaoyu\Desktop\显示位4.png)

注：

​		?id=-1 union select 1,2,3,4--+ /联合查询第1 2 3 4列，空格-+的作用是注释后面的内容。

​		进行联合查询判断显示位时，在1的前面加-号或者改为0让前面的select语句查询为空错误，从而采用后面的语句进行查询。

​		联合查询要构造假的，1前面一定要加号，或者是?id=1 and 1=2构造前面的查询语句错误，从而使用后面的select语句。因为有两条select语句，要用号/把1改为0把前面的select语句注释掉(字符型、数字型均可)。

3.爆数据库中的表

![](C:\Users\wanghaoyu\Desktop\数据库中的表.png)

注：

information_schema：表示所有信息，包括库、表、列

information_schema.tables：记录所有表名信息的表

information_schema.columns：记录所有列名信息的表

table_schema：数据库的名称

table_name:表名

column_name:列名

group_concat():显示所有查询到的数据

4.爆表中字段

![](C:\Users\wanghaoyu\Desktop\表中字段.png)

5.爆相应字段的所有数据

![](C:\Users\wanghaoyu\Desktop\用户名密码.png)

### 第二关

1.判断注入点

![](C:\Users\wanghaoyu\Desktop\注入点0.png)

![](C:\Users\wanghaoyu\Desktop\注入点2.png)

and 1=1/and 1=2是都可以正常执行的但是返回的界面是不一样，说明为数字型注入

2.判断当前表的字段个数

![](C:\Users\wanghaoyu\Desktop\orderby4.png)

说明表有3列

3.判断显示位

![](C:\Users\wanghaoyu\Desktop\显示位5.png)

4.爆数据库中的表

![](C:\Users\wanghaoyu\Desktop\爆表.png)

5.爆表中字段

![](C:\Users\wanghaoyu\Desktop\爆字段.png)

6.爆相应字段的所有数据

![](C:\Users\wanghaoyu\Desktop\密码.png)

### 第三关

1.判断注入点

![](C:\Users\wanghaoyu\Desktop\判断注入点.png)

![注入点3](C:\Users\wanghaoyu\Desktop\注入点3.png)

![](C:\Users\wanghaoyu\Desktop\注入点5.png)

说明注入点为1’）

2.判断当前表的字段个数

![](C:\Users\wanghaoyu\Desktop\orderby.png)

3.判断显示位

![](C:\Users\wanghaoyu\Desktop\显示位.png)

4.爆数据库中的表

![](C:\Users\wanghaoyu\Desktop\爆表2.png)

5.爆表中字段

![](C:\Users\wanghaoyu\Desktop\字段.png)

6.爆相应字段的所有数据

![](C:\Users\wanghaoyu\Desktop\密码2.png)