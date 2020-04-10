# mysql-final-test

2019-2020 mysql final test

姓名：刘浩

学号：17061519

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果
```SQL
select current_timestamp,
current_timestamp();
+---------------------+---------------------+
| current_timestamp   | current_timestamp() |
+---------------------+---------------------+
| 2020-04-10 08:08:34 | 2020-04-10 08:08:34 |
+---------------------+---------------------+
1 row in set (0.00 sec)
```

2 组合打印自己的姓名和学号

(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果
```SQL
select concat("刘浩+",17061519);
+----------------------------+
| concat("刘浩+",17061519)   |
+----------------------------+
| 刘浩+17061519              |
+----------------------------+
```

3 建立如下表1和表2，写出建表语句和插入语句。
```SQL
create table t_dept1(
deptno int primary key,
dname varchar(20),
loc varchar(20)
);
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| deptno | int(11)     | NO   | PRI | NULL    |       |
| dname  | varchar(20) | YES  |     | NULL    |       |
| loc    | varchar(20) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
insert into t_dept1(deptno,dname,loc)
values(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON");
select*from t_dept1;
+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
```
表1：其中deptno为主键,
```
deptno, dname,    loc
(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON")
```
```SQL
create table t_dept2(
empno int primary key,
ename varchar(20),
job varchar(20),
mgr int,
hiredate varchar(40),
sal int,
comm int,
deptno int
);
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| empno    | int(11)     | NO   | PRI | NULL    |       |
| ename    | varchar(20) | YES  |     | NULL    |       |
| job      | varchar(20) | YES  |     | NULL    |       |
| mgr      | int(11)     | YES  |     | NULL    |       |
| hiredate | varchar(40) | YES  |     | NULL    |       |
| sal      | int(11)     | YES  |     | NULL    |       |
| comm     | int(11)     | YES  |     | NULL    |       |
| deptno   | int(11)     | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
insert into t_dept2(empno, ename,job,MGR,Hiredate,sal,comm, deptno)
values(7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
;
+----------+--------+-----------+------+------------+------+------+--------+
| empno    | ename  | job       | mgr  | hiredate   | sal  | comm | deptno |
+----------+--------+-----------+------+------------+------+------+--------+
|     7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 | 
+----------+--------+-----------+------+------------+------+------+--------+
表2：其中empno字段为主键
```
        empno, ename,    job,    MGR,   Hiredate,    sal,   comm, deptno
        (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
	(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
	(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
	(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
	(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
	(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
	(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
	(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
	(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
	(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
	(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
	
```

3.1 表2 中再插入一条记录：

`(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)`
 
例如：`(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)`
```SQL
insert into t_dept2(empno, ename,job,MGR,Hiredate,sal,comm, deptno)
 values(17061519, "LiuHao", "student", 7782, "1998-09-10", NULL, NULL, 10);
 +----------+--------+-----------+------+------------+------+------+--------+
| empno    | ename  | job       | mgr  | hiredate   | sal  | comm | deptno |
+----------+--------+-----------+------+------------+------+------+--------+
|     7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
| 17061519 | LiuHao | student   | 7782 | 1998-09-10 | NULL | NULL |     10 |
+----------+--------+-----------+------+------------+------+------+--------+
 ```
3.2 表中入职时间（Hiredate字段）最短的人。
```SQL
mysql> select*from t_dept2 where hiredate=(select max(hiredate)from t_dept2);
+----------+--------+---------+------+------------+------+------+--------+
| empno    | ename  | job     | mgr  | hiredate   | sal  | comm | deptno |
+----------+--------+---------+------+------------+------+------+--------+
| 17061519 | LiuHao | student | 7782 | 1998-09-10 | NULL | NULL |     10 |
+----------+--------+---------+------+------------+------+------+--------+
```
3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？
```SQL
select count(distinct(job)) from t_dept2;
+----------------------+
| count(distinct(job)) |
+----------------------+
|                    6 |
+----------------------+
```

3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；
```SQL
 update t_employeeset 
 set comm=100
 where ename='miller';
 select * from t_employee;
+----------+--------+-----------+------+------------+------+------+--------+
| empno    | ename  | job       | mgr  | hiredate   | sal  | comm | deptno |
+----------+--------+-----------+------+------------+------+------+--------+
|     7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 |  100 |     10 |
| 17061519 | liuhao | student   | 7782 | 1998-09-10 | NULL | NULL |     10 |
+----------+--------+-----------+------+------------+------+------+--------+
```
```SQL
select ename
from t_employee
where comm<100;
+--------+
| ename  |
+--------+
| TURNER |
+--------+
```
3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 
```SQL
create view tu1 as
select ename,sal+comm from t_dept2;
select*from tu1；
+--------+----------+
| ename  | sal+comm |
+--------+----------+
| SMITH  |     NULL |
| ALLEN  |     1900 |
| WARD   |     1750 |
| JONES  |     NULL |
| MARTIN |     2650 |
| BLAKE  |     NULL |
| SCOTT  |     NULL |
| KING   |     NULL |
| TURNER |     1500 |
| ADAMS  |     NULL |
| JAMES  |     NULL |
| FORD   |     NULL |
| MILLER |     1400 |
| liuhao |     NULL |
+--------+----------+
```
3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？
```SQL
select*from(t_dept2 t1 inner join t_dept2 t2 on t1. mgr=t2.empno)
inner join t_dept2 t3 on t2. mgr=t3.empno;
```
连接、选择
3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。
```SQL
create view tu2 as
select empno,ename,job from t_dept2;
select*from tu2;
+----------+--------+-----------+
| empno    | ename  | job       |
+----------+--------+-----------+
|     7369 | SMITH  | CLERK     |
|     7499 | ALLEN  | SALESMAN  |
|     7521 | WARD   | SALESMAN  |
|     7566 | JONES  | MANAGER   |
|     7654 | MARTIN | SALESMAN  |
|     7698 | BLAKE  | MANAGER   |
|     7788 | SCOTT  | ANALYST   |
|     7839 | KING   | PRESIDENT |
|     7844 | TURNER | SALESMAN  |
|     7878 | ADAMS  | CLERK     |
|     7900 | JAMES  | CLERK     |
|     7902 | FORD   | ANALYST   |
|     7934 | MILLER | CLERK     |
| 17061519 | LiuHao | student   |
+----------+--------+-----------+
```

3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？

3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引
```SQL
create index index_ename
on t_dept2(ename);
show create table t_dept2;
+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Table   | Create Table                                                                                                                                                                                                                                                                                                                                                                              |
+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| t_dept2 | CREATE TABLE `t_dept2` (
  `empno` int(11) NOT NULL,
  `ename` varchar(20) DEFAULT NULL,
  `job` varchar(20) DEFAULT NULL,
  `mgr` int(11) DEFAULT NULL,
  `hiredate` varchar(40) DEFAULT NULL,
  `sal` int(11) DEFAULT NULL,
  `comm` int(11) DEFAULT NULL,
  `deptno` int(11) DEFAULT NULL,
  PRIMARY KEY (`empno`),
  KEY `index_ename` (`ename`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 |
+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
```
为了提高从表中检索数据的速度
3.10 将表2的 sal 字段改名为 salary
```SQL
alter table t_dept2
change sal salalr int;
desc t_dept2;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| empno    | int(11)     | NO   | PRI | NULL    |       |
| ename    | varchar(20) | YES  | MUL | NULL    |       |
| job      | varchar(20) | YES  |     | NULL    |       |
| mgr      | int(11)     | YES  |     | NULL    |       |
| hiredate | varchar(40) | YES  |     | NULL    |       |
| salalr   | int(11)     | YES  |     | NULL    |       |
| comm     | int(11)     | YES  |     | NULL    |       |
| deptno   | int(11)     | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
```
3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。
```SQL
CREATE FUNCTION get_deptno_from_empno()
RETURNS int(8)
RETURN
(SELECT deptno FROM biao2
WHERE empno=biao2.empno);
```
4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；

4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。

4.2 显示该账号权限
```SQL
use mysql;
select*from user;
 Host: localhost
                  User: root
           Select_priv: Y
           Insert_priv: Y
           Update_priv: Y
           Delete_priv: Y
           Create_priv: Y
             Drop_priv: Y
           Reload_priv: Y
         Shutdown_priv: Y
          Process_priv: Y
             File_priv: Y
            Grant_priv: Y
       References_priv: Y
            Index_priv: Y
            Alter_priv: Y
          Show_db_priv: Y
            Super_priv: Y
 Create_tmp_table_priv: Y
      Lock_tables_priv: Y
          Execute_priv: Y
       Repl_slave_priv: Y
      Repl_client_priv: Y
      Create_view_priv: Y
        Show_view_priv: Y
   Create_routine_priv: Y
    Alter_routine_priv: Y
      Create_user_priv: Y
            Event_priv: Y
          Trigger_priv: Y
Create_tablespace_priv: Y
              ssl_type:
            ssl_cipher:
           x509_issuer:
          x509_subject:
         max_questions: 0
           max_updates: 0
       max_connections: 0
  max_user_connections: 0
                plugin: mysql_native_password
 authentication_string: *7997D5F206D3AC56D4844272ECB338F2BE30F517
      password_expired: N
 password_last_changed: 2020-02-20 10:44:39
     password_lifetime: NULL
        account_locked: N
*************************** 2. row ***************************
                  Host: localhost
                  User: mysql.sys
           Select_priv: N
           Insert_priv: N
           Update_priv: N
           Delete_priv: N
           Create_priv: N
             Drop_priv: N
           Reload_priv: N
         Shutdown_priv: N
          Process_priv: N
             File_priv: N
            Grant_priv: N
       References_priv: N
            Index_priv: N
            Alter_priv: N
          Show_db_priv: N
            Super_priv: N
 Create_tmp_table_priv: N
      Lock_tables_priv: N
          Execute_priv: N
       Repl_slave_priv: N
      Repl_client_priv: N
      Create_view_priv: N
        Show_view_priv: N
   Create_routine_priv: N
    Alter_routine_priv: N
      Create_user_priv: N
            Event_priv: N
          Trigger_priv: N
Create_tablespace_priv: N
              ssl_type:
            ssl_cipher:
           x509_issuer:
          x509_subject:
         max_questions: 0
           max_updates: 0
       max_connections: 0
  max_user_connections: 0
                plugin: mysql_native_password
 authentication_string: *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE
      password_expired: N
 password_last_changed: 2020-02-20 10:44:26
     password_lifetime: NULL
        account_locked: Y
2 rows in set (0.00 sec)
```
4.3 `with grant option` 是什么意思。
传递权限

5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？

6 画出表 1 和表 2 所对应的 E-R 图

7 什么是外模式，什么是内模式。为什么要分成这几层？
外模式：外模式又称子模式，对应于用户级。它是某个或某几个e79fa5e98193e58685e5aeb931333239306661用户所看到的数据库的数据视图，是与某一应用有关的数据的逻辑表示。外模式是从模式导出的一个子集，包含模式中允许特定用户使用的那部分数据。用户可以通过外模式描述语言来描述、定义对应于用户的数据记录(外模式)，也可以利用数据操纵语言(Data Manipulation Lang uage，DML)对这些数据记录进行。外模式反映了数据库的用户观。 
内模式：内模式又称存储模式，对应于物理级，它是数据库中全体数据的内部表示或底层描述，是数据库最低一级的逻辑描述，它描述了数据在存储介质上的存储方式翱物理结构，对应着实际存储在外存储介质上的数据库。内模式由内模式描述语言来描述、定义，它是数据库的存储观。 
在一个数据库系统中，只有唯一的数据库， 因而作为定义 、描述数据库存储结构的内模式和定义、描述数据库逻辑结构的模式，也是惟一的，但建立在数据库系统之上的应用则是非常广泛、多样的，所以对应的外模式不是惟一的，也不可能是惟一的。 

8 什么是ACID？
ACID，指数据库事务正确执行的四个基本要素的缩写。包含：原子性（Atomicity）、一致性（Consistency）、隔离性（Isolation）、持久性（Durability）。一个支持事务（Transaction）的数据库，必须要具有这四种特性，否则在事务过程（Transaction processing）当中无法保证数据的正确性，交易过程极可能达不到交易方的要求。
原子性：整个事务中的所有操作，要么全部完成，要么全部不完成，不可能停滞在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。
一致性：一个事务可以封装状态改变（除非它是一个只读的）。事务必须始终保持系统处于一致的状态，不管在任何给定的时间并发事务有多少。
隔离性：隔离状态执行事务，使它们好像是系统在给定时间内执行的唯一操作。如果有两个事务，运行在相同的时间内，执行相同的功能，事务的隔离性将确保每一事务在系统中认为只有该事务在使用系统。这种属性有时称为串行化，为了防止事务操作间的混淆，必须串行化或序列化请求，使得在同一时间仅有一个请求用于同一数据。
持久性：在事务完成以后，该事务对数据库所作的更改便持久的保存在数据库之中，并不会被回滚。
8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？
+ 1.选择数据库,查看当前事务隔离界别
```SQL
select @@tx_isolation;
```
+ 2.开启事务,回滚事务
+ 3.事务级别中脏读,幻读 
+ 4.MySQL事务autocommit设置,每次sql必须用commit提交生效.
+ MySQL默认操作模式就是autocommit自动提交模式。这就表示除非显式地开始一个事务，否则每个查询都被当做一个单独的事务自动执行。我们可以通过设置autocommit的值改变是否是自动提交autocommit模式。
+ 通过以下命令可以查看当前autocommit模式
```SQL
show variables like 'autocommit';
```
+ 关闭自动提交,每次sql必须通过commit命令提交.
```SQL
set autocommit = 0;
```


8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？

9 有哪些场景不适合用关系型数据库？为什么？
1、图片、文件、二进制数据
对数据库的读/写的速度永远都赶不上文件系统处理的速度，数据库备份变的巨大，越来越耗时间，对文件的访问需要穿越你的应用层和数据库层
2、短生命期数据
使用情况统计数据，测量数据，GPS定位数据，session数据，任何只是短时间内对你有用，或经常变化的数据。如果你发现自己正在使用定时任务从某个表里删除有效期只有一小时，一天或数周的数据，那说明你没有找对正确的做事情的方法。使用redis， statsd/graphite， Riak，它们都是干这种事情更合适的工具。这建议也适用于对于收集那些短生命期的数据。
3、日志文件
也许你的日志记录做的很保守，每次web请求只产生一条日志。对于整个网站的每个事件来说，这仍然会产生大量的数据库插入操作，争夺你用户需要的数据库资源。如果你的日志级别设置为verbose或debug，那等着看你的数据库着火吧。
