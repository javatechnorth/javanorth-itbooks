# MySQL面试题大全带答案（2021年MySQL面试题及答案整理）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、MySQL中有哪几种锁？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#1mysql中有哪几种锁)  


1.表级锁：开销小，加锁快；不会出现死锁；锁定粒度大，发生锁冲突的概率最高，并发度最低。

2.行级锁：开销大，加锁慢；会出现死锁；锁定粒度最小，发生锁冲突的概率最低，并发度也最高。

3\、页面锁：开销和加锁时间界于表锁和行锁之间；会出现死锁；锁定粒度界于表锁和行锁之间，并发度一般。


### [2、myisamchk是用来做什么的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#2myisamchk是用来做什么的)  


它用来压缩MyISAM表，这减少了磁盘或内存使用。


### [3、NULL是什么意思](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#3null是什么意思)  


NULL这个值表示UNKNOWN(未知):它不表示“”(空字符串)。对NULL这个值的任何比较都会生产一个NULL值。您不能把任何值与一个 NULL值进行比较，并在逻辑上希望获得一个答案。

使用IS NULL来进行NULL判断


### [4、读写分离有哪些解决方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#4读写分离有哪些解决方案)  


读写分离是依赖于主从复制，而主从复制又是为读写分离服务的。因为主从复制要求`slave`不能写只能读（如果对`slave`执行写操作，那么`show slave status`将会呈现`Slave_SQL_Running=NO`，此时你需要按照前面提到的手动同步一下`slave`）。

**方案一**

使用MySQL-proxy代理

**优点：**

直接实现读写分离和负载均衡，不用修改代码，master和slave用一样的帐号，MySQL官方不建议实际生产中使用

**缺点：**

降低性能， 不支持事务

**方案二**

**1、** 使用AbstractRoutingDataSource+aop+annotation在dao层决定数据源。

**2、** 如果采用了mybatis， 可以将读写分离放在ORM层，比如mybatis可以通过mybatis plugin拦截sql语句，所有的insert/update/delete都访问master库，所有的select 都访问salve库，这样对于dao层都是透明。 plugin实现时可以通过注解或者分析语句是读写方法来选定主从库。不过这样依然有一个问题， 也就是不支持事务， 所以我们还需要重写一下DataSourceTransactionManager， 将read-only的事务扔进读库， 其余的有读有写的扔进写库。

**方案三**

**1、** 使用AbstractRoutingDataSource+aop+annotation在service层决定数据源，可以支持事务.

**2、** 缺点：类内部方法通过this.xx()方式相互调用时，aop不会进行拦截，需进行特殊处理。


### [5、数据库为什么使用B+树而不是B树](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#5数据库为什么使用b+树而不是b树)  


**1、** B树只适合随机检索，而B+树同时支持随机检索和顺序检索；

**2、** B+树空间利用率更高，可减少I/O次数，磁盘读写代价更低。一般来说，索引本身也很大，不可能全部存储在内存中，因此索引往往以索引文件的形式存储的磁盘上。这样的话，索引查找过程中就要产生磁盘I/O消耗。B+树的内部结点并没有指向关键字具体信息的指针，只是作为索引使用，其内部结点比B树小，盘块能容纳的结点中关键字数量更多，一次性读入内存中可以查找的关键字也就越多，相对的，IO读写次数也就降低了。而IO读写次数是影响索引检索效率的最大因素；

**3、** B+树的查询效率更加稳定。B树搜索有可能会在非叶子结点结束，越靠近根节点的记录查找时间越短，只要找到关键字即可确定记录的存在，其性能等价于在关键字全集内做一次二分查找。而在B+树中，顺序检索比较明显，随机检索时，任何关键字的查找都必须走一条从根节点到叶节点的路，所有关键字的查找路径长度相同，导致每一个关键字的查询效率相当。

**4、** B-树在提高了磁盘IO性能的同时并没有解决元素遍历的效率低下的问题。B+树的叶子节点使用指针顺序连接在一起，只要遍历叶子节点就可以实现整棵树的遍历。而且在数据库中基于范围的查询是非常频繁的，而B树不支持这样的操作。

**5、** 增删文件（节点）时，效率更高。因为B+树的叶子节点包含所有关键字，并以有序的链表结构存储，这样可很好提高增删效率。


### [6、Innodb的事务实现原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#6innodb的事务实现原理)  


**1、** 原子性：是使用 undo log来实现的，如果事务执行过程中出错或者用户执行了rollback，系统通过undo log日志返回事务开始的状态。

**2、** 持久性：使用 redo log来实现，只要redo log日志持久化了，当系统崩溃，即可通过redo log把数据恢复。

**3、** 隔离性：通过锁以及MVCC,使事务相互隔离开。

**4、** 一致性：通过回滚、恢复，以及并发情况下的隔离性，从而实现一致性。


### [7、varchar(50)中50的涵义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#7varchar50中50的涵义)  


**1、** 字段最多存放 50 个字符

**2、** 如 varchar(50) 和 varchar(200) 存储 "jay" 字符串所占空间是一样的，后者在排序时会消耗更多内存


### [8、一条SQL语句在MySQL中如何执行的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#8一条sql语句在mysql中如何执行的)  


先看一下MySQL的逻辑架构图吧~

![](https://user-gold-cdn.xitu.io/2020/5/23/1724037179201fe9?w=661&h=500&f=png&s=289132#alt=)

**查询语句：**

**1、** 先检查该语句是否有权限

**2、** 如果没有权限，直接返回错误信息

**3、** 如果有权限，在 MySQL8.0 版本以前，会先查询缓存。

**4、** 如果没有缓存，分析器进行词法分析，提取 sql 语句select等的关键元素。然后判断sql 语句是否有语法错误，比如关键词是否正确等等。

**5、** 优化器进行确定执行方案

**6、** 进行权限校验，如果没有权限就直接返回错误信息，如果有权限就会调用数据库引擎接口，返回执行结果。


### [9、什么是死锁？怎么解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#9什么是死锁怎么解决)  


死锁是指两个或多个事务在同一资源上相互占用，并请求锁定对方的资源，从而导致恶性循环的现象。

**常见的解决死锁的方法**

**1、** 如果不同程序会并发存取多个表，尽量约定以相同的顺序访问表，可以大大降低死锁机会。

**2、** 在同一个事务中，尽可能做到一次锁定所需要的所有资源，减少死锁产生概率；

**3、** 对于非常容易产生死锁的业务部分，可以尝试使用升级锁定颗粒度，通过表级锁定来减少死锁产生的概率；

如果业务不好处理,可以用分布式事务锁或者使用乐观锁


### [10、如何在Unix和MySQL时间戳之间进行转换？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#10如何在unix和mysql时间戳之间进行转换)  


UNIX_TIMESTAMP是从MySQL时间戳转换为Unix时间戳的命令

FROM_UNIXTIME是从Unix时间戳转换为MySQL时间戳的命令


### [11、简述在MySQL数据库中MyISAM和InnoDB的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#11简述在mysql数据库中myisam和innodb的区别)  

### [12、索引哪些情况会失效](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#12索引哪些情况会失效)  

### [13、MySQL中有哪几种锁，列举一下？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#13mysql中有哪几种锁列举一下)  

### [14、列对比运算符是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#14列对比运算符是什么)  

### [15、什么是触发器？触发器的使用场景有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#15什么是触发器触发器的使用场景有哪些)  

### [16、视图有哪些特点？哪些使用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#16视图有哪些特点哪些使用场景)  

### [17、MySQL数据库作发布系统的存储，一天五万条以上的增量，预计运维三年,怎么优化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#17mysql数据库作发布系统的存储一天五万条以上的增量预计运维三年,怎么优化)  

### [18、InnoDB引擎的4大特性，了解过吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#18innodb引擎的4大特性了解过吗)  

### [19、你怎么看到为表格定义的所有索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#19你怎么看到为表格定义的所有索引)  

### [20、完整性约束包括哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#20完整性约束包括哪些)  

### [21、既然提到了InnoDB使用户的B+树的索引模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#21既然提到了innodb使用户的b+树的索引模型)  

### [22、MySQL的binlog有几种录入格式？分别有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#22mysql的binlog有几种录入格式分别有什么区别)  

### [23、4.说说分库与分表的设计](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#234说说分库与分表的设计)  

### [24、索引有哪些优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#24索引有哪些优缺点)  

### [25、MySQL支持事务吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#25mysql支持事务吗)  

### [26、数据库的乐观锁和悲观锁。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#26数据库的乐观锁和悲观锁。)  

### [27、MySQL 的内连接、左连接、右连接有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#27mysql-的内连接左连接右连接有什么区别)  

### [28、SQL注入漏洞产生的原因？如何防止？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#28sql注入漏洞产生的原因如何防止)  

### [29、索引的分类?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#29索引的分类)  

### [30、什么是SQL？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题大全带答案（2021年MySQL面试题及答案整理）.md#30什么是sql)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
