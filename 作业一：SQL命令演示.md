## 从零开始学习MySQL语言命令

### 一、介绍对数据库操作相关的命令
#### 1.创建一个新的数据库

**执行命令如下:**

```SQL
	CREATE DATABASE biu1;   # biu1为数据库名称
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/1.png?raw=true)

#### 2.查看和选择数据库：

**执行命令如下：**

```SQL
	SHOW DATABASES; 	# 显示全部数据库
	USE biu1;		# 选择biu1数据库
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/2.png?raw=true)

#### 3.删除数据库：

**执行命令如下：**

```SQL
	DROP DATABASE biu1; 	# 删除biu1数据库
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/3.png?raw=true)

### 二、如何查看MySQL数据库中的存储引擎
#### 1.查看所支持的存储引擎

**执行命令如下:**

```SQL
	SHOW ENGINES;  
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/4.png?raw=true) 

#### 2.查看默认的存储引擎

**执行命令如下:**

```MySQL
	SHOW VARIABLES LIKE '%storage_engine%';  
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/5.png?raw=true) 

### 三、介绍对表操作的相关命令
#### 1.在数据库中创建一个新的表

**执行命令如下:**

```SQL
	CREATE TABLE t_dept(
 	deptno INT,
	dname VARCHAR(20),
	loc VARCHAR(40)
	); 
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/6.png?raw=true) 

#### 2.查看表的定义信息

**执行命令如下:**

```SQL
	DESCRIBE t_dept;	# 查看表的定义
	SHOW CREATE TABLE t_dept; 	 # 查看表的详细定义
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/7.png?raw=true) 

#### 3.删除表

**执行命令如下:**

```SQL
	DROP TABLE t_dept;	#删除表t_dept
	DESCRIBE t_dept;      #查看表t_dept是否存在
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/8.png?raw=true) 

#### 4.修改表名

**执行命令如下:**

```SQL
	ALTER TABLE t_dept RENAME t_dept1;  # 将表明 t_dept 变为 t_dept1
	SHOW TABLE;	# 查看数据库biu1中的全部表
	DESC t_dept;	# 查看表对象t_dept
	DESC t_dept1;	# 查看表对象t_dept1
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/9.png?raw=true) 

#### 5.增加字段和删除字段

**执行命令如下:**
##### 在表的最后面增加字段
```SQL
	DESC t_dept1;		# 查看表的内容
	ALTER TABLE t_dept1 
		ADD Tel VARCHAR(20); # 在表的最后面增加字段
	DESC t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/10.png?raw=true) 

**执行命令如下:**
##### 在表的最前面增加字段
```SQL
	DESC t_dept1;		
	ALTER TABLE t_dept1 
		ADD Aname VARCHAR(10) FIRST, # 在表的最前面增加字段
	DESC t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/11.png?raw=true)

**执行命令如下:**
##### 在表指定字段后增加字段
```SQL
	DESC t_dept1;
	ALTER TABLE t_dept1 
		ADD Bname VARCHAR(10)
			AFTER dname; # 在指定字段位置dname后增加字段
	DESC t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/12.png?raw=true)

**执行命令如下:**
##### 删除字段
```SQL
	DESC t_dept1;
	ALTER TABLE t_dept1 
		DROP Bname; # 删除字段
	DESC t_dept1;
```
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/13.png?raw=true)

#### 6.修改字段

##### 修改字段的数据类型
**执行命令如下:**

```SQL
	DESC t_dept1;		# 查看表的内容
	ALTER TABLE t_dept1 
		MODIFY Tel INT; # 修改属性Tel的数据类型
	DESC t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/14.png?raw=true)

##### 同时修改字段的名字和数据类型
**执行命令如下:**

```SQL
	DESC t_dept1;		# 查看表的内容
	ALTER TABLE t_dept1 
		CHANGE dname Dname VARCHAR(10);  # 将字段dname修改为Dname且数据类型变为VARCHAR(10)
	DESC t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/15.png?raw=true)

##### 修改字段的顺序
**执行命令如下:**

```SQL
	DESC t_dept1;		# 查看表的内容
	ALTER TABLE t_dept1 
		MODIFY  deptno INT(11) AFTER loc;   # 将字段deptno放到字段loc前面	
	DESC t_dept1;
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/16.png?raw=true)

### 四、操作表的约束
**执行命令如下:**

```SQL
	CREATE TABLE t_dept2(
 	deptno INT NOT NULL,  # 设置非空约束(NOT NULL,NK)
	dname VARCHAR(20) DEFAULT 'Petter', # 设置字段的默认值(DEFAULT)
	cname VARCHAR(20) UNIQUE,	#设置唯一约束（UNIQUE,UK）
	loc VARCHAR(40)， 
	number INT PRIMARY KEY AUTO_INCREMENT	#设置字段自动增加
	); 
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/17.png?raw=true) 

### 五、数据的操作
#### 1.插入数据记录

**执行命令如下:**

```SQL
	INSERT INTO t_dept1(Aname,Dname,loc,deptno,Tel)
		values('Kangkang','Lisa','Zhejiang',0123,0235221);
	INSERT INTO t_dept1(Aname,Dname,loc,deptno,Tel)
		values('Xuxin','Laowang','Chongqing',0124,0235222);
	SELECT * FROM T_DEPT1;  #查询表的数据记录
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/20.png?raw=true)

#### 2.同时插入多条数据记录

**执行命令如下:**

```SQL
	INSERT INTO t_dept1(Aname,Dname,loc,deptno,Tel)
	values	('Kangkang','Lisa','Zhejiang',0123,0235221),
		('Xuxin','Laowang','Chongqing',0124,0235222),
		('Yguang','Laoba','Chongqing',0125,0235223);
	SELECT * FROM T_DEPT1;  #查询表的数据记录
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/21.png?raw=true)

#### 3.将一个表的记录插入另一个表中

**执行命令如下:**

```SQL
	#创建一个新的表t_loader,其中的字段类型与t_dept1一样
	create table t_loader(
	Aname varchar(10),
	Cname varchar(10),
	loc varchar(40),
	deptno int,
	Tel int
	);		
	#给t_loader中插入记录
	INSERT INTO t_loader(Aname,Cname,loc,deptno,Tel)
	values	('Qiuqiu','Hanhan','Shanghai',0126,0235221),
		('Xubao','Xiaohong','Sichuan',0128,0235222);
	SELECT * FROM t_loader;  #查询表的数据记录
	#将t_loader中的部分记录插入t_dept1中
	INSERT INTO t_dept1(Aname,loc,Tel)
		SELECT Cname,loc,Tel
		FROM t_loader;
	SELECT * FROM t_dept1;    ##查询表的数据记录
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/22.png?raw=true)
