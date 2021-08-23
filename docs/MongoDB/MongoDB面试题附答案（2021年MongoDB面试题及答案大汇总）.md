# MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）

MongoDB面试题及答案【最新版】MongoDB高级面试题大全(2021版)，发现网上很多MongoDB面试题及答案整理都没有答案，所以花了很长时间搜集，本套MongoDB面试题大全，MongoDB面试题大汇总，有大量经典的MongoDB面试题以及答案，包含MongoDB语言常见面试题、MongoDB工程师高级面试题及一些大厂MongoDB开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MongoDB面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MongoDB面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、复制在MongoDB中如何工作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#1复制在mongodb中如何工作)  


在多台服务器之间，同步数据的过程称为复制。它通过不同数据库服务器上的多个数据副本提供冗余并提高数据可用性。复制有助于防止数据库丢失单个服务器。


### [2、解释什么是MongoDB？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#2解释什么是mongodb)  


Mongo-DB是一个文档数据库，可提供高性能，高可用性和易扩展性。


### [3、说明Profiler在MongoDB中的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#3说明profiler在mongodb中的作用是什么)  


MongoDB数据库分析器显示针对数据库的每个操作的性能特征。您可以使用探查器找到比其慢的查询。


### [4、分析器在MongoDB中的作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#4分析器在mongodb中的作用是什么)  


分析器就是explain 显示每次操作性能特点的数据库分析器。通过分析器可能查找比预期慢的操作


### [5、什么是文档(记录)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#5什么是文档记录)  


文档由一组key value组成。文档是动态模式,这意味着同一集合里的文档不需要有相同的字段和结构。在关系型

数据库中table中的每一条记录相当于MongoDB中的一个文


### [6、提到用于查看Mongo的命令语法正在使用链接吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#6提到用于查看mongo的命令语法正在使用链接吗)  


用于查看mongo的命令语法使用的链接是db._adminCommand（“ connPoolStats。”）。


### [7、你怎么比较MongoDB、CouchDB及CouchBase?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#7你怎么比较mongodbcouchdb及couchbase)  


不知道


### [8、如果用户移除对象的属性,该属性是否从存储层中删除?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#8如果用户移除对象的属性,该属性是否从存储层中删除)  


是的,用户移除属性然后对象会重新保存(re-save()).


### [9、什么是NoSQL数据库？NoSQL和RDBMS有什么区别？在哪些情况下使用和不使用NoSQL数据库？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#9什么是nosql数据库nosql和rdbms有什么区别在哪些情况下使用和不使用nosql数据库)  


NoSQL是非关系型数据库，NoSQL = Not Only SQL。

关系型数据库采用的结构化的数据，NoSQL采用的是键值对的方式存储数据。 在处理非结构化/半结构化的大数据时；在水平方向上进行扩展时；随时应对动态增加的数据项时可以优先考虑

使用NoSQL数据库。 在考虑数据库的成熟度；支持；分析和商业智能；管理及专业性等问题时，应优先考虑关系型数据库。


### [10、MongoDB相似的产品有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#10mongodb相似的产品有哪些)  


Cassandra，CouchDB，Redis，Riak，Hbase



### [11、我怎么查看 Mongo 正在使用的链接？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#11我怎么查看-mongo-正在使用的链接)  

### [12、什么是MongoDB中的“命名空间”？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#12什么是mongodb中的“命名空间)  

### [13、解释一下您可以将旧文件移动到moveChunk目录中吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#13解释一下您可以将旧文件移动到movechunk目录中吗)  

### [14、当更新一个正在被迁移的块（Chunk）上的文档时会发生什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#14当更新一个正在被迁移的块chunk上的文档时会发生什么)  

### [15、什么是集合(表)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#15什么是集合表)  

### [16、如果块移动操作(movechunk)失败了,我需要手动清除部分转移的文档吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#16如果块移动操作movechunk失败了,我需要手动清除部分转移的文档吗)  

### [17、分片(sharding)和复制(replication)是怎样工作的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#17分片sharding和复制replication是怎样工作的)  

### [18、在MongoDB中如何排序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#18在mongodb中如何排序)  

### [19、MongoDB中的命名空间是什么意思?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#19mongodb中的命名空间是什么意思)  

### [20、分片（sharding）和复制（replication）是怎样工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#20分片sharding和复制replication是怎样工作的)  

### [21、用什么方法可以格式化输出结果](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#21用什么方法可以格式化输出结果)  

### [22、提及插入文档的命令语法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#22提及插入文档的命令语法是什么)  

### [23、可以把movechunk目录里的旧文件删除吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#23可以把movechunk目录里的旧文件删除吗)  

### [24、ObjectID"有哪些部分组成](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#24objectid"有哪些部分组成)  

### [25、31如何理解MongoDB中的GridFS机制，MongoDB为何使用GridFS来存储文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#2531如何理解mongodb中的gridfs机制mongodb为何使用gridfs来存储文件)  

### [26、为什么要在MongoDB中使用分析器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#26为什么要在mongodb中使用分析器)  

### [27、如何查询集合中的文档](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#27如何查询集合中的文档)  

### [28、getLastError的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#28getlasterror的作用)  

### [29、允许空值null吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MongoDB/MongoDB面试题附答案（2021年MongoDB面试题及答案大汇总）.md#29允许空值null吗)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
