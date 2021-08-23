# Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）

Elasticsearch面试题及答案【最新版】Elasticsearch高级面试题大全(2021版)，发现网上很多Elasticsearch面试题及答案整理都没有答案，所以花了很长时间搜集，本套Elasticsearch面试题大全，Elasticsearch面试题大汇总，有大量经典的Elasticsearch面试题以及答案，包含Elasticsearch语言常见面试题、Elasticsearch工程师高级面试题及一些大厂Elasticsearch开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Elasticsearch面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Elasticsearch面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、lucence内部结构是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#1lucence内部结构是什么)  


`面试官`：想了解你的知识面的广度和深度。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0814/01/img_4.png#alt=img%5C_4.png)

Lucene是有索引和搜索的两个过程，包含索引创建，索引，搜索三个要点。可以基于这个脉络展开一些。

最近面试一些公司，被问到的关于Elasticsearch和搜索引擎相关的问题，以及自己总结的回答。


### [2、ElasticSearch中的分析器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#2elasticsearch中的分析器是什么)  


在ElasticSearch中索引数据时，数据由为索引定义的Analyzer在内部进行转换。分析器由一个Tokenizer和零个或多个TokenFilter组成。编译器可以在一个或多个CharFilter之前，分析模块允许你在逻辑名称下注册分析器，然后可以在映射定义或某些API中引用它们。ElasticSearch附带了许多可以随时使用的预建分析器。或者，你可以组合内置的字符过滤器，编译器和过滤器来创建自定义分析器。


### [3、elasticsearch 的 document设计](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#3elasticsearch-的-document设计)  


在使用es时 避免使用复杂的查询语句（Join 、聚合），就是在建立索引时，

就根据查询语句建立好对应的元数据。


### [4、您能否分步介绍如何启动 Elasticsearch 服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#4您能否分步介绍如何启动-elasticsearch-服务器)  


启动方式有很多种，一般 bin 路径下

```
./elasticsearch -d
```

就可以后台启动。

打开浏览器输入 [http://ES](http://ES) IP:9200 就能知道集群是否启动成功。

如果启动报错，日志里会有详细信息，逐条核对解决就可以。


### [5、能列出 10 个使用 Elasticsearch 作为其搜索引擎或数据库的公司吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#5能列出-10-个使用-elasticsearch-作为其搜索引擎或数据库的公司吗)  


这个问题，铭毅本来想删掉。但仔细一想，至少能看出求职者的视野够不够开阔。

参与过 Elastic中文社区活动或者经常关注社区动态的就知道，公司太多了，列举如下（排名不分先后）：

1、阿里

2、腾讯

3、百度

4、京东

5、美团

6、小米

7、滴滴

8、携程

**9、** 今日头条

**10、** 贝壳找房

**11、** 360

**12、** IBM

**13、** 顺丰快递

几乎我们能想到的互联网公司都在使用 Elasticsearch。

关注 TOP 互联网公司的相关技术的动态和技术博客，也是一种非常好的学习方式。


### [6、客户端在和集群连接时，是如何选择特定的节点执行请求的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#6客户端在和集群连接时是如何选择特定的节点执行请求的)  


TransportClient利用transport模块远程连接一个ElasticSearch集群。它并不加入到集群中，只是简单的获得一个或者多个初始化的transport地址，并以轮询的方式与这些地址进行通信。


### [7、elasticsearch是如何实现master选举的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#7elasticsearch是如何实现master选举的)  


`面试官`：想了解ES集群的底层原理，不再只关注业务层面了。

**前置前提：**

**1、** 只有候选主节点（master：true）的节点才能成为主节点。

**2、** 最小主节点数（min_master_nodes）的目的是防止脑裂。

这个我看了各种网上分析的版本和源码分析的书籍，云里雾里。

核对了一下代码，核心入口为findMaster，选择主节点成功返回对应Master，否则返回null。选举流程大致描述如下：

第一步：确认候选主节点数达标，elasticsearch.yml设置的值discovery.zen.minimum_master_nodes；

第二步：比较：先判定是否具备master资格，具备候选主节点资格的优先返回；若两节点都为候选主节点，则id小的值会主节点。注意这里的id为string类型。

题外话：获取节点id的方法。

```
 1GET /_cat/nodes?v&h=ip,port,heapPercent,heapMax,id,name
2ip        port heapPercent heapMax id   name
```


### [8、迁移 Migration API 如何用作 Elasticsearch？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#8迁移-migration-api-如何用作-elasticsearch)  


迁移 API简化了X-Pack索引从一个版本到另一个版本的升级。

点到为止即可，类似问题实际开发现用现查，类似问题没有什么意义。

[https://www.elastic.co/guide/en/elasticsearch/reference/current/migration-api.html](https://www.elastic.co/guide/en/elasticsearch/reference/current/migration-api.html)


### [9、详细描述一下Elasticsearch索引文档的过程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#9详细描述一下elasticsearch索引文档的过程。)  


协调节点默认使用文档ID参与计算（也支持通过routing），以便为路由提供合适的分片。

```
shard = hash(document_id) % (num_of_primary_shards)
```

**1、** 当分片所在的节点接收到来自协调节点的请求后，会将请求写入到Memory Buffer，然后定时（默认是每隔1秒）写入到Filesystem Cache，这个从Momery Buffer到Filesystem Cache的过程就叫做refresh；

**2、** 当然在某些情况下，存在Momery Buffer和Filesystem Cache的数据可能会丢失，ES是通过translog的机制来保证数据的可靠性的。其实现机制是接收到请求后，同时也会写入到translog中，当Filesystem cache中的数据写入到磁盘中时，才会清除掉，这个过程叫做flush；

**3、** 在flush过程中，内存中的缓冲将被清除，内容被写入一个新段，段的fsync将创建一个新的提交点，并将内容刷新到磁盘，旧的translog将被删除并开始一个新的translog。

**4、** flush触发的时机是定时触发（默认30分钟）或者translog变得太大（默认为512M）时；

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0820/02/img_1.png#alt=img%5C_1.png)

**补充：关于Lucene的Segement：**

**1、** Lucene索引是由多个段组成，段本身是一个功能齐全的倒排索引。

**2、** 段是不可变的，允许Lucene将新的文档增量地添加到索引中，而不用从头重建索引。

**3、** 对于每一个搜索请求而言，索引中的所有段都会被搜索，并且每个段会消耗CPU的时钟周、文件句柄和内存。这意味着段的数量越多，搜索性能会越低。

**4、** 为了解决这个问题，Elasticsearch会合并小段到一个较大的段，提交新的合并段到磁盘，并删除那些旧的小段。


### [10、客户端在和集群连接时，如何选择特定的节点执行请求的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#10客户端在和集群连接时如何选择特定的节点执行请求的)  


TransportClient 利用 transport 模块远程连接一个 elasticsearch 集群。它并不加入到集群中，只是简单的获得一个或者多个初始化的 transport 地址，并以 轮询 的方式与这些地址进行通信。


### [11、详细描述一下Elasticsearch更新和删除文档的过程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#11详细描述一下elasticsearch更新和删除文档的过程。)  

### [12、19、解释 Elasticsearch 中的相关性和得分？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#1219解释-elasticsearch-中的相关性和得分)  

### [13、Elasticsearch Analyzer 中的字符过滤器如何利用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#13elasticsearch-analyzer-中的字符过滤器如何利用)  

### [14、你能否在 Elasticsearch 中定义映射？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#14你能否在-elasticsearch-中定义映射)  

### [15、Elasticsearch是如何实现master选举的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#15elasticsearch是如何实现master选举的)  

### [16、您能否说明当前可下载的稳定Elasticsearch版本？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#16您能否说明当前可下载的稳定elasticsearch版本)  

### [17、在并发情况下，Elasticsearch如果保证读写一致？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#17在并发情况下elasticsearch如果保证读写一致)  

### [18、Elasticsearch对于大数据量（上亿量级）的聚合如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#18elasticsearch对于大数据量上亿量级的聚合如何实现)  

### [19、详细描述一下 Elasticsearch 搜索的过程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#19详细描述一下-elasticsearch-搜索的过程。)  

### [20、在 Elasticsearch 中，是怎么根据一个词找到对应的倒排索引的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#20在-elasticsearch-中是怎么根据一个词找到对应的倒排索引的)  

### [21、详细描述一下 Elasticsearch 索引文档的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#21详细描述一下-elasticsearch-索引文档的过程)  

### [22、如何监控 Elasticsearch 集群状态？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#22如何监控-elasticsearch-集群状态)  

### [23、Elasticsearch中的节点（比如共20个），其中的10个选了一个master，另外10个选了另一个master，怎么办？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#23elasticsearch中的节点比如共20个其中的10个选了一个master另外10个选了另一个master怎么办)  

### [24、如何在 Elasticsearch中 搜索数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#24如何在-elasticsearch中-搜索数据)  

### [25、能列举过你使用的 X-Pack 命令吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#25能列举过你使用的-x-pack-命令吗)  

### [26、Elasticsearch 在部署时，对 Linux 的设置有哪些优化方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#26elasticsearch-在部署时对-linux-的设置有哪些优化方法)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
