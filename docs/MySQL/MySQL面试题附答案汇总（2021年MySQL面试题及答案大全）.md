# MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、使用悲观锁](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#1使用悲观锁)  


悲观锁思想就是，当前线程要进来修改数据时，别的线程都得拒之门外~ 比如，可以使用select…for update ~

```
select * from User where name=‘jay’ for update
```

以上这条sql语句会锁定了User表中所有符合检索条件（name=‘jay’）的记录。本次事务提交之前，别的线程都无法修改这些记录。


### [2、一个6亿的表a，一个3亿的表b，通过外间tid关联，你如何最快的查询出满足条件的第50000到第50200中的这200条数据记录。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#2一个6亿的表a一个3亿的表b通过外间tid关联你如何最快的查询出满足条件的第50000到第50200中的这200条数据记录。)  


**1、** 如果A表TID是自增长,并且是连续的,B表的ID为索引

select * from a,b where a.tid = b.id and a.tid>500000 limit 200;

**2、** 如果A表的TID不是连续的,那么就需要使用覆盖索引.TID要么是主键,要么是辅助索引,B表ID也需要有索引。

select * from b , (select tid from a limit 50000,200) a where b.id = a .tid;


### [3、覆盖索引、回表等这些，了解过吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#3覆盖索引回表等这些了解过吗)  


覆盖索引： 查询列要被所建的索引覆盖，不必从数据表中读取，换句话说查询列要被所使用的索引覆盖。

回表：二级索引无法直接查询所有列的数据，所以通过二级索引查询到聚簇索引后，再查询到想要的数据，这种通过二级索引查询出来的过程，就叫做回表。

网上这篇文章讲得很清晰： [MySQL覆盖索引与回表](https://link.zhihu.com/?target=https%3A//www.jianshu.com/p/8991cbca3854)


### [4、索引能干什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#4索引能干什么)  


索引非常关键，尤其是当表中的数据量越来越大时，索引对于性能的影响愈发重要。 索引能够轻易将查询性能提高好几个数量级，总的来说就是可以明显的提高查询效率。


### [5、为什么要尽量设定一个主键？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#5为什么要尽量设定一个主键)  


主键是数据库确保数据行在整张表唯一性的保障，即使业务上本张表没有主键，也建议添加一个自增长的ID列作为主键。设定了主键之后，在后续的删改查的时候可能更加快速以及确保操作数据范围安全。


### [6、数据库三大范式是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#6数据库三大范式是什么)  


第一范式：每个列都不可以再拆分。

第二范式：在第一范式的基础上，非主键列完全依赖于主键，而不能是依赖于主键的一部分。

第三范式：在第二范式的基础上，非主键列只依赖于主键，不依赖于其他非主键。

在设计数据库结构的时候，要尽量遵守三范式，如果不遵守，必须有足够的理由。比如性能。事实上我们经常会为了性能而妥协数据库的设计。


### [7、MySQL的binlog有有几种录入格式？分别有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#7mysql的binlog有有几种录入格式分别有什么区别)  


有三种格式，statement，row和mixed。

**1、** statement模式下，每一条会修改数据的sql都会记录在binlog中。不需要记录每一行的变化，减少了binlog日志量，节约了IO，提高性能。由于sql的执行是有上下文的，因此在保存的时候需要保存相关的信息，同时还有一些使用了函数之类的语句无法被记录复制。

**2、** row级别下，不记录sql语句上下文相关信息，仅保存哪条记录被修改。记录单元为每一行的改动，基本是可以全部记下来但是由于很多操作，会导致大量行的改动(比如alter table)，因此这种模式的文件保存的信息太多，日志量太大。

**3、** mixed，一种折中的方案，普通操作使用statement记录，当无法使用statement的时候使用row。

此外，新版的MySQL中对row级别也做了一些优化，当表结构发生变化的时候，会记录语句而不是逐行记录


### [8、MySQL为什么这么设计](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#8mysql为什么这么设计)  


对大多数应用没有意义，只是规定一些工具用来显示字符的个数；int(1)和int(20)存储和计算均一样；


### [9、主键使用自增ID还是UUID，为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#9主键使用自增id还是uuid为什么)  


如果是单机的话，选择自增ID；如果是分布式系统，优先考虑UUID吧，但还是最好自己公司有一套分布式唯一ID生产方案吧。

**1、** 自增ID：数据存储空间小，查询效率高。但是如果数据量过大,会超出自增长的值范围，多库合并，也有可能有问题。

**2、** uuid：适合大量数据的插入和更新操作，但是它无序的，插入数据效率慢，占用空间大。


### [10、索引使用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#10索引使用场景)  


**1、** 当数据多且字段值有相同的值得时候用普通索引。

**2、** 当字段多且字段值没有重复的时候用唯一索引。

**3、** 当有多个字段名都经常被查询的话用复合索引。

**4、** 普通索引不支持空值，唯一索引支持空值。

**5、** 但是，若是这张表增删改多而查询较少的话，就不要创建索引了，因为如果你给一列创建了索引，那么对该列进行增删改的时候，都会先访问这一列的索引，

**6、** 若是增，则在这一列的索引内以新填入的这个字段名的值为名创建索引的子集，

**7、** 若是改，则会把原来的删掉，再添入一个以这个字段名的新值为名创建索引的子集，

**8、** 若是删，则会把索引中以这个字段为名的索引的子集删掉。

**9、** 所以，会对增删改的执行减缓速度，

**10、**  所以，若是这张表增删改多而查询较少的话，就不要创建索引了。

**11、**  更新太频繁地字段不适合创建索引。

**12、**  不会出现在where条件中的字段不该建立索引。


### [11、MySQL存储引擎MyISAM与InnoDB区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#11mysql存储引擎myisam与innodb区别)  

### [12、如何定位及优化SQL语句的性能问题？创建的索引有没有被使用到?或者说怎么才可以知道这条语句运行很慢的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#12如何定位及优化sql语句的性能问题创建的索引有没有被使用到或者说怎么才可以知道这条语句运行很慢的原因)  

### [13、MySQL数据库作发布系统的存储，一天五万条以上的增量，预计运维三年,怎么优化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#13mysql数据库作发布系统的存储一天五万条以上的增量预计运维三年,怎么优化)  

### [14、MySQL中InnoDB支持的四种事务隔离级别名称，以及逐级之间的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#14mysql中innodb支持的四种事务隔离级别名称以及逐级之间的区别)  

### [15、什么是通用SQL函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#15什么是通用sql函数)  

### [16、数据库自增主键可能遇到什么问题。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#16数据库自增主键可能遇到什么问题。)  

### [17、优化LIMIT分页](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#17优化limit分页)  

### [18、数据库结构优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#18数据库结构优化)  

### [19、视图的缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#19视图的缺点)  

### [20、使用乐观锁](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#20使用乐观锁)  

### [21、varchar(50)中50的涵义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#21varchar50中50的涵义)  

### [22、InnoDB引擎中的索引策略，了解过吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#22innodb引擎中的索引策略了解过吗)  

### [23、Innodb的事务与日志的实现方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#23innodb的事务与日志的实现方式)  

### [24、什么是SQL？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#24什么是sql)  

### [25、MySQL自增主键用完了怎么办？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#25mysql自增主键用完了怎么办)  

### [26、MySQL有哪些数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#26mysql有哪些数据类型)  

### [27、为什么要优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#27为什么要优化)  

### [28、MySQL中有哪些不同的表格？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#28mysql中有哪些不同的表格)  

### [29、优化UNION查询](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#29优化union查询)  

### [30、视图有哪些特点？哪些使用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案汇总（2021年MySQL面试题及答案大全）.md#30视图有哪些特点哪些使用场景)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
