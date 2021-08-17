# MySQL面试题带答案（2021年MySQL面试题及答案大汇总）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、UNION与UNION ALL的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#1union与union-all的区别)  


**1、** Union：对两个结果集进行并集操作，不包括重复行，同时进行默认规则的排序；

**2、** Union All：对两个结果集进行并集操作，包括重复行，不进行排序；

**3、** UNION的效率高于 UNION ALL


### [2、CHAR和VARCHAR的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#2char和varchar的区别)  


1.CHAR和VARCHAR类型在存储和检索方面有所不同

2.CHAR列长度固定为创建表时声明的长度，长度值范围是1到255

当CHAR值被存储时，它们被用空格填充到特定长度，检索CHAR值时需删除尾随空格。


### [3、Hash索引和B+树所有有什么区别或者说优劣呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#3hash索引和b+树所有有什么区别或者说优劣呢)  


**1、** 首先要知道Hash索引和B+树索引的底层实现原理：

**2、** hash索引底层就是hash表，进行查找时，调用一次hash函数就可以获取到相应的键值，之后进行回表查询获得实际数据。B+树底层实现是多路平衡查找树。对于每一次的查询都是从根节点出发，查找到叶子节点方可以获得所查键值，然后根据查询判断是否需要回表查询数据。

**那么可以看出他们有以下的不同：**

**1、** hash索引进行等值查询更快(一般情况下)，但是却无法进行范围查询。

**2、** 因为在hash索引中经过hash函数建立索引之后，索引的顺序与原顺序无法保持一致，不能支持范围查询。而B+树的的所有节点皆遵循(左节点小于父节点，右节点大于父节点，多叉树也类似)，天然支持范围。

**3、** hash索引不支持使用索引进行排序，原理同上。

**4、** hash索引不支持模糊查询以及多列索引的最左前缀匹配。原理也是因为hash函数的不可预测。AAAA和AAAAB的索引没有相关性。

**5、** hash索引任何时候都避免不了回表查询数据，而B+树在符合某些条件(聚簇索引，覆盖索引等)的时候可以只通过索引完成查询。

**6、** hash索引虽然在等值查询上较快，但是不稳定。性能不可预测，当某个键值存在大量重复的时候，发生hash碰撞，此时效率可能极差。而B+树的查询效率比较稳定，对于所有的查询都是从根节点到叶子节点，且树的高度较低。

**7、** 因此，在大多数情况下，直接选择B+树索引可以获得稳定且较好的查询速度。而不需要使用hash索引。


### [4、索引的基本原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#4索引的基本原理)  


索引用来快速地寻找那些具有特定值的记录。如果没有索引，一般来说执行查询时遍历整张表。

**索引的原理很简单，就是把无序的数据变成有序的查询**

**1、** 把创建了索引的列的内容进行排序

**2、** 对排序结果生成倒排表

**3、** 在倒排表内容上拼上数据地址链

**4、** 在查询的时候，先拿到倒排表内容，再取出数据地址链，从而拿到具体数据


### [5、简单总结下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#5简单总结下)  


**1、** MySQL使用B+Tree作为索引数据结构。

**2、** B+Tree在新增数据时，会根据索引指定列的值对旧的B+Tree做调整。

**4、** 从物理存储结构上说，B-Tree和B+Tree都以页(4K)来划分节点的大小，但是由于B+Tree中中间节点不存储数据，因此B+Tree能够在同样大小的节点中，存储更多的key，提高查找效率。

**5、** 影响MySQL查找性能的主要还是磁盘IO次数，大部分是磁头移动到指定磁道的时间花费。

**6、** MyISAM存储引擎下索引和数据存储是分离的，InnoDB索引和数据存储在一起。

**7、** InnoDB存储引擎下索引的实现，(辅助索引)全部是依赖于主索引建立的(辅助索引中叶子结点存储的并不是数据的地址，还是主索引的值，因此，所有依赖于辅助索引的都是先根据辅助索引查到主索引，再根据主索引查数据的地址)。

**8、** 由于InnoDB索引的特性，因此如果主索引不是自增的(id作主键)，那么每次插入新的数据，都很可能对B+Tree的主索引进行重整，影响性能。因此，尽量以自增id作为InnoDB的主索引。




### [6、什么是死锁？怎么解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#6什么是死锁怎么解决)  


死锁是指两个或多个事务在同一资源上相互占用，并请求锁定对方的资源，从而导致恶性循环的现象。看图形象一点，如下：

![](https://user-gold-cdn.xitu.io/2020/5/23/17241317342078b9?w=641&h=575&f=png&s=133003#alt=)

死锁有四个必要条件：互斥条件，请求和保持条件，环路等待条件，不剥夺条件。

**解决死锁思路，一般就是切断环路，尽量避免并发形成环路。**

**1、** 如果不同程序会并发存取多个表，尽量约定以相同的顺序访问表，可以大大降低死锁机会。

**2、** 在同一个事务中，尽可能做到一次锁定所需要的所有资源，减少死锁产生概率；

**3、** 对于非常容易产生死锁的业务部分，可以尝试使用升级锁定颗粒度，通过表级锁定来减少死锁产生的概率；

**4、** 如果业务处理不好可以用分布式事务锁或者使用乐观锁

**5、** 死锁与索引密不可分，解决索引问题，需要合理优化你的索引，



### [7、LIKE声明中的％和_是什么意思？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#7like声明中的％和_是什么意思)  


％对应于0个或更多字符，_只是LIKE语句中的一个字符。


### [8、SQL 约束有哪几种呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#8sql-约束有哪几种呢)  


**1、** NOT NULL: 约束字段的内容一定不能为NULL。

**2、** UNIQUE: 约束字段唯一性，一个表允许有多个 Unique 约束。

**3、** PRIMARY KEY: 约束字段唯一，不可重复，一个表只允许存在一个。

**4、** FOREIGN KEY: 用于预防破坏表之间连接的动作，也能防止非法数据插入外键。

**5、** CHECK: 用于控制字段的值范围。


### [9、创建索引的三种方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#9创建索引的三种方式)  


在执行CREATE TABLE时创建索引

```
CREATE TABLE `employee` (
  `id` int(11) NOT NULL,
  `name` varchar(255) DEFAULT NULL,
  `age` int(11) DEFAULT NULL,
  `date` datetime DEFAULT NULL,
  `sex` int(1) DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `idx_name` (`name`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

使用ALTER TABLE命令添加索引

```
ALTER TABLE table_name ADD INDEX index_name (column);
```

使用CREATE INDEX命令创建

```
CREATE INDEX index_name ON table_name (column);
```


### [10、为什么官方建议使用自增长主键作为索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#10为什么官方建议使用自增长主键作为索引)  


结合B+Tree的特点，自增主键是连续的，在插入过程中尽量减少页分裂，即使要进行页分裂，也只会分裂很少一部分。并且能减少数据的移动，每次插入都是插入到最后。总之就是减少分裂和移动的频率。

插入连续的数据：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0814/04/img_8.png#alt=img%5C_8.png)

插入非连续的数据

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0814/04/img_9.png#alt=img%5C_9.png)


### [11、怎么创建索引的，有什么好处，有哪些分类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#11怎么创建索引的有什么好处有哪些分类)  

### [12、日常工作中你是怎么优化SQL的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#12日常工作中你是怎么优化sql的)  

### [13、MySQL中有哪些不同的表格？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#13mysql中有哪些不同的表格)  

### [14、索引不适合哪些场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#14索引不适合哪些场景)  

### [15、如何优化长难的查询语句？有实战过吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#15如何优化长难的查询语句有实战过吗)  

### [16、SQL语言包括哪几部分？每部分都有哪些操作关键字？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#16sql语言包括哪几部分每部分都有哪些操作关键字)  

### [17、说说对SQL语句优化有哪些方法？（选择几条）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#17说说对sql语句优化有哪些方法选择几条)  

### [18、为什么要使用视图？什么是视图？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#18为什么要使用视图什么是视图)  

### [19、简单描述MySQL中，索引，主键，唯一索引，联合索引的区别，对数据库的性能有什么影响（从读写两方面）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#19简单描述mysql中索引主键唯一索引联合索引的区别对数据库的性能有什么影响从读写两方面)  

### [20、100.MySQL一条SQL加锁分析](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#20100mysql一条sql加锁分析)  

### [21、组合索引是什么？为什么需要注意组合索引中的顺序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#21组合索引是什么为什么需要注意组合索引中的顺序)  

### [22、百万级别或以上的数据如何删除](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#22百万级别或以上的数据如何删除)  

### [23、MySQL如何优化DISTINCT？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#23mysql如何优化distinct)  

### [24、覆盖索引是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#24覆盖索引是什么)  

### [25、优化数据库的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#25优化数据库的方法)  

### [26、数据库存储日期格式时，如何考虑时区转换问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#26数据库存储日期格式时如何考虑时区转换问题)  

### [27、select for update有什么含义，会锁表还是锁行还是其他。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#27select-for-update有什么含义会锁表还是锁行还是其他。)  

### [28、存储引擎选择](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#28存储引擎选择)  

### [29、InnoDB与MyISAM的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#29innodb与myisam的区别)  

### [30、对于关系型数据库而言，索引是相当重要的概念，请回答有关索引的几个问题：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题带答案（2021年MySQL面试题及答案大汇总）.md#30对于关系型数据库而言索引是相当重要的概念请回答有关索引的几个问题：)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
