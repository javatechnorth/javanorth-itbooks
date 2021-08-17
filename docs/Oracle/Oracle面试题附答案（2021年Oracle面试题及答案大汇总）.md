# Oracle面试题附答案（2021年Oracle面试题及答案大汇总）

Oracle面试题及答案【最新版】Oracle高级面试题大全(2021版)，发现网上很多Oracle面试题及答案整理都没有答案，所以花了很长时间搜集，本套Oracle面试题大全，Oracle面试题大汇总，有大量经典的Oracle面试题以及答案，包含Oracle语言常见面试题、Oracle工程师高级面试题及一些大厂Oracle开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Oracle面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Oracle面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、如何增加buffer cache的命中率?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#1如何增加buffer-cache的命中率)  


在数据库较繁忙时，适用buffer cache advisory 工具，查询v$db_cache_advice.如果有必要更改，可以使用 alter system set db_cache_size 命令


### [2、如何判断哪个session正在连结以及它们等待的资源？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#2如何判断哪个session正在连结以及它们等待的资源)  


V$$SESSION / V$$SESSION_WAIT


### [3、如何变动数据文件的大小？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#3如何变动数据文件的大小)  


ALTER DATABASE DATAFILE <datafile_name> RESIZE <new_size>;


### [4、集合操作符](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#4集合操作符)  


**1、** Union ： 不包含重复值，默认按第一个查询的第一列升序排列。

**2、** Union All : 完全并集包含重复值。不排序。

**3、** Minus 不包含重复值，不排序。


### [5、FACT Table上需要建立何种索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#5fact-table上需要建立何种索引)  


位图索引（bitmap index）


### [6、解释data block , extent 和 segment的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#6解释data-block-,-extent-和-segment的区别)  


**1、** data block 数据块，是oracle最小的逻辑单位，通常oracle从磁盘读写的就是块

**2、** extent 区，是由若干个相邻的block组成

**3、** segment段，是有一组区组成

**4、** tablespace表空间，数据库中数据逻辑存储的地方，一个tablespace可以包含多个数据文件


### [7、简单描述table / segment / extent / block之间的关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#7简单描述table-/-segment-/-extent-/-block之间的关系)  


table创建时,默认创建了一个data segment，每个datasegment含有min extents指定的extents数，每个extent据据表空间的存储参数分配一定数量的blocks


### [8、回滚段的作用是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#8回滚段的作用是什么)  


事务回滚：当事务修改表中数据的时候，该数据修改前的值(即前影像)会存放在回滚段中，当用户回滚事务(ROLLBACK)时，ORACLE将会利用回滚段中的数据前影像来将修改的数据恢复到原来的值。

事务恢复：当事务正在处理的时候，例程失败，回滚段的信息保存在undo表空间中，ORACLE将在下次打开数据库时利用回滚来恢复未提交的数据。

**1、** 读一致性：当一个会话正在修改数据时，其他的会话将看不到该会话未提交的修改。

**2、** 当一个语句正在执行时，该语句将看不到从该语句开始执行后的未提交的修改(语句级读一致性)。

**3、** 当ORACLE执行Select语句时，ORACLE依照当前的系统改变号(SYSTEM CHANGE NUMBER-SCN)。

**4、** 来保证任何前于当前SCN的未提交的改变不被该语句处理。可以想象：当一个长时间的查询正在执行时。

**5、** 若其他会话改变了该查询要查询的某个数据块，ORACLE将利用回滚段的数据前影像来构造一个读一致性视图。


### [9、在Oracle Forms Report中，Record组列的最大长度是多少?什么是不同类型的记录组?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#9在oracle-forms-report中record组列的最大长度是多少什么是不同类型的记录组)  


记录组列名的最大长度不能超过30个字符。不同类型的记录组包括：查询记录组　　状态记录组　　非查询记录组


### [10、Oracle的导入导出有几种方式，有何区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#10oracle的导入导出有几种方式有何区别)  


**1、** 使用oracle工具 exp/imp

**2、** 使用plsql相关工具

**方法1.**

导入/导出的是二进制的数据， 2.plsql导入/导出的是sql语句的文本文件

**3、** sqlloader

**4、** dblink


### [11、如何启动SESSION级别的TRACE](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#11如何启动session级别的trace)  

### [12、解释$$ORACLE_HOME和$$ORACLE_BASE的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#12解释$$oracle_home和$$oracle_base的区别)  

### [13、描述什么是 redo logs](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#13描述什么是-redo-logs)  

### [14、如何生成explain plan?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#14如何生成explain-plan)  

### [15、解释data block , extent 和 segment的区别(这里建议用英文术语)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#15解释data-block-,-extent-和-segment的区别这里建议用英文术语)  

### [16、哪个VIEW用来判断tablespace的剩余空间](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#16哪个view用来判断tablespace的剩余空间)  

### [17、解释FUNCTION,PROCEDURE和PACKAGE区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#17解释function,procedure和package区别)  

### [18、如何判断数据库的时区？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#18如何判断数据库的时区)  

### [19、什么是绑定变量?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#19什么是绑定变量)  

### [20、oracle中存储过程，游标和函数的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#20oracle中存储过程游标和函数的区别)  

### [21、创建数据库时自动建立的tablespace名称？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#21创建数据库时自动建立的tablespace名称)  

### [22、比较truncate和delete 命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#22比较truncate和delete-命令)  

### [23、提示窗体中触发的顺序是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#23提示窗体中触发的顺序是什么)  

### [24、说下 Oracle中function和procedure的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#24说下-oracle中function和procedure的区别)  

### [25、如何在tablespace里增加数据文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#25如何在tablespace里增加数据文件)  

### [26、给出在STAR SCHEMA中的两种表及它们分别含有的数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#26给出在star-schema中的两种表及它们分别含有的数据)  

### [27、Oracle中function和procedure的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Oracle/Oracle面试题附答案（2021年Oracle面试题及答案大汇总）.md#27oracle中function和procedure的区别)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
