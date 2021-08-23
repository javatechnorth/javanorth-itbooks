# MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、SQL的生命周期？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#1sql的生命周期)  


**1、** 应用服务器与数据库服务器建立一个连接

**2、** 数据库进程拿到请求sql

**3、** 解析并生成执行计划，执行

**4、** 读取数据到内存并进行逻辑处理

**5、** 通过步骤一的连接，发送结果到客户端

**6、** 关掉连接，释放资源

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/049/50/99_8.png#alt=99%5C_8.png)


### [2、索引有哪几种类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#2索引有哪几种类型)  


**主键索引:** 数据列不允许重复，不允许为NULL，一个表只能有一个主键。

**唯一索引:** 数据列不允许重复，允许为NULL值，一个表允许多个列创建唯一索引。

**1、** 可以通过 `ALTER TABLE table_name ADD UNIQUE (column);` 创建唯一索引

**2、** 可以通过 `ALTER TABLE table_name ADD UNIQUE (column1,column2);` 创建唯一组合索引

**普通索引:** 基本的索引类型，没有唯一性的限制，允许为NULL值。

**1、** 可以通过`ALTER TABLE table_name ADD INDEX index_name (column);`创建普通索引

**2、** 可以通过`ALTER TABLE table_name ADD INDEX index_name(column1, column2, column3);`创建组合索引

**全文索引：** 是目前搜索引擎使用的一种关键技术。

可以通过`ALTER TABLE table_name ADD FULLTEXT (column);`创建全文索引


### [3、前缀索引](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#3前缀索引)  


**1、** 语法：`index(field(10))`，使用字段值的前10个字符建立索引，默认是使用字段的全部内容建立索引。

**2、** 前提：前缀的标识度高。比如密码就适合建立前缀索引，因为密码几乎各不相同。

**3、** 实操的难度：在于前缀截取的长度。

**4、** 我们可以利用`select count(*)/count(distinct left(password,prefixLen));`，通过从调整`prefixLen`的值（从1自增）查看不同前缀长度的一个平均匹配度，接近1时就可以了（表示一个密码的前`prefixLen`个字符几乎能确定唯一一条记录）


### [4、MyISAM表格将在哪里存储，并且还提供其存储格式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#4myisam表格将在哪里存储并且还提供其存储格式)  


每个MyISAM表格以三种格式存储在磁盘上：

·“.frm”文件存储表定义

·数据文件具有“.MYD”（MYData）扩展名

索引文件具有“.MYI”（MYIndex）扩展名


### [5、联合索引是什么？为什么需要注意联合索引中的顺序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#5联合索引是什么为什么需要注意联合索引中的顺序)  


MySQL可以使用多个字段同时建立一个索引，叫做联合索引。在联合索引中，如果想要命中索引，需要按照建立索引时的字段顺序挨个使用，否则无法命中索引。

**具体原因为:**

MySQL使用索引时需要索引有序，假设现在建立了"name，age，school"的联合索引，那么索引的排序为: 先按照name排序，如果name相同，则按照age排序，如果age的值也相等，则按照school进行排序。

当进行查询时，此时索引仅仅按照name严格有序，因此必须首先使用name字段进行等值查询，之后对于匹配到的列而言，其按照age字段严格有序，此时可以使用age字段用做索引查找，以此类推。因此在建立联合索引的时候应该注意索引列的顺序，一般情况下，将查询需求频繁或者字段选择性高的列放在前面。此外可以根据特例的查询或者表结构进行单独的调整。


### [6、Myql中的事务回滚机制概述](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#6myql中的事务回滚机制概述)  


事务是用户定义的一个数据库操作序列，这些操作要么全做要么全不做，是一个不可分割的工作单位，事务回滚是指将该事务已经完成的对数据库的更新操作撤销。

要同时修改数据库中两个不同表时，如果它们不是一个事务的话，当第一个表修改完，可能第二个表修改过程中出现了异常而没能修改，此时就只有第二个表依旧是未修改之前的状态，而第一个表已经被修改完毕。而当你把它们设定为一个事务的时候，当第一个表修改完，第二表修改出现异常而没能修改，第一个表和第二个表都要回到未修改的状态，这就是所谓的事务回滚


### [7、MySQL中有哪几种锁，列举一下？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#7mysql中有哪几种锁列举一下)  


![](https://user-gold-cdn.xitu.io/2020/5/23/17240a13fa147bea?w=1280&h=687&f=png&s=248056#alt=)

**如果按锁粒度划分，有以下3种：**

**1、** 表锁： 开销小，加锁快；锁定力度大，发生锁冲突概率高，并发度最低;不会出现死锁。

**2、** 行锁： 开销大，加锁慢；会出现死锁；锁定粒度小，发生锁冲突的概率低，并发度高。

**3、** 页锁： 开销和加锁速度介于表锁和行锁之间；会出现死锁；锁定粒度介于表锁和行锁之间，并发度一般


### [8、limit 1000000 加载很慢的话，你是怎么解决的呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#8limit-1000000-加载很慢的话你是怎么解决的呢)  


**方案一：**如果id是连续的，可以这样，返回上次查询的最大记录(偏移量)，再往下limit

```
select id，name from employee where id>1000000 limit 10.
```

**方案二：**在业务允许的情况下限制页数：

建议跟业务讨论，有没有必要查这么后的分页啦。因为绝大多数用户都不会往后翻太多页。

**方案三：**order by + 索引（id为索引）

```
select id，name from employee order by id  limit 1000000，10
```

**方案四：**利用延迟关联或者子查询优化超多分页场景。（先快速定位需要获取的id段，然后再关联）

```
SELECT a.* FROM employee a, (select id from employee where 条件 LIMIT 1000000,10 ) b where a.id=b.id
```


### [9、MySQL中int(20)和char(20)以及varchar(20)的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#9mysql中int20和char20以及varchar20的区别)  


**1、** int(20) 表示字段是int类型，显示长度是 20

**2、** char(20)表示字段是固定长度字符串，长度为 20

**3、** varchar(20) 表示字段是可变长度字符串，长度为 20


### [10、什么是内连接、外连接、交叉连接、笛卡尔积呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#10什么是内连接外连接交叉连接笛卡尔积呢)  


**1、** 内连接（inner join）：取得两张表中满足存在连接匹配关系的记录。

**2、** 外连接（outer join）：取得两张表中满足存在连接匹配关系的记录，以及某张表（或两张表）中不满足匹配关系的记录。

**3、** 交叉连接（cross join）：显示两张表所有记录一一对应，没有匹配关系进行筛选，也被称为：笛卡尔积。


### [11、怎么查询SQL语句是否使用了索引查询？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#11怎么查询sql语句是否使用了索引查询)  

### [12、一条sql执行过长的时间，你如何优化，从哪些方面入手？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#12一条sql执行过长的时间你如何优化从哪些方面入手)  

### [13、备份计划，MySQLdump以及xtranbackup的实现原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#13备份计划mysqldump以及xtranbackup的实现原理)  

### [14、linux添加索引](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#14linux添加索引)  

### [15、列的字符串类型可以是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#15列的字符串类型可以是什么)  

### [16、如何显示前50行？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#16如何显示前50行)  

### [17、存储时期](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#17存储时期)  

### [18、六种关联查询](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#18六种关联查询)  

### [19、你是否做过主从一致性校验，如果有，怎么做的，如果没有，你打算怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#19你是否做过主从一致性校验如果有怎么做的如果没有你打算怎么做)  

### [20、什么是索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#20什么是索引)  

### [21、什么叫视图？游标是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#21什么叫视图游标是什么)  

### [22、什么是数据库连接池?为什么需要数据库连接池呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#22什么是数据库连接池为什么需要数据库连接池呢)  

### [23、谈谈MySQL的Explain](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#23谈谈mysql的explain)  

### [24、事物的四大特性(ACID)介绍一下?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#24事物的四大特性acid介绍一下)  

### [25、MySQL的复制原理以及流程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#25mysql的复制原理以及流程)  

### [26、MySQL中DATETIME和TIMESTAMP的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#26mysql中datetime和timestamp的区别)  

### [27、什么情况下设置了索引但无法使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#27什么情况下设置了索引但无法使用)  

### [28、count(1)、count(*) 与 count(列名) 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#28count1count*-与-count列名-的区别)  

### [29、索引算法有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL高级面试题大全带答案（2021年MySQL面试题及答案整理）.md#29索引算法有哪些)  





