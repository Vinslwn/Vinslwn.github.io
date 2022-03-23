# Mysql数据库

## 一、数据类型种类

#### 1.整型：int

可以由**十进制**和**十六进制**表示

#### 2.浮点型：float

由一个数字加一个小数点再加一个数字组成

#### 3.字符串

由单**引号**或双引号括起来的**字符或者数字**，如：“abc”,'abc10'

字符串中要用**转义字符**才能表示的特殊符号

| 序列 |  说明  | 序列 |  说明  |
| :--: | :----: | :--: | :----: |
|  \0  |  NULL  |  \n  |  新行  |
| \\'  | 单引号 |  \r  |  回车  |
| \\"  | 双引号 |  \t  | 制表符 |
|  \b  |  退格  |  \\  | 反斜杠 |

#### 4.日期和时间

Mysql是日期是按“年-月-日”的顺序

#### 5.NULL值

是一种**无类型**的值，表示“**空**”，什么也没有

#### 6.数值列类型

|  类型名   |      说明      | 类型名  |      说明      |
| :-------: | :------------: | :-----: | :------------: |
|  TINYINT  |  非常小的整数  | BIGINT  |     大整数     |
| SMALLINT  |   较小的整数   |  FLOAT  |  单精度浮点数  |
| MEDIUMINT | 中等大小的整数 | DOUBLE  |  双精度浮点数  |
|    INT    |    标准整数    | DECIMAL | 一个串的浮点数 |

#### 7.字符串列类型

| 类型名  |     说明     | 类型名 |            说明            |
| :-----: | :----------: | :----: | :------------------------: |
|  CHAR   |  定长字符串  |  ENUM  | 枚举；列可赋予某个枚举成员 |
| VARCHAR | 可变长字符串 |  SET   | 集合；列可赋予多个集合成员 |
|  BLOB   | 存储图像文件 |  TEXT  |          小文本串          |

#### 8.总结：常用数据类型

| 分类           | 备注和说明                                 | 数据类型                     | 说明                                                         |
| -------------- | ------------------------------------------ | ---------------------------- | ------------------------------------------------------------ |
| 二进制数据类型 | 储存非字符和文本的数据                     | BLOB                         | 可用来存储图像                                               |
| 文本数据类型   | 字符数据包括任意字母、符号或数字字符的组合 | char\|varchar\|text          | 固定长度的非Unicoke字符数据\|可变长度非Unicode\|存储长文本信息 |
| 日期和时间     | 日期和时间在单引号内输入                   | time\|date\|datetime         | 时间\|日期\|日期和时间                                       |
| 数值型数据     | 该数据仅包含数字，包括正数、负数以及浮点数 | int、smallint\|float、double | 整数\|浮点数                                                 |

## 二、常用SQL语言

#### 1.建立数据库操作

create database 数据库名;

#### 2.建立表操作

create table 表名(列名1 列类型 [列的完整性约束]，列名2 列类型 [列的完整性约束]，......);

例：create table test_table(id int(10), name varchar(20));

#### 3.删除表操作

drop table 表名;

#### 4.删除数据库操作

drop database 数据库名;

#### 5.更改表结构操作

alter table  表名 action;

其中，action可以是如下语句：

|                    语句                    |                             说明                             |
| :----------------------------------------: | :----------------------------------------------------------: |
|   add 列名 建表语句 [first\|after 列名]    | 可以为表添加一列，若没指定first或者after，则在列尾添加一列，否则在指定列添加新列 |
|           add primary key (列名)           |         为表添加一个主键，若主键已经存在，则出现错误         |
| modify 列名 <建表语句> [first\|after 列名] |      可以更改类型和列名称，若原列的名字和新列的名字相同      |
|                 drop 列名                  |                         可以删除一列                         |
|              rename as 新表名              |                           更改表名                           |

例：① 向test表中添加字段address2，类型为varchar，最大长度为100

​             alter table test address2 varchar（100）;

​        ② 将test表中的name列默认值改为100

​             alter table test alter name set default 100;

​        ③ 向student表增加“入学时间”列，其数据类型为日期型

​             alter table student add scome date;

#### 6.插入记录操作

insert [into] <表名> [列名] values <值列表>

例：insert into test(name,age) values("icq",25);

说明：如果表名后面没写字段名，则**默认**是向**所有的字段**添加值，另外字符串应该用‘ ’或“ ”引号括起来

#### 7.插入多行数据

insert into <表名> [列名] values(<列名值>),(<列名值>),(<列名值>)......

例：insert into test [name,age] values('icq',1),('icq',2),('icq',3);

#### 8更新数据行

update <表名> set <列名=更新值> [where <更新条件>]

例：将test表中名字为“icq”的改为“ICQ”

​        update test set name="ICQ" where name ="icq";

说明：where子句是判断语句，用来设定条件，限制只更新匹配的行，如果不带where子句，则更新所有行数据

#### 9.删除记录操作

delete from <表名> [where <删除条件>]

例：将test表中名字中，年龄大于20的删除

​        delete from test where age>20;

说明：此语句删除表中的行，若不带where子句，则删除整个表中的记录，但是表不被删除

#### 10.查询操作

select <列名> from <表名>  【 where <查询条件表达式>][order by<排序的列名>[ASC或者DESC] 】

例：![](C:\Users\wanghaoyu\Desktop\1.png)

​		select name,age from test where name='icq' order by age

#### 11.Mysql程序常用命令

显示所有数据库：show databases;

选定默认数据库：use dbname;

显示默认数据库中所有表：show tables;

放弃正在输入的命令：\c

显示命令清单：\h

退出Mysql程序：\q

查看Mysql服务器状态信息：\s

## 三、PHP操作Mysql

#### 1.PHP访问Mysql数据库的流程

第一步：连接Mysql服务器

​			   使用mysql_connect()函数建立Mysql服务器的连接

第二步：选择Mysql数据库

​		       使用mysql_select_db()函数选择Mysql数据库服务器上的数据库，并与数据库建立连接

第三步：执行SQL语句

​               在选择的数据库中使用mysql_query()函数执行SQL语句。对数据的操作方式主要包括4中方式：

| 数据操作 |                 说明                  |
| :------: | :-----------------------------------: |
| 查询数据 |   使用select语句实现数据的查询功能    |
| 插入数据 | 使用insert into语句向数据库中插入数据 |
| 更新数据 |   使用update语句修改数据库中的记录    |
| 删除数据 |    使用delete语句删除数据库中记录     |

第四步：关闭结果集

​			   数据库操作完成后，需要**关闭结果集**，以释放系统资源。语句为：mysql_free_result($result);

第五步：关闭Mysql服务器

​			   每使用一次mysql_connect()或mysql_query()函数，都会消耗系统资源

​			   如果用户连接超过一定数量时，就会造成系统性能的下降

​			   因此在完成数据库的操作后，应使用mysql_close()函数	关闭与Mysql服务器的连接，以**节省系统资源**

​			   语法为：mysql_close($Link);

总结：![](C:\Users\wanghaoyu\Desktop\2.png)