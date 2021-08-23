# MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、非聚簇索引一定会回表查询吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#1非聚簇索引一定会回表查询吗)  


不一定，这涉及到查询语句所要求的字段是否全部命中了索引，如果全部命中了索引，那么就不必再进行回表查询。

**举个简单的例子**

假设我们在员工表的年龄上建立了索引，那么当进行`select age from employee where age < 20`的查询时，在索引的叶子节点上，已经包含了age信息，不会再次进行回表查询。


### [2、varchar(50)中50的涵义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#2varchar50中50的涵义)  


最多存放50个字符，varchar(50)和(200)存储hello所占空间一样，但后者在排序时会消耗更多内存，因为order by col采用fixed_length计算col长度(memory引擎也一样)。在早期 MySQL 版本中， 50 代表字节数，现在代表字符数。


### [3、完整性约束包括哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#3完整性约束包括哪些)  


数据完整性(Data Integrity)是指数据的精确(Accuracy)和可靠性(Reliability)。

**分为以下四类：**

**1、** 实体完整性：规定表的每一行在表中是惟一的实体。

**2、** 域完整性：是指表中的列必须满足某种特定的数据类型约束，其中约束又包括取值范围、精度等规定。

**3、** 参照完整性：是指两个表的主关键字和外关键字的数据应一致，保证了表之间的数据的一致性，防止了数据丢失或无意义的数据在数据库中扩散。

**4、** 用户定义的完整性：不同的关系数据库系统根据其应用环境的不同，往往还需要一些特殊的约束条件。用户定义的完整性即是针对某个特定关系数据库的约束条件，它反映某一具体应用必须满足的语义要求。

与表有关的约束：包括列约束(NOT NULL（非空约束）)和表约束(PRIMARY KEY、foreign key、check、UNIQUE) 。


### [4、谈谈六种关联查询，使用场景。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#4谈谈六种关联查询使用场景。)  


**1、** 交叉连接

**2、** 内连接

**3、** 外连接

**4、** 联合查询

**5、** 全连接

**6、** 交叉连接


### [5、MVCC熟悉吗，它的底层原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#5mvcc熟悉吗它的底层原理)  


MVCC,多版本并发控制,它是通过读取历史版本的数据，来降低并发事务冲突，从而提高并发性能的一种机制。

**「MVCC需要关注这几个知识点：」**

**1、** 事务版本号

**2、** 表的隐藏列

**3、** undo log

**4、** read view


### [6、锁的优化策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#6锁的优化策略)  


**1、** 读写分离

**2、** 分段加锁

**3、** 减少锁持有的时间

4.多个线程尽量以相同的顺序去获取资源

不能将锁的粒度过于细化，不然可能会出现线程的加锁和释放次数过多，反而效率不如一次加一把大锁。


### [7、什么是聚簇索引？何时使用聚簇索引与非聚簇索引](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#7什么是聚簇索引何时使用聚簇索引与非聚簇索引)  


**聚簇索引：**

将数据存储与索引放到了一块，找到索引也就找到了数据

**非聚簇索引：**

将数据存储于索引分开结构，索引结构的叶子节点指向了数据的对应行，myisam通过key_buffer把索引先缓存到内存中，当需要访问数据时（通过索引访问数据），在内存中直接搜索索引，然后通过索引找到磁盘相应数据，这也就是为什么索引不在key buffer命中时，速度慢的原因

**澄清一个概念：**

innodb中，在聚簇索引之上创建的索引称之为辅助索引，辅助索引访问数据总是需要二次查找，非聚簇索引都是辅助索引，像复合索引、前缀索引、唯一索引，辅助索引叶子节点存储的不再是行的物理位置，而是主键值

**何时使用聚簇索引与非聚簇索引**

![99_5.png][99_5.png]


### [8、500台db，在最快时间之内重启。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#8500台db在最快时间之内重启。)  


**2、** 可以使用批量 ssh 工具 pssh 来对需要重启的机器执行重启命令。

**3、** 也可以使用 salt（前提是客户端有安装 salt）或者 ansible（ ansible 只需要 ssh 免登通了就行）等多线程工具同时操作多台服务


### [9、你们数据库是否支持emoji表情存储，如果不支持，如何操作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#9你们数据库是否支持emoji表情存储如果不支持如何操作)  


更换字符集utf8-->utf8mb4


### [10、说一下大表查询的优化方案](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#10说一下大表查询的优化方案)  


**1、** 优化shema、sql语句+索引；

**2、** 可以考虑加缓存，Memcached, Redis，或者JVM本地缓存；

**3、** 主从复制，读写分离；

**4、** 分库分表；


### [11、优化特定类型的查询语句](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#11优化特定类型的查询语句)  

### [12、慢查询日志](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#12慢查询日志)  

### [13、什么是死锁？怎么解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#13什么是死锁怎么解决)  

### [14、视图有哪些特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#14视图有哪些特点)  

### [15、按照锁的粒度分，数据库锁有哪些呢？锁机制与InnoDB锁算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#15按照锁的粒度分数据库锁有哪些呢锁机制与innodb锁算法)  

### [16、InnoDB存储引擎的锁的算法有三种](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#16innodb存储引擎的锁的算法有三种)  

### [17、索引设计的原则？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#17索引设计的原则)  

### [18、MySQL中有哪几种锁？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#18mysql中有哪几种锁)  

### [19、创建索引的三种方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#19创建索引的三种方式)  

### [20、优化WHERE子句](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#20优化where子句)  

### [21、MySQL数据库cpu飙升的话，要怎么处理呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#21mysql数据库cpu飙升的话要怎么处理呢)  

### [22、MySQL有关权限的表都有哪几个](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#22mysql有关权限的表都有哪几个)  

### [23、InnoDB引擎的4大特性](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#23innodb引擎的4大特性)  

### [24、UNION与UNION ALL的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#24union与union-all的区别)  

### [25、select for update 含义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#25select-for-update-含义)  

### [26、MyISAM Static和MyISAM Dynamic有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#26myisam-static和myisam-dynamic有什么区别)  

### [27、SQL优化的一般步骤是什么，怎么看执行计划（explain），如何理解其中各个字段的含义。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#27sql优化的一般步骤是什么怎么看执行计划explain如何理解其中各个字段的含义。)  

### [28、关心过业务系统里面的sql耗时吗？统计过慢查询吗？对慢查询都怎么优化过？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#28关心过业务系统里面的sql耗时吗统计过慢查询吗对慢查询都怎么优化过)  

### [29、什么是脏读？幻读？不可重复读？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#29什么是脏读幻读不可重复读)  

### [30、大表怎么优化？分库分表了是怎么做的？分表分库了有什么问题？有用到中间件么？他们的原理知道么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#30大表怎么优化分库分表了是怎么做的分表分库了有什么问题有用到中间件么他们的原理知道么)  





