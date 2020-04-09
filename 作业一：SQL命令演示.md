## MySQL语言命令

### 一、数据库操作相关的命令
#### 1.创建一个新的数据库

**执行命令如下:**

```SQL 
create database test;   # 创建名为“test”的数据库
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/1.png)

#### 2.查看和选择数据库：

**执行命令如下：**

```SQL
show databases; 	# 显示全部数据库
use test;		# 选择test数据库
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/2.png)

#### 3.删除数据库：

**执行命令如下：**

```SQL
drop database test; 	# 删除test数据库
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/3.png)

### 二、查看MySQL数据库中的存储引擎
#### 1.查看所支持的存储引擎

**执行命令如下:**

```SQL
show engines;  
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/4.png) 

#### 2.查看默认的存储引擎

**执行命令如下:**

```MySQL
show variables like '%storage_engine%';  
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/5.png) 

### 三、对表操作的相关命令
#### 1.在数据库中创建一个新的表

**执行命令如下:**

```SQL
create table t_dept(
 deptno int,
dname varchar(20),
loc varchar(40)
); 
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/6.png) 

#### 2.查看表的定义信息

**执行命令如下:**

```SQL
describe t_dept;		 # 查看表的定义
show create table t_dept; 	 # 查看表的详细定义
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/7.png) 

#### 3.删除表

**执行命令如下:**

```SQL
drop table t_dept;	#删除表t_dept
describe t_dept;       #查看表t_dept是否存在
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/8.png) 

#### 4.修改表名

**执行命令如下:**

```SQL
alter table t_dept rename t_dept1;  # 将表明 t_dept 变为 t_dept1
show tables;	# 查看数据库biu1中的全部表
desc t_dept;	# 查看表对象t_dept
desc t_dept1;	# 查看表对象t_dept1
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/9.png) 

#### 5.增加字段和删除字段

**执行命令如下:**
##### 在表的最后面增加字段
```SQL
desc t_dept1;		# 查看表的内容
alter table t_dept1 add tel varchar(20); 	# 在表的最后面增加字段
desc t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/10.png) 

**执行命令如下:**
##### 在表的最前面增加字段
```SQL
desc t_dept1;		
alter table t_dept1 add name varchar(10) first; # 在表的最前面增加字段
desc t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/11.png)

**执行命令如下:**
##### 在表指定字段后增加字段
```SQL
desc t_dept1;
alter table t_dept1 add class varchar(10) after dname; # 在指定字段位置dname后增加字段
desc t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/12.png)

**执行命令如下:**
##### 删除字段
```SQL
desc t_dept1;
alter table t_dept1 drop class; # 删除字段
desc t_dept1;
```
![](https://github.com/fyh1234/homework/blob/master/photo/13.png)

#### 6.修改字段

##### 修改字段的数据类型
**执行命令如下:**

```SQL
desc t_dept1;			    # 查看表的内容
alter table t_dept1 modify tel int; # 修改属性Tel的数据类型
desc t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/14.png)

##### 同时修改字段的名字和数据类型
**执行命令如下:**

```SQL
desc t_dept1;		# 查看表的内容
alter table t_dept1 change dname Dname VARCHAR(10);  # 将字段dname修改为Dname且数据类型变为VARCHAR(10)
desc t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/15.png)

##### 修改字段的顺序
**执行命令如下:**

```SQL
desc t_dept1;		# 查看表的内容
alter table t_dept1 modify  deptno int(11) after loc;   # 将字段deptno放到字段loc前面	
desc t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/16.png)

### 四、操作表的约束
**执行命令如下:**

```SQL
create table t_dept2(
deptno int not null,  			# 设置非空约束
dname varchar(20) default 'Petter',	# 设置字段的默认值
name varchar(20) unique,		#设置唯一约束
loc varchar(40), 
number int primary key auto_increment	#设置字段自动增加
); 
desc t_dept2;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/17.png) 

### 五、数据的操作
#### 1.插入数据记录

**执行命令如下:**

```SQL
insert into t_dept1 values('Goudan','Ergouzi','Zhejiang',123,123456);
insert into t_dept1 values('Zhangsan','Lisi','Guangdong',124,123457);
select* from t_dept1;  #查询表的数据记录
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/18.png)

#### 2.同时插入多条数据记录

**执行命令如下:**

```SQL
insert into t_dept1 values('Zhangfei','Guanyu','heibei',123,123456),
('Dianwei','Caocao','anhui',148,123457),
('Zhugeliang','Kongming','Sichuan',234,123458);
select* from t_dept1; #查询表的数据记录
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/19.png)

#### 3.将一个表的记录插入另一个表中

**执行命令如下:**

```SQL
#创建一个新的表class,其中的字段类型与t_dept1一样
create table class(
Aname varchar(10),
Bname varchar(10),
loc varchar(40),
deptno int,
tel int
);		
#给class中插入记录
insert into class values ('Xiaobai','Xiaohong','Beijing',888,16688),
('Xiaobao','Xiaoqiang','Sichuan',666,57688);
select * from class;  #查询表的数据记录
#将class中的部分记录插入t_dept1中
insert into t_dept1(name,loc,tel) select Bname,loc,Tel from class;
select * from t_dept1;    ##查询表的数据记录
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/fyh1234/homework/blob/master/photo/20.png)
