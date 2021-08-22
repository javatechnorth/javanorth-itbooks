# Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）

Oracle面试题及答案【最新版】Oracle高级面试题大全(2021版)，发现网上很多Oracle面试题及答案整理都没有答案，所以花了很长时间搜集，本套Oracle面试题大全，Oracle面试题大汇总，有大量经典的Oracle面试题以及答案，包含Oracle语言常见面试题、Oracle工程师高级面试题及一些大厂Oracle开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Oracle面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Oracle面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、描述tablespace和datafile之间的关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#1描述tablespace和datafile之间的关系)  


一个tablespace可以有一个或多个datafile，每个datafile只能在一个tablespace内，table中的数据,通过hash算法分布在tablespace中的各个datafile中，tablespace是逻辑上的概念,datafile则在物理上储存了数据库的种种对象。


### [2、说下 Oracle的导入导出有几种方式，有何区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#2说下-oracle的导入导出有几种方式有何区别)  


**1、** 使用oracle工具 exp/imp

**2、** 使用plsql相关工具

方法1、导入/导出的是二进制的数据，

方法2、.plsql导入/导出的是sql语句的文本文件


### [3、如何生成explain plan?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#3如何生成explain-plan)  


运行utlxplan.sql. 建立plan 表

针对特定SQL语句，使用 explain plan set statement_id = 'tst1' into plan_table运行utlxplp.sql 或 utlxpls.sql察看explain plan


### [4、ORA-01555的应对方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#4ora-01555的应对方法)  


具体的出错信息是snapshot too old within rollback seg , 通常可以通过增大rollback seg来解决问题。当然也需要察看一下具体造成错误的SQL文本


### [5、oracle的锁又几种,定义分别是什么;](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#5oracle的锁又几种,定义分别是什么;)  


**1、**  行共享锁 (ROW SHARE)

**2、**  行排他锁(ROW EXCLUSIVE)

**3、** 共享锁(SHARE)

**4、**  共享行排他锁(SHARE ROW EXCLUSIVE)

**5、**  排他锁(EXCLUSIVE)

**使用方法：**

```
SELECT * FROM order_master WHERE vencode="V002" 
FOR UPDATE WAIT 5; 
LOCK TABLE order_master IN SHARE MODE; 
LOCK TABLE itemfile IN EXCLUSIVE MODE NOWAIT;
```

**ORACLE锁具体分为以下几类：**

**1、** 按用户与系统划分，可以分为自动锁与显示锁

自动锁：当进行一项数据库操作时，缺省情况下，系统自动为此数据库操作获得所有有必要的锁。

显示锁：某些情况下，需要用户显示的锁定数据库操作要用到的数据，才能使数据库操作执行得更好，显示锁是用户为数据库对象设定的。

**2、** 按锁级别划分，可分为共享锁与排它锁

**共享锁：**

共享锁使一个事务对特定数据库资源进行共享访问——另一事务也可对此资源进行访问或获得相同共享锁。共享锁为事务提供高并发性，但如拙劣的事务设计+共享锁容易造成死锁或数据更新丢失。

**排它锁：**

事务设置排它锁后，该事务单独获得此资源，另一事务不能在此事务提交之前获得相同对象的共享锁或排它锁。

**3、** 按操作划分，可分为DML锁、DDL锁

DML锁又可以分为，行锁、表锁、死锁

**行锁：**

当事务执行数据库插入、更新、删除操作时，该事务自动获得操作表中操作行的排它锁。

**表级锁：**

当事务获得行锁后，此事务也将自动获得该行的表锁(共享锁),以防止其它事务进行DDL语句影响记录行的更新。事务也可以在进行过程中获得共享

锁或排它锁，只有当事务显示使用LOCK TABLE语句显示的定义一个排它锁时，事务才会获得表上的排它锁,也可使用LOCK TABLE显示的定义一个表级的共享锁(LOCK TABLE具体用法请参考相关文档)。

**死锁：**

当两个事务需要一组有冲突的锁，而不能将事务继续下去的话，就出现死锁。

如事务1在表A行记录#3中有一排它锁，并等待事务2在表A中记录#4中排它锁的释放，而事务2在表A记录行#4中有一排它锁，并等待事务; 1在表A中记录#3中排它锁的释放，事务1与事务2彼此等待，因此就造成了死锁。死锁一般是因拙劣的事务设计而产生。死锁只能使用SQL下:alter system kill session "sid,serial#"；或者使用相关操作系统kill进程的命令，如UNIX下kill -9 sid,或者使用其它工具杀掉死锁进程。

**DDL锁又可以分为：**

排它DDL锁、共享DDL锁、分析锁

**排它DDL锁：**

创建、修改、删除一个数据库对象的DDL语句获得操作对象的 排它锁。如使用alter table语句时，为了维护数据的完成性、一致性、合法性，该事务获得一排它DDL锁。

共享DDL锁：需在数据库对象之间建立相互依赖关系的DDL语句通常需共享获得DDL锁。

如创建一个包，该包中的过程与函数引用了不同的数据库表，当编译此包时，该事务就获得了引用表的共享DDL锁。

**分析锁：**

ORACLE使用共享池存储分析与优化过的SQL语句及PL/SQL程序，使运行相同语句的应用速度更快。一个在共享池中缓存的对象获得它所引用数据库对象的分析锁。分析锁是一种独特的DDL锁类型，ORACLE使用它追踪共享池对象及它所引用数据库对象之间的依赖关系。当一个事务修改或删除了共享池持有分析锁的数据库对象时，ORACLE使共享池中的对象作废，下次在引用这条SQL/PLSQL语句时，ORACLE重新分析编译此语句。

**4.内部闩锁**

内部闩锁：这是ORACLE中的一种特殊锁，用于顺序访问内部系统结构。当事务需向缓冲区写入信息时，为了使用此块内存区域，ORACLE首先必须取得这块内存区域的闩锁，才能向此块内存写入信息。



### [6、解释TABLE Function的用途](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#6解释table-function的用途)  


TABLE Function是通过PL/SQL逻辑返回一组纪录，用于普通的表/视图。他们也用于pipeline和ETL过程。


### [7、说明如何在指定的块中迭代项目和记录?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#7说明如何在指定的块中迭代项目和记录)  


要遍历指定块中的项目和记录，可以使用NEXT_FIELD来迭代特定块中的项，并且NEXT_RECORD遍历块中的记录。


### [8、解释归档和非归档模式之间的不同和它们各自的优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#8解释归档和非归档模式之间的不同和它们各自的优缺点)  


归档模式是指你可以备份所有的数据库 transactions并恢复到任意一个时间点。非归档模式则相反，不能恢复到任意一个时间点。但是非归档模式可以带来数据库性能上的少许提高.


### [9、解释data block , extent 和 segment的区别（这里建议用英文术语）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#9解释data-block-,-extent-和-segment的区别这里建议用英文术语)  


data block是数据库中最小的逻辑存储单元。当数据库的对象需要更多的物理存储空间时，连续的data block就组成了extent . 一

个数据库对象拥有的所有extents被称为该对象的segment.


### [10、Oracle 分区在什么情况下使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#10oracle-分区在什么情况下使用)  


当一张表的数据量到达上亿行的时候，表的性能会严重降低，这个时候就需要用到分区了，通过划分成多个小表，并在每个小表上建立本地索引可以大大缩小索引数据文件的大小，从而更快的定位到目标数据来提升访问性能。

分区除了可以用来提升访问性能外，还因为可以指定分区所使用的表空间，因此也用来做数据的生命周期管理。当前需要频繁使用的活跃数据可以放到访问速度更快但价格也更贵的存储设备上，而2、3年前的历史数据，或者叫冷数据可以放到更廉价、速度更低的设备上。从而降低存储费用。


### [11、解释什么是Oracle Forms?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#11解释什么是oracle-forms)  

### [12、解释什么是死锁，如何解决Oracle中的死锁？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#12解释什么是死锁如何解决oracle中的死锁)  

### [13、提及11g版本2中Oracle Forms Services中引入的新功能是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#13提及11g版本2中oracle-forms-services中引入的新功能是什么)  

### [14、如何加密PL/SQL程序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#14如何加密pl/sql程序)  

### [15、pctused and pctfree 表示什么含义有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#15pctused-and-pctfree-表示什么含义有什么作用)  

### [16、truncate和delete区别：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#16truncate和delete区别：)  

### [17、解释GLOBAL_NAMES设为TRUE的用途？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#17解释global_names设为true的用途)  

### [18、说下 怎样创建一个视图,视图的好处, 视图可以控制权限吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#18说下-怎样创建一个视图,视图的好处,-视图可以控制权限吗)  

### [19、解释data block , extent 和 segment的区别（这里建议用英文术语）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#19解释data-block-,-extent-和-segment的区别这里建议用英文术语)  

### [20、Oracle跟SQL Server 2005的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#20oracle跟sql-server-2005的区别)  

### [21、索引是用来干什么的？有那些约束建立索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#21索引是用来干什么的有那些约束建立索引)  

### [22、如何建立一个备份控制文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#22如何建立一个备份控制文件)  

### [23、哪个column可以用来区别V$$视图和GV$$视图?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#23哪个column可以用来区别v$$视图和gv$$视图)  

### [24、本地管理表空间和字典管理表空间的特点，ASSM有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#24本地管理表空间和字典管理表空间的特点assm有什么特点)  

### [25、创建用户时，需要赋予新用户什么权限才能使它联上数据库。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#25创建用户时需要赋予新用户什么权限才能使它联上数据库。)  

### [26、给出两种相关约束?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#26给出两种相关约束)  

### [27、数据库的三大范式是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle中级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#27数据库的三大范式是什么)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
