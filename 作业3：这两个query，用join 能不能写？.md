## 作业3：这两个query，用join能不能写？
#### 1.两个query

```SQL
select * from t_employee where sal > (
select sal from t_employee where ename='SMITH');

select * from t_employee where (sal, job) = (
select sal,job from t_employee where ename = 'SMITH');
```

##### 第一个query可以这样
**执行命令如下：**

```SQL
select t1.deptno,t1.empno,t1.ename,t1.job,t1.MGR,t1.Hiredate,t1.sal,t1.comm    #挑选显示的内容
from t_employee t1 inner join t_employee t2 
on t1.sal>t2.sal and (t2.ename='SMITH');                       #inner join 的条件

select * from t_employee;               #显示表t_employee2的所有记录

select * from t_employee where sal > (
select sal from t_employee where ename='SMITH');                   #第一个query
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/31.png?raw=true)

##### 第二个query可以这样
**执行命令如下：**

```SQL
select * from t_employee where (sal, job) = (
select sal,job from t_employee where ename = 'smith');                 #第二个query

select t1.deptno,t1.empno,t1.ename,t1.job,t1.MGR,t1.Hiredate,t1.sal,t1.comm          #挑选显示的内容
from t_employee t1 inner join t_employee t2 
on (t1.sal = t2.sal and (t2.ename='SMITH')) AND (t1.job = t2.job and (t2.ename='SMITH'));        #inner join 的条件

select * from t_employee;               #显示表t_employee2的所有记录
```
##### 执行上面SQL语句结果显示如图所示：
![](https://github.com/BiubiuOoo/Homework-of-MySQL/blob/master/images/32.png?raw=true)


