# Oracle面试题带答案（2021年Oracle面试题及答案大汇总）

Oracle面试题及答案【最新版】Oracle高级面试题大全(2021版)，发现网上很多Oracle面试题及答案整理都没有答案，所以花了很长时间搜集，本套Oracle面试题大全，Oracle面试题大汇总，有大量经典的Oracle面试题以及答案，包含Oracle语言常见面试题、Oracle工程师高级面试题及一些大厂Oracle开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Oracle面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Oracle面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、如何增加buffer cache的命中率？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#1如何增加buffer-cache的命中率)  


在数据库较繁忙时，适用buffer cache advisory 工具，查询v$db_cache_advice.如果有必要更改，可以使用 alter system set db_cache_size 命令


### [2、比较truncate和delete 命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#2比较truncate和delete-命令)  


两者都可以用来删除表中所有的记录。区别在于：truncate是DDL操作，它移动HWK，不需要rollback segment .而Delete是DML操作, 需要rollback segment 且花费较长时间.


### [3、Coalescing做了什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#3coalescing做了什么)  


Coalescing针对于字典管理的tablespace进行碎片整理，将临近的小extents合并成单个的大extent.


### [4、解释什么是死锁，如何解决Oracle中的死锁？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#4解释什么是死锁如何解决oracle中的死锁)  


简言之就是存在加了锁而没有解锁，可能是使用锁没有提交或者回滚事务，如果是表级锁则不能操作表，客户端处于等在状态，如果是行级锁则不能操作锁定行

**解决办法：**

**1、** 查找出被锁的表

**1、** select b.owner,b.object_name,a.session_id,a.locked_mode

**2、** from v$locked_object a,dba_objects b

**3、** where b.object_id = a.object_id;

**1、** select b.username,b.sid,b.serial#,logon_time

**2、** from v$$locked_object a,v$$session b

**3、** where a.session_id = b.sid order by b.logon_time;

**2、** 杀进程中的会话

alter system kill session "sid,serial#";


### [5、哪个VIEW用来检查数据文件的大小？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#5哪个view用来检查数据文件的大小)  


DBA_DATA_FILES


### [6、事务的特性（ACID）是指什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#6事务的特性acid是指什么)  


**1、** 原子性（Atomic）： 事务中的各项操作，要么全做要么全不做，任何一项操作的失败都会导致整个事务的失败。

**2、** 一致性（Consistent）： 事务结束后系统状态是一样的。

**3、** 隔离性（Isolated）: 并发执行的事务彼此无法看到对方的中间状态。

**4、** 持久性（Durable）:事务完成后，即使发生灾难性故障，通过日志和同步备份可以在故障发生后重建数据。


### [7、使用索引的理由](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#7使用索引的理由)  


快速访问表中的data block


### [8、存储过程的操作 当它抛出异常的时候 你是如何解决的用了什么技术](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#8存储过程的操作-当它抛出异常的时候-你是如何解决的用了什么技术)  


**1、** 中止当前语句执行，转到exception语句块执行。

**2、** 在异常处理时，捕获相应异常，并执行对应解决方案语句。


### [9、说明你可以将FMX转换或反向回到FMB文件吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#9说明你可以将fmx转换或反向回到fmb文件吗)  


不，不可能将FMX转换或反向回到FMB文件，以确保它们不会丢失。


### [10、举出两个判断DDL改动的方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#10举出两个判断ddl改动的方法)  


你可以使用 Logminer 或 Streams


### [11、Oracle的游标在存储过程里是放在begin与end的里面还是外面？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#11oracle的游标在存储过程里是放在begin与end的里面还是外面)  

### [12、提到一个项目的“验证LOV”属性?提到lov和list项目有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#12提到一个项目的“验证lov属性提到lov和list项目有什么区别)  

### [13、如何生成explain plan?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#13如何生成explain-plan)  

### [14、如何转换init.ora到spfile?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#14如何转换initora到spfile)  

### [15、说说Oracle中经常使用到的函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#15说说oracle中经常使用到的函数)  

### [16、说一下，Oracle的分区有几种](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#16说一下oracle的分区有几种)  

### [17、解释$$ORACLE_HOME和$$ORACLE_BASE的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#17解释$$oracle_home和$$oracle_base的区别)  

### [18、给出数据库正常启动所经历的几种状态 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#18给出数据库正常启动所经历的几种状态-)  

### [19、ORA-01555的应对方法?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#19ora-01555的应对方法)  

### [20、ORA-01555的应对方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#20ora-01555的应对方法)  

### [21、简述oracle中 dml、ddl、dcl的使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#21简述oracle中-dmlddldcl的使用)  

### [22、TEMPORARY tablespace和PERMANENT tablespace 的区别是？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#22temporary-tablespace和permanent-tablespace-的区别是)  

### [23、给出两个检查表结构的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#23给出两个检查表结构的方法)  

### [24、你必须利用备份恢复数据库，但是你没有控制文件，该如何解决问题呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#24你必须利用备份恢复数据库但是你没有控制文件该如何解决问题呢)  

### [25、举出3种可以收集three advisory statistics](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#25举出3种可以收集three-advisory-statistics)  

### [26、如何重构索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#26如何重构索引)  

### [27、你必须利用备份恢复数据库，但是你没有控制文件，该如何解决问题呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题带答案（2021年Oracle面试题及答案大汇总）.md#27你必须利用备份恢复数据库但是你没有控制文件该如何解决问题呢)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
