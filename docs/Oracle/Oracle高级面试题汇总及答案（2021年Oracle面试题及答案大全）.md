# Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）

Oracle面试题及答案【最新版】Oracle高级面试题大全(2021版)，发现网上很多Oracle面试题及答案整理都没有答案，所以花了很长时间搜集，本套Oracle面试题大全，Oracle面试题大汇总，有大量经典的Oracle面试题以及答案，包含Oracle语言常见面试题、Oracle工程师高级面试题及一些大厂Oracle开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Oracle面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Oracle面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、说下如何使用Oracle的游标？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#1说下如何使用oracle的游标)  


**1、** oracle中的游标分为显示游标和隐式游标

**2、** 显示游标是用cursor...is命令定义的游标，它可以对查询语句(select)返回的多条记录进行处理；隐式游标是在执行插入 (insert)、删除(delete)、修改(update)和返回单条记录的查询(select)语句时由PL/SQL自动定义的。

**3、** 显式游标的操作：打开游标、操作游标、关闭游标；PL/SQL隐式地打开SQL游标，并在它内部处理SQL语句，然后关闭它


### [2、FACT Table上需要建立何种索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#2fact-table上需要建立何种索引)  


位图索引 （bitmap index）


### [3、用于网络连接的2个文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#3用于网络连接的2个文件)  


TNSNAMES.ORA and SQLNET.ORA


### [4、给出两个检查表结构的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#4给出两个检查表结构的方法)  


**1、** DESCRIBE命令

**2、**  DBMS_METADATA.GET_DDL 包


### [5、当用户进程出错，哪个后台进程负责清理它](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#5当用户进程出错哪个后台进程负责清理它)  


PMON


### [6、解释Oracle表单服务组件包括什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#6解释oracle表单服务组件包括什么)  


Oracle表单包含：　　客户端：客户端发送HTTP请求　　窗口监听器Servlet：它启动，停止并与窗体运行进程通信　　表单运行过程：它执行特定表单应用程序中包含的代码　　数据库：从数据库中获取的数据


### [7、解释materialized views的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#7解释materialized-views的作用)  


Materialized views 用于减少那些汇总，集合和分组的信息的集合数量。它们通常适合于数据仓库和DSS系统。


### [8、可以从表单执行动态SQL吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#8可以从表单执行动态sql吗)  


是的，可以通过使用内置的FORMS_DDL或通过从表单调用DBNS_SQL数据库包从表单执行动态SQL。


### [9、列出Oracle Forms配置文件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#9列出oracle-forms配置文件)  


Oracle Forms配置文件包括：　　基本HTML文件(base.htm，basejini.htm，basejpi.htm和baseie.htm)　　ENV　　CFG　　CFG　　DEVLOBER


### [10、如何使用Oracle的游标？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#10如何使用oracle的游标)  


**1、** oracle中的游标分为显示游标和隐式游标

**2、** 显示游标是用cursor...is命令定义的游标，它可以对查询语句(select)返回的多条记录进行处理；隐式游标是在执行插入 (insert)、删除(delete)、修改(update)和返回单条记录的查询(select)语句时由PL/SQL自动定义的。

**3、** 显式游标的操作：打开游标、操作游标、关闭游标；PL/SQL隐式地打开SQL游标，并在它内部处理SQL语句，然后关闭它


### [11、日志的作用是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#11日志的作用是什么)  

### [12、如何判断谁往表里增加了一条纪录？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#12如何判断谁往表里增加了一条纪录)  

### [13、解释$$ORACLE\_HOME和$$ORACLE_BASE的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#13解释$$oracle\_home和$$oracle_base的区别)  

### [14、怎样查看数据库引擎的报错](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#14怎样查看数据库引擎的报错)  

### [15、解释归档和非归档模式之间的不同和它们各自的优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#15解释归档和非归档模式之间的不同和它们各自的优缺点)  

### [16、哪个column可以用来区别V$$视图和GV$$视图?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#16哪个column可以用来区别v$$视图和gv$$视图)  

### [17、说下 oracle的锁又几种,定义分别是什么;](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#17说下-oracle的锁又几种,定义分别是什么;)  

### [18、如何进行强制LOG SWITCH?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#18如何进行强制log-switch)  

### [19、解释 冷备份 和 热备份 的不同点，以及各自的优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#19解释-冷备份-和-热备份-的不同点以及各自的优点)  

### [20、不借助第三方工具，怎样查看sql的执行计划](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#20不借助第三方工具怎样查看sql的执行计划)  

### [21、MySQL数据库与Oracle 数据库有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#21mysql数据库与oracle-数据库有什么区别)  

### [22、SGA主要有那些部分，主要作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#22sga主要有那些部分主要作用是什么)  

### [23、delete 与Truncate区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#23delete-与truncate区别)  

### [24、怎样创建一个一个索引,索引使用的原则,有什么优点和缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#24怎样创建一个一个索引,索引使用的原则,有什么优点和缺点)  

### [25、给出数据库正常启动所经历的几种状态 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#25给出数据库正常启动所经历的几种状态-)  

### [26、在千万级的数据库查询中，如何提高效率？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle高级面试题汇总及答案（2021年Oracle面试题及答案大全）.md#26在千万级的数据库查询中如何提高效率)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
