# MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、数据库自增主键可能遇到什么问题。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#1数据库自增主键可能遇到什么问题。)  


**1、** 使用自增主键对数据库做分库分表，可能出现诸如主键重复等的问题。解决方案的话，简单点的话可以考虑使用UUID哈

**2、** 自增主键会产生表锁，从而引发问题

**3、** 自增主键可能用完问题。


### [2、MySQL中InnoDB引擎的行锁是怎么实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#2mysql中innodb引擎的行锁是怎么实现的)  


**InnoDB是基于索引来完成行锁**

例:

`select \* from tab\_with\_index where id = 1 for update;`

for update 可以根据条件来完成行锁锁定，并且 id 是有索引键的列，如果 id 不是索引键那么InnoDB将完成表锁，并发将无从谈起


### [3、MySQL有关权限的表都有哪几个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#3mysql有关权限的表都有哪几个)  


MySQL服务器通过权限表来控制用户对数据库的访问，权限表存放在MySQL数据库里，由MySQL_install_db脚本初始化。这些权限表分别user，db，table_priv，columns_priv和host。


### [4、索引失效情况？ ==校验SQL语句是否使用了索引方式为：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#4索引失效情况-校验sql语句是否使用了索引方式为：)  


**在SQL语句前面使用explain关键字==**

**1、** like以%开头索引无效，当like以&结尾，索引有效。

**2、** or语句前后没有同事使用索引，当且仅当or语句查询条件的前后列均为索引时，索引生效。

**3、** 组合索引，使用的不是第一列索引时候，索引失效，即最左匹配规则。

**4、** 数据类型出现隐式转换，如varchar不加单引号的时候可能会自动转换为int类型，这个时候索引失效。

**5、** 在索引列上使用IS NULL或者 IS NOT NULL 时候，索引失效，因为索引是不索引空值得。

**6、** 在索引字段上使用，NOT、 <>、！= 、时候是不会使用索引的，对于这样的处理只会进行全表扫描。

**7、** 对索引字段进行计算操作，函数操作时不会使用索引。

**8、** 当全表扫描速度比索引速度快的时候不会使用索引。


### [5、什么情况下设置了索引但无法使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#5什么情况下设置了索引但无法使用)  


**1、** 以“%”开头的LIKE语句，模糊匹配

**2、** OR语句前后没有同时使用索引

**3、** 数据类型出现隐式转化（如varchar不加单引号的话可能会自动转换为int型）


### [6、为什么要使用视图？什么是视图？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#6为什么要使用视图什么是视图)  


**「为什么要使用视图？」**

为了提高复杂SQL语句的复用性和表操作的安全性，MySQL数据库管理系统提供了视图特性。

**「什么是视图？」**

视图是一个虚拟的表，是一个表中的数据经过某种筛选后的显示方式，视图由一个预定义的查询select语句组成。


### [7、MySQL中InnoDB引擎的行锁是怎么实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#7mysql中innodb引擎的行锁是怎么实现的)  


基于索引来完成行锁的。

```
select * from t where id = 666 for update;
```

for update 可以根据条件来完成行锁锁定，并且 id 是有索引键的列，如果 id 不是索引键那么InnoDB将实行表锁。


### [8、怎么优化SQL查询语句吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#8怎么优化sql查询语句吗)  


**1、** 对查询进行优化，应尽量避免全表扫描，首先应考虑在 where 及 order by 涉及的列上建立索引

**2、** 用索引可以提高查询

**3、** SELECT子句中避免使用*号，尽量全部大写SQL

**4、** 应尽量避免在 where 子句中对字段进行 is null 值判断，否则将导致引擎放弃使用索引而进行全表扫描，使用 IS NOT NULL

**5、** where 子句中使用 or 来连接条件，也会导致引擎放弃使用索引而进行全表扫描

**6、** in 和 not in 也要慎用，否则会导致全表扫描


### [9、如何删除索引](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#9如何删除索引)  


根据索引名删除普通索引、唯一索引、全文索引：`alter table 表名 drop KEY 索引名`

```
alter table user_index drop KEY name;
alter table user_index drop KEY id_card;
alter table user_index drop KEY information;
```

**删除主键索引：**`alter table 表名 drop primary key`（因为主键只有一个）。这里值得注意的是，如果主键自增长，那么不能直接执行此操作（自增长依赖于主键索引）：

![99_3.png][99_3.png]

**需要取消自增长再行删除：**

```
alter table user_index
-- 重新定义字段
MODIFY id int,
drop PRIMARY KEY
```

但通常不会删除主键，因为设计主键一定与业务逻辑无关。


### [10、说一下数据库的三大范式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#10说一下数据库的三大范式)  


**1、** 第一范式：数据表中的每一列（每个字段）都不可以再拆分。

**2、** 第二范式：在第一范式的基础上，分主键列完全依赖于主键，而不能是依赖于主键的一部分。

**3、** 第三范式：在满足第二范式的基础上，表中的非主键只依赖于主键，而不依赖于其他非主键。


### [11、数据库索引的原理，为什么要用 B+树，为什么不用二叉树？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#11数据库索引的原理为什么要用-b+树为什么不用二叉树)  

### [12、MySQL_fetch_array和MySQL_fetch_object的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#12mysql_fetch_array和mysql_fetch_object的区别是什么)  

### [13、MySQL中都有哪些触发器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#13mysql中都有哪些触发器)  

### [14、索引是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#14索引是什么)  

### [15、MySQL中InnoDB支持的四种事务隔离级别名称，以及逐级之间的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#15mysql中innodb支持的四种事务隔离级别名称以及逐级之间的区别)  

### [16、MySQL 索引使用有哪些注意事项呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#16mysql-索引使用有哪些注意事项呢)  

### [17、SQL的执行顺序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#17sql的执行顺序)  

### [18、视图的优点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#18视图的优点)  

### [19、如果一个表有一列定义为TIMESTAMP，将发生什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#19如果一个表有一列定义为timestamp将发生什么)  

### [20、MySQL如何优化DISTINCT？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#20mysql如何优化distinct)  

### [21、如果某个表有近千万数据，CRUD比较慢，如何优化。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#21如果某个表有近千万数据crud比较慢如何优化。)  

### [22、什么是非标准字符串类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#22什么是非标准字符串类型)  

### [23、如何优化长难的查询语句](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#23如何优化长难的查询语句)  

### [24、你可以用什么来确保表格里的字段只接受特定范围里的值?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#24你可以用什么来确保表格里的字段只接受特定范围里的值)  

### [25、MySQL中 in 和 exists 区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#25mysql中-in-和-exists-区别)  

### [26、什么是游标？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#26什么是游标)  

### [27、实践中如何优化MySQL](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#27实践中如何优化mysql)  

### [28、drop、delete与truncate的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#28dropdelete与truncate的区别)  

### [29、数据库存储日期格式时，如何考虑时区转换问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题及答案大全（2021年MySQL面试题答案大汇总）.md#29数据库存储日期格式时如何考虑时区转换问题)  





