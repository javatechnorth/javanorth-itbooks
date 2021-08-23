# MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、按照锁的粒度分数据库锁有哪些？锁机制与InnoDB锁算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#1按照锁的粒度分数据库锁有哪些锁机制与innodb锁算法)  


在关系型数据库中，可以**按照锁的粒度把数据库锁分**为行级锁(INNODB引擎)、表级锁(MYISAM引擎)和页级锁(BDB引擎 )。

**MyISAM和InnoDB存储引擎使用的锁：**

**1、** MyISAM采用表级锁(table-level locking)。

**2、** InnoDB支持行级锁(row-level locking)和表级锁，默认为行级锁

**行级锁，表级锁和页级锁对比**

**行级锁**

行级锁是MySQL中锁定粒度最细的一种锁，表示只针对当前操作的行进行加锁。行级锁能大大减少数据库操作的冲突。其加锁粒度最小，但加锁的开销也最大。行级锁分为共享锁 和 排他锁。

**特点：**

开销大，加锁慢；会出现死锁；锁定粒度最小，发生锁冲突的概率最低，并发度也最高。

**表级锁**

表级锁是MySQL中锁定粒度最大的一种锁，表示对当前操作的整张表加锁，它实现简单，资源消耗较少，被大部分MySQL引擎支持。最常使用的MYISAM与INNODB都支持表级锁定。表级锁定分为表共享读锁（共享锁）与表独占写锁（排他锁）

**特点：**

开销小，加锁快；不会出现死锁；锁定粒度大，发出锁冲突的概率最高，并发度最低。

**页级锁**

页级锁是MySQL中锁定粒度介于行级锁和表级锁中间的一种锁。表级锁速度快，但冲突多，行级冲突少，但速度慢。所以取了折衷的页级，一次锁定相邻的一组记录。

**特点：**

开销和加锁时间界于表锁和行锁之间；会出现死锁；锁定粒度界于表锁和行锁之间，并发度一般


### [2、数据库索引的原理，为什么要用 B+树，为什么不用二叉树？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#2数据库索引的原理为什么要用-b+树为什么不用二叉树)  


可以从几个维度去看这个问题，查询是否够快，效率是否稳定，存储数据多少，以及查找磁盘次数，为什么不是二叉树，为什么不是平衡二叉树，为什么不是B树，而偏偏是B+树呢？

**为什么不是一般二叉树？**

如果二叉树特殊化为一个链表，相当于全表扫描。平衡二叉树相比于二叉查找树来说，查找效率更稳定，总体的查找速度也更快。

**为什么不是平衡二叉树呢？**

我们知道，在内存比在磁盘的数据，查询效率快得多。如果树这种数据结构作为索引，那我们每查找一次数据就需要从磁盘中读取一个节点，也就是我们说的一个磁盘块，但是平衡二叉树可是每个节点只存储一个键值和数据的，如果是B树，可以存储更多的节点数据，树的高度也会降低，因此读取磁盘的次数就降下来啦，查询效率就快啦。

**那为什么不是B树而是B+树呢？**

1）B+树非叶子节点上是不存储数据的，仅存储键值，而B树节点中不仅存储键值，也会存储数据。innodb中页的默认大小是16KB，如果不存储数据，那么就会存储更多的键值，相应的树的阶数（节点的子节点树）就会更大，树就会更矮更胖，如此一来我们查找数据进行磁盘的IO次数有会再次减少，数据查询的效率也会更快。

2）B+树索引的所有数据均存储在叶子节点，而且数据是按照顺序排列的，链表连着的。那么B+树使得范围查找，排序查找，分组查找以及去重查找变得异常简单。


### [3、MYSQL数据库服务器性能分析的方法命令有哪些?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#3mysql数据库服务器性能分析的方法命令有哪些)  


**Show status, 一些值得监控的变量值：**

**1、** Bytes_received和Bytes_sent 和服务器之间来往的流量。

**2、** Com_*服务器正在执行的命令。

**3、** Created_*在查询执行期限间创建的临时表和文件。

**4、** Handler_*存储引擎操作。

**5、** Select_*不同类型的联接执行计划。

**6、** Sort_*几种排序信息。

**Show profiles 是MySql用来分析当前会话SQL语句执行的资源消耗情况**


### [4、SQL语句的语法顺序：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#4sql语句的语法顺序：)  


**1、** SELECT

**2、** FROM

**3、** JOIN

4、ON

**5、** WHERE

**6、** GROUP BY

**7、** HAVING

**8、** UNION

**9、** ORDER BY

**10、**  LIMIT


### [5、简述在MySQL数据库中MyISAM和InnoDB的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#5简述在mysql数据库中myisam和innodb的区别)  


MyISAM：

不支持事务，但是每次查询都是原子的；

支持表级锁，即每次操作是对整个表加锁；

存储表的总行数；

一个MYISAM表有三个文件：索引文件、表结构文件、数据文件；

采用菲聚集索引，索引文件的数据域存储指向数据文件的指针。辅索引与主索引基本一致，但是辅索引不用保证唯一性。

InnoDb：

支持ACID的事务，支持事务的四种隔离级别；

支持行级锁及外键约束：因此可以支持写并发；

不存储总行数；

一个InnoDb引擎存储在一个文件空间（共享表空间，表大小不受操作系统控制，一个表可能分布在多个文件里），也有可能为多个（设置为独立表空，表大小受操作系统文件大小限制，一般为2G），受操作系统文件大小的限制；

主键索引采用聚集索引（索引的数据域存储数据文件本身），辅索引的数据域存储主键的值；因此从辅索引查找数据，需要先通过辅索引找到主键值，再访问辅索引；最好使用自增主键，防止插入数据时，为维持B+树结构，文件的大调整。


### [6、一个6亿的表a，一个3亿的表b，通过外间tid关联，你如何最快的查询出满足条件的第50000到第50200中的这200条数据记录。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#6一个6亿的表a一个3亿的表b通过外间tid关联你如何最快的查询出满足条件的第50000到第50200中的这200条数据记录。)  


**1、** 如果A表TID是自增长,并且是连续的,B表的ID为索引 select * from a,b where a.tid = b.id and a.tid>500000 limit 200;

**2、** 如果A表的TID不是连续的,那么就需要使用覆盖索引.TID要么是主键,要么是辅助索引,B表ID也需要有索引。 select * from b , (select tid from a limit 50000,200) a where b.id = a .tid;


### [7、MySQL的复制原理以及流程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#7mysql的复制原理以及流程)  


「主从复制原理，简言之，就三步曲，如下：」

**1、** 主数据库有个bin-log二进制文件，纪录了所有增删改Sql语句。（binlog线程）

**2、** 从数据库把主数据库的bin-log文件的sql语句复制过来。（io线程）

**3、** 从数据库的relay-log重做日志文件中再执行一次这些sql语句。（Sql执行线程）

**上图主从复制分了五个步骤进行：**

步骤一：主库的更新事件(update、insert、delete)被写到binlog

步骤二：从库发起连接，连接到主库。

步骤三：此时主库创建一个binlog dump thread，把binlog的内容发送到从库。

步骤四：从库启动之后，创建一个I/O线程，读取主库传过来的binlog内容并写入到relay log

步骤五：还会创建一个SQL线程，从relay log里面读取内容，从Exec_Master_Log_Pos位置开始执行读取到的更新事件，将更新内容写入到slave的db


### [8、读写分离常见方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#8读写分离常见方案)  


**1、** 应用程序根据业务逻辑来判断，增删改等写操作命令发给主库，查询命令发给备库。

**2、** 利用中间件来做代理，负责对数据库的请求识别出读还是写，并分发到不同的数据库中。（如：amoeba，MySQL-proxy）


### [9、drop、delete与truncate的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#9dropdelete与truncate的区别)  

|  | delete | truncate | drop |
| --- | --- | --- | --- |
| 类型 | DML | DDL | DDL |
| 回滚 | 可回滚 | 不可回滚 | 不可回滚 |
| 删除内容 | 表结构还在，删除表的全部或者一部分数据行 | 表结构还在，删除表中的所有数据 | 从数据库中删除表，所有的数据行，索引和权限也会被删除 |
| 删除速度 | 删除速度慢，逐行删除 | 删除速度快 | 删除速度最快 |



### [10、字段为什么要求定义为not null？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#10字段为什么要求定义为not-null)  


null值会占用更多的字节，并且null有很多坑的。


### [11、为什么要使用数据库](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#11为什么要使用数据库)  

### [12、一条SQL语句在MySQL中如何执行的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#12一条sql语句在mysql中如何执行的)  

### [13、视图的使用场景有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#13视图的使用场景有哪些)  

### [14、从锁的类别上分MySQL都有哪些锁呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#14从锁的类别上分mysql都有哪些锁呢)  

### [15、MySQL 遇到过死锁问题吗，你是如何解决的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#15mysql-遇到过死锁问题吗你是如何解决的)  

### [16、MYSQL的主从延迟，你怎么解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#16mysql的主从延迟你怎么解决)  

### [17、聚簇索引和非聚簇索引，在查询数据的时候有区别吗？为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#17聚簇索引和非聚簇索引在查询数据的时候有区别吗为什么)  

### [18、B树和B+树的区别，数据库为什么使用B+树而不是B树？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#18b树和b+树的区别数据库为什么使用b+树而不是b树)  

### [19、如何显示前50行？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#19如何显示前50行)  

### [20、索引有哪些优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#20索引有哪些优缺点)  

### [21、试述视图的优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#21试述视图的优点)  

### [22、主键索引与唯一索引的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#22主键索引与唯一索引的区别)  

### [23、myisamchk是用来做什么的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#23myisamchk是用来做什么的)  

### [24、何时使用聚簇索引与非聚簇索引](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#24何时使用聚簇索引与非聚簇索引)  

### [25、什么是子查询](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#25什么是子查询)  

### [26、如何选择合适的分布式主键方案呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#26如何选择合适的分布式主键方案呢)  

### [27、为什么索引结构默认使用B+Tree，而不是Hash，二叉树，红黑树？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#27为什么索引结构默认使用b+tree而不是hash二叉树红黑树)  

### [28、列值为NULL时，查询是否会用到索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#28列值为null时查询是否会用到索引)  

### [29、MYSQL的主从延迟，你怎么解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#29mysql的主从延迟你怎么解决)  

### [30、优化数据库的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题汇总及答案（2021年MySQL面试题及答案大全）.md#30优化数据库的方法)  





