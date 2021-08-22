# MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）

MongoDB面试题及答案【最新版】MongoDB高级面试题大全(2021版)，发现网上很多MongoDB面试题及答案整理都没有答案，所以花了很长时间搜集，本套MongoDB面试题大全，MongoDB面试题大汇总，有大量经典的MongoDB面试题以及答案，包含MongoDB语言常见面试题、MongoDB工程师高级面试题及一些大厂MongoDB开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MongoDB面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MongoDB面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何执行事务/加锁?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#1如何执行事务/加锁)  


mongodb没有使用传统的锁或者复杂的带回滚的事务,因为它设计的宗旨是轻量,快速以及可预计的高性能.可以把它类比成MySQL mylsam的自动提交模式.通过精简对事务的支持,性能得到了提升,特别是在一个可能会穿过多个服务器的系统里.


### [2、什么是数据库](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#2什么是数据库)  


数据库可以看成是一个电子化的文件柜,用户可以对文件中的数据运行新增、检索、更新、删除等操作。数据库是一个

所有集合的容器，在文件系统中每一个数据库都有一个相关的物理文件。


### [3、nosql数据库有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#3nosql数据库有哪些)  


Redis mongodb  hbase


### [4、更新操作立刻fsync到磁盘?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#4更新操作立刻fsync到磁盘)  


不会,磁盘写操作默认是延迟执行的.写操作可能在两三秒(默认在60秒内)后到达磁盘.例如,如果一秒内数据库收到一千个对一个对象递增的操作,仅刷新磁盘一次.


### [5、提到如何检查函数的源代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#5提到如何检查函数的源代码)  


要检查没有任何括号的函数源代码，必须调用该函数。


### [6、为什么用MOngoDB？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#6为什么用mongodb)  


1. 架构简单
2. 没有复杂的连接
3. 深度查询能力,MongoDB支持动态查询。
4. 容易调试
5. 容易扩展
6. 不需要转化/映射应用对象到数据库对象
7. 使用内部内存作为存储工作区,以便更快的存取数据。


### [7、mongodb是否支持事务](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#7mongodb是否支持事务)  


MongoDB 4.0的新特性——事务（Transactions）：MongoDB 是不支持事务的，因此开发者在需要用到事务的时候，不得不借用其他工具，在业务代码层面去弥补数据库的不足。

事务和会话(Sessions)关联，一个会话同一时刻只能开启一个事务操作，当一个会话断开，这个会话中的事务也会结束。



### [8、要进行安全备份，可以使用MongoDB中的功能是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#8要进行安全备份可以使用mongodb中的功能是什么)  


日记功能是MongoDB中的功能，可用于执行安全备份。


### [9、数据库的整体结构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#9数据库的整体结构)  


键值对–》文档–》集合–》数据库



### [10、解释什么是副本集？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#10解释什么是副本集)  


副本集是一组托管相同数据集的mongo实例。在副本集中，一个节点是主节点，另一个是辅助节点。从主节点到辅助节点，所有数据都会复制。


### [11、.MongoDB支持主键外键关系吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#11mongodb支持主键外键关系吗)  

### [12、MongoDB在A:{B,C}上建立索引，查询A:{B,C}和A:{C,B}都会使用索引吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#12mongodb在a:{b,c}上建立索引查询a:{b,c}和a:{c,b}都会使用索引吗)  

### [13、什么是master或primary？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#13什么是master或primary)  

### [14、MySQL与mongodb本质之间最基本的差别是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#14mysql与mongodb本质之间最基本的差别是什么)  

### [15、为什么在MongoDB中使用"Object ID"数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#15为什么在mongodb中使用"object-id"数据类型)  

### [16、如何使用"AND"或"OR"条件循环查询集合中的文档](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#16如何使用"and"或"or"条件循环查询集合中的文档)  

### [17、如何执行事务/加锁？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#17如何执行事务/加锁)  

### [18、提及Objecld由什么组成？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#18提及objecld由什么组成)  

### [19、MongoDB的优势有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#19mongodb的优势有哪些)  

### [20、在MongoDb中什么是索引](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#20在mongodb中什么是索引)  

### [21、我应该启动一个集群分片(sharded)还是一个非集群分片的 mongodb 环境?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#21我应该启动一个集群分片sharded还是一个非集群分片的-mongodb-环境)  

### [22、如果用户移除对象的属性，该属性是否从存储层中删除？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#22如果用户移除对象的属性该属性是否从存储层中删除)  

### [23、提到在MongoDB中使用索引的基本语法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#23提到在mongodb中使用索引的基本语法是什么)  

### [24、MongoDB中的分片是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#24mongodb中的分片是什么)  

### [25、当我试图更新一个正在被迁移的块(chunk)上的文档时会发生什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#25当我试图更新一个正在被迁移的块chunk上的文档时会发生什么)  

### [26、在哪些场景使用MongoDB](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#26在哪些场景使用mongodb)  

### [27、解释什么是MongoDB中的GridFS？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#27解释什么是mongodb中的gridfs)  

### [28、MongoDB支持存储过程吗？如果支持的话，怎么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#28mongodb支持存储过程吗如果支持的话怎么用)  

### [29、mongodb的结构介绍](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题汇总及答案（2021年MongoDB面试题及答案大全）.md#29mongodb的结构介绍)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
