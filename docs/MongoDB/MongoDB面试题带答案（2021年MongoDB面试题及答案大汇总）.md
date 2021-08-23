# MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）

MongoDB面试题及答案【最新版】MongoDB高级面试题大全(2021版)，发现网上很多MongoDB面试题及答案整理都没有答案，所以花了很长时间搜集，本套MongoDB面试题大全，MongoDB面试题大汇总，有大量经典的MongoDB面试题以及答案，包含MongoDB语言常见面试题、MongoDB工程师高级面试题及一些大厂MongoDB开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MongoDB面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MongoDB面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是非关系型数据库](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#1什么是非关系型数据库)  


非关系型数据库的显著特点是不使用SQL作为查询语言，数据存储不需要特定的表格模式。


### [2、为什么要在MongoDB中用"Code"数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#2为什么要在mongodb中用"code"数据类型)  


"Code"类型用于在文档中存储 JavaScript 代码。


### [3、能否使用日志特征进行安全备份？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#3能否使用日志特征进行安全备份)  


是的。


### [4、在MongoDB中什么是副本集（避免单点故障）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#4在mongodb中什么是副本集避免单点故障)  


在MongoDB中副本集由一组MongoDB实例组成，包括一个主节点多个次节点，MongoDB客户端的所有数据都

写入主节点(Primary),副节点从主节点同步写入数据，以保持所有复制集内存储相同的数据，提高数据可用性。


### [5、查看Mongos使用的连接？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#5查看mongos使用的连接)  


要查看Mongos使用的连接，请使用db_adminCommand（“ connPoolStats”）；


### [6、如果在一个分片(shard)停止或者很慢的时候,我发起一个查询会怎样?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#6如果在一个分片shard停止或者很慢的时候,我发起一个查询会怎样)  


如果一个分片(shard)停止了,除非查询设置了“partial”选项,否则查询会返回一个错误.如果一个分片(shard)响应很慢,mongodb则会等待它的响应.


### [7、MongoDB支持哪些数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#7mongodb支持哪些数据类型)  


1. String
2. Integer
3. Double
4. Boolean
5. Object
6. Object ID
7. Arrays
8. Min/Max Keys
9. Datetime
10. Code
11. Regular Expression等


### [8、为什么mongodb的数据文件那么庞大](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#8为什么mongodb的数据文件那么庞大)  


mongodb会积极的预分配预留空间，防止文件系统碎片


### [9、数据在什么时候才会扩展到多个分片(shard)里?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#9数据在什么时候才会扩展到多个分片shard里)  


mongodb 分片是基于区域(range)的.所以一个集合(collection)中的所有的对象都被存放到一个块(chunk)中.只有当存在多余一个块的时候,才会有多个分片获取数据的选项.现在,每个默认块的大小是 64mb,所以你需要至少 64 mb 空间才可以实施一个迁移.


### [10、当我试图更新一个正在被迁移的块（chunk）上的文档时会发生什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#10当我试图更新一个正在被迁移的块chunk上的文档时会发生什么)  


会立即更新旧的分片，然后更改才会在所有权转移前复制到新的分片上


### [11、为什么MongoDB的数据文件很大？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#11为什么mongodb的数据文件很大)  

### [12、如何添加索引](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#12如何添加索引)  

### [13、名字空间（namespace）是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#13名字空间namespace是什么)  

### [14、更新数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#14更新数据)  

### [15、mongodb成为最好nosql数据库的原因是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#15mongodb成为最好nosql数据库的原因是什么)  

### [16、更新操作立刻fsync到磁盘？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#16更新操作立刻fsync到磁盘)  

### [17、使用mongodb的优点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#17使用mongodb的优点)  

### [18、数据在什么时候才会扩展到多个分片（shard）里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#18数据在什么时候才会扩展到多个分片shard里)  

### [19、在MongoDB中创建集合并将其删除的语法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#19在mongodb中创建集合并将其删除的语法是什么)  

### [20、查看是否在主服务器上的命令语法是什么？MongoDB允许多少个主机？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#20查看是否在主服务器上的命令语法是什么mongodb允许多少个主机)  

### [21、启用备份故障恢复需要多久?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#21启用备份故障恢复需要多久)  

### [22、什么是MongoDB](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#22什么是mongodb)  

### [23、什么是master或primary?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#23什么是master或primary)  

### [24、在MongoDB中创建模式时，需要考虑哪些要点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#24在mongodb中创建模式时需要考虑哪些要点)  

### [25、解释一下MongoDB中的索引是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#25解释一下mongodb中的索引是什么)  

### [26、monogodb 中的分片什么意思](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#26monogodb-中的分片什么意思)  

### [27、什么是聚合](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#27什么是聚合)  

### [28、为什么要在MongoDB中用"Regular Expression"数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#28为什么要在mongodb中用"regular-expression"数据类型)  

### [29、如何删除文档](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题带答案（2021年MongoDB面试题及答案大汇总）.md#29如何删除文档)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
