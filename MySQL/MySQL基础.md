# MySQL基础

## SQL
### SQL通用语法
 - SQL可以多行书写，以分号结尾
 - 关键字使用**大写**以规范
 - 注释为：--XXX或#XXX（MySQL特有）；多行：/* XXX */
### DDL(数据定义语言)
#### 数据库操作
##### 查询
```
	查询所有数据库
	show databases;

	查询当前数据库
	select database();
```
##### 创建
```
 create database [if not exists] 数据库名 [default charset 字符集][collate 排序规则];
```
##### 删除
```
	drop atabase[if exists] 数据库名;
```
##### 使用
```
	use 数据库名;
```
#### 表操作
##### 查询
```
	查询当前数据库所有表
	show tables;

	查询表结构
	desc 表名;

	查询指定表的建表语句
	show create table 表名;
```
##### 创建
```
	create table 表名(
		字段1 字段1类型[comment 字段1注释],
		字段2 字段2类型[comment 字段2注释],
		...
		字段n 字段n类型[comment 字段n注释]
	)[comment 表注释];
```
![输入图片说明](assets/wRXe4FdFtg1DfYCM.png)
##### 修改
```
	添加字段
	alter table 表名 add 字段名 类型(长度) [comment 注释][约束];

	修改数据类型
	alter table 表名 modify 字段名 新数据类型(长度)

	修改字段名和字段类型
	alter table 表名 change 旧字段名 新字段名 类型(长度) [comment 注释][约束];

	删除字段
	alter table 表名 drop 字段名;

	修改表名
	alter table 表名 rename to 新表名;
```
##### 删除
在删除表时，表中数据也会一并删除
```
	删除表
	drop table[if exists] 表名;

	删除指定表，并重新创建该表
	truncate table 表名;
```
### DML(数据操作语言)
#### 添加数据
```
	给指定字段添加数据
	insert into 表名(字段名1,字段名2,...) values(值1,值2,...);

	给全部字段添加数据
	insert into 表名 valuse(值1,值2,...);
```
#### 修改数据
```
	update 表名 set 字段名1=值1,字段名2=值2,...[where 条件];
```
#### 删除数据
```
	delete from 表名 [where 条件];
```
### DQL(数据查询语言)
#### 查询多个字段
```
	select 字段1,字段2,... from 表名;
	select * from 表名;
```
#### 设置别名
```
	select 字段1 [as 别名1],字段2[as 别名2]... from 表名;
```
#### 去重查询
```
	select distinct 字段列表 from 表名;
```
#### 条件查询
```
	select 字段列表 from 表名 where 条件列表;
```
#### 聚合函数
```
	select 聚合函数() from 表名;
	常见聚合函数：
		count  统计数量
		max	   最大值
		min    最小值
		avg    平均值
		sum    求和
	null值不参与其运算
```
#### 分组查询
```
	select 字段列表 from 表名 [where 条件] group by 分组字段名 [having 分组后过滤条件];
```
where和having区别
1. 执行时机不同：where是分组前过滤，不满足where条件，不参与分组；而having是分组后对结果进行过滤
2. 判断条件不同：where不能对聚合函数进行判断，而having可以

#### 排序查询
```
	select 字段列表 from 表名 order by 字段1 排序方式1,字段2 排序方式2;
```
1. 排序方式：asc(升序),desc(降序)；
2. 若是多个字段排序，当第一个字段相同时，才会根据第二个字段进行排序

#### 分页查询
```
	select 字段列表 from 表名 limit 起始索引,查询记录数;
```
注意：
1. 起始索引从零开始，起始索引=(查询页码-1)*每页显示记录数。
2. 分页查询为方言，MySQL中是limit。
3. 若查询第一页，起始索引可以省略，直接简写为limit 10.

#### 顺序
![顺序](assets/N1RLIGfluQMAfQjR.png)

### DCL(数据控制语言)
#### 管理用户
##### 查询用户
```
use mysql;
select * from user;
```
##### 创建用户
```
create user '用户名'@'主机名' identified by '密码';
```
##### 修改用户密码
```
alter user '用户名'@'主机名' identified with mysql_native_password by '新密码';
```
##### 删除用户
```
drop user '用户名'@'主机名';
```
***
#### 权限控制
1. 多个权限之间，使用逗号分隔
2. 授权时，数据库名和表名可以使用*进行通配，代表所有
##### 查询权限
```
show grants for '用户名'@'主机名';
```
##### 授予权限
```
grant 权限列表 on 数据库名.表名 to '用户名'@'主机名';
```
##### 撤销权限
```
revoke 权限列表 on 数据库名.表名 form '用户名'@'主机名';
```
##### 权限列表
![权限](assets/rs71KA3okvMdnPwI.png)
## 函数
### 字符串函数
```
1.concat(s1,s2,...sn);
字符串拼接，将s1,s2,...sn拼接成一个字符串

2.lower(str);
将字符串str全部转化为小写

3.upper(str);
将字符串str全部转化为大写

4.lpad(str,n,pad);
左填充，用字符串pad对str的左边进行填充，达到n个字符串长度

5.rpad(str,n,pad);
右填充，用字符串pad对str的右边进行填充，达到n个字符串长度

6.trim(str);
去掉字符串头部和尾部的空格

7.substring(str,start,len);
返回从字符串str从start位置起的len个长度的字符串
```
### 数值函数
```
1.ceil(x);
向上取整

2.floor(x);
向下取整

3.mod(x,y);
返回x/y的模

4.rand();
返回0~1内的随机数

5.round(x,y);
求参数x的四舍五入的值，保留y位小数
```
### 日期函数
```
1.curdate();
返回当前日期

2.curtime();
返回当前时间

3.now();
返回当前日期和时间

4.year(date)
获取指定date的年份

5.month(date);
获取指定date的月份

6.day(date);
获取指定date的日期

7.date_add(date,INTERVAL expr type);
返回一个日期/时间值加上一个时间间隔expr后的时间值

8.datediff(date1,date2);
返回起始时间date1和结束时间date2之间的天数
```
### 流程函数
```
1.if(value,t,f);
如果value为true，则返回t，否则返回f

2.ifnull(value1,value2);
如果value1不为空，返回value1，否则返回value2

3.case when [val1] then [res1]...else [dafault] end;
如果val1为true，返回res1，...否则返回default默认值

4.case [expr] when [val1] then [res1]...else [default] end;
如果expr的值等于val1，返回res1，...否则返回default默认值
```
## 约束
![约束](assets/FfDAsXhAPIspI4tl.png)
约束是作用在表中字段上的，可以在创建表/修改表的时候添加约束

示例：
![例子](assets/XNiTaQH0bhyb8u2V.png)

### 外键约束
#### 添加外键
```
creat table 表名(
	字段名 数据类型,
	...
	[constraint] [外键名称] foreign key(外键字段名) references 主表(主表列名)
);

alter table 表名 add constraint 外键名称 foreign key (外键字段名) references 主表(主表列名);
```
#### 删除外键
```
alter table 表名 drop foreign key 外键名称;
```
#### 删除/更新行为
![输入图片说明](assets/ApYSrHW5TaXy8x0b.png)
语法：
```
alter table 表名 add constraint 外键名称 foreign key (外键字段) references 主表名(主表字段名) on update ... on delete ...;
```

