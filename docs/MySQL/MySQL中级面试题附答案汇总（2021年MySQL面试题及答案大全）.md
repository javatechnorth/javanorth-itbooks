# MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、B+树在满足聚簇索引和覆盖索引的时候不需要回表查询数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#1b+树在满足聚簇索引和覆盖索引的时候不需要回表查询数据)  



> - 在B+树的索引中，叶子节点可能存储了当前的key值，也可能存储了当前的key值以及整行的数据，这就是聚簇索引和非聚簇索引。 在InnoDB中，只有主键索引是聚簇索引，如果没有主键，则挑选一个唯一键建立聚簇索引。如果没有唯一键，则隐式的生成一个键来建立聚簇索引。
> - 当查询使用聚簇索引时，在对应的叶子节点，可以获取到整行数据，因此不用再次进行回表查询。




### [2、MySQL数据库cpu飙升到500%的话他怎么处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#2mysql数据库cpu飙升到500%的话他怎么处理)  


**1、** 当 cpu 飙升到 500%时，先用操作系统命令 top 命令观察是不是 MySQLd 占用导致的，如果不是，找出占用高的进程，并进行相关处理。

**2、** 如果是 MySQLd 造成的， show processlist，看看里面跑的 session 情况，是不是有消耗资源的 sql 在运行。找出消耗高的 sql，看看执行计划是否准确， index 是否缺失，或者实在是数据量太大造成。

**3、** 一般来说，肯定要 kill 掉这些线程(同时观察 cpu 使用率是否下降)，等进行相应的调整(比如说加索引、改 sql、改内存参数)之后，再重新跑这些 SQL。

**4、** 也有可能是每个 sql 消耗资源并不多，但是突然之间，有大量的 session 连进来导致 cpu 飙升，这种情况就需要跟应用一起来分析为何连接数会激增，再做出相应的调整，比如说限制连接数等


### [3、谈谈MySQL的Explain](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#3谈谈mysql的explain)  


Explain 执行计划包含字段信息如下：分别是 id、select_type、table、partitions、type、possible_keys、key、key_len、ref、rows、filtered、Extra 等12个字段。

我们重点关注的是type，它的属性排序如下：

```
system  > const > eq_ref > ref  > ref_or_null >
index_merge > unique_subquery > index_subquery >
range > index > ALL
```

推荐大家看这篇文章哈： [面试官：不会看 Explain执行计划，简历敢写 SQL 优化？](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzIwOTE2MzU4NA%3D%3D%26mid%3D2247484319%26idx%3D1%26sn%3D17c98e757c24a853374cb7e06c9c9302%26chksm%3D977947b0a00ecea66f3971c723cd844158a24c6c602c22c562223f6932b5b7ad1eee8b700255%26token%3D1596384379%26lang%3Dzh_CN%23rd)


### [4、MyISAM表格将在哪里存储，并且还提供其存储格式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#4myisam表格将在哪里存储并且还提供其存储格式)  


**每个MyISAM表格以三种格式存储在磁盘上：**

**1、** ·“.frm”文件存储表定义

**2、** ·数据文件具有“.MYD”（MYData）扩展名

**3、** 索引文件具有“.MYI”（MYIndex）扩展名


### [5、什么是基本表？什么是视图？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#5什么是基本表什么是视图)  


基本表是本身独立存在的表，在 SQL 中一个关系就对应一个表。 视图是从一个或几个基本表导出的表。视图本身不独立存储在数据库中，是一个虚表


### [6、什么是数据库事务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#6什么是数据库事务)  


数据库事务（简称：事务），是数据库管理系统执行过程中的一个逻辑单位，由一个有限的数据库操作序列构成，这些操作要么全部执行,要么全部不执行，是一个不可分割的工作单位。


### [7、B+Tree的页子节点都可以存放哪些东西？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#7b+tree的页子节点都可以存放哪些东西)  


innoDB的B+Tree可能存储的是整行数据，也有可能是主键的值。


### [8、BLOB和TEXT有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#8blob和text有什么区别)  


BLOB是一个二进制对象，可以容纳可变数量的数据。TEXT是一个不区分大小写的BLOB。

BLOB和TEXT类型之间的唯一区别在于对BLOB值进行排序和比较时区分大小写，对TEXT值不区分大小写。


### [9、覆盖索引、回表等这些，了解过吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#9覆盖索引回表等这些了解过吗)  


**1、** 覆盖索引： 查询列要被所建的索引覆盖，不必从数据表中读取，换句话说查询列要被所使用的索引覆盖。

**2、** 回表：二级索引无法直接查询所有列的数据，所以通过二级索引查询到聚簇索引后，再查询到想要的数据，这种通过二级索引查询出来的过程，就叫做回表。

网上这篇文章讲得很清晰：

[MySQL覆盖索引与回表](https://www.jianshu.com/p/8991cbca3854)


### [10、非主键索引一定会查询多次吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#10非主键索引一定会查询多次吗)  


不一定的？因为通过覆盖索引也可以只查询一次。


### [11、索引有哪些优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#11索引有哪些优缺点)  

### [12、为什么要使用视图？什么是视图？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#12为什么要使用视图什么是视图)  

### [13、MySQL如何获取当前日期？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#13mysql如何获取当前日期)  

### [14、试述视图的优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#14试述视图的优点)  

### [15、列的字符串类型可以是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#15列的字符串类型可以是什么)  

### [16、隔离级别与锁的关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#16隔离级别与锁的关系)  

### [17、什么是触发器？触发器的使用场景有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#17什么是触发器触发器的使用场景有哪些)  

### [18、什么是存储过程？有哪些优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#18什么是存储过程有哪些优缺点)  

### [19、优化器的执行过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#19优化器的执行过程)  

### [20、索引的底层实现](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#20索引的底层实现)  

### [21、MySQL 分页](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#21mysql-分页)  

### [22、创建索引有什么原则呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#22创建索引有什么原则呢)  

### [23、什么是锁？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#23什么是锁)  

### [24、索引的数据结构（b树，hash）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#24索引的数据结构b树hash)  

### [25、聚集索引与非聚集索引的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#25聚集索引与非聚集索引的区别)  

### [26、超键、候选键、主键、外键分别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#26超键候选键主键外键分别是什么)  

### [27、如果要存储用户的密码散列，应该使用什么字段进行存储？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#27如果要存储用户的密码散列应该使用什么字段进行存储)  

### [28、什么是通用SQL函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#28什么是通用sql函数)  

### [29、MySQL里记录货币用什么字段类型好](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#29mysql里记录货币用什么字段类型好)  

### [30、MySQL数据库cpu飙升的话，要怎么处理呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题附答案汇总（2021年MySQL面试题及答案大全）.md#30mysql数据库cpu飙升的话要怎么处理呢)  





