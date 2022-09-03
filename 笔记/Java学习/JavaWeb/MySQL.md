JavaWeb网站的工作原理

![image-20220708214410335](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708214410335.png)

这些过程用到的技术叫做Javaweb技术栈。

数据传输的格式由协议规定。

![image-20220708214851541](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708214851541.png)



# 1、初识MySQL

JavaEE:企业级Java开发 Web

前端(页面：展示，数据！)

后台（连接点：连接数据库JDBC，链接前端（控制视图跳转，和给前端传递数据））

数据库（存数据，Txt,Excel,word)



## 1.1、什么是数据库

数据库（DB,DataBase)

概念：数据仓库，软件，安装在操作系统之上！SQL语句操作，可以存储大量的数据，500万以下。

作用：存储数据，管理数据

## 1.2、数据库分类

关系型数据库：（SQL)

- MySQL，Oracle,Sql Server,DB2，SQLlite
- 通过表和表之间，行和列之间的关系进行数据的存储。



非关系型数据库：(NoSQL) Not Only SQL

- Redis,MongDB
  - 对象存储，通过对象的自身属性来决定。

**DBMS(数据库管理系统)**

- 数据库的管理软件，科学有效的管理我们的数据。维护和获取数据。

- MySQL,数据库管理系统。

  ![image-20220704154303559](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220704154303559.png)

## 1.3、MySQL简介

MySQL是一个关系型数据库管理系统

由瑞典MySQL AB 公司开发，属于 Oracle 旗下产品。

MySQL是最好的 RDBMS (Relational Database Management System，关系数据库管理系统) 应用软件之一。

开源的数据库软件。

体积小、速度快、总体拥有成本低。招人成本比较低，所有人必须会。

中小型网站、或者大型网站，可以集群。

版本

- 5.7稳定
- 8.0相对稳定



## 1.4、安装MySQL（略）

## 1.5、安装SQLyog（略）

## 1.6、SQLyog的使用

### 步骤：

1. 无脑安装

2. 注册

3. 打开数据库连接![image-20220704160349573](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220704160349573.png)

4. 新建一个数据库school

   ![image-20220704160659057](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220704160659057.png)

5. 新建一张表student

   ```
   字段：id,name,age
   ```

   

![image-20220704160827491](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220704160827491.png)

字符集：utf8mb4

核对：utf8mb4_bin

6.查看表

![image-20220704161032710](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220704161032710.png)

7.插入数据

![image-20220704161039205](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220704161039205.png)

## 1.7、连接数据库

命令行（cmd）连接！

```
mysql -uroot -p123456 //连接数据库

//所有语句都是用分号;结尾，除了use语句

show databases; //查看所有数据库

use 数据库名;//切换到对应数据库

show tables;//查看所有表

describe 表名;//查看对应表

create database 数据库名;//创建一个数据库

exit//退出连接

// --单行注释，两个减号

//多行注释 /*  */
```



数据库四种语言 （CURD：增删改查  CV程序员 API程序员 CURD程序员）

DDL 定义

DML 操作

DQL 查询

DCL 控制

# 2、操作数据库

![image-20220708215319276](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708215319276.png)



Mysql自带的四个数据库

![image-20220708215411239](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708215411239.png)



information_schema存放视图；

mysql存放权限、安全信息。

performance_schema存放性能信息

sys存放系统相关信息



操作数据库->操作数据库中的表->操作数据库表中的数据

**mysql关键字不区分大小写**

***以下操作带中括号[]可选，带大括号{}必选***

## 2.1、操作数据库

### 2.1.1、创建数据库

```
create database [if not exist] westos;
```



### 2.1.2、删除数据库

```
drop database [if exist] westos;
```



### 2.1.3、使用数据库

```
use westos;//如果表名或字段名是一个特殊字符，就要带``
```

### 2.1.4、查看数据库

```
show databases;
```

## 2.2、数据库的列类型

> **数值**

- tinyint 	     十分小的数据	     1个字节
- smallint 	   较小的数据	        2个字节
- mediumint  中等的数据            3个字节
- **int                 标准的数据            4个字节**
- bigint            较大的数据            8个字节
- float              浮点数                    4个字节
- double         读点数                    8个字节
- decimal       字符串形式的浮点数 金融计算的时候，一般使用decimal，防止精度损失

> **字符串**

- char	字符串固定大小的 0~255	
- **varchar 可变字符串         0~65536 **对应String
- tinytext 微型文本               2^8-1
- **text        文本                      2^16-1 保存大文本**

> **日期**

java.util.Date

- Date	YYYY-MM-DD,	日期格式
- time    HH:   mm: ss,      时间格式
- **datetime YYYY-MM-DD HH:mm:ss 最常用的日期格式**
- **timestamp 时间戳，1970，1，1到现在的的毫秒数！也较为常用**
- year 年份表示

> null

- 没有值，未知
- 不要使用null进行计算，结果为null

## 2.3、数据库的字段属性（重点）

Unsigned:

- 无符号的整数
- 声明了该列不能为负数

zerofill：

- 0填充
- 不足位数使用0来填充 int (3),  5,  005

自增：

- 通常理解为自增，自动在上一条记录的基础上+步长（默认为1）
- 通常用来设计唯一的主键~index，必须是整数类型
- 可以自定义设计主键自增的起始值和步长

非空 NUll not null

- 假设设置为not null,如果不给它赋值，它就会报错。
- NULL,如果不填写值，默认就是null。

默认：

- 设置默认的值！
- sex,默认为男，如果不指定该列的值，则会有默认的值

## 2.4、创建数据库表（重点）

**注意点**

- 使用英文的,和()  ，表的名称尽量用``包起来
- AUTO_INCREMENT 自增
- 字符串使用英文单引号或双引号括起来，默认单引号。
- 所有语句后面加,（英文逗号），最后一个不加
- PRIMARY KEY 主键，一般一个表中只有一个主键。

```mysql
CREATE TABLE IF NOT EXISTS `student`(
`id` INT(4) NOT NULL AUTO_INCREMENT COMMENT '学号',
`name` VARCHAR(20) NOT NULL DEFAULT '匿名' COMMENT '姓名',
`pwd` VARBINARY(20) NOT NULL DEFAULT '123456' COMMENT '密码',
`sex` VARCHAR(2) NOT NULL DEFAULT '女' COMMENT '性别',
`birthday` DATETIME DEFAULT NULL COMMENT '出生日期',
`address` VARCHAR(100) DEFAULT NULL COMMENT '家庭住址',
`email` VARCHAR(50) DEFAULT NULL COMMENT '邮箱',
PRIMARY KEY(`id`)
)ENGINE=INNODB DEFAULT CHARSET utf8

```



```mysql
create table [if not exists] `表名`（
	`字段名` 列类型 [属性][索引][注释]，
	`字段名` 列类型 [属性][索引][注释]，
	`字段名` 列类型 [属性][索引][注释]，
	......
	`字段名` 列类型 [属性][索引][注释]
	)[表类型][字符集设置][注释]
```

```
show create database 数据库名 --查看创建数据库的语句
show create table 表名--查看创建表的语句
desc 表名--查看表的结构
```

## 2.5、数据库表的类型

```mysql
--关于数据库引擎
/*
INNODB 默认使用
MYISAM 早些年使用
*/
```

|              | MYISAM | INNODB   |
| ------------ | ------ | -------- |
| 事务支持     | 不支持 | 支持     |
| 数据行锁定   | 不支持 | 支持     |
| 外键约束     | 不支持 | 支持     |
| 全文索引     | 支持   | 不支持   |
| 表空间的大小 | 较小   | 约为两倍 |

常规使用操作：

- MYISAM 节约空间，速度快
- INNODB 安全性高，事务的处理，多表多用户操作



> 在物理空间的位置 

所有的数据库文件都存在data文件下，一个文件夹就对应一个数据库

本质还是文件的存储！



MySQL引擎在物理文件上的区别

- InnoDB在数据库表中只有一个*.frm文件，以及上级目录下的ibdata1文件
- MYISAM对应文件
  - *.frm 表结构的定义文件
  - *.MYD 数据文件（data)
  - *.MYI 索引文件（index)





设置数据库表的字符集编码

```
charset=utf8
```

不设置的话，会是mysql默认的字符集编码Latin1 ,不支持中文。

## 2.6、修改删除表

> 修改

```mysql
--alter table 旧表名 rename as 新表名
alter table teacher rename as teacher1

--增加表的字段 alter table 表名 add 字段名 列属性
alter table teacher1 add age int(11)

--修改表的字段（重命名，修改约束！）
--change用来字段重命名，也能修改字段类型和约束
--modify不用来字段重命名，只能修改字段的类型和约束
--alter table 表名 modify 字段名 列属性[]
alter table teacher1 modify age varchar(11)
--alter table 表名 modify 旧字段名 新字段名 列属性[]
alter table teacher1 modify age age1 varchar(11)

--删除表的字段：alter table 表名 drop 字段名
alter table teacher1 drop age1
```



> 删除

```mysql
--删除表
drop table [if exists] 表名 --尽量都加上判断，创建删除表
```

# 3、MySQL数据管理

## 3.1、外键（了解，阿里规定强制不得使用外键）

```mysql
--方式一：创建表时使用
key `FK_gradeid` (`gradeid`),
constraint `FK_gradeid` foreign key (`gradeid`) references `grade` (`gradeid`)
--方式二：单独定义
--alter table 表名 add constraint 约束名 foreign key （作为外键的列）references 另一个表 (字段名)
alter table student add constraint `FK_gradeid` foreign key (`gradeid`) references `grade` (`gradeid`)
```

方法一：直接在属性值后面添加
create table 表名(
字段1 int(11),
字段2 int(50) references 外表表名(约束字段),
字段3 int(30) references 外表表名(约束字段),
primary key(字段2,字段3)
);

方法二：
create table 表名(
字段1 int(11),
字段2 int(50),
字段3 int(30),
primary key(字段2,字段3),
FOREIGN KEY(字段2) REFERENCES 外表表名(约束字段),
FOREIGN KEY(字段3) REFERENCES 外表表名(约束字段),
);

方法三：
create table 表名(
字段1 int(11),
字段2 int(50),
字段3 int(30),
primary key(字段2,字段3),
CONSTRAINT 外键名称 FOREIGN KEY (字段2) REFERENCES 外表表名(约束字段),
CONSTRAINT 外键名称 FOREIGN KEY (字段3) REFERENCES 外表表名(约束字段),
);

方法四：在表的定义外进行添加
alter table 表名 add constraint FK_ID foreign key(外键字段名) REFERENCES 外表表名(对应的表的主键字段名);

## 3.2、DML语言（全部记住）

### 3.2.1、添加

![image-20220708215952031](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708215952031.png)

![image-20220708220624898](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708220624898.png)

### 3.2.2、修改

![image-20220708220409443](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708220409443.png)

​	![image-20220708220603082](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708220603082.png)![image-20220708220531092](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708220531092.png)

### 3.2.3、删除

![image-20220708220649713](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708220649713.png)

![image-20220708220736102](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708220736102.png)

## 3.3、DQL

![image-20220708221053537](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708221053537.png)

### 3.3.1、基础查询

![image-20220708221758853](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708221758853.png)![image-20220708221316982](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708221316982.png)

![image-20220708221334945](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708221334945.png)

![image-20220708221404846](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708221404846.png)

​	![image-20220708221422448](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708221422448.png)	distinct关键字

![image-20220708221457929](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708221457929.png)	

​	as代替显示，as可省略。![image-20220708221534015](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708221534015.png)

### 3.3.2、条件查询

![image-20220708222137240](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708222137240.png)

![image-20220708221951736](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708221951736.png)

![image-20220708222027352](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708222027352.png)

![image-20220708222113665](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708222113665.png)

### 3.3.3、排序查询

![image-20220708222315428](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708222315428.png)

![image-20220708222341461](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708222341461.png)

![image-20220708222406566](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708222406566.png)

### 3.3.4、聚合查询

![image-20220708222445612](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708222445612.png)

![image-20220708225541510](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708225541510.png)

![image-20220708225633121](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708225633121.png)

### 3.3.5、分组查询

![image-20220708225710628](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708225710628.png)	![image-20220708225756122](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708225756122.png)	![image-20220708225848289](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708225848289.png)

![image-20220708225902002](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708225902002.png)

### 3.3.6、分页查询

![image-20220708225948145](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708225948145.png)

![image-20220708230120954](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708230120954.png)	

## 3.4、约束



![image-20220708230235991](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708230235991.png)	

## 3.5、数据库设计

![image-20220708234515214](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708234515214.png)	

![image-20220708234743722](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220708234743722.png)

![image-20220709121941087](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709121941087.png)		

## 3.6、多表查询

![image-20220709123003364](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709123003364.png)	![image-20220709123100776](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709123100776.png)	![image-20220709123341023](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709123341023.png)	![image-20220709123525430](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709123525430.png)	![image-20220709123641918](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709123641918.png)

案列见[JavaWeb基础教程P28 多表查询-案例](https://www.bilibili.com/video/BV1Qf4y1T7Hx?p=28&vd_source=720815f194a8e07f74e49abf87b21225)

## 3.7、事务

![image-20220709125843111](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709125843111.png)	![image-20220709125930307](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709125930307.png)	

# 4、JDBC

![image-20220709130108769](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709130108769.png)	

## 4.1、JDBC简介

![image-20220709130549812](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709130549812.png)



## 4.2、JDBC快速入门

![image-20220709130735645](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709130735645.png)	

```java
package com.kai;

import java.sql.Connection;
import java.sql.Driver;
import java.sql.DriverManager;
import java.sql.Statement;

public class JDBCDemo {
    public static void main(String[] args) throws Exception {
        //1.注册驱动
        Class.forName("com.mysql.cj.jdbc.Driver");
        //2.获取连接
        String url = "jdbc:mysql://127.0.0.1:3306/school?serverTimezone=GMT%2B8&useSSL=false";
        String username = "root";
        String password = "123456";
        Connection connection=DriverManager.getConnection(url,username,password);

        //3.定义sql
        String sql="INSERT INTO `school`.`student`(`id`, `name`, `age`) VALUES (3, '小红', 20)";
        //4.获取执行sql的对象Statement
        Statement statement=connection.createStatement();
        //5.执行sql
        int count = statement.executeUpdate(sql);//受影响的行数
        //6.处理结果
        System.out.println(count);
        //7.释放资源
        statement.close();
        connection.close();

    }
}

```

导入jar包之后需要右键jar包选Add as Library指定jar包生效范围。

mysql5.0版本之后不需要写第一步，因为jar包下的META-INF下的services文件夹下的java.sql.Driver文件下导入了Driver类。 

如果连接是本级并且端口是3306，可以简化书写，省略127.0.0.1:3306

注意mysql8.0版本之后要指明时区：serverTimezone=GMT

还要指明是否同意SSL协议: useSSL=false

## 4.3、JDBC API详解

### 4.3.1、DriverManager

![image-20220709134716152](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709134716152.png)

![image-20220709134702531](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709134702531.png)

参数用&连接

### 4.3.2、Connection

![image-20220709135004516](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709135004516.png)	第三个不常用

![image-20220709135038113](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709135038113.png)	![image-20220709135314328](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709135314328.png)	

### 4.3.3、Statement

![image-20220709135410080](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709135410080.png)	

### 4.3.4、ResultSet

![](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709135631665.png)	

![image-20220709140012439](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709140012439.png)

![image-20220709140116243](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709140116243.png)	![image-20220709140153652](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709140153652.png)	![image-20220709140209313](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709140209313.png)	

![image-20220709140246263](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709140246263.png)

![image-20220709140352890](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709140352890.png)

![image-20220709140411583](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709140411583.png)

### 4.3.5、PrepareStatement([没搞懂之后看](https://www.bilibili.com/video/BV1Qf4y1T7Hx?p=35&vd_source=720815f194a8e07f74e49abf87b21225))



​	![image-20220709140549344](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709140549344.png)	

## 4.4、数据库连接池

![image-20220709141052916](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709141052916.png)	![image-20220709141324063](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709141324063.png)	![image-20220709141418410](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709141418410.png)

![image-20220709141710801](C:/Users/23893/AppData/Roaming/Typora/typora-user-images/image-20220709141710801.png)	

## [4.5、JDBC练习](https://www.bilibili.com/video/BV1Qf4y1T7Hx?p=39&vd_source=720815f194a8e07f74e49abf87b21225)







# 5、Maven



