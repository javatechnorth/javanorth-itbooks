# Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）

Elasticsearch面试题及答案【最新版】Elasticsearch高级面试题大全(2021版)，发现网上很多Elasticsearch面试题及答案整理都没有答案，所以花了很长时间搜集，本套Elasticsearch面试题大全，Elasticsearch面试题大汇总，有大量经典的Elasticsearch面试题以及答案，包含Elasticsearch语言常见面试题、Elasticsearch工程师高级面试题及一些大厂Elasticsearch开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Elasticsearch面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Elasticsearch面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、elasticsearch 的倒排索引是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#1elasticsearch-的倒排索引是什么)  


面试官：想了解你对基础概念的认知。

解通俗解释一下就可以。

传统的我们的检索是通过文章，逐个遍历找到对应关键词的位置。

而倒排索引，是通过分词策略，形成了词和文章的映射关系表，这种词典+映射表

即为倒排索引。

有了倒排索引，就能实现 o

**时间复杂度的效率检索文章了，极大的提高了检索效率。**

**学术的解答方式：**

倒排索引，相反于一篇文章包含了哪些词，它从词出发，记载了这个词在哪些文档中出现过，由两部分组成——词典和倒排表。

加分项：倒排索引的底层实现是基于：

```
FST（Finite State Transducer）数据结构
```

lucene 从 4+版本后开始大量使用的数据结构是 FST。FST 有两个优点：

**1、** 空间占用小。通过对词典中单词前缀和后缀的重复利用，压缩了存储空间；

**2、** 查询速度快。O(len(str))的查询时间复杂度。


### [2、解释一下Elasticsearch Cluster？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#2解释一下elasticsearch-cluster)  


Elasticsearch 集群是一组连接在一起的一个或多个 Elasticsearch 节点实例。

Elasticsearch 集群的功能在于在集群中的所有节点之间分配任务，进行搜索和建立索引。


### [3、Elasticsearch 中常用的 cat命令有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#3elasticsearch-中常用的-cat命令有哪些)  


面试时说几个核心的就可以，包含但不限于：

| 含义 | 命令 |
| --- | --- |
| 别名 | GET _cat/aliases?v |
| 分配相关 | GET _cat/allocation |
| 计数 | GET _cat/count?v |
| 字段数据 | GET _cat/fielddata?v |
| 运行状况 | GET_cat/health? |
| 索引相关 | GET _cat/indices?v |
| 主节点相关 | GET _cat/master?v |
| 节点属性 | GET _cat/nodeattrs?v |
| 节点 | GET _cat/nodes?v |
| 待处理任务 | GET _cat/pending_tasks?v |
| 插件 | GET _cat/plugins?v |
| 恢复 | GET _cat / recovery?v |
| 存储库 | GET _cat /repositories?v |
| 段 | GET _cat /segments?v |
| 分片 | GET _cat/shards?v |
| 快照 | GET _cat/snapshots?v |
| 任务 | GET _cat/tasks?v |
| 模板 | GET _cat/templates?v |
| 线程池 | GET _cat/thread_pool?v |



### [4、请解释有关 Elasticsearch的 NRT？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#4请解释有关-elasticsearch的-nrt)  


从文档索引（写入）到可搜索到之间的延迟默认一秒钟，因此Elasticsearch是近实时（NRT）搜索平台。

也就是说：文档写入，最快一秒钟被索引到，不能再快了。

写入调优的时候，我们通常会动态调整：refresh_interval = 30s 或者更达值，以使得写入数据更晚一点时间被搜索到。


### [5、客户端在和集群连接时，如何选择特定的节点执行请求的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#5客户端在和集群连接时如何选择特定的节点执行请求的)  


**1、** TransportClient利用transport模块远程连接一个elasticsearch集群。它并不加入到集群中，只是简单的获得一个或者多个初始化的transport地址，并以 **轮询** 的方式与这些地址进行通信。


### [6、在Elasticsearch中 按 ID检索文档的语法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#6在elasticsearch中-按-id检索文档的语法是什么)  


```
GET test_001/_doc/1
```


### [7、详细描述一下Elasticsearch搜索的过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#7详细描述一下elasticsearch搜索的过程)  


面试官：想了解ES搜索的底层原理，不再只关注业务层面了。

搜索拆解为“query then fetch” 两个阶段。

query阶段的目的：定位到位置，但不取。

**步骤拆解如下：**

**1、** 假设一个索引数据有5主+1副本 共10分片，一次请求会命中（主或者副本分片中）的一个。

**2、** 每个分片在本地进行查询，结果返回到本地有序的优先队列中。

**3、** 第2）步骤的结果发送到协调节点，协调节点产生一个全局的排序列表。

fetch阶段的目的：取数据。

路由节点获取所有文档，返回给客户端。


### [8、ElasticSearch对于大数据量（上亿量级）的聚合如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#8elasticsearch对于大数据量上亿量级的聚合如何实现)  


ElasticSearch提供的首个近似聚合是cardinality度量。它提供一个字段的基数，即该字段的distinct或者unique值的数目。它是基于HLL算法的。HLL会先对我们的输入做哈希运算，然后根据哈希运算结果中的bits做概率估算从而得到基数。其特点是：

可配置的精度，用来控制内存的使用（更精确＝更多内存），小的数据集精度是非常高的；我们可以通过配置参数来设置去重需要的固定内存使用量，无论数千还是数十亿的唯一值，内存使用量只与你配置的精确度相关 。

图片


### [9、elasticsearch的倒排索引是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#9elasticsearch的倒排索引是什么)  


`面试官`：想了解你对基础概念的认知。

通俗解释一下就可以。

传统的我们的检索是通过文章，逐个遍历找到对应关键词的位置。

而倒排索引，是通过分词策略，形成了词和文章的映射关系表，这种词典+映射表即为倒排索引。

有了倒排索引，就能实现`o（1）时间复杂度`的效率检索文章了，极大的提高了检索效率。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0814/01/img_2.png#alt=img%5C_2.png)

学术的解答方式：

> 倒排索引，相反于一篇文章包含了哪些词，它从词出发，记载了这个词在哪些文档中出现过，由两部分组成——词典和倒排表。


`加分项`：倒排索引的底层实现是基于：FST（Finite State Transducer）数据结构。

lucene从4+版本后开始大量使用的数据结构是FST。FST有两个优点：

**1、** 空间占用小。通过对词典中单词前缀和后缀的重复利用，压缩了存储空间；

**2、** 查询速度快。O(len(str))的查询时间复杂度。


### [10、Elasticsearch的 文档是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#10elasticsearch的-文档是什么)  


文档是存储在 Elasticsearch 中的 JSON 文档。它等效于关系数据库表中的一行记录。


### [11、Elasticsearch 中的节点（比如共 20 个），其中的 10 个选了一个master，另外 10 个选了另一个 master，怎么办？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#11elasticsearch-中的节点比如共-20-个其中的-10-个选了一个master另外-10-个选了另一个-master怎么办)  

### [12、Elasticsearch中的 Ingest 节点如何工作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#12elasticsearch中的-ingest-节点如何工作)  

### [13、elasticsearch 实际设计](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#13elasticsearch-实际设计)  

### [14、Elasticsearch中的属性 enabled, index 和 store 的功能是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#14elasticsearch中的属性-enabled,-index-和-store-的功能是什么)  

### [15、介绍下你们电商搜索的整体技术架构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#15介绍下你们电商搜索的整体技术架构)  

### [16、详细描述一下 Elasticsearch 索引文档的过程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#16详细描述一下-elasticsearch-索引文档的过程。)  

### [17、Elasticsearch在部署时，对Linux的设置有哪些优化方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#17elasticsearch在部署时对linux的设置有哪些优化方法)  

### [18、你能告诉我 Elasticsearch 中的数据存储功能吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#18你能告诉我-elasticsearch-中的数据存储功能吗)  

### [19、ElasticSearch如何监控集群状态？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#19elasticsearch如何监控集群状态)  

### [20、解释一下 Elasticsearch 的 分片？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#20解释一下-elasticsearch-的-分片)  

### [21、在Elasticsearch中 cat API的功能是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#21在elasticsearch中-cat-api的功能是什么)  

### [22、ElasticSearch中的副本是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#22elasticsearch中的副本是什么)  

### [23、如何监控Elasticsearch集群状态？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#23如何监控elasticsearch集群状态)  

### [24、ES在生产集群的部署架构是什么，每个索引有多大的数据量，每个索引有多少分片](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#24es在生产集群的部署架构是什么每个索引有多大的数据量每个索引有多少分片)  

### [25、安装 Elasticsearch 需要依赖什么组件吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#25安装-elasticsearch-需要依赖什么组件吗)  

### [26、解释一下 Elasticsearch Node？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题附答案（2021年Elasticsearch面试题及答案大汇总）.md#26解释一下-elasticsearch-node)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
