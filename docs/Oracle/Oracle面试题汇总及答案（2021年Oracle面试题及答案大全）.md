# Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）

Oracle面试题及答案【最新版】Oracle高级面试题大全(2021版)，发现网上很多Oracle面试题及答案整理都没有答案，所以花了很长时间搜集，本套Oracle面试题大全，Oracle面试题大汇总，有大量经典的Oracle面试题以及答案，包含Oracle语言常见面试题、Oracle工程师高级面试题及一些大厂Oracle开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Oracle面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Oracle面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、存储过程 、函数 、游标 在项目中怎么用的：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#1存储过程-函数-游标-在项目中怎么用的：)  


**存储过程：**

**2、** 能够批量执行的一组SQL语句，且容易控制事务。但没有返回值，可以通过设置in out|out类型的参数返回结果

**3、** 存储过程可以没有参数,不需要返回值

**函数：**

与存储过程相似，函数可以没有参数,但是一定需要一个返回值

**游标：**

游标类似指针，游标可以执行多个不相关的操作.如果希望当产生了结果集后,对结果集中的数据进行多 种不相关的数据操作


### [2、如何搜集表的各种状态数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#2如何搜集表的各种状态数据)  


ANALYZE

The ANALYZE command.


### [3、如何在不影响子表的前提下，重建一个母表](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#3如何在不影响子表的前提下重建一个母表)  


子表的外键强制实效，重建母表，激活外键


### [4、触发器的作用有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#4触发器的作用有哪些)  


**1、** 触发器可通过数据库中的相关表实现级联更改；通过级联引用完整性约束可以更有效地执行这些更改。

**2、** 触发器可以强制比用 CHECK 约束定义的约束更为复杂的约束。与 CHECK 约束不同，触发器可以引用其它表中的列。例如，触发器可以使用另一个表中的 SELECT 比较插入或更新的数据，以及执行其它操作，如修改数据或显示用户定义错误信息。

**3、** 触发器还可以强制执行业务规则

**4、** 触发器也可以评估数据修改前后的表状态，并根据其差异采取对策。


### [5、FACT Table上需要建立何种索引?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#5fact-table上需要建立何种索引)  


位图索引 (bitmap index)


### [6、说下 oracle 中 dml、ddl、dcl 的使用有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#6说下-oracle-中-dmlddldcl-的使用有哪些)  


**1、** Dml 数据操纵语言，如select、update、delete，insert

**2、** Ddl 数据定义语言，如create table 、drop table 等等

**3、** Dcl 数据控制语言， 如 commit、 rollback、grant、 invoke等


### [7、如何建立一个备份控制文件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#7如何建立一个备份控制文件)  


Alter database backup control file to trace.


### [8、给出两个检查表结构的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#8给出两个检查表结构的方法)  


1.DESCRIBE命令

**2、** DBMS_METADATA.GET_DDL 包


### [9、Audit trace 存放在哪个oracle目录结构中?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#9audit-trace-存放在哪个oracle目录结构中)  


unix $ORACLE_HOME/rdbms/audit Windows the event viewer


### [10、使用存储过程访问数据库比直接用SQL语句访问有何优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#10使用存储过程访问数据库比直接用sql语句访问有何优点)  


**1、** 存储过程是预编译过的，执行时不须编译，执行速度更快。

**2、** 存储过程封装了多条SQL，便于维护数据的完整性与一致性。

**3、** 实现代码复用。


### [11、比较truncate和delete 命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#11比较truncate和delete-命令)  

### [12、解释冷备份和热备份的不同点以及各自的优点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#12解释冷备份和热备份的不同点以及各自的优点)  

### [13、Oralce怎样存储文件，能够存储哪些文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#13oralce怎样存储文件能够存储哪些文件)  

### [14、你刚刚编译了一个PL/SQL Package但是有错误报道，如何显示出错信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#14你刚刚编译了一个pl/sql-package但是有错误报道如何显示出错信息)  

### [15、说下，内连接，左连接，右连接的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#15说下内连接左连接右连接的区别)  

### [16、说一下，什么是Oracle分区](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#16说一下什么是oracle分区)  

### [17、如何定位重要(消耗资源多)的SQL](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#17如何定位重要消耗资源多的sql)  

### [18、说明如何使用相同的LOV 2列?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#18说明如何使用相同的lov-2列)  

### [19、如何增加buffer cache的命中率？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#19如何增加buffer-cache的命中率)  

### [20、哪个后台进程刷新materialized views?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#20哪个后台进程刷新materialized-views)  

### [21、解释冷备份和热备份的不同点以及各自的优点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#21解释冷备份和热备份的不同点以及各自的优点)  

### [22、说下 Oracle中有哪几种文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#22说下-oracle中有哪几种文件)  

### [23、解释CALL_FORM，NEW_FORM和OPEN_FORM之间有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#23解释call_formnew_form和open_form之间有什么区别)  

### [24、解释什么是Partitioning（分区）以及它的优点。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#24解释什么是partitioning分区以及它的优点。)  

### [25、给出在STAR SCHEMA中的两种表及它们分别含有的数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#25给出在star-schema中的两种表及它们分别含有的数据)  

### [26、如何转换init.ora到spfile?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#26如何转换initora到spfile)  

### [27、解释冷备份和热备份的不同点以及各自的优点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题汇总及答案（2021年Oracle面试题及答案大全）.md#27解释冷备份和热备份的不同点以及各自的优点)  





