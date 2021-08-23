# MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、实践中如何优化MySQL](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#1实践中如何优化mysql)  


最好是按照以下顺序优化：

**1、** SQL语句及索引的优化

**2、** 数据库表结构的优化

**3、** 系统配置的优化

**4、** 硬件的优化

详细可以查看 [阿里P8架构师谈：MySQL慢查询优化、索引优化、以及表等优化总结](http://youzhixueyuan.com/MySQL-slow-query-optimization-index-optimization.html)


### [2、如何通俗地理解三个范式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#2如何通俗地理解三个范式)  


第一范式：1NF是对属性的原子性约束，要求属性具有原子性，不可再分解；

第二范式：2NF是对记录的惟一性约束，要求记录有惟一标识，即实体的惟一性；

第三范式：3NF是对字段冗余性的约束，即任何字段不能由其他字段派生出来，它要求字段没有冗余。。

范式化设计优缺点:

优点:

可以尽量得减少数据冗余，使得更新快，体积小

缺点:对于查询需要多个表进行关联，减少写得效率增加读得效率，更难进行索引优化

反范式化:

优点:可以减少表得关联，可以更好得进行索引优化

缺点:数据冗余以及数据异常，数据得修改需要更多的成本


### [3、索引有哪几种类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#3索引有哪几种类型)  


**1、** 主键索引: 数据列不允许重复，不允许为NULL，一个表只能有一个主键。

**2、** 唯一索引: 数据列不允许重复，允许为NULL值，一个表允许多个列创建唯一索引。

**3、** 普通索引: 基本的索引类型，没有唯一性的限制，允许为NULL值。

**4、** 全文索引：是目前搜索引擎使用的一种关键技术，对文本的内容进行分词、搜索。

**5、** 覆盖索引：查询列要被所建的索引覆盖，不必读取数据行

**6、** 组合索引：多列值组成一个索引，用于组合搜索，效率大于索引合并


### [4、MySQL的复制原理以及流程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#4mysql的复制原理以及流程)  


**主从复制：**

将主数据库中的DDL和DML操作通过二进制日志（BINLOG）传输到从数据库上，然后将这些日志重新执行（重做）；从而使得从数据库的数据与主数据库保持一致。

**主从复制的作用**

**1、** 主数据库出现问题，可以切换到从数据库。

**2、** 可以进行数据库层面的读写分离。

**3、** 可以在从数据库上进行日常备份。

MySQL主从复制解决的问题

**1、** 数据分布：随意开始或停止复制，并在不同地理位置分布数据备份

**2、** 负载均衡：降低单个服务器的压力

**3、** 高可用和故障切换：帮助应用程序避免单点失败

**4、** 升级测试：可以用更高版本的MySQL作为从库

**MySQL主从复制工作原理**

**1、** 在主库上把数据更高记录到二进制日志

**2、** 从库将主库的日志复制到自己的中继日志

**3、** 从库读取中继日志的事件，将其重放到从库数据中

**基本原理流程，3个线程以及之间的关联**

**主**：

binlog线程——记录下所有改变了数据库数据的语句，放进master上的binlog中；

**从**：

io线程——在使用start slave 之后，负责从master上拉取 binlog 内容，放进自己的relay log中；

**从**：

sql执行线程——执行relay log中的语句；

**复制过程**

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/049/50/99_14.png#alt=99%5C_14.png)

**Binary log：**主数据库的二进制日志

**Relay log：**从服务器的中继日志

**1、** master在每个事务更新数据完成之前，将该操作记录串行地写入到binlog文件中。

**2、** salve开启一个I/O Thread，该线程在master打开一个普通连接，主要工作是binlog dump process。如果读取的进度已经跟上了master，就进入睡眠状态并等待master产生新的事件。I/O线程最终的目的是将这些事件写入到中继日志中。

**3、** SQL Thread会读取中继日志，并顺序执行该日志中的SQL事件，从而与主数据库中的数据保持一致。


### [5、Hash索引和B+树区别是什么？你在设计索引是怎么抉择的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#5hash索引和b+树区别是什么你在设计索引是怎么抉择的)  


**1、** B+树可以进行范围查询，Hash索引不能。

**2、** B+树支持联合索引的最左侧原则，Hash索引不支持。

**3、** B+树支持order by排序，Hash索引不支持。

**4、** Hash索引在等值查询上比B+树效率更高。

**5、** B+树使用like 进行模糊查询的时候，like后面（比如%开头）的话可以起到优化的作用，Hash索引根本无法进行模糊查询。


### [6、什么是基本表？什么是视图？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#6什么是基本表什么是视图)  


基本表是本身独立存在的表，在 SQL 中一个关系就对应一个表。  视图是从一个或几个基本表导出的表。视图本身不独立存储在数据库中，是一个虚表


### [7、什么是MySQL?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#7什么是mysql)  


MySQL是一个关系型数据库管理系统，由瑞典MySQL AB 公司开发，属于 Oracle 旗下产品。MySQL 是最流行的关系型数据库管理系统之一，在 WEB 应用方面，MySQL是最好的 RDBMS (Relational Database Management System，关系数据库管理系统) 应用软件之一。在Java企业级开发中非常常用，因为 MySQL 是开源免费的，并且方便扩展。


### [8、什么是锁？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#8什么是锁)  


数据库是一个多用户使用的共享资源。当多个用户并发地存取数据时，在数据库中就会产生多个事务同时存取同一数据的情况。若对并发操作不加控制就可能会读取和存储不正确的数据，破坏数据库的一致性。

加锁是实现数据库并发控制的一个非常重要的技术。当事务在对某个数据对象进行操作前，先向系统发出请求，对其加锁。加锁后事务就对该数据对象有了一定的控制，在该事务释放锁之前，其他的事务不能对此数据对象进行更新操作。

**基本锁类型：锁包括行级锁和表级锁**


### [9、NOW（）和CURRENT_DATE（）有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#9now和current_date有什么区别)  


NOW（）命令用于显示当前年份，月份，日期，小时，分钟和秒。

CURRENT_DATE（）仅显示当前年份，月份和日期。


### [10、数据库的乐观锁和悲观锁。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#10数据库的乐观锁和悲观锁。)  


**悲观锁：**

悲观锁她专一且缺乏安全感了，她的心只属于当前事务，每时每刻都担心着它心爱的数据可能被别的事务修改，所以一个事务拥有（获得）悲观锁后，其他任何事务都不能对数据进行修改啦，只能等待锁被释放才可以执行。


### [11、关心过业务系统里面的sql耗时吗？统计过慢查询吗？对慢查询都怎么优化过？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#11关心过业务系统里面的sql耗时吗统计过慢查询吗对慢查询都怎么优化过)  

### [12、索引分类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#12索引分类)  

### [13、什么是数据库连接池?为什么需要数据库连接池呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#13什么是数据库连接池为什么需要数据库连接池呢)  

### [14、B树和B+树的区别，数据库为什么使用B+树而不是B树？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#14b树和b+树的区别数据库为什么使用b+树而不是b树)  

### [15、主键、外键和索引的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#15主键外键和索引的区别)  

### [16、Blob和text有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#16blob和text有什么区别)  

### [17、MySQL中int(10)和char(10)以及varchar(10)的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#17mysql中int10和char10以及varchar10的区别)  

### [18、MYSQL数据库服务器性能分析的方法命令有哪些?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#18mysql数据库服务器性能分析的方法命令有哪些)  

### [19、B+ Tree索引和Hash索引区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#19b+-tree索引和hash索引区别)  

### [20、什么是非标准字符串类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#20什么是非标准字符串类型)  

### [21、你怎么看到为表格定义的所有索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#21你怎么看到为表格定义的所有索引)  

### [22、什么是游标？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#22什么是游标)  

### [23、LIKE声明中的％和_是什么意思？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#23like声明中的％和_是什么意思)  

### [24、创建索引的原则？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#24创建索引的原则)  

### [25、什么是触发器？触发器的使用场景有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#25什么是触发器触发器的使用场景有哪些)  

### [26、按照锁的粒度分，数据库锁有哪些呢？锁机制与InnoDB锁算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#26按照锁的粒度分数据库锁有哪些呢锁机制与innodb锁算法)  

### [27、简单描述MySQL中，索引，主键，唯一索引，联合索引的区别，对数据库的性能有什么影响（从读写两方面）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#27简单描述mysql中索引主键唯一索引联合索引的区别对数据库的性能有什么影响从读写两方面)  

### [28、数据库中间件了解过吗，sharding jdbc，mycat？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#28数据库中间件了解过吗sharding-jdbcmycat)  

### [29、MySQL里记录货币用什么字段类型好](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#29mysql里记录货币用什么字段类型好)  

### [30、MYSQL支持事务吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#30mysql支持事务吗)  





