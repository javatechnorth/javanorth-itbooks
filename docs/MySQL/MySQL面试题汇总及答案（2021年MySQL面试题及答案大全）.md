# MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、隔离级别与锁的关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#1隔离级别与锁的关系)  


**1、** 在Read Uncommitted级别下，读取数据不需要加共享锁，这样就不会跟被修改的数据上的排他锁冲突

**2、** 在Read Committed级别下，读操作需要加共享锁，但是在语句执行完以后释放共享锁；

**3、** 在Repeatable Read级别下，读操作需要加共享锁，但是在事务提交之前并不释放共享锁，也就是必须等待事务执行完毕以后才释放共享锁。

**4、** SERIALIZABLE 是限制性最强的隔离级别，因为该级别**锁定整个范围的键**，并一直持有锁，直到事务完成。


### [2、MySQL事务得四大特性以及实现原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#2mysql事务得四大特性以及实现原理)  


![](https://user-gold-cdn.xitu.io/2020/5/21/17237f45a661cbb7?w=626&h=466&f=png&s=127652#alt=)

**1、** 原子性： 事务作为一个整体被执行，包含在其中的对数据库的操作要么全部被执行，要么都不执行。

**2、** 一致性： 指在事务开始之前和事务结束以后，数据不会被破坏，假如A账户给B账户转10块钱，不管成功与否，A和B的总金额是不变的。

**3、** 隔离性： 多个事务并发访问时，事务之间是相互隔离的，即一个事务不影响其它事务运行效果。简言之，就是事务之间是进水不犯河水的。

**4、** 持久性： 表示事务完成以后，该事务对数据库所作的操作更改，将持久地保存在数据库之中。

**事务ACID特性的实现思想**

**1、** 原子性：是使用 undo log来实现的，如果事务执行过程中出错或者用户执行了rollback，系统通过undo log日志返回事务开始的状态。

**2、** 持久性：使用 redo log来实现，只要redo log日志持久化了，当系统崩溃，即可通过redo log把数据恢复。

**3、** 隔离性：通过锁以及MVCC,使事务相互隔离开。

**4、** 一致性：通过回滚、恢复，以及并发情况下的隔离性，从而实现一致性。


### [3、锁的优化策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#3锁的优化策略)  


1\、读写分离

2\、分段加锁

3\、减少锁持有的时间

4\、多个线程尽量以相同的顺序去获取资源

不能将锁的粒度过于细化，不然可能会出现线程的加锁和释放次数过多，反而效率不如一次加一把大锁。


### [4、varchar与char的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#4varchar与char的区别)  


**char的特点**

**1、** char表示定长字符串，长度是固定的；

**2、** 如果插入数据的长度小于char的固定长度时，则用空格填充；

**3、** 因为长度固定，所以存取速度要比varchar快很多，甚至能快50%，但正因为其长度固定，所以会占据多余的空间，是空间换时间的做法；

**4、** 对于char来说，最多能存放的字符个数为255，和编码无关

**varchar的特点**

**1、** varchar表示可变长字符串，长度是可变的；

**2、** 插入的数据是多长，就按照多长来存储；

**3、** varchar在存取方面与char相反，它存取慢，因为长度不固定，但正因如此，不占据多余的空间，是时间换空间的做法；

**4、** 对于varchar来说，最多能存放的字符个数为65532

**总之**

结合性能角度（char更快）和节省磁盘空间角度（varchar更小），具体情况还需具体来设计数据库才是妥当的做法


### [5、最左匹配原则？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#5最左匹配原则)  


在创建联合索引时候，一般需要遵循最左匹配原则。即联合索引中的属性识别度最高的放在查询语句的最前面。


### [6、创建索引的三种方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#6创建索引的三种方式)  


**第一种方式：**在执行CREATE TABLE时创建索引

```
CREATE TABLE user\_index2 ( id INT auto\_increment PRIMARY KEY, first\_name VARCHAR (16), last\_name VARCHAR (16), id\_card VARCHAR (18), information text, KEY name (first\_name, last\_name), FULLTEXT KEY (information), UNIQUE KEY (id\_card) );
```

**第二种方式：**使用ALTER TABLE命令去增加索引

```
ALTER TABLE table_name ADD INDEX index_name (column_list);
```

**1、** ALTER TABLE用来创建普通索引、UNIQUE索引或PRIMARY KEY索引。

**2、** 其中table_name是要增加索引的表名，column_list指出对哪些列进行索引，多列时各列之间用逗号分隔。

**3、** 索引名index_name可自己命名，缺省时，MySQL将根据第一个索引列赋一个名称。另外，ALTER TABLE允许在单个语句中更改多个表，因此可以在同时创建多个索引。

**4、** 第三种方式：使用CREATE INDEX命令创建

```
CREATE INDEX index_name ON table_name (column_list);
```

CREATE INDEX可对表增加普通索引或UNIQUE索引。（但是，不能创建PRIMARY KEY索引）


### [7、日常工作中你是怎么优化SQL的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#7日常工作中你是怎么优化sql的)  


**可以从这几个维度回答这个问题：**

**1、** 加索引

**2、** 避免返回不必要的数据

**3、** 适当分批量进行

**4、** 优化sql结构

**5、** 分库分表

**6、** 读写分离


### [8、主从同步延迟的解决办法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#8主从同步延迟的解决办法)  


**1、** 主服务器要负责更新操作，对安全性的要求比从服务器要高，所以有些设置参数可以修改，比如sync_binlog=1，innodb_flush_log_at_trx_commit = 1 之类的设置等。

**2、** 选择更好的硬件设备作为slave。

**3、** 把一台从服务器当度作为备份使用， 而不提供查询， 那边他的负载下来了， 执行relay log 里面的SQL效率自然就高了。

**4、** 增加从服务器喽，这个目的还是分散读的压力，从而降低服务器负载。


### [9、关心过业务系统里面的sql耗时吗？统计过慢查询吗？对慢查询都怎么优化过？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#9关心过业务系统里面的sql耗时吗统计过慢查询吗对慢查询都怎么优化过)  


**1、** 我们平时写Sql时，都要养成用explain分析的习惯。

**2、** 慢查询的统计，运维会定期统计给我们

**优化慢查询：**

**1、** 分析语句，是否加载了不必要的字段/数据。

**2、** 分析SQl执行句话，是否命中索引等。

**3、** 如果SQL很复杂，优化SQL结构

**4、** 如果表数据量太大，考虑分表


### [10、MySQL的binlog有几种录入格式？分别有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#10mysql的binlog有几种录入格式分别有什么区别)  


有三种格式哈，statement，row和mixed。

**1、** statement，每一条会修改数据的sql都会记录在binlog中。不需要记录每一行的变化，减少了binlog日志量，节约了IO，提高性能。由于sql的执行是有上下文的，因此在保存的时候需要保存相关的信息，同时还有一些使用了函数之类的语句无法被记录复制。

**2、** row，不记录sql语句上下文相关信息，仅保存哪条记录被修改。记录单元为每一行的改动，基本是可以全部记下来但是由于很多操作，会导致大量行的改动(比如alter table)，因此这种模式的文件保存的信息太多，日志量太大。

**3、** mixed，一种折中的方案，普通操作使用statement记录，当无法使用statement的时候使用row。


### [11、MySQL驱动程序是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#11mysql驱动程序是什么)  

### [12、索引的底层实现原理和优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#12索引的底层实现原理和优化)  

### [13、主键、外键和索引的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#13主键外键和索引的区别)  

### [14、B+树在满足聚簇索引和覆盖索引的时候不需要回表查询数据，](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#14b+树在满足聚簇索引和覆盖索引的时候不需要回表查询数据)  

### [15、一条Sql的执行顺序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#15一条sql的执行顺序)  

### [16、超键、候选键、主键、外键分别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#16超键候选键主键外键分别是什么)  

### [17、MySQL里记录货币用什么字段类型比较好？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#17mysql里记录货币用什么字段类型比较好)  

### [18、存储时期](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#18存储时期)  

### [19、MySQL 遇到过死锁问题吗，你是如何解决的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#19mysql-遇到过死锁问题吗你是如何解决的)  

### [20、什么是索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#20什么是索引)  

### [21、为表中得字段选择合适得数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#21为表中得字段选择合适得数据类型)  

### [22、MVCC熟悉吗，它的底层原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#22mvcc熟悉吗它的底层原理)  

### [23、存储引擎分类有哪些以及使用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#23存储引擎分类有哪些以及使用场景)  

### [24、百万级别或以上的数据，你是如何删除的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#24百万级别或以上的数据你是如何删除的)  

### [25、从锁的类别角度讲，MySQL都有哪些锁呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#25从锁的类别角度讲mysql都有哪些锁呢)  

### [26、什么是事务的隔离级别？MySQL的默认隔离级别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#26什么是事务的隔离级别mysql的默认隔离级别是什么)  

### [27、什么是幻读，脏读，不可重复读呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#27什么是幻读脏读不可重复读呢)  

### [28、B+树在满足聚簇索引和覆盖索引的时候不需要回表查询数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#28b+树在满足聚簇索引和覆盖索引的时候不需要回表查询数据)  

### [29、使用B树的好处](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#29使用b树的好处)  

### [30、如何通俗地理解三个范式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题汇总及答案（2021年MySQL面试题及答案大全）.md#30如何通俗地理解三个范式)  





