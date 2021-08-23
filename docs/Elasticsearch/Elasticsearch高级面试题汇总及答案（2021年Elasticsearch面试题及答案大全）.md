# Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）

Elasticsearch面试题及答案【最新版】Elasticsearch高级面试题大全(2021版)，发现网上很多Elasticsearch面试题及答案整理都没有答案，所以花了很长时间搜集，本套Elasticsearch面试题大全，Elasticsearch面试题大汇总，有大量经典的Elasticsearch面试题以及答案，包含Elasticsearch语言常见面试题、Elasticsearch工程师高级面试题及一些大厂Elasticsearch开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Elasticsearch面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Elasticsearch面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是Elasticsearch Analyzer？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#1什么是elasticsearch-analyzer)  


分析器用于文本分析，它可以是内置分析器也可以是自定义分析器。


### [2、Elasticsearch 支持哪些配置管理工具？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#2elasticsearch-支持哪些配置管理工具)  


**1、** Ansible

**2、** Chef

**3、** Puppet

**4、** Salt Stack

是 DevOps 团队使用的 Elasticsearch支持的配置工具。


### [3、logstash 如何与 Elasticsearch 结合使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#3logstash-如何与-elasticsearch-结合使用)  


logstash 是ELK Stack附带的开源 ETL 服务器端引擎，该引擎可以收集和处理来自各种来源的数据。

最典型应用包含：同步日志、邮件数据，同步关系型数据库（MySQL、Oracle）数据，同步非关系型数据库（MongoDB）数据，同步实时数据流 Kafka数据、同步高性能缓存 Redis 数据等。


### [4、Elasticsearch 在部署时，对 Linux 的设置有哪些优化方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#4elasticsearch-在部署时对-linux-的设置有哪些优化方法)  


**1、** 64 GB 内存的机器是非常理想的， 但是 32 GB 和 16 GB 机器也是很常见的。少于 8 GB 会适得其反。

**2、** 如果你要在更快的 CPUs 和更多的核心之间选择，选择更多的核心更好。多个内核提供的额外并发远胜过稍微快一点点的时钟频率。

**3、** 如果你负担得起 SSD，它将远远超出任何旋转介质。基于 SSD 的节点，查询和索引性能都有提升。如果你负担得起，SSD 是一个好的选择。

**4、** 即使数据中心们近在咫尺，也要避免集群跨越多个数据中心。绝对要避免集群跨越大的地理距离。

**5、** 请确保运行你应用程序的 JVM 和服务器的 JVM 是完全一样的。在Elasticsearch 的几个地方，使用 Java 的本地序列化。

**6、** 通过设置 gateway.recover_after_nodes、gateway.expected_nodes、gateway.recover_after_time 可以在集群重启的时候避免过多的分片交换，这可能会让数据恢复从数个小时缩短为几秒钟。

**7、** Elasticsearch 默认被配置为使用单播发现，以防止节点无意中加入集群。只有在同一台机器上运行的节点才会自动组成集群。最好使用单播代替组播。

**8、** 不要随意修改垃圾回收器（CMS）和各个线程池的大小。

**9、** 把你的内存的（少于）一半给 Lucene（但不要超过 32 GB！），通过ES_HEAP_SIZE 环境变量设置。

**10、** 内存交换到磁盘对服务器性能来说是致命的。如果内存交换到磁盘上，一个100 微秒的操作可能变成 10 毫秒。再想想那么多 10 微秒的操作时延累加起来。不难看出 swapping 对于性能是多么可怕。

**11、** Lucene 使用了_大量 的_文件。同时，Elasticsearch 在节点和 HTTP 客户端之间进行通信也使用了大量的套接字。所有这一切都需要足够的文件描述符。你应该增加你的文件描述符，设置一个很大的值，如 64,000。

补充：索引阶段性能提升方法.

**1、** 使用批量请求并调整其大小：每次批量数据 5–15 MB 大是个不错的起始点。

**2、存储：**使用 SSD

**3、段和合并：**Elasticsearch 默认值是 20 MB/s，对机械磁盘应该是个不错的设置。如果你用的是 SSD，可以考虑提高到 100–200 MB/s。如果你在做批量导入，完全不在意搜索，你可以彻底关掉合并限流。另外还可以增加index.translog.flush_threshold_size 设置，从默认的 512 MB 到更大一些的值，比如 1 GB，这可以在一次清空触发的时候在事务日志里积累出更大的段。

**4、** 如果你的搜索结果不需要近实时的准确度，考虑把每个索引的index.refresh_interval 改到 30s。

**5、** 如果你在做大批量导入，考虑通过设置 index.number_of_replicas: 0 关闭副本。


### [5、elasticsearch 冷热分离](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#5elasticsearch-冷热分离)  


类似于MySQL的分表分库

将热数据单独建立一个索引 分配3台机器只保持热机器的索引

另外的机器保持冷数据的索引，但有一个问题，就是事先必须知道哪些是热数据 哪些是冷数据


### [6、在安装Elasticsearch时，请说明不同的软件包及其重要性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#6在安装elasticsearch时请说明不同的软件包及其重要性)  


这个貌似没什么好说的，去官方文档下载对应操作系统安装包即可。

部分功能是收费的，如机器学习、高级别 kerberos 认证安全等选型要知悉。


### [7、精准匹配检索和全文检索匹配检索的不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#7精准匹配检索和全文检索匹配检索的不同)  


**两者的本质区别：**

精确匹配用于：是否完全一致？

**举例：邮编、身份证号的匹配往往是精准匹配。**

全文检索用于：是否相关？

举例：类似B站搜索特定关键词如“马保国 视频”往往是模糊匹配，相关的都返回就可以。


### [8、你可以列出 Elasticsearch 各种类型的分析器吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#8你可以列出-elasticsearch-各种类型的分析器吗)  


Elasticsearch Analyzer 的类型为内置分析器和自定义分析器。

**Standard Analyzer**

标准分析器是默认分词器，如果未指定，则使用该分词器。

它基于Unicode文本分割算法，适用于大多数语言。

**Whitespace Analyzer**

基于空格字符切词。

**Stop Analyzer**

在simple Analyzer的基础上，移除停用词。

**Keyword Analyzer**

不切词，将输入的整个串一起返回。

自定义分词器的模板

自定义分词器的在Mapping的Setting部分设置：

```
PUT my_custom_index
{
 "settings":{
  "analysis":{
  "char_filter":{},
  "tokenizer":{},
  "filter":{},
  "analyzer":{}
  }
 }
}
```

脑海中还是上面的三部分组成的图示。其中：

“char_filter”:{},——对应字符过滤部分；

“tokenizer”:{},——对应文本切分为分词部分；

“filter”:{},——对应分词后再过滤部分；

“analyzer”:{}——对应分词器组成部分，其中会包含：1. 2. 3。


### [9、你能否列出与 Elasticsearch 有关的主要可用字段数据类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#9你能否列出与-elasticsearch-有关的主要可用字段数据类型)  


**1、** 字符串数据类型，包括支持全文检索的 text 类型 和 精准匹配的 keyword 类型。

**2、** 数值数据类型，例如字节，短整数，长整数，浮点数，双精度数，half_float，scaled_float。

**3、** 日期类型，日期纳秒Date nanoseconds，布尔值，二进制（Base64编码的字符串）等。

**4、** 范围（整数范围 integer_range，长范围 long_range，双精度范围 double_range，浮动范围 float_range，日期范围 date_range）。

**5、** 包含对象的复杂数据类型，nested 、Object。

**6、** GEO 地理位置相关类型。

**7、** 特定类型如：数组（数组中的值应具有相同的数据类型）


### [10、Kibana在Elasticsearch的哪些地方以及如何使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#10kibana在elasticsearch的哪些地方以及如何使用)  


Kibana是ELK Stack –日志分析解决方案的一部分。

它是一种开放源代码的可视化工具，可以以拖拽、自定义图表的方式直观分析数据，极大降低的数据分析的门槛。

未来会向类似：商业智能和分析软件 - Tableau 发展。


### [11、在 Elasticsearch 中列出集群的所有索引的语法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#11在-elasticsearch-中列出集群的所有索引的语法是什么)  

### [12、我们可以在 Elasticsearch 中执行搜索的各种可能方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#12我们可以在-elasticsearch-中执行搜索的各种可能方式有哪些)  

### [13、elasticsearch 了解多少，说说你们公司 es 的集群架构，索引数据大小，分片有多少，以及一些调优手段 。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#13elasticsearch-了解多少说说你们公司-es-的集群架构索引数据大小分片有多少以及一些调优手段-。)  

### [14、介绍一下你们的个性化搜索方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#14介绍一下你们的个性化搜索方案)  

### [15、你是如何做 ElasticSearch 写入调优的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#15你是如何做-elasticsearch-写入调优的)  

### [16、elasticsearch 索引数据多了怎么办，如何调优，部署](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#16elasticsearch-索引数据多了怎么办如何调优部署)  

### [17、详细描述一下Elasticsearch索引文档的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#17详细描述一下elasticsearch索引文档的过程)  

### [18、elasticsearch 索引数据多了怎么办，如何调优，部署](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#18elasticsearch-索引数据多了怎么办如何调优部署)  

### [19、lucence 内部结构是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#19lucence-内部结构是什么)  

### [20、解释一下 Elasticsearch 集群中的 Type 的概念 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#20解释一下-elasticsearch-集群中的-type-的概念-)  

### [21、可以列出X-Pack API 吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#21可以列出x-pack-api-吗)  

### [22、Beats 如何与 Elasticsearch 结合使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#22beats-如何与-elasticsearch-结合使用)  

### [23、您能解释一下X-Pack for Elasticsearch的功能和重要性吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#23您能解释一下x-pack-for-elasticsearch的功能和重要性吗)  

### [24、详细描述一下Elasticsearch搜索的过程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#24详细描述一下elasticsearch搜索的过程。)  

### [25、ES更新数据的执行流程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch高级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#25es更新数据的执行流程)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
