# MySQL
* SQL (Structured Query Language)是一种用于管理和操作关系型数据库的标准语言。通过SQL语言，可以对数据库中的数据进行增、删、改、查等操作。

* DB (Database)是指数据库，是一个保存着有组织的数据的集合。数据库可以被存储在计算机或其他电子设备上，并通过DBMS进行管理和访问。

* DBMS (Database Management System)是指数据库管理系统，是一种软件系统，用于创建、管理、维护和操作数据库。DBMS提供了一些基本功能，如数据存储、数据访问、数据安全等，使用户可以方便地对数据库进行管理和操作。

* 因此，SQL是一种用于操作关系型数据库的语言，而DB是指实际的数据库存储，DBMS是用于管理和访问数据库的软件系统。它们之间的关系是：DBMS管理和操作DB中存储的数据，SQL是用于在DBMS中操作数据的语言。

* 安装 MySQL 数据库，就是在主机安装一个数据库管理系统（DBMS)，这个管理程序可以管理多个数据库。（database manage system）

* 常见的DB（Database）包括：

    1. MySQL：一种流行的关系型数据库管理系统（RDBMS），免费开源，具有高性能、可靠性和易于使用等特点，适用于大多数Web应用程序。

    2. Oracle：一种功能强大的商业关系型数据库管理系统，具有高可靠性、高性能、高安全性和可扩展性等特点，适用于企业级应用程序。

    3. SQL Server：一种由Microsoft开发的关系型数据库管理系统，适用于大型企业和小型企业的数据存储和管理。

    4. PostgreSQL：一种开源关系型数据库管理系统，免费使用，具有高可靠性、高可扩展性和可定制性等特点，适用于大多数应用程序。

    5. MongoDB：一种流行的NoSQL数据库，使用JSON格式存储文档，具有高可扩展性、高性能和易于部署等特点，适用于Web应用程序和大数据分析等场景。

    6. Redis：一种基于内存的高性能键值数据库，支持多种数据结构，如字符串、列表、哈希和集合等，适用于缓存和数据存储等场景。

    7. Cassandra：一种分布式NoSQL数据库，适用于大规模数据存储和处理，具有高可扩展性和高可用性等特点。

    8. SQLite：一种轻量级的关系型数据库，适用于小型应用程序和嵌入式设备等场景。

## <font class="text-color-13" color="#ffeb3b">表</font>
* 在数据库中，表是一种数据结构，用于组织和存储相关数据的集合。它通常由一组命名的列和每个列中的行数据组成。每个表都有一个唯一的名称，并且可以在数据库中包含多个表。表是关系数据库的核心组成部分，可以通过 SQL 语句进行查询、插入、更新和删除数据。通过在不同的表之间建立关系，可以在数据库中存储和检索大量数据，并提供高效的数据管理和查询功能。
* 一个数据库中可以创建多个表，以保存数据
* 行：数据、记录 （data）
* 列：字段（column）
* 每一个字段应该包括哪些属性：字段名、数据类型、相关的约束。

## <font class="text-color-13" color="#ffeb3b">命令行连接到 MySQL 服务（数据库）</font>
* mysql -h 主机 -P 端口 -u 用户名 -p密码
    如果没有写 -h 主机，默认就是本机
    如果没有写 -P 端口，默认 3306
* 实际工作中，3306会修改

## <font class="text-color-13" color="#ffeb3b">SQL语句分类</font>
* DDL：数据定义语句  create drop alter，对表的结构增删改
* DML：数据操作语句 insert、update、delete，对表中的数据进行增删改
* DQL：数据查询语句，凡是 select 语句都是 DQL
* TCL：事务控制语言 commit 提交事务，rollback 回滚事务
* DCL：数据控制语句 grant授权、revoke 撤销权限
* 注：
    1. 任何一条 sql 语句以“；”结尾
    2. sql 语句不区分大小写
    3. 标准 sql 语句要求字符串用单引号括起来

## <font class="text-color-121" color="#ffeb3b">常用命令</font>
* 查看当前数据库
```sql
select database();
```
* 查看mysql版本号
```sql
select version();
```
* 终止sql语句
```sql
\c 或 ctrl + c
```
* 查看现有数据库
```sql
show databases;
```
* 使用指定数据库
```sql
use <dbname>;
```

* 数据库重命名
```sql
RENAME DATABASE old_database_name TO new_database_name;
```

## <font class="text-color-13" color="#ffeb3b">操作数据库</font>
* 查看当前使用的数据库有哪些表
```sql
show tables;
```

* 查看指定数据库有哪些表
```sql
show tables from <dbname>;
```

* 初始化数据
```sql
source <文件路径>
```
* 删除
```sql
# 删除指定数据库
drop database <dbname>;
# 删除指定数据库（加判断）
drop database if exists <dbname>;
```
* 创建
* 在创建数据库、表的时候，为了规避关键字，可以使用 \` ` 反引号将名字括起来
```sql
# 演示创建数据库的操作
# 创建一个名为 wjh_db01 的数据库（默认字符集和校对规则）
create database wjh_db01;

# 创建一个名为 wjh_db02 的使用uff8字符集的数据库
create database wjh_db02 character set utf8;

# 创建一个名为 wjh_db03 的使用uff8字符集,并且带校对规则的数据库
create database wjh_db03 character set utf8 collate utf8_bin;

# utf8_bin：区分大小写
# utf8_general_ci：不区分大小写
```

* 显示数据库创建语句
```sql
show create database <dbname>;
```

## <font class="text-color-121" color="#ffeb3b">操作表</font>
* 查看表结构
```sql
desc <tablename>;
```
* 查看表的创建语句
```sql
show create table <tablename>;
```
### <font class="text-color-15" color="#ff9800">对表结构的增删改</font>


## <font class="text-color-13" color="#ffeb3b">单表查询</font>
* 语法格式
```sql
select <col1>,<col2>,<col3> from <tablename>
```
* 字段可以参与数学运算
```sql
select <col1>, <col2> * 12 from <tablename>;
```
* 查询字段重命名（as 可以省略）
```sql
select <col1>, <col2> * 12 as <col>, <col3> from <tablename>;
```
* 查看所有字段（效率较低）
```sql
select * from <tablename>;
```
### <font class="text-color-15" color="#ff9800">条件查询</font>
* 语法格式（执行顺序：from, where, select）
```sql
select <col1>,<col2> from <tablename> where <条件1> and <条件2>
```
例子：
```sql
select ename, sal from emp where sal >= 3000;
```
* 条件运算符

| 运算符      | 说明       |
| ----------- | ---------- |
| =           | 等于       |
| <>或!=      | 不等于     |
| <           | 小于       |
| >           | 大于       |
| >=          | 小于等于   |
| between and | 两个值之间，等同于 >= and <= |
| is null     | 为 null    |
| is not null | 不为 null  |
| and         | 且       |
| or          | 或       |
| in          | 属于，相当于多个 or       |
| not in      |   不属于，相当于多个 and     |
|    like         |     模糊查询，支持%或_匹配       |

* 在数据库中的 null 代表什么也没有，它不是一个值，所以不能使用等号衡量。
* and 比 or 优先级高，可以使用括号区分优先级。
* in 的例子（相当于多个or）
```sql
select 
	ename, sal, job
from
	emp
where
	job in ('manager','salesman');
```
* 模糊查询：
    1. %匹配任意多个字符
    2. \_匹配任意一个字符
    3. 若查询内容中含这两个特殊字符，则需要使用转义字符 \ 。
```sql
select 
	ename, sal, job
from
	emp
where
	ename like '_o%';
```
---
### <font class="text-color-15" color="#ff9800">排序</font>
* 使用 order by (默认升序)
```sql
select 
	ename, sal, job
from
	emp
order by 
	sal;
```
* 指定降序（desc）
```sql
select 
	ename, sal, job
from
	emp
order by 
	sal desc;
```
* 指定升序（asc）
```sql
select 
	ename, sal, job
from
	emp
order by 
	sal asc;
```
* 多字段排序（order by 后面越靠前的排序优先级越高）
```sql
select 
	ename, sal
from
	emp
order by 
	sal asc, ename desc;
```
* 根据字段位置排序
    例：按照查询结果的第二列进行排序
```sql
select 
	ename, sal
from
	emp
order by 
	2;
```

---
### <font class="text-color-15" color="#ff9800">单行处理函数</font>
| 函数名称 | 作用 |
| -------- | -------- |
| lower     |   转换小写   |
| upper   | 转换大写   |
| substr   | 取子串 ，substr(被截取的字符串, 起始下标, 截取的长度)   |
| length   | 取长度  |
| trim  | 去除前后空白   |
| str_to_date  | 将字符串转换成日期   |
| date_format  | 日期格式化  |
| format  | 设置千分位  |
| round   | 四舍五入  |
| rand()  | 生成随机数   |
|    ifnull   |    可以将 null 转换为一个具体值      |

例：
```sql
 select lower(ename) from emp;
```
#### <font class="text-color-7" color="#03a9f4">substr</font> 
* 函数起始下标从1开始
```sql
-- 保留第1到第3字符
select 
	substr(ename,1,3)
from
	emp;
```
```sql
-- ename首字母为A的行
select 
	ename
from
	emp
where
	substr(ename,1,1) = 'A';
```
#### <font class="text-color-61" color="#03a9f4">length</font>
```sql
--- 每个ename长度
select 
	length(ename)
from
	emp;
```
* select 后面可以跟字面值（根据表的结构发生变化）
```sql
 select 'haha' as result from dept;
```
```
+--------+
| result |
+--------+
| haha   |
| haha   |
| haha   |
| haha   |
+--------+
```
#### <font class="text-color-61" color="#03a9f4">round</font>
* 第二个参数指定保留几位小数
```sql
select round(1234.567,1) as result from dept;
```
```
+--------+
| result |
+--------+
| 1234.6 |
| 1234.6 |
| 1234.6 |
| 1234.6 |
+--------+
```
```sql
select round(1234.567,-2) as result from dept;
```
```
+--------+
| result |
+--------+
|   1200 |
|   1200 |
|   1200 |
|   1200 |
+--------+
```
#### <font class="text-color-61" color="#03a9f4">rand()</font> 
* 0-1之间的随机数
```sql
 select round(rand() * 100,0) as result from dept;
```
```
+--------+
| result |
+--------+
|     22 |
|     60 |
|     34 |
|     90 |
+--------+
```
#### <font class="text-color-61" color="#03a9f4">ifnull</font>
* 语法：
```ifnull(数据,被当作哪个值)```
```sql
 select ifnull(comm,0) from emp;
```
```
+----------------+
| ifnull(comm,0) |
+----------------+
|           0.00 |
|         300.00 |
|         500.00 |
|           0.00 |
|        1400.00 |
|           0.00 |
|           0.00 |
|           0.00 |
|           0.00 |
|           0.00 |
|           0.00 |
|           0.00 |
|           0.00 |
|           0.00 |
+----------------+
```
#### <font class="text-color-61" color="#03a9f4">format</font>
```sql
-- 显示薪资（加上千分位）
select ename, format(sal,'$999,999') as sal from emp;
```
#### <font class="text-color-61" color="#03a9f4">str_to_date</font>
* 将字符串 varchar 类型转换成 date 类型。
* 语法格式：
```str_to_date('字符串日期'， '日期格式')```
* mysql 的日期格式
```
%Y 年
%m 月
%d 日
%h 时
%i 分
%s 秒
```
* 示例
```sql
-- 将字符串数据插入 date 类型字段
insert into t_user
    (id, name, birth)
values 
    (1, 'Sam', str_to_date('01-10-1990','%d-%m-%Y'));
```
* 如果提供的短日期字符串是这个格式（默认格式）：```%Y-%m-%d```，str_to_date函数就不需要了。如：
```sql
insert into t_user
    (id, name, birth)
values 
    (1, 'Sam', '1990-10-01');
```
* mysql 长日期默认格式：```%Y-%m-%d %h:%i:%s```，如
```sql
insert into t_user
    (id, name, birth, create_time)
values 
    (1, 'Sam', '1990-10-01','2020-03-18 15:49:50');
```
```
+------+------+------------+---------------------+
| id   | name | birth      | create_time         |
+------+------+------------+---------------------+
|    1 | Sam  | 1990-10-01 | 2020-03-18 15:49:50 |
+------+------+------------+---------------------+
```
* now() 函数可以获取当前时间（datetime类型）
```sql
insert into t_user
    (id, name, birth, create_time)
values 
    (2, 'Alex', '2001-12-01',now()); 
```





#### <font class="text-color-61" color="#03a9f4">date_format</font>
* 将 date 类型转换成具有一定格式的 varchar 类型字符串，通常使用在查询日期方面
* 语法格式：```date_format(日期类型数据， '日期格式')```
```sql
select id,name, date_format(birth, '%m/%d/%Y') as birth from t_user;
```
```
+------+------+------------+
| id   | name | birth      |
+------+------+------------+
|    1 | Sam  | 10/01/1990 |
+------+------+------------+
```


---
### <font class="text-color-15" color="#ff9800">多行处理函数</font>

| 函数 | 作用 |
| -------- | -------- |
| count  | 计数  |
|  sum  | 求和  |
| avg    | 平均值  |
| max   | 最大值  |
| min  | 最小值  |
* 分组函数在使用的时候必须先进行分组，然后才能用。（如果没有对数据进行分组，整张表默认为一组）
* 注意：
	1. 分组函数自动忽略 null，不需要提前处理。
	2. 分组函数不能直接使用在 where 子句中。
```sql
select sum(sal) from emp;
```
```
+----------+
| sum(sal) |
+----------+
| 29025.00 |
+----------+
```
* count(具体字段)：表示统计该字段下所有不为 null 的元素的总数
```sql
select count(ename) from emp;
```
```
+--------------+
| count(ename) |
+--------------+
|           14 |
+--------------+
```
* count(\*)：统计表当中的总行数。（每行记录不可能都为 null，一行数据有一列不为 null，则这行数据就是有效的）


---
### <font class="text-color-15" color="#ff9800">分组查询</font>
#### <font class="text-color-61" color="#03a9f4">group by</font>
* 在一条 select 语句当中，如果有 group by 语句，则 select 后面只能跟：参加分组的字段，以及分组函数。其他一律不行。
```sql
--  按工作岗位分组，对薪资求和
select
	sum(sal),job 
from 
	emp 
group by 
	job;
```
```
+----------+-----------+
| sum(sal) | job       |
+----------+-----------+
|  6000.00 | ANALYST   |
|  4150.00 | CLERK     |
|  8275.00 | MANAGER   |
|  5000.00 | PRESIDENT |
|  5600.00 | SALESMAN  |
+----------+-----------+
```

* 可以按照多个字段分组，逗号后面越靠前优先级越高（靠后分得更细）
```sql
-- 按部门分组，再按岗位分组的最高薪资
select
	max(sal),job,deptno
from 
	emp 
group by 
	deptno,job;
```
```
+----------+-----------+--------+
| max(sal) | job       | deptno |
+----------+-----------+--------+
|  1300.00 | CLERK     |     10 |
|  2450.00 | MANAGER   |     10 |
|  5000.00 | PRESIDENT |     10 |
|  3000.00 | ANALYST   |     20 |
|  1100.00 | CLERK     |     20 |
|  2975.00 | MANAGER   |     20 |
|   950.00 | CLERK     |     30 |
|  2850.00 | MANAGER   |     30 |
|  1600.00 | SALESMAN  |     30 |
+----------+-----------+--------+
```
#### <font class="text-color-7" color="#03a9f4">having</font>
* having 可以对分完组之后的数据进行进一步过滤。
* having 不能单独使用，having 不能代替 where 使用，having必须和 group by 联合使用
* having子句会根据分组函数的结果过滤行，只有满足指定条件的行才会在查询结果中出现。因此，having子句用于筛选分组后的结果。
```sql
-- 高于2000平均薪资的部门
select
	avg(sal),deptno
from 
	emp
group by 
	deptno
having avg(sal) > 2000;
```
```
+-------------+--------+
| avg(sal)    | deptno |
+-------------+--------+
| 2916.666667 |     10 |
| 2175.000000 |     20 |
+-------------+--------+
```
---
### <font class="text-color-15" color="#ff9800">其他查询语句</font>
#### <font class="text-color-61" color="#03a9f4">concat</font>
* concat(<>,<>) 函数用于字符串或数字拼接。
```sql
select 
	concat(ename,' : ',sal)
from emp;
```
```
+-------------------------+
| concat(ename,' : ',sal) |
+-------------------------+
| SMITH : 800.00          |
| ALLEN : 1600.00         |
| WARD : 1250.00          |
| JONES : 2975.00         |
| MARTIN : 1250.00        |
| BLAKE : 2850.00         |
| CLARK : 2450.00         |
| SCOTT : 3000.00         |
| KING : 5000.00          |
| TURNER : 1500.00        |
| ADAMS : 1100.00         |
| JAMES : 950.00          |
| FORD : 3000.00          |
| MILLER : 1300.00        |
+-------------------------+
```
#### <font class="text-color-7" color="#03a9f4">case...when...then...when...then...else...end</font>

```sql
-- 当岗位为"manager"，工资上调10%，当岗位为"salesman"，工资上调50%，其他岗位下调10%。
select 
	ename,
	job, 
	(case job 
		when 'manager' then sal * 1.1
		when 'salesman' then sal * 1.5
		else sal * 0.9
	end) as sal
from emp;
```
```
+--------+-----------+---------+
| ename  | job       | sal     |
+--------+-----------+---------+
| SMITH  | CLERK     |  720.00 |
| ALLEN  | SALESMAN  | 2400.00 |
| WARD   | SALESMAN  | 1875.00 |
| JONES  | MANAGER   | 3272.50 |
| MARTIN | SALESMAN  | 1875.00 |
| BLAKE  | MANAGER   | 3135.00 |
| CLARK  | MANAGER   | 2695.00 |
| SCOTT  | ANALYST   | 2700.00 |
| KING   | PRESIDENT | 4500.00 |
| TURNER | SALESMAN  | 2250.00 |
| ADAMS  | CLERK     |  990.00 |
| JAMES  | CLERK     |  855.00 |
| FORD   | ANALYST   | 2700.00 |
| MILLER | CLERK     | 1170.00 |
+--------+-----------+---------+
```
#### <font class="text-color-61" color="#03a9f4">distinct</font>
* distinct 可以将查询结果去重
* distinct 只能出现在所有字段最前方，若出现在多个字段前面，则表示多字段联合去重。
```sql
select 
	distinct job,deptno
from emp;
```
```
+-----------+--------+
| job       | deptno |
+-----------+--------+
| CLERK     |     20 |
| SALESMAN  |     30 |
| MANAGER   |     20 |
| MANAGER   |     30 |
| MANAGER   |     10 |
| ANALYST   |     20 |
| PRESIDENT |     10 |
| CLERK     |     30 |
| CLERK     |     10 |
+-----------+--------+
```
* 可以在外面使用函数
```sql
-- 统计工作岗位的数量
select 
	count(distinct job) as jobNum
from emp;
```
```
+--------+
| jobNum |
+--------+
|      5 |
+--------+
```

---
### <font class="text-color-15" color="#ff9800">DQL执行顺序</font>
* 语法
```sql
select 
    ...
from
    ...
where
    ...
group by
	...
having
	...
order by
    ...
limit
	...
```
* 执行顺序
	1. from
	2. where
	3. group by
	4. having
	5. select
	6. order by
	7. limit

## <font class="text-color-13" color="#ffeb3b">连接查询</font>
* 连接查询是通过联结（join）两个或多个表来获取需要的数据的一种查询方式。连接查询通常用于处理多个表中的相关数据，将它们合并为一个结果集。使用连接查询可以解决单表无法完成的复杂查询需求，但也需要注意性能问题，尤其是当连接的表数据量较大时，需要优化查询语句和索引来提高查询效率。

* 根据表连接的方式分类：
	1. 内连接：等值连接，非等值连接，自连接
	2. 外连接：左外连接（左连接），右外连接（右连接）
	3. 全连接

* 当两张表进行连接查询，没有任何条件限制的时候，最终查询结果的条数，是两张表条数的乘积。（笛卡尔积）

```sql
-- 在两张表中查找员工对应部门的名字 (sql92语法)
select 
	emp.ename, dept.dname
from 
	emp, dept
where
	emp.deptno = dept.deptno;
```
```
+--------+------------+
| ename  | dname      |
+--------+------------+
| SMITH  | RESEARCH   |
| ALLEN  | SALES      |
| WARD   | SALES      |
| JONES  | RESEARCH   |
| MARTIN | SALES      |
| BLAKE  | SALES      |
| CLARK  | ACCOUNTING |
| SCOTT  | RESEARCH   |
| KING   | ACCOUNTING |
| TURNER | SALES      |
| ADAMS  | RESEARCH   |
| JAMES  | SALES      |
| FORD   | RESEARCH   |
| MILLER | ACCOUNTING |
+--------+------------+
```
---
### <font class="text-color-15" color="#ff9800">起别名</font>
* 在 from 子句中给表起别名
```sql
select 
	e.ename,d.dname
from 
	emp e,dept d
where
	e.deptno = d.deptno;
```
---
### <font class="text-color-141" color="#ff9800">内连接</font>
* 特点：完全能够匹配上这个条件的数据查询出来
* 所有表平等，没有主次关系
* join 前面的 inner 可以省略

#### <font class="text-color-7" color="#03a9f4">等值连接</font>

```sql
-- 在两张表中查找员工对应部门的名字
-- 条件：e.deptno = d.deptno
select 
	e.ename, d.dname
from 
	emp e inner join dept d
on
	e.deptno = d.deptno;
```
#### <font class="text-color-7" color="#03a9f4">非等值连接</font>
```sql
-- 在两张表中查找员工对薪资等级
select 
	e.ename, e.sal, s.grade
from 
	emp e join salgrade s
on
	e.sal >= s.losal and e.sal <= s.hisal;
```
```
+--------+---------+-------+
| ename  | sal     | grade |
+--------+---------+-------+
| SMITH  |  800.00 |     1 |
| ALLEN  | 1600.00 |     3 |
| WARD   | 1250.00 |     2 |
| JONES  | 2975.00 |     4 |
| MARTIN | 1250.00 |     2 |
| BLAKE  | 2850.00 |     4 |
| CLARK  | 2450.00 |     4 |
| SCOTT  | 3000.00 |     4 |
| KING   | 5000.00 |     5 |
| TURNER | 1500.00 |     3 |
| ADAMS  | 1100.00 |     1 |
| JAMES  |  950.00 |     1 |
| FORD   | 3000.00 |     4 |
| MILLER | 1300.00 |     2 |
+--------+---------+-------+
```
#### <font class="text-color-7" color="#03a9f4">自连接</font>
* 一张表看作两张表
```sql
-- 员工名字对应领导名字
select 
	e1.ename as ename, e2.ename as manager
from 
	emp e1 join emp e2
on
	e1.mgr = e2.empno;
```
```
+--------+---------+
| ename   | manager |
+--------+---------+
| SMITH  | FORD    |
| ALLEN  | BLAKE   |
| WARD   | BLAKE   |
| JONES  | KING    |
| MARTIN | BLAKE   |
| BLAKE  | KING    |
| CLARK  | KING    |
| SCOTT  | JONES   |
| TURNER | BLAKE   |
| ADAMS  | SCOTT   |
| JAMES  | BLAKE   |
| FORD   | JONES   |
| MILLER | CLARK   |
+--------+---------+
```

---
### <font class="text-color-141" color="#ff9800">外连接</font>
* join 前面的 outer 可以省略
* 会将主表的数据全部显示（外连接查询结果条数 >= 内连接查询结果条数）

#### <font class="text-color-7" color="#03a9f4">右连接</font>
* right 表示将 join 关键字右边的这张表看成主表，主要是为了将这张表的数据全部查询出来，捎带着关联查询左边的表。
```sql
-- 在两张表中查找员工对应部门的名字，且部门名称全显示
select 
	e.ename, d.dname
from 
	emp e  right join dept d
on
	e.deptno = d.deptno;
```
```
+--------+------------+
| ename  | dname      |
+--------+------------+
| SMITH  | RESEARCH   |
| ALLEN  | SALES      |
| WARD   | SALES      |
| JONES  | RESEARCH   |
| MARTIN | SALES      |
| BLAKE  | SALES      |
| CLARK  | ACCOUNTING |
| SCOTT  | RESEARCH   |
| KING   | ACCOUNTING |
| TURNER | SALES      |
| ADAMS  | RESEARCH   |
| JAMES  | SALES      |
| FORD   | RESEARCH   |
| MILLER | ACCOUNTING |
| NULL   | OPERATIONS |      <--- 右表数据会全部显示
+--------+------------+
```
#### <font class="text-color-7" color="#03a9f4">左连接</font>
```sql
-- 员工名字对应领导名字,且员工名字全显示
select 
	e1.ename as ename, e2.ename as manager
from 
	emp e1 left join emp e2
on
	e1.mgr = e2.empno;
```
```
+--------+---------+
| ename  | manager |
+--------+---------+
| SMITH  | FORD    |
| ALLEN  | BLAKE   |
| WARD   | BLAKE   |
| JONES  | KING    |
| MARTIN | BLAKE   |
| BLAKE  | KING    |
| CLARK  | KING    |
| SCOTT  | JONES   |
| KING   | NULL    |       <--- 左表数据会全部显示
| TURNER | BLAKE   |
| ADAMS  | SCOTT   |
| JAMES  | BLAKE   |
| FORD   | JONES   |
| MILLER | CLARK   |
+--------+---------+
```
---
### <font class="text-color-15" color="#ff9800">多表连接</font>
* 可以内外连接混合
* 语法
```sql
select 
	...
from
	a
join
	b
on 
	a和b的连接条件
join 
	c
on
	a和c的连接条件
join
	d
on
	a和d的连接条件
```
* 例子
```sql
-- 找出所有员工名字，部门名字，薪资，薪资等级，上级名称
select 
	e.ename, d.dname, e.sal, s.grade, e2.ename as manager 
from 
	emp e 
join 
	dept d
	on
	e.deptno = d.deptno
join
	salgrade s
	on 
	e.sal between s.losal and s.hisal
left join 
	emp e2
	on
	e.mgr = e2.empno;
```
```
+--------+------------+---------+-------+---------+
| ename  | dname      | sal     | grade | manager |
+--------+------------+---------+-------+---------+
| SMITH  | RESEARCH   |  800.00 |     1 | FORD    |
| ADAMS  | RESEARCH   | 1100.00 |     1 | SCOTT   |
| JAMES  | SALES      |  950.00 |     1 | BLAKE   |
| WARD   | SALES      | 1250.00 |     2 | BLAKE   |
| MARTIN | SALES      | 1250.00 |     2 | BLAKE   |
| MILLER | ACCOUNTING | 1300.00 |     2 | CLARK   |
| ALLEN  | SALES      | 1600.00 |     3 | BLAKE   |
| TURNER | SALES      | 1500.00 |     3 | BLAKE   |
| JONES  | RESEARCH   | 2975.00 |     4 | KING    |
| BLAKE  | SALES      | 2850.00 |     4 | KING    |
| CLARK  | ACCOUNTING | 2450.00 |     4 | KING    |
| SCOTT  | RESEARCH   | 3000.00 |     4 | JONES   |
| FORD   | RESEARCH   | 3000.00 |     4 | JONES   |
| KING   | ACCOUNTING | 5000.00 |     5 | NULL    |
+--------+------------+---------+-------+---------+
```

## <font class="text-color-13" color="#ffeb3b">子查询</font>
* select 语句中嵌套 select 语句，被嵌套的 select 语句称为子查询
* 出现的位置
```sql
select
	...(select)
from
	...(select)
where
	...(select)
```
### <font class="text-color-15" color="#ff9800">where子句中的子查询</font>
```sql
-- 查询比最低工资高的员工的名字和薪资
select 
	ename, sal
from 
	emp
where
	sal > (select min(sal) from emp);  -- 嵌套
```
```
+--------+---------+
| ename  | sal     |
+--------+---------+
| ALLEN  | 1600.00 |
| WARD   | 1250.00 |
| JONES  | 2975.00 |
| MARTIN | 1250.00 |
| BLAKE  | 2850.00 |
| CLARK  | 2450.00 |
| SCOTT  | 3000.00 |
| KING   | 5000.00 |
| TURNER | 1500.00 |
| ADAMS  | 1100.00 |
| JAMES  |  950.00 |
| FORD   | 3000.00 |
| MILLER | 1300.00 |
+--------+---------+
```
### <font class="text-color-15" color="#ff9800">from 子句中的子查询</font>
* from 后面的子查询，可以将子查询的查询结果当做一张临时表
```sql
-- 找出每个工作岗位平均薪资的薪资等级
select 
	t.job, t.avgsal, s.grade
from 
	salgrade s 
join
	(select 
		job,avg(sal) as avgsal
	from 
		emp
	group by
		job) t
on 
	t.avgsal between s.losal and s.hisal
order by
	t.avgsal desc;
```
```
+-----------+-------------+-------+
| job       | avgsal      | grade |
+-----------+-------------+-------+
| PRESIDENT | 5000.000000 |     5 |
| ANALYST   | 3000.000000 |     4 |
| MANAGER   | 2758.333333 |     4 |
| SALESMAN  | 1400.000000 |     2 |
| CLERK     | 1037.500000 |     1 |
+-----------+-------------+-------+
```

### <font class="text-color-15" color="#ff9800">select 子句中的子查询</font>
* 这个子查询一次只返回一条结果，多于1条就会报错
```sql
-- 查询员工名字和对应部门名字
select
	e.ename, 
	(select d.dname from dept d where e.deptno = d.deptno) dname
from 
	emp e;
```
```
+--------+------------+
| ename  | dname      |
+--------+------------+
| SMITH  | RESEARCH   |
| ALLEN  | SALES      |
| WARD   | SALES      |
| JONES  | RESEARCH   |
| MARTIN | SALES      |
| BLAKE  | SALES      |
| CLARK  | ACCOUNTING |
| SCOTT  | RESEARCH   |
| KING   | ACCOUNTING |
| TURNER | SALES      |
| ADAMS  | RESEARCH   |
| JAMES  | SALES      |
| FORD   | RESEARCH   |
| MILLER | ACCOUNTING |
+--------+------------+
```

## <font class="text-color-13" color="#ffeb3b">union 合并</font>
* union 可以合并查询结果集
```sql
-- 查询工作岗位为 manager 和 salesman 的员工名字
select ename,job from emp where job = 'manager'
union
select ename,job from emp where job = 'salesman';
```
```
+--------+----------+
| ename  | job      |
+--------+----------+
| JONES  | MANAGER  |
| BLAKE  | MANAGER  |
| CLARK  | MANAGER  |
| ALLEN  | SALESMAN |
| WARD   | SALESMAN |
| MARTIN | SALESMAN |
| TURNER | SALESMAN |
+--------+----------+
```
* union 的效率高一些。对于表连接来说，每连接一次新表，则匹配的次数为笛卡尔积。但是 union 可以减少匹配的次数。在减少匹配次数的情况下，还可以完成两个结果集的拼接。
* union 在进行结果集合并的时候，要求两个结果集的列数相同
* 合并列的数据类型如果不相同，mysql 可以，oracle 会报错。
* 当使用UNION操作符时，可以使用UNION ALL来保留重复的行，或者省略ALL以删除重复的行。这对于需要对结果集进行去重的查询非常有用。

## <font class="text-color-13" color="#ffeb3b">limit 取部分</font>
* limit 是将查询结果集的一部分取出，通常使用在分页查询中
* 完整用法：limit \<start>, \<length> ，起始下标从0开始
* 缺省用法：limit \<length> ，取前 length 个
* limit 在 order by 之后执行
```sql
--- 查询工资前5的员工
select
	ename,sal
from 
	emp
order by
	sal desc
limit 0,5;
```
```
+-------+---------+
| ename | sal     |
+-------+---------+
| KING  | 5000.00 |
| FORD  | 3000.00 |
| SCOTT | 3000.00 |
| JONES | 2975.00 |
| BLAKE | 2850.00 |
+-------+---------+
```

### <font class="text-color-15" color="#ff9800">分页</font>
* 第 pageNo 页 sql 语句：
```sql
limit (pageNo - 1) * pageSize , pageSize 
```

## <font class="text-color-13" color="#ffeb3b">表的创建</font>
* 创建表的语法格式
```sql
create table <表名> (
	<字段名1> <数据类型>, 
	<字段名2> <数据类型>, 
	<字段名3> <数据类型>
);
```
* 表名建议以 t_ 或者 tbl_ 开始，可读性更强
* 数据类型后面可以加括号规定数据的长度。
### <font class="text-color-15" color="#ff9800">数据类型</font>

* 常见的数据类型

| 数据类型 | 描述 |
| -------- | -------- |
|   varchar   |   可变长度的字符串，会根据实际的数据长度动态地分配空间。节省空间，速度慢（最长255）   |
|   char   |   定长字符串，分配固定长度的空间存储数据。使用不当浪费空间，速度快（最长255）   |
|   int   |   整数型，等同于 java 的 int （最长11）   |
|   bigint   |  长整型，等同于 java 的 long    |
|   float   |   单精度浮点型   |
|   double   |   双精度浮点型   |
|   date   |   短日期类型，只包括年月日信息   |
|   datetime   |   长日期类型，包括年月日时分秒信息   |
|   clob   |   字符大对象，最多可以存储 4G 的字符串，存储文章或说明等（character large object）  |
|   blob   |   二进制大对象，最多可以存储 4G 的二进制数据，存储视频、声音、视频等流媒体数据（binary large object）向 blob 类型的字段上插入数据的时候，需要使用 IO 流  |

### <font class="text-color-15" color="#ff9800">创建表</font>
* 可以使用 default 指定默认值
* 例子
```sql
create table t_student(
	no int(10),
	name varchar(32),
	age int(3),
	sex char(5) default 'male',
	email varchar(255)
	);
```


### <font class="text-color-141" color="#ff9800">删除表</font>
```sql
drop table <表名>；--表不存在会报错
```
```sql
drop table if exists <表名>;  --表不存在也不会报错
```
### <font class="text-color-141" color="#ff9800">快速复制表</font>
* 语法格式：
```sql
create table <新表名> as select * from <源表名>;
```
* 原理：将一个查询结果当做一张表新建
* 将查询结果创建为一张表
```sql
create table some as select ename,sal from emp;
```
* 将查询结果插入到一张表中
```sql
insert into some select * from dept;
```
### <font class="text-color-141" color="#ff9800">设置字符集</font>
* 以 utf-8 字符集为例
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
    .....
) CHARACTER SET utf8 COLLATE utf8_general_ci;
```

## <font class="text-color-13" color="#ffeb3b">数据插入</font>

### <font class="text-color-141" color="#ff9800">insert</font>
* 语法格式
```sql
insert into <表名> 
	(<字段名1>,<字段名2>,<字段名3>)
values
	(<值1>,<值2>,<值3>);
```
* 没有指定值的字段默认为 NULL
* insert 语句一旦执行成功，就会在表中多一条数据
* insert 语句中的“字段名”可以省略，省略等于全部写上了，所以需要对全部字段进行赋值
* 例子
```sql
-- 插入两条学生数据
insert into t_student 
values (279,'Bob',20,'male','Bob@gmail.com');
		
insert into t_student 
	(age,name,email,sex,no)
values
	(23,'Alex','Alex@qq.com','male',524);
```

### <font class="text-color-141" color="#ff9800">多条数据插入</font>
* 示例
```sql
insert into t_user
    (id, name, birth, create_time)
values 
    (3, 'Ashley', '1985-06-22', now()),
    (4, 'Christopher', '1979-07-29', now()),
    (5, 'Megan', '1995-11-02', now());
```

## <font class="text-color-13" color="#ffeb3b">数据修改</font>
### <font class="text-color-141" color="#ff9800">update</font>
* 语法格式：
```sql
update <表名> set <字段1> = <值1>, <字段2> = <值2> where <条件>
```
* 示例：
```sql
update t_user set name='Bob', birth='2003-05-11', create_time=now() where id=2;
```
```
+------+------+------------+---------------------+
| id   | name | birth      | create_time         |
+------+------+------------+---------------------+
|    1 | Sam  | 1990-10-01 | 2020-03-18 15:49:50 |
|    2 | Bob  | 2003-05-11 | 2023-03-11 17:39:41 |
+------+------+------------+---------------------+
```
* 注：不使用 where 会更新所有行，如 
```sql
upate t_user set name='abc'
```
## <font class="text-color-13" color="#ffeb3b">数据删除</font>
### <font class="text-color-141" color="#ff9800">delete</font>
* 语法格式 
```sql
delete from <表名> where <条件>;
```
* 示例
```sql
-- 删除一条数据
delete from t_user where id=2;
-- 删除全部数据
delete from t_user;
```
### <font class="text-color-141" color="#ff9800">删除表中所有数据</font>
* 与 ```drop table <表名>``` 不同，删除的是数据，表还在
* **方法一**
```sql
delete from <表名>;
```
* delete 原理：表中的数据被删除了，但是这个数据在硬盘上的真实存储空间不会被释放。
	缺点：删除效率较低
	优点：支持回滚，可以恢复数据
* **方法二**
```sql
truncate from <表名>;
```
* truncate 原理：表被一次截断，物理删除。
	缺点：不支持回滚，无法恢复数据
	优点：删除效率较高
	
## <font class="text-color-13" color="#ffeb3b">约束</font>
* 在创建表的时候，可以给表的字段上加一些约束，来保证这个表中数据的完整性、有效性，保证表中数据有效。
* 约束的分类：
	1. 非空约束：not null
	2. 唯一性约束：unique
	3. 主键约束：primary key 
	4. 外键约束：foreign key
	5. 检查约束：check 

### <font class="text-color-15" color="#ff9800">非空约束 not null</font>
* 非空约束 not null 约束的字段不能为 null
* 示例
```sql
create table t_vip(
    id int,
    name varchar(255) not null
);

insert into t_vip(id, name) values(1,'Bob');
insert into t_vip(id, name) values(2,'Alex');
insert into t_vip(name) values('David');   -- 可以
insert into t_vip(id) values(4);   -- 报错
```
### <font class="text-color-15" color="#ff9800">唯一性约束 unique</font>
* 唯一性约束 unique 约束的字段不能重复，但可以为 null（null 可以重复）
```sql
drop table if exists t_vip;
create table t_vip(
    id int,
    name varchar(255) unique,  -- 列级约束
    email varchar(255)
);

INSERT INTO t_vip (id, name, email) VALUES
(1, 'Alice', 'alice@example.com'),
(2, 'Bob', 'bob@example.com'),
(3, 'Charlie', 'charlie@example.com'),
(4, 'David', 'david@example.com'),
(5, 'David', 'david@example.com'); -- 报错
```
* 多字段联合唯一性约束
```sql
create table t_vip(
    id int,
    name varchar(255),
    email varchar(255),
    unique(name, email) -- 表级约束
);
```
* unique 和 not null 可以联合使用
```sql
create table t_vip(
    id int,
    name varchar(255) not null unique
);
```
* 在 MySQL 中，如果一个字段同时被 not null 和 unique 约束，该字段自动变为主键字段

### <font class="text-color-15" color="#ff9800">主键约束 primary key</font>
* 主键约束相关术语：
	1. 主键约束：一种约束
	2. 主键字段：该字段上添加了主键约束，这样的字段叫做：主键字段
	3. 主键值：主键字段上的每一个值都叫做：主键值
* 主键是每一行记录的唯一标识： not null + unique
* 一张表主键约束只能添加一个

* 示例
```sql
drop table if exists t_vip;
create table t_vip(
    id int primary key,   -- （单一主键）
    name varchar(255)
);

INSERT INTO t_vip (id, name) VALUES
(1, 'Alice'),
(2, 'Bob'),
(1, 'Charlie'); -- 报错

INSERT INTO t_vip (name) VALUES ('Frank');  -- 报错
```
* 使用表级约束使多字段做联合主键（复合主键）
```sql
drop table if exists t_vip;
create table t_vip(
    id int,
    name varchar(255),
	primary key(id,name)
);
```
* 自然主键：主键值是一个自然数，和业务没关系

* 业务主键：主键值和业务紧密关联（拿银行卡号做主键）

	自然主键使用较多，因为主键只需要不重复，不需要有意义。业务主键不好，因为主键一旦和业务紧密关联，那么当业务发生变动的时候，可能会影响主键值。

* <font class="text-color-141" color="#ff9800">auto_increment</font>：在 MySQL 当中，有一种机制，可以帮助我们自动维护一个主键值
```sql
drop table if exists t_vip;
create table t_vip(
    id int primary key auto_increment,  -- 自增（从1开始以1递增）
    name varchar(255)
);

INSERT INTO t_vip (name) VALUES
('Alice'),
('Bob'),
('Charlie'),
('David');
```
```
+----+---------+
| id | name    |
+----+---------+
|  1 | Alice   |
|  2 | Bob     |
|  3 | Charlie |
|  4 | David   |
+----+---------+
```
### <font class="text-color-15" color="#ff9800">外键约束 foreign key</font>
* 主键约束相关术语：
	1. 外键约束：一种约束
	2. 外键字段：该字段上添加了外键约束
	3. 外键值：外键字段当中的每一个值
* 外键约束（Foreign Key Constraint）是关系型数据库中一种约束条件，用于保证数据完整性和一致性。它定义了一个表的外键与另一个表的主键之间的关系，确保在修改或删除一个表中的数据时，相关联的表中的数据也能够相应地进行修改或删除。

* 例如，如果有两个表，一个是顾客信息表，另一个是订单表。订单表中可能有一个“顾客ID”列，它与顾客信息表中的“ID”列相关联。在这种情况下，可以将订单表的“顾客ID”列定义为外键，以确保在删除或修改顾客信息表中的数据时，订单表中的数据也能够相应地进行修改或删除。外键约束可以防止在数据库中产生不一致的数据。
* 外键字段中可以有 null
* 子表中的外键引用父表中的某个字段，被引用的这个字段不一定是主键，但至少具有 unique 约束
* 示例
```sql
drop table if exists t_student;
drop table if exists t_class;

create table t_class(
    classno int primary key,
    classname varchar(255)
);

create table t_student(
    no int primary key auto_increment,
    name varchar(255),
    cno int,
    foreign key(cno) references t_class(classno) -- 外键约束
);

insert into t_class (classno, classname) values
(1, 'Math'),
(2, 'Physics'),
(3, 'Chemistry');

insert into t_student (name, cno) values
('Alice', 1),
('Bob', 2),
('Charlie', 1),
('David', 3),
('Emily', 2),
('Frank', 3);

insert into t_student (name, cno) values ('Tom',5);    
-- ERROR: Cannot add or update a child row: a foreign key constraint fails
```

## <font class="text-color-13" color="#ffeb3b">存储引擎</font>
* 存储引擎是 mysql 中特有的一个术语，其他数据库没有（Oracle 中有，但不叫这个名字）
* 存储引擎是是一个表存储 / 组织数据的方式，不同的存储引擎，存储数据的方式不同
* 可以在建表的时候指定存储引擎
```sql
 CREATE TABLE `t_student` (
  `no` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `cno` int(11) DEFAULT NULL,
  PRIMARY KEY (`no`),
  KEY `cno` (`cno`),
  CONSTRAINT `t_student_ibfk_1` FOREIGN KEY (`cno`) REFERENCES `t_class` (`classno`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=latin1 |
```
* 建表的时候可以在最后“ ) ” 的右边使用
	```engine``` 来指定存储引擎
	```charset``` 来指定这张表的编码方式
```sql
create table t_some(
    num int primary key,
    name varchar(255)
)engine=innodb default charset=utf8;
```
* 查看 MySQL 支持的存储引擎
```sql
 show engines；
```
* 查看 MySQL 支持的字符集
 ```sql
 show charset；
```
* MySQL支持多种不同的存储引擎，每个存储引擎都有其独特的特点和用途。以下是MySQL的一些常见存储引擎：

1. InnoDB
InnoDB是MySQL的默认存储引擎，它支持事务和行级锁定，并且可以提供ACID事务的支持。InnoDB是一个高度可靠的存储引擎，它支持外键和约束，因此在数据完整性方面非常有用。InnoDB适用于高并发的应用程序，特别是在需要处理大量写操作的场景下，如电子商务、社交网络和在线游戏等。

2. MyISAM
MyISAM是MySQL中最常用的存储引擎之一，它不支持事务和行级锁定，但在执行大量SELECT查询时具有很高的性能，支持全文本索引和压缩表格。MyISAM对于只读或很少更新的应用程序非常适用，例如新闻网站或博客等。

3. MEMORY
MEMORY存储引擎将表数据存储在内存中，因此它的查询速度非常快。但是，由于数据存储在内存中，如果服务器崩溃或重新启动，表中的数据将会丢失。MEMORY存储引擎适用于临时表、缓存表和需要高速读写的临时数据等。

4. Archive
Archive存储引擎被设计用于存储大量归档数据，它支持高效地插入和压缩数据，但不支持索引、更新和删除操作。Archive存储引擎适用于归档数据的存储，例如日志文件、历史记录等。

5. NDB Cluster
NDB Cluster是MySQL的集群存储引擎，它提供高可用性、高扩展性和高可靠性的数据存储和管理。NDB Cluster具有分布式体系结构，可以将数据分布在多个节点上，并提供事务处理和并发控制功能。

6. CSV：
CSV存储引擎是一种将数据存储在CSV文件中的存储引擎。它对于需要频繁导入和导出CSV格式的数据非常有用，但是它不支持索引、外键约束以及事务。此外，由于数据存储在文件中，CSV存储引擎的性能较低，适用于小型数据集。

## <font class="text-color-13" color="#ffeb3b">事务</font>
* MySQL的事务是一系列的数据库操作，这些操作被视为一个单一的逻辑工作单元（一个完整的业务逻辑），并且要么全部执行成功，要么全部失败回滚，保证了数据的完整性和一致性。

* 只有 DML 语句 ```insert delete  update``` 支持事务。

* InnoDB 存储引擎提供了一组用来记录事务性活动的日志文件。在事物的执行过程中，每一条记录的操作都会被记录到“事务性活动的日志文件”中。在事务的执行过程中，可以提交事务、回滚事务。
* 提交事务：
	清空事务性活动的日志文件，将数据全部彻底持久化到数据库表中
	提交事务标志着事务的结束。并且是一种全部成功的结束

* 回滚事务：
	将之前的 DML 操作全部撤销，并且清空事务性活动的日志文件
	回滚事务标志着事务的结束。并且是一种全部失败的结束
	回滚只能回滚到上一次的提交点

* MySQL 默认情况下会自动提交事务
* ACID原则：
	1. 原子性（Atomicity）：事务必须是原子操作，即事务内的操作要么全部执行，要么全部不执行，不会出现执行部分操作而另外一部分未执行的情况。如果事务执行失败，所有修改将会回滚到事务开始前的状态，数据库不会被修改。

	2. 一致性（Consistency）：事务执行前和执行后，数据库都必须处于一致性状态，即事务执行后必须满足所有的约束、触发器、外键等规定的限制条件，数据库不会被破坏。

	3. 隔离性（Isolation）：多个事务同时进行时，事务之间是相互隔离的，一个事务不会影响另外一个事务的执行。每个事务必须感知到其他事务的存在，但是不受其他事务的影响，防止多个并发事务执行时出现问题。

	4. 持久性（Durability）：事务完成后，对于数据的修改必须能够持久化到数据库中，即使系统崩溃或发生其他故障，已提交的事务的结果也不会丢失。

### <font class="text-color-15" color="#ff9800">开启事务</font>
```sql
start transaction; -- 此命令会关闭事务自动提交
```
### <font class="text-color-15" color="#ff9800">回滚</font>
```sql
rollback;
```
### <font class="text-color-15" color="#ff9800">提交</font>
```sql
commit;
```
### <font class="text-color-15" color="#ff9800">隔离级别（级别递增）</font>
1. 读未提交：```read uncommitted ```
	最低级别的隔离，一个事务能读到另一个未提交的事务中的数据，可能导致脏读、不可重复读和幻读等问题。
	
3. 读已提交：```read committed ```
	一个事务开始后，只能看到已提交的事务所做的变更，其他事务所做的未提交的变更对该事务是不可见的，可以避免脏读，但可能会导致不可重复读和幻读问题。（Oracle 默认）
	
5. 可重复读：```repeatable read```
	在一个事务内，多次读取同一行数据时，得到的结果是一致的，即在该事务中，其他事务所做的更新不会影响该事务中已经读取的数据。可以避免脏读和不可重复读问题，但是可能会出现幻读问题。（永远读到的是事务开启时的数据，MySQL默认）
	
7. 序列化/串行化：```serializable```
	最高级别，通过对事务进行串行化，来避免所有并发问题。即使多个事务并发执行，它们执行的结果也与顺序执行时的结果一致。由于需要对事务进行串行化，可能会导致并发性能下降。（事务排队执行，前一个事务没有结束，后一个事务的 DQL 语句会一直等待）

### <font class="text-color-15" color="#ff9800">隔离级别设置</font>
#### <font class="text-color-7" color="#03a9f4">查看当前事务隔离级别</font>
```sql
select @@tx_isolation;
```
#### <font class="text-color-7" color="#03a9f4">设置全局事务隔离级别</font>
```sql
set global transaction isolation level <级别>;
```

## <font class="text-color-13" color="#ffeb3b">锁</font>
### <font class="text-color-15" color="#ff9800">悲观锁</font>
* MySQL 的悲观锁是指在事务中使用 ```SELECT ... FOR UPDATE``` 或 ```SELECT ... FOR SHARE``` 语句来加锁，以避免并发操作导致数据的不一致性。

* 当一个事务在执行 ```SELECT ... FOR UPDATE``` 或 ```SELECT ... FOR SHARE``` 语句时，会对查询结果中涉及到的行进行加锁，防止其他事务对这些行进行修改或删除。这种锁的加锁方式称为行级锁，即只对查询结果中的行进行加锁，而不是对整个表或整个数据页进行加锁。

* 使用悲观锁需要注意以下几点：

	1. 悲观锁会降低数据库的并发性能，因为加锁需要消耗额外的资源，并且可能会导致事务的阻塞。

	2. 悲观锁只在事务中有效，如果没有使用事务，则悲观锁不会生效。

	3. 在使用悲观锁时，需要注意加锁的范围，过于广泛的加锁会导致其他事务的阻塞，从而影响数据库的并发性能。

* 总之，悲观锁可以确保数据的一致性和完整性，但是需要在使用时权衡锁的范围和效率，避免对数据库性能造成不良影响。

* 在 MySQL 中，SELECT 语句可以使用 FOR UPDATE 或 FOR SHARE 语句来加锁，以控制并发访问。

#### <font class="text-color-7" color="#03a9f4">FOR UPDATE 和 FOR SHARE 的区别</font>
* https://www.cnblogs.com/qilong853/p/9427145.html
* FOR UPDATE 语句会对查询结果中涉及到的行进行排他锁（Exclusive Lock），即其他事务无法对这些行进行读取、修改或删除，直到当前事务提交或回滚。而 FOR SHARE 则会对查询结果中涉及到的行进行共享锁（Shared Lock），即其他事务可以对这些行进行读取操作，但无法对其进行修改或删除。

* FOR UPDATE 语句一般用于更新操作，可以避免多个事务同时修改同一行数据导致的冲突。而 FOR SHARE 语句一般用于读取操作，可以避免读取到未提交的数据，从而保证读取数据的一致性。

* FOR UPDATE 语句会阻塞其他事务对涉及到的行进行读取、修改或删除，直到当前事务提交或回滚。而 FOR SHARE 则不会阻塞其他事务对涉及到的行进行读取操作，只会阻塞其他事务对这些行进行修改或删除。

* 需要注意的是，FOR UPDATE 和 FOR SHARE 只在事务中有效，如果没有使用事务，则这些锁不会生效。并且，使用锁需要权衡锁的范围和效率，过于广泛的加锁会导致其他事务的阻塞，从而影响数据库的并发性能。

### <font class="text-color-15" color="#ff9800">乐观锁</font>
* MySQL 的乐观锁是一种并发控制机制，它基于假设在大多数情况下，事务之间不会产生冲突的假设，以避免对数据进行加锁，提高并发性能。

* 在乐观锁中，事务在读取数据时不会对数据进行加锁，而是在修改数据时检查数据版本号或时间戳等标识，以确保在事务提交时数据没有被其他事务修改过。

* 在 MySQL 中，可以使用版本号或时间戳等方式实现乐观锁。例如，可以在表中添加一个版本号列，每次修改数据时自动递增版本号，当一个事务要修改数据时，先读取数据的版本号，在修改时比较版本号是否一致，如果一致则进行修改并更新版本号，如果不一致则放弃修改。

* 使用乐观锁需要注意以下几点：

	1. 乐观锁只在事务中有效，如果没有使用事务，则乐观锁不会生效。

	2. 在使用乐观锁时，需要确保事务之间不会产生冲突，否则会导致数据不一致。

	3. 在实现乐观锁时，需要考虑并发更新的情况，以确保数据的正确性和完整性。

* 总之，乐观锁可以避免对数据进行加锁，提高并发性能，但需要在使用时权衡锁的范围和效率，避免对数据的正确性和完整性造成影响。

## <font class="text-color-13" color="#ffeb3b">索引</font>
* 索引是在数据库表的字段上添加的，是为了提高查询效率存在的一种机制。索引相当于字典的目录（已排序），可以缩小查找  / 扫描范围

* MySQL使用B+树索引结构来实现索引机制。B+树是一种平衡多路查找树，每个节点有多个子节点，每个节点最多可以存储多个键值对，键值对按照键值的大小进行排序。
	https://blog.csdn.net/qq_45814695/article/details/117171536

* MySQL中的索引可以用来加速数据查询、排序和分组等操作，但也会占用磁盘空间、降低写入性能，并且索引的使用需要遵循一定的规则，如避免过度索引、避免使用不必要的索引等。因此，在创建索引时需要根据具体的业务场景进行权衡和选择。

* 一张表的一个字段可以添加一个索引，多个字段联合也可以添加复合索引（主键自动添加索引，MySQL中 unique 的字段也会自动创建索引）
```
+----+---------+---------------------+
| id | name    | email               |
+----+---------+---------------------+
|  1 | Alice   | alice@example.com   |
|  2 | Bob     | bob@example.com     |
|  3 | Charlie | charlie@example.com |
+----+---------+---------------------+
```
```sql
select * from user where name = 'Bob';
```
* 如果 name 字段上有索引，查询语句会在根据该字段的索引扫描。如果没有给 name 字段创建索引，会进行全扫描，把该字段上所有值扫描一遍。

* 给字段添加索引的条件：
	1. 数据量庞大（需测试，每一个硬件环境不同）
	2. 该字段经常出现在 where 后面，以条件的形式存在，也就是说这个字段总是被扫描
	3. 该字段有很少的 DML（增删改）操作。（DML 之后，索引需要重新排序）
### <font class="text-color-15" color="#ff9800">索引分类</font>
1. 单一索引：一个字段上添加索引
2. 复合索引：两个或多个字段上添加索引
3. 主键索引：主键上添加索引
4. 唯一性索引：具有 unique 约束的字段上添加索引

### <font class="text-color-15" color="#ff9800">创建索引</font>
```sql
create index <索引名称> on <表名>(<字段名>);
```
### <font class="text-color-15" color="#ff9800">删除索引</font>
```sql
drop index <索引名称> on <表名>;
```
### <font class="text-color-15" color="#ff9800">查看 DQL 语句是否使用索引</font>
```sql
explain <DQL语句>
```
* 例：
```sql
explain select * from t_student where name='frank';
```

### <font class="text-color-15" color="#ff9800">索引失效</font>
* 模糊查询以 ```%``` 开头会使得索引失效，尽量优化
```sql
select * from emp where ename like  '%t_'
```
* 使用 ```or``` 查询可能会使索引失效，如果使用 or 则要求 or 两边的条件字段都要有索引，索引才会生效。可以考虑使用 ```union``` 。当使用 ```!=``` 操作符时，MySQL也无法使用索引进行优化查询，因为 != 操作符会导致MySQL扫描整个表，而不使用索引。
```sql
select * from emp where ename = 'Ford' or empno = 7839;   -- 索引失效
```
* 使用多字段复合索引时，没有使用左侧的列查找，索引会失效。
* 例：
```sql
create index emp_job_sal_index on emp(job,sal); -- 创建复合索引

select * from emp where sal = 800;   -- 索引失效
select * from emp where job = 'manager';   -- 索引不失效
```
* 在 ```where``` 中索引列参加了数学运算或使用了函数时，索引会失效
```sql
create index emp_sal_index on emp(sal);
create index emp_ename_index on emp(ename);

 explain select * from emp where 2*sal=1600;  -- 索引失效
 select * from emp where length(ename)=5;
```

## <font class="text-color-13" color="#ffeb3b">视图</font>
* MySQL视图（View）是一种虚拟的表，不是存储数据的物理表，而是从一个或多个物理表中的数据产生的逻辑表。视图的数据是从物理表的数据中导出的，并且根据需要的情况，可以包括一个或多个物理表的数据。

* 视图是一个虚拟表，因此它没有实际的数据存储。它仅仅是一个查询语句的别名。当使用视图查询数据时，MySQL会动态地执行视图所定义的查询语句，并将查询结果返回给用户。使用视图的好处是可以简化复杂的查询操作，同时也可以保护敏感数据，只允许有访问权限的用户进行查询。

* 视图可以用来隐藏敏感数据，从而保护数据库中的数据安全性。它可以用来简化常见的查询操作，提高查询效率，并且可以为数据提供更好的组织结构和逻辑。视图还可以用来将多个表中的数据进行整合，以便更容易地查询和分析。

* 除了简化查询操作和提高效率外，视图还可以在不破坏现有的数据库结构的情况下，对数据进行重新组织。例如，可以将多个表中的数据组合成一个视图，以便更容易地查询和分析这些数据。此外，通过在视图中定义一些计算列，还可以方便地对数据进行处理和分析。
### <font class="text-color-15" color="#ff9800">创建和删除视图</font>
```sql
-- 创建视图
create view <视图名称> as <DQL语句>
```
```sql
-- 删除视图
drop view <视图名称> 
```
* 例子
```sql
-- 两表联查创建视图
create view emp_dept_view as
select 
    e.ename, e.sal, d.dname
from
    emp e
join
    dept d
on
    e.deptno = d.deptno;
```
* 面向视图查询
```sql
select * from  emp_dept_view;
```
```
+--------+---------+------------+
| ename  | sal     | dname      |
+--------+---------+------------+
| SMITH  |  800.00 | RESEARCH   |
| ALLEN  | 1600.00 | SALES      |
| WARD   | 1250.00 | SALES      |
| JONES  | 2975.00 | RESEARCH   |
| MARTIN | 1250.00 | SALES      |
| BLAKE  | 2850.00 | SALES      |
| CLARK  | 2450.00 | ACCOUNTING |
| SCOTT  | 3000.00 | RESEARCH   |
| KING   | 5000.00 | ACCOUNTING |
| TURNER | 1500.00 | SALES      |
| ADAMS  | 1100.00 | RESEARCH   |
| JAMES  |  950.00 | SALES      |
| FORD   | 3000.00 | RESEARCH   |
| MILLER | 1300.00 | ACCOUNTING |
+--------+---------+------------+
```
* 面向视图修改数据，原表数据也会修改
```sql
update emp_dept_view 
set
    ename = 'Jerry',
    sal = 9999
where
    ename = 'Smith';
```
```
+-------+--------+-----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | Jerry  | CLERK     | 7902 | 1980-12-17 | 9999.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
```
* 通过一个视图来修改多个基本表的数据时会报错：``` Can not modify more than one base table through a join view 'mydb.emp_dept_view'```。因为视图本质上是从一个或多个基本表中检索数据的虚拟表，所以修改操作可能会影响多个表，这是不被允许的。这个错误提示是 MySQL 数据库的保护机制，旨在防止意外修改多个表的数据，从而导致数据不一致或其他问题。


* 开发中的作用：假设有一条非常复杂的 sql 语句，需要在不同的位置上反复使用（查询）。每一次使用的时候都需要将这条 sql 语句重新编写。可以把这条 sql 语句封装成一个视图对象。简化开发，利于后期维护，只需修改视图所映射的 sql 语句。
	
## <font class="text-color-13" color="#ffeb3b">DBA命令</font>
### <font class="text-color-15" color="#ff9800">新建用户</font>
```sql
create user <用户名> identified by '<密码>';
```
* 密码可以为空,如果为空则该用户可以不需要密码登陆服务器
* 例：
```sql
create user p361 identified by '123'
```
### <font class="text-color-15" color="#ff9800">授权</font>
```sql
grant all privileges on <dbname>.<tbname> to '<用户名>'@'<login ip>' identified by '<密码>' with grant option;
```
* 注：
	1. dbname = \* 表示所有数据库
	2. tbname = \* 表示所有表
	3. login ip = % 表示任何 ip
	4. password 为空，表示不需要密码即可登录
	5. with grant option  表示该用户还可以授权给其他用户（可以不加）
* 例：
```sql
grant all privileges on *.* to 'p361'@'%' identified by "123" with grant option;
```
#### <font class="text-color-7" color="#03a9f4">细粒度授权</font>
* privileges 包括：

| <font class="text-color-141" color="#ff9800">privileges</font> | <font class="text-color-141" color="#ff9800">作用</font> |
| -------- | -------- |
|   alter    |   修改数据库的表    |
|   create    |   创建新的数据库或表    |
|    delete   |    删除表数据   |
|   drop    |    删除数据库/表   |
|   index    |    创建/删除索引   |
|   insert    |   添加表数据    |
|   select    |     查询表数据  |
|   update    |   更新表数据    |
|    all   |    允许任何操作   |
|   usage    |   只允许登录    |
* 例：
```sql
grant select,insert,update,delete on *.* to p361 @localhost Identified by "123";
```

### <font class="text-color-15" color="#ff9800">回收权限</font>
```sql
revoke privileges on <dbname>.<tbname> from <用户名>;
```
* 例：
```sql
revoke all privileges on *.* from p361;
```

### <font class="text-color-15" color="#ff9800">导入导出</font>
#### <font class="text-color-7" color="#03a9f4">导出</font>
* 在 windows 的 dos 命令窗口中执行：
```
mysqldump <dbname> > <路径>\<文件名>.sql -u<用户名> -p<密码>
```
* 例：
```
mysqldump mydb2 > D:\mydb2.sql -uroot -p123
```

* 导出指定库下的指定表：
```
mysqldump mydb2 emp > D:\mydb2_emp.sql -uroot -p123
```
#### <font class="text-color-7" color="#03a9f4">导入</font>
```sql
source <sql 文件路径>
```
## <font class="text-color-13" color="#ffeb3b">数据库设计范式</font>
### <font class="text-color-15" color="#ff9800">第一范式（1NF）</font>
* 属性不可再分：第一范式要求一个关系表中的所有属性都是不可再分的，也就是说，每个属性必须是原子的。如果属性可以被进一步拆分，那么就需要将其拆分成新的属性。
```
+------+----------+-------------------------+
| id   | name     | contact                 |
+------+----------+-------------------------+
| 1001 | ZhangSan | zs@gmail.com,1359999999 |
| 1002 | LiSI     | ls@gmail.com,1368888888 |
| 1001 | WangWu   | ww@gmail.com,1377777777 |
+------+----------+-------------------------+

不符合第一范式的示例
* 最后一条记录和第一条重复（不唯一，没有主键）
* 联系方式字段可以再分，不是原子性的
```
* 关于第一范式，每一行必须唯一，也就是每个表必须有主键，这是我们数据库设计的最基本要求，主要通常采用数值型或定长字符串表示，关于列不可再分，应该根据具体的情况来决定。如联系方式，为了开发上的便利行可能就采用一个字段了。

### <font class="text-color-15" color="#ff9800">第二范式（2NF）</font>
* 第二范式要求一个关系表中的非主键属性必须完全依赖于主键。如果一个非主键属性只依赖于主键的一部分，则需要将该属性拆分到新的表中。
```
+--------------+--------------+-------------+-------------+
| studentId_PK | teacherId_PK | studentName | teacherName |
+--------------+--------------+-------------+-------------+
|            1 |         1001 | Alice       | Bob         |
|            2 |         1002 | Bob         | Charlie     |
|            3 |         1003 | Cathy       | David       |
|            4 |         1004 | David       | Alice       |
+--------------+--------------+-------------+-------------+
```
* 以上虽然确定了主键，但此表会出现大量的冗余，主要涉及到的冗余字段为“学生姓名”和“教师姓名”，出现冗余的原因在于，学生姓名部分依赖了主键的一个字段学生编号，而没有依赖教师编号，而教师姓名部门依赖了主键的一个字段教师编号，这就是第二范式部分依赖。
* 需要使用三张表来表示这种多对多的关系（多对多，三张表，关系表两个主键外键）
```
学生表
| studentId_PK | studentName |

教师表
| teacherId_PK | teacherName | 

学生教师关系表
| studentId_PK_fk | teacherId_PK_fk |
```
```sql
drop table if exists asso;
drop table if exists student;
drop table if exists teacher;

create table student (
	student_id int primary key,
	student_name varchar(255)
);

	
create table teacher (
	teacher_id int primary key,
	teacher_name varchar(255)
);

create table asso (
	student_id int,
	teacher_id int,
	foreign key(student_id) references student(student_id),
	foreign key(teacher_id) references teacher(teacher_id),
	primary key(student_id,teacher_id)
);
```
```sql
insert into student values
	(1001,'Jerry'),
	(1002,'David'),
	(1003,'Alice');
	
insert into teacher values
	(001,'Alex'),
	(002,'Bob'),
	(003,'Theo');

insert into asso values(1001,001);
insert into asso values(1001,001); -- 因联合主键约束重复报错
insert into asso values(1004,001); -- 因外键约束报错
```
### <font class="text-color-15" color="#ff9800">第三范式（3NF）</font>
* 非主键属性不依赖于其他非主键属性：第三范式要求一个关系表中的非主键属性不依赖于其他非主键属性。如果存在这样的属性，需要将其拆分到新的表中。
```
+---------------+--------------+----------+------------+
| student_id_PK | student_name | class_id | class_name |
+---------------+--------------+----------+------------+
|          1001 | Jerry        |        1 | Class_1    |
|          1002 | Tom          |        2 | Class_2    |
|          1003 | Lucy         |        1 | Class_1    |
|          1004 | Peter        |        3 | Class_3    |
+---------------+--------------+----------+------------+

从上表可以看出，班级名称字段存在冗余，因为班级名称字段没有直接依赖于主键，班级名称字段依赖于班级编号，班级编号依赖于学生编号，那么这就是传递依赖
```
* 解决的办法是将冗余字段单独拿出来建立表（一对多，两张表，多的表加外键）
```
学生信息表
| student_id_PK | student_name | class_id_fk |

班级信息表
| class_id_PK | class_name |
```
### <font class="text-color-15" color="#ff9800">巴斯-科德范式（BCNF）</font>
* 巴斯-科德范式要求一个关系表中消除主键依赖的非主键属性。如果存在这样的属性，需要将其拆分到新的表中。
* 第三范式（3NF）主要是通过消除非关键字对主键的传递依赖来消除数据冗余，确保每个属性只与主键直接相关，避免重复数据的存储，提高数据存储的效率。

* 而巴斯-科德范式（BCNF）是第三范式的进一步拓展，它更加注重消除关系模式中的所有属性之间的依赖关系，保证所有属性都依赖于候选键，而不是部分依赖于候选键。这就能够确保每个关系都是“自描述”的，且不包含重复的数据，从而更进一步地减少数据冗余和错误。

* 因此，可以说BCNF是第三范式的加强版，更为严格。但在实际应用中，通常使用第三范式足以满足需求，而BCNF则可能需要更多的规划和设计。

### <font class="text-color-15" color="#ff9800">第四范式（4NF）</font>
* 第四范式要求一个关系表中消除多值依赖。如果存在多值依赖，需要将其拆分到新的表中。（字段量庞大的一对一关系表需要做拆分）

* 一对一外键唯一
```
用户登录信息表
| id(PK) | login_name | login_pwd | email | ...

用户详细信息表
| id(PK) | real_name | address | ... | login_id(fk + unique)
```

* 注：数据库设计尽量遵循三范式，但是还是根据实际情况进行取舍，有时可能会拿冗余换速度，最终用目的要满足客户需求。

## <font class="text-color-13" color="#ffeb3b">演示用表</font>
### emp
```
+-------+--------+-----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
```
### dept
```
+--------+------------+----------+
| DEPTNO | DNAME      | LOC      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
```
 ### salgrade
```
+-------+-------+-------+
| GRADE | LOSAL | HISAL |
+-------+-------+-------+
|     1 |   700 |  1200 |
|     2 |  1201 |  1400 |
|     3 |  1401 |  2000 |
|     4 |  2001 |  3000 |
|     5 |  3001 |  9999 |
+-------+-------+-------+
```
	


