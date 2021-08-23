# MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、有多少种日志](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#1有多少种日志)  


innodb两种日志redo和undo。


### [2、在高并发情况下，如何做到安全的修改同一行数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#2在高并发情况下如何做到安全的修改同一行数据)  


要安全的修改同一行数据，就要保证一个线程在修改时其它线程无法更新这行记录。一般有悲观锁和乐观锁两种方案~

**使用悲观锁**

悲观锁思想就是，当前线程要进来修改数据时，别的线程都得拒之门外~

比如，可以使用select…for update ~

```
select * from User where name=‘jay’ for update
```

以上这条sql语句会锁定了User表中所有符合检索条件（name=‘jay’）的记录。本次事务提交之前，别的线程都无法修改这些记录。

**使用乐观锁**

乐观锁思想就是，有线程过来，先放过去修改，如果看到别的线程没修改过，就可以修改成功，如果别的线程修改过，就修改失败或者重试。实现方式：乐观锁一般会使用版本号机制或CAS算法实现。


### [3、如果一个表有一列定义为TIMESTAMP，将发生什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#3如果一个表有一列定义为timestamp将发生什么)  


每当行被更改时，时间戳字段将获取当前时间戳。


### [4、MySQL中DATETIME和TIMESTAMP的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#4mysql中datetime和timestamp的区别)  


**存储精度都为秒**

**区别：**

**1、** DATETIME 的日期范围是 1001——9999 年；TIMESTAMP 的时间范围是 1970——2038 年

**2、** DATETIME 存储时间与时区无关；TIMESTAMP 存储时间与时区有关，显示的值也依赖于时区

**3、** DATETIME 的存储空间为 8 字节；TIMESTAMP 的存储空间为 4 字节

**4、** DATETIME 的默认值为 null；TIMESTAMP 的字段默认不为空(not null)，默认值为当前时间(CURRENT_TIMESTAMP)


### [5、大表数据查询，怎么优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#5大表数据查询怎么优化)  


**1、** 优化shema、sql语句+索引；

**2、** 第二加缓存，Memcached, Redis；

**3、** 主从复制，读写分离；

**4、** 垂直拆分，根据你模块的耦合度，将一个大的系统分为多个小的系统，也就是分布式系统；

**5、** 水平切分，针对数据量大的表，这一步最麻烦，最能考验技术水平，要选择一个合理的sharding key, 为了有好的查询效率，表结构也要改动，做一定的冗余，应用也要改，sql中尽量带sharding key，将数据定位到限定的表上去查，而不是扫描全部的表；


### [6、MyISAM索引与InnoDB索引的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#6myisam索引与innodb索引的区别)  


**1、** InnoDB索引是聚簇索引，MyISAM索引是非聚簇索引。

**2、** InnoDB的主键索引的叶子节点存储着行数据，因此主键索引非常高效。

**3、** MyISAM索引的叶子节点存储的是行数据地址，需要再寻址一次才能得到数据。

**4、** InnoDB非主键索引的叶子节点存储的是主键和其他带索引的列数据，因此查询时做到覆盖索引会非常高效。


### [7、MySQL中TEXT数据类型的最大长度](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#7mysql中text数据类型的最大长度)  


**1、** TINYTEXT：256 bytes

**2、** TEXT：65,535 bytes(64kb)

**3、** MEDIUMTEXT：16,777,215 bytes(16MB)

**4、** LONGTEXT：4,294,967,295 bytes(4GB)


### [8、MySQL中TEXT数据类型的最大长度](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#8mysql中text数据类型的最大长度)  


**1、** TINYTEXT：256 bytes

**2、** TEXT：65,535 bytes(64kb)

**3、** MEDIUMTEXT：16,777,215 bytes(16MB)

**4、** LONGTEXT：4,294,967,295 bytes(4GB)

**1、** 
### [9、limit 1000000 加载很慢的话，你是怎么解决的呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#9limit-1000000-加载很慢的话你是怎么解决的呢)  


**方案一：如果id是连续的，可以这样，返回上次查询的最大记录(偏移量)，再往下limit**

```
select id，name from employee where id>1000000 limit 10.
```

**方案二：在业务允许的情况下限制页数：**

建议跟业务讨论，有没有必要查这么后的分页啦。因为绝大多数用户都不会往后翻太多页。

**方案三：order by + 索引（id为索引）**

```
select id，name from employee order by id  limit 1000000，10
```

**方案四：利用延迟关联或者子查询优化超多分页场景。（先快速定位需要获取的id段，然后再关联）**

```
SELECT a.* FROM employee a, (select id from employee where 条件 LIMIT 1000000,10 ) b where a.id=b.id
```


### [10、drop、delete与truncate的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#10dropdelete与truncate的区别)  


三者都表示删除，但是三者有一些差别：

| 比较 | Delete | Truncate | Drop |
| --- | --- | --- | --- |
| 类型 | 属于DML | 属于DDL | 属于DDL |
| 回滚 | 可回滚 | 不可回滚 | 不可回滚 |
| 删除内容 | 表结构还在，删除表的全部或者一部分数据行 | 表结构还在，删除表中的所有数据 | 从数据库中删除表，所有的数据行，索引和权限也会被删除 |
| 删除速度 | 删除速度慢，需要逐行删除 | 删除速度快 | 删除速度最快 |


因此，在不再需要一张表的时候，用drop；在想删除部分数据行时候，用delete；在保留表而删除所有数据的时候用truncate。


### [11、优化关联查询](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#11优化关联查询)  

### [12、MySQL 索引使用有哪些注意事项呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#12mysql-索引使用有哪些注意事项呢)  

### [13、非聚簇索引一定会回表查询吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#13非聚簇索引一定会回表查询吗)  

### [14、innoDB的B+Tree 存储整行数据和主键的值得区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#14innodb的b+tree-存储整行数据和主键的值得区别)  

### [15、SQL语句主要分为哪几类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#15sql语句主要分为哪几类)  

### [16、Innodb的事务与日志的实现方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#16innodb的事务与日志的实现方式)  

### [17、创建索引时需要注意什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#17创建索引时需要注意什么)  

### [18、可以使用多少列创建索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#18可以使用多少列创建索引)  

### [19、什么是存储过程？用什么来调用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#19什么是存储过程用什么来调用)  

### [20、简述有哪些索引和作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#20简述有哪些索引和作用)  

### [21、使用索引查询一定能提高查询的性能吗？为什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#21使用索引查询一定能提高查询的性能吗为什么)  

### [22、列设置为AUTO INCREMENT时，如果在表中达到最大值，会发生什么情况？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#22列设置为auto-increment时如果在表中达到最大值会发生什么情况)  

### [23、你是如何监控你们的数据库的？你们的慢日志都是怎么查询的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#23你是如何监控你们的数据库的你们的慢日志都是怎么查询的)  

### [24、SQL注入漏洞产生的原因？如何防止？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#24sql注入漏洞产生的原因如何防止)  

### [25、说出一些数据库优化方面的经验?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#25说出一些数据库优化方面的经验)  

### [26、B树和B+树的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#26b树和b+树的区别)  

### [27、什么是幻读，脏读，不可重复读呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#27什么是幻读脏读不可重复读呢)  

### [28、数据库的乐观锁和悲观锁是什么？怎么实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#28数据库的乐观锁和悲观锁是什么怎么实现的)  

### [29、视图的优点，缺点，讲一下？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL中级面试题大全带答案（2021年MySQL面试题及答案整理）.md#29视图的优点缺点讲一下)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
