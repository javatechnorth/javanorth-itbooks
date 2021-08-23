# MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、主键和候选键有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#1主键和候选键有什么区别)  


表格的每一行都由主键唯一标识,一个表只有一个主键。

主键也是候选键。按照惯例，候选键可以被指定为主键，并且可以用于任何外键引用。


### [2、解释MySQL外连接、内连接与自连接的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#2解释mysql外连接内连接与自连接的区别)  


先说什么是交叉连接: 交叉连接又叫笛卡尔积，它是指不使用任何条件，直接将一个表的所有记录和另一个表中的所有记录一一匹配。

内连接 则是只有条件的交叉连接，根据某个条件筛选出符合条件的记录，不符合条件的记录不会出现在结果集中，即内连接只连接匹配的行。

外连接 其结果集中不仅包含符合连接条件的行，而且还会包括左表、右表或两个表中

的所有数据行，这三种情况依次称之为左外连接，右外连接，和全外连接。

左外连接，也称左连接，左表为主表，左表中的所有记录都会出现在结果集中，对于那些在右表中并没有匹配的记录，仍然要显示，右边对应的那些字段值以NULL来填充。右外连接，也称右连接，右表为主表，右表中的所有记录都会出现在结果集中。左连接和右连接可以互换，MySQL目前还不支持全外连接。


### [3、SQL的生命周期？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#3sql的生命周期)  


**1、** 服务器与数据库建立连接

**2、** 数据库进程拿到请求sql

**3、** 解析并生成执行计划，执行

**4、** 读取数据到内存，并进行逻辑处理

**5、** 通过步骤一的连接，发送结果到客户端

**6、** 关掉连接，释放资源


### [4、如何写sql能够有效的使用到复合索引。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#4如何写sql能够有效的使用到复合索引。)  


复合索引，也叫组合索引，用户可以在多个列上建立索引,这种索引叫做复合索引。

当我们创建一个组合索引的时候，如(k1,k2,k3)，相当于创建了（k1）、(k1,k2)和(k1,k2,k3)三个索引，这就是最左匹配原则。

```
select * from table where k1=A AND k2=B AND k3=D
```

有关于复合索引，我们需要关注查询Sql条件的顺序，确保最左匹配原则有效，同时可以删除不必要的冗余索引。


### [5、对MySQL的锁了解吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#5对mysql的锁了解吗)  


当数据库有并发事务的时候，可能会产生数据的不一致，这时候需要一些机制来保证访问的次序，锁机制就是这样的一个机制。

就像酒店的房间，如果大家随意进出，就会出现多人抢夺同一个房间的情况，而在房间上装上锁，申请到钥匙的人才可以入住并且将房间锁起来，其他人只有等他使用完毕才可以再次使用。


### [6、什么是最左前缀原则？什么是最左匹配原则？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#6什么是最左前缀原则什么是最左匹配原则)  


**1、** 最左前缀原则，就是最左优先，在创建多列索引时，要根据业务需求，where子句中使用最频繁的一列放在最左边。

**2、** 当我们创建一个组合索引的时候，如(k1,k2,k3)，相当于创建了（k1）、(k1,k2)和(k1,k2,k3)三个索引，这就是最左匹配原则。。


### [7、MySQL中都有哪些触发器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#7mysql中都有哪些触发器)  


**在MySQL数据库中有如下六种触发器：**

**1、** Before Insert

**2、** After Insert

**3、** Before Update

**4、** After Update

**5、** Before Delete

**6、** After Delete


### [8、什么是存储过程？有哪些优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#8什么是存储过程有哪些优缺点)  


**存储过程**，就是一些编译好了的SQL语句，这些SQL语句代码像一个方法一样实现一些功能（对单表或多表的增删改查），然后给这些代码块取一个名字，在用到这个功能的时候调用即可。

**优点：**

**1、** 存储过程是一个预编译的代码块，执行效率比较高

**2、** 存储过程在服务器端运行，减少客户端的压力

**3、** 允许模块化程序设计，只需要创建一次过程，以后在程序中就可以调用该过程任意次，类似方法的复用

**4、** 一个存储过程替代大量T_SQL语句 ，可以降低网络通信量，提高通信速率

**5、** 可以一定程度上确保数据安全

**缺点：**

**1、** 调试麻烦

**2、** 可移植性不灵活

**3、** 重新编译问题


### [9、什么是存储过程？有哪些优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#9什么是存储过程有哪些优缺点)  


存储过程是一个预编译的SQL语句，优点是允许模块化的设计，就是说只需要创建一次，以后在该程序中就可以调用多次。如果某次操作需要执行多次SQL，使用存储过程比单纯SQL语句执行要快。

**优点**

**1、** 存储过程是预编译过的，执行效率高。

**2、** 存储过程的代码直接存放于数据库中，通过存储过程名直接调用，减少网络通讯。

**3、** 安全性高，执行存储过程需要有一定权限的用户。

**4、** 存储过程可以重复使用，减少数据库开发人员的工作量。

**缺点**

**1、** 调试麻烦，但是用 PL/SQL Developer 调试很方便！弥补这个缺点。

**2、** 移植问题，数据库端代码当然是与数据库相关的。但是如果是做工程型项目，基本不存在移植问题。

**3、** 重新编译问题，因为后端代码是运行前编译的，如果带有引用关系的对象发生改变时，受影响的存储过程、包将需要重新编译（不过也可以设置成运行时刻自动编译）。

**4、** 如果在一个程序系统中大量的使用存储过程，到程序交付使用的时候随着用户需求的增加会导致数据结构的变化，接着就是系统的相关问题了，最后如果用户想维护该系统可以说是很难很难、而且代价是空前的，维护起来更麻烦。


### [10、如何优化查询过程中的数据访问](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#10如何优化查询过程中的数据访问)  


**1、** 访问数据太多导致查询性能下降

**2、** 确定应用程序是否在检索大量超过需要的数据，可能是太多行或列

**3、** 确认MySQL服务器是否在分析大量不必要的数据行

**4、** 避免犯如下SQL语句错误

**5、** 避免查询不需要的数据。解决办法：使用limit解决

**6、** 多表关联返回全部列。解决办法：指定列名

**7、** 总是返回全部列。解决办法：避免使用SELECT *

**8、** 重复查询相同的数据。解决办法：可以缓存数据，下次直接读取缓存

**9、** 使用explain进行分析，如果发现查询需要扫描大量的数据，但只返回少数的行，可以通过如下技巧去优化：

**10、** 使用索引覆盖扫描，把所有的列都放到索引中，这样存储引擎不需要回表获取对应行就可以返回结果。

**11、** 改变数据库和表的结构，修改数据表范式

**12、** 重写SQL语句，让优化器可以以更优的方式执行查询。


### [11、从锁的类别角度讲，MySQL都有哪些锁呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#11从锁的类别角度讲mysql都有哪些锁呢)  

### [12、如果要存储用户的密码散列，应该使用什么字段进行存储？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#12如果要存储用户的密码散列应该使用什么字段进行存储)  

### [13、int(20)中20的涵义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#13int20中20的涵义)  

### [14、创建索引的原则](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#14创建索引的原则)  

### [15、说说分库与分表的设计](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#15说说分库与分表的设计)  

### [16、CHAR和VARCHAR的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#16char和varchar的区别)  

### [17、SQL语言包括哪几部分？每部分都有哪些操作关键字？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#17sql语言包括哪几部分每部分都有哪些操作关键字)  

### [18、说说MySQL 的基础架构图](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#18说说mysql-的基础架构图)  

### [19、你怎么知道SQL语句性能是高还是低](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#19你怎么知道sql语句性能是高还是低)  

### [20、数据库中的事务是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#20数据库中的事务是什么)  

### [21、超大分页怎么处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#21超大分页怎么处理)  

### [22、MySQL有关权限的表有哪几个呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#22mysql有关权限的表有哪几个呢)  

### [23、在高并发情况下，如何做到安全的修改同一行数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#23在高并发情况下如何做到安全的修改同一行数据)  

### [24、说说MySQL 的基础架构图](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#24说说mysql-的基础架构图)  

### [25、主键使用自增ID还是UUID？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#25主键使用自增id还是uuid)  

### [26、SQL 约束有哪几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#26sql-约束有哪几种)  

### [27、对于关系型数据库而言，索引是相当重要的概念，请回答有关索引的几个问题：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#27对于关系型数据库而言索引是相当重要的概念请回答有关索引的几个问题：)  

### [28、FLOAT和DOUBLE的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#28float和double的区别是什么)  

### [29、使用B+树的好处](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题及答案大全（2021年MySQL面试题答案大汇总）.md#29使用b+树的好处)  





