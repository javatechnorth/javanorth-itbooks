# Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）

Elasticsearch面试题及答案【最新版】Elasticsearch高级面试题大全(2021版)，发现网上很多Elasticsearch面试题及答案整理都没有答案，所以花了很长时间搜集，本套Elasticsearch面试题大全，Elasticsearch面试题大汇总，有大量经典的Elasticsearch面试题以及答案，包含Elasticsearch语言常见面试题、Elasticsearch工程师高级面试题及一些大厂Elasticsearch开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Elasticsearch面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Elasticsearch面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、是否了解字典树？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#1是否了解字典树)  


**常用字典数据结构如下所示：**

![70_8.png][70_8.png]

**Trie 的核心思想是空间换时间，利用字符串的公共前缀来降低查询时间的开销以**

达到提高效率的目的。

**它有 3 个基本性质：**

**1、** 根节点不包含字符，除根节点外每一个节点都只包含一个字符。

**2、** 从根节点到某一节点，路径上经过的字符连接起来，为该节点对应的字符串。

**3、** 每个节点的所有子节点包含的字符都不相同。

![70_9.png][70_9.png]

**1、** 可以看到，trie 树每一层的节点数是 26^i 级别的。所以为了节省空间，我们还可以用动态链表，或者用数组来模拟动态。而空间的花费，不会超过单词数×单词长度。

**2、实现：**对每个结点开一个字母集大小的数组，每个结点挂一个链表，使用左儿子右兄弟表示法记录这棵树；

**3、** 对于中文的字典树，每个节点的子节点用一个哈希表存储，这样就不用浪费太大的空间，而且查询速度上可以保留哈希的复杂度 O(1)。


### [2、token filter 过滤器 在 Elasticsearch 中如何工作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#2token-filter-过滤器-在-elasticsearch-中如何工作)  


针对 tokenizers 处理后的字符流进行再加工，比如：转小写、删除（删除停用词）、新增（添加同义词）等。


### [3、什么是ElasticSearch索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#3什么是elasticsearch索引)  


索引（名词）： 一个索引(index)就像是传统关系数据库中的数据库，它是相关文档存储的地方，index的复数是indices或indexes。

索引（动词）：「索引一个文档」表示把一个文档存储到索引（名词）里，以便它可以被检索或者查询。这很像SQL中的INSERT关键字，差别是，如果文档已经存在，新的文档将覆盖旧的文档。


### [4、您能否列出 与 ELK日志分析相关的应用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#4您能否列出-与-elk日志分析相关的应用场景)  


**1、** 电子商务搜索解决方案

**2、** 欺诈识别

**3、** 市场情报

**4、** 风险管理

**5、** 安全分析 等。

### [5、拼写纠错是如何实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#5拼写纠错是如何实现的)  


**1、拼写纠错是基于编辑距离来实现**；编辑距离是一种标准的方法，它用来表示经过插入、删除和替换操作从一个字符串转换到另外一个字符串的最小操作步数；

**2、编辑距离的计算过程：**比如要计算 batyu 和 beauty 的编辑距离，先创建一个7×8 的表（batyu 长度为 5，coffee 长度为 6，各加 2），接着，在如下位置填入

黑色数字。

**其他格的计算过程是取以下三个值的最小值：**

如果最上方的字符等于最左方的字符，则为左上方的数字。否则为左上方的数字 +1。（对于 3,3 来说为 0）左方数字+1（对于 3,3 格来说为 2）上方数字+1（对于 3,3 格来说为 2）

最终取右下角的值即为编辑距离的值 3。

![70_10.png][70_10.png]

对于拼写纠错，我们考虑构造一个度量空间（Metric Space），该空间内任何关

系满足以下三条基本条件：

> d(x,y) = 0 -- 假如 x 与 y 的距离为 0，则 x=y

d(x,y) = d(y,x) -- x 到 y 的距离等同于 y 到 x 的距离

d(x,y) + d(y,z) >= d(x,z) -- 三角不等式


**1、** 根据三角不等式，则满足与 query 距离在 n 范围内的另一个字符转 B，其与 A的距离最大为 d+n，最小为 d-n。

**2、** BK 树的构造就过程如下：每个节点有任意个子节点，每条边有个值表示编辑距离。所有子节点到父节点的边上标注 n 表示编辑距离恰好为 n。比如，我们有棵树父节点是”book”和两个子

**点”cake”和”books”，”book”到”books”的边标号 ：**

**1、** ”book”到”cake”的边上标号.

**2、** 从字典里构造好树后，无论何时你想插入新单词时.计算该单词与根节点的编辑距离，并且查找数值为 d(neweord, root)的边。递归得与各子节点进行比较，直到没有子节点，你就可以创建新的子节点并将新单词保存在那。比如，插入”boo”到刚才上述例子的树中，我们先检查根节点，查找 d(“book”, “boo”) = 1 的边，然后检查标号为1 的边的子节点，得到单词”books”。我们再计算距离 d(“books”, “boo”)=2，则将新单词插在”books”之后，边标号为 2。

**3、** 查询相似词如下：计算单词与根节点的编辑距离 d，然后递归查找每个子节点标号为 d-n 到 d+n（包含）的边。假如被检查的节点与搜索单词的距离 d 小于n，则返回该节点并继续查询。比如输入 cape 且最大容忍距离为 1，则先计算和根的编辑距离 d(“book”,“cape”)=4，然后接着找和根节点之间编辑距离为 3 到5 的，这个就找到了cake 这个节点，计算 d(“cake”, “cape”)=1，满足条件所以返回 cake，然后再找和 cake 节点编辑距离是 0 到 2 的，分别找到 cape 和cart 节点，这样就得到 cape 这个满足条件的结果。



### [6、ElasticSearch是如何实现Master选举的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#6elasticsearch是如何实现master选举的)  


ElasticSearch的选举是ZenDiscovery模块负责的，主要包含Ping（节点之间通过这个RPC来发现彼此）和Unicast（单播模块包含一个主机列表以控制哪些节点需要ping通）这两部分；

对所有可以成为master的节点（node.master: true）根据nodeId字典排序，每次选举每个节点都把自己所知道节点排一次序，然后选出第一个（第0位）节点，暂且认为它是master节点。

如果对某个节点的投票数达到一定的值（可以成为master节点数n/2+1）并且该节点自己也选举自己， 那这个节点就是master。否则重新选举一直到满足上述条件。


### [7、您能解释一下 Elasticsearch 中的 Explore API 吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#7您能解释一下-elasticsearch-中的-explore-api-吗)  


没有用过，这是 Graph （收费功能）相关的API。

点到为止即可，类似问题实际开发现用现查，类似问题没有什么意义。

[https://www.elastic.co/guide/en/elasticsearch/reference/current/graph-explore-api.html](https://www.elastic.co/guide/en/elasticsearch/reference/current/graph-explore-api.html)


### [8、对于 GC 方面，在使用 Elasticsearch 时要注意什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#8对于-gc-方面在使用-elasticsearch-时要注意什么)  


**1、** SEE

**2、** 倒排词典的索引需要常驻内存，无法 GC，需要监控 data node 上 segmentmemory 增长趋势。

**3、** 各类缓存，field cache, filter cache, indexing cache, bulk queue 等等，要设置合理的大小，并且要应该根据最坏的情况来看 heap 是否够用，也就是各类缓存全部占满的时候，还有 heap 空间可以分配给其他任务吗？避免采用 clear cache等“自欺欺人”的方式来释放内存。

**4、** 避免返回大量结果集的搜索与聚合。确实需要大量拉取数据的场景，可以采用scan & scroll api 来实现。

**5、** cluster stats 驻留内存并无法水平扩展，超大规模集群可以考虑分拆成多个集群通过 tribe node 连接。

**6、** 想知道 heap 够不够，必须结合实际应用场景，并对集群的 heap 使用情况做持续的监控。


### [9、详细描述一下ElasticSearch更新和删除文档的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#9详细描述一下elasticsearch更新和删除文档的过程)  


删除和更新都是写操作，但是ElasticSearch中的文档是不可变的，因此不能被删除或者改动以展示其变更。

磁盘上的每个段都有一个相应的.del文件。当删除请求发送后，文档并没有真的被删除，而是在.del文件中被标记为删除。该文档依然能匹配查询，但是会在结果中被过滤掉。当段合并时，在.del文件中被标记为删除的文档将不会被写入新段。

在新的文档被创建时，ElasticSearch会为该文档指定一个版本号，当执行更新时，旧版本的文档在.del文件中被标记为删除，新版本的文档被索引到一个新段。旧版本的文档依然能匹配查询，但是会在结果中会被过滤掉。


### [10、请解释一下 Elasticsearch 中聚合？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#10请解释一下-elasticsearch-中聚合)  


聚合有助于从搜索中使用的查询中收集数据，聚合为各种统计指标，便于统计信息或做其他分析。聚合可帮助回答以下问题：

**1、** 我的网站平均加载时间是多少？

**2、** 根据交易量，谁是我最有价值的客户？

**3、** 什么会被视为我网络上的大文件？

**4、** 每个产品类别中有多少个产品？

**聚合的分三类：**

主要查看7.10 的官方文档，早期是4个分类，别大意啊！

**分桶 Bucket 聚合**

根据字段值，范围或其他条件将文档分组为桶（也称为箱）。

**指标 Metric 聚合**

从字段值计算指标（例如总和或平均值）的指标聚合。

**管道 Pipeline 聚合**

子聚合，从其他聚合（而不是文档或字段）获取输入。


### [11、请解释在 Elasticsearch 集群中添加或创建索引的过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#11请解释在-elasticsearch-集群中添加或创建索引的过程)  

### [12、elasticsearch 是如何实现 master 选举的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#12elasticsearch-是如何实现-master-选举的)  

### [13、详细描述一下 Elasticsearch 更新和删除文档的过程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#13详细描述一下-elasticsearch-更新和删除文档的过程。)  

### [14、解释一下 Elasticsearch集群中的 索引的概念 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#14解释一下-elasticsearch集群中的-索引的概念-)  

### [15、在索引中更新 Mapping 的语法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#15在索引中更新-mapping-的语法)  

### [16、elasticsearch 数据的写入原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#16elasticsearch-数据的写入原理)  

### [17、Elasticsearch 支持哪些类型的查询？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#17elasticsearch-支持哪些类型的查询)  

### [18、ElasticSearch主分片数量可以在后期更改吗？为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#18elasticsearch主分片数量可以在后期更改吗为什么)  

### [19、是否了解字典树？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#19是否了解字典树)  

### [20、Elasticsearch 是如何实现 Master 选举的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#20elasticsearch-是如何实现-master-选举的)  

### [21、elasticsearch 的 filesystem](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#21elasticsearch-的-filesystem)  

### [22、elasticsearch了解多少，说说你们公司es的集群架构，索引数据大小，分片有多少，以及一些调优手段 。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#22elasticsearch了解多少说说你们公司es的集群架构索引数据大小分片有多少以及一些调优手段-。)  

### [23、详细描述一下Elasticsearch搜索的过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#23详细描述一下elasticsearch搜索的过程)  

### [24、elasticsearch 数据的写入过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#24elasticsearch-数据的写入过程)  

### [25、什么是ElasticSearch脑裂？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#25什么是elasticsearch脑裂)  

### [26、elasticsearch 分布式架构原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch面试题带答案（2021年Elasticsearch面试题及答案大汇总）.md#26elasticsearch-分布式架构原理)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
