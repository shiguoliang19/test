## 启动与停止服务器

```cmd
//以管理员身份启动cmd，输入
//启动服务器
net start mysql
//停止服务器
net stop mysql
```





## 连接与断开服务器

```sql
//连接
mysql -u root -p
Enter password:******
mysql -h localhost -u root -p
Enter password:******
mysql -h 127.0.0.1 -u root -p
Enter password:******
//断开
quit
```

## 输入查询

```sql
select version();
select user();
select current_date;
```

## 数据库CURD

```sql
//创建数据库
create database db_name;//创建db_name数据库
create database db_name character set utf-8;//创建使用utf-8字符db_name数据库
//查看数据库
show databases;//显示所有数据库
show create database db_name;//显示创建数据库的语句信息
//修改数据库
alter database db_name character set utf8;
//删除数据库
drop database db_name;
```

## 表的CURD

```sql
//创建表
create tables tb_name(id int,name varchar(20));
//显示表
show tables;//显看所有表
show create table tb_name;//查看指定表的创建语句
desc tb_name;//显示指定表的结构
//修改表
rename table tb_name to new_tb_name;//更改表名
alter table tb_name add column height double;//增加一个字段
alter table tb_name modify column height float;//修改一个字段
alter table tb_name drop column height;//删除一个字段
alter table tb_name character set gbk;//修改表的字符集
//删除表
drop table tb_name;
```

## 表数据的CURD

```sql
/插入
insert into tb_name(id,name) values(1,'张三');
//更新
update tb_name set id=2 where name='张三';
//删除
delete from tb_name where name='张三';
//查询
select id '帐号',name '姓名' from tb_name;
```

## 日期时间函数

```c++
select now(),year(now()),month(now()),day(now());
select current_date(),current_time(),current_timestamp;
```

![1588685355756](C:\Users\shiguoliang\Desktop\assets\1588685355756.png)

## 字符串相关函数

```sql
select concat(id,name) from tb_name;
```

![1588685654151](C:\Users\shiguoliang\Desktop\assets\1588685654151.png)

## 数学相关函数

```sql
select abs(-3.14) from dual;
```

![1588686331163](C:\Users\shiguoliang\Desktop\assets\1588686331163.png)

## 多表查询

```sql
//交叉连接
select e.*,d.*
from emp e cross join dept d;
//内连接
select e.*,d.*
from emp e inner join dept d
on e.deptno=d.deptno;
//左外连接
select e.*,d.*
from emp e left outer join dept d
on e.deptno=d.deptno;
//右外连接
select e.*,d.*
from emp e left outer join dept d
on e.deptno=d.deptno;
//全外连接
select e.*,d.*
from emp e full outer join dept d
on e.depton=d.depton;
//自连接
select e.ename,b.ename
from emp e,emp b
where e.mgr=b.empno;
```

## 表的约束

```c++
//定义主键约束(允许为空，不允许重复)
primary key
//定义主键自动增长
auto incremnet
//定义唯一约束
unique
//定义非空约束
not null
```











```sql
select b.mac_address as 'mac地址',
b.ip_address as 'ip地址',
b.local_host_name as '主机名',
b.user_name as '用户名',
'在线' as '在线状态'
from information_schema.processlist a inner join user_info b
on a.host=b.ip_address;
```

