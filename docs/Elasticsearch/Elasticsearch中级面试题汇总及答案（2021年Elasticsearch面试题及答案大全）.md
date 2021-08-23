# Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）

Elasticsearch面试题及答案【最新版】Elasticsearch高级面试题大全(2021版)，发现网上很多Elasticsearch面试题及答案整理都没有答案，所以花了很长时间搜集，本套Elasticsearch面试题大全，Elasticsearch面试题大汇总，有大量经典的Elasticsearch面试题以及答案，包含Elasticsearch语言常见面试题、Elasticsearch工程师高级面试题及一些大厂Elasticsearch开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Elasticsearch面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Elasticsearch面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、在并发情况下，Elasticsearch 如果保证读写一致？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#1在并发情况下elasticsearch-如果保证读写一致)  


**1、** 可以通过版本号使用乐观并发控制，以确保新版本不会被旧版本覆盖，**由应用**

**层来处理具体的冲突；**

**2、** 另外对于写操作，一致性级别支持 quorum/one/all，默认为 quorum，即只有当大多数分片可用时才允许写操作。但即使大多数可用，也可能存在因为网络等原因导致写入副本失败，这样该副本被认为故障，分片将会在一个不同的节点

上重建。

**3、** 对于读操作，可以设置 replication 为 sync(默认)，这使得操作在主分片和副本分片都完成后才会返回；如果设置 replication 为 async 时，也可以通过设置搜索请求参数_preference 为 primary 来查询主分片，确保文档是最新版本。


### [2、ElasticSearch中的倒排索引是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#2elasticsearch中的倒排索引是什么)  


倒排索引是搜索引擎的核心，搜索引擎的主要目标是在查找发生搜索条件的文档时提供快速搜索。倒排索引是一种像数据结构一样的散列图，可将用户从单词导向文档或网页，它是搜索引擎的核心。其主要目标是快速搜索从数百万文件中查找数据。


### [3、elasticsearch 读取数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#3elasticsearch-读取数据)  


使用RestFul API向对应的node发送查询请求，根据did来判断在哪个shard上，返回的是primary和replica的node节点集合

这样会负载均衡地把查询发送到对应节点，之后对应节点接收到请求，将document数据返回协调节点，协调节点把document返回给客户端

![](https://image-static.segmentfault.com/277/237/2772379432-5e5b563f9a221_articlex#alt=3cI6RP.png)


### [4、拼写纠错是如何实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#4拼写纠错是如何实现的)  


**1、** 拼写纠错是基于编辑距离来实现；编辑距离是一种标准的方法，它用来表示经过插入、删除和替换操作从一个字符串转换到另外一个字符串的最小操作步数；

**2、** 编辑距离的计算过程：比如要计算batyu和beauty的编辑距离，先创建一个7×8的表（batyu长度为5，coffee长度为6，各加2），接着，在如下位置填入黑色数字。其他格的计算过程是取以下三个值的最小值：

如果最上方的字符等于最左方的字符，则为左上方的数字。否则为左上方的数字+1。（对于3,3来说为0）

左方数字+1（对于3,3格来说为2）

上方数字+1（对于3,3格来说为2）

最终取右下角的值即为编辑距离的值3。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0820/02/img_6.png#alt=img%5C_6.png)

对于拼写纠错，我们考虑构造一个度量空间（Metric Space），该空间内任何关系满足以下三条基本条件：

d(x,y) = 0 -- 假如x与y的距离为0，则x=y

d(x,y) = d(y,x)  -- x到y的距离等同于y到x的距离

d(x,y) + d(y,z) >= d(x,z) -- 三角不等式

**1、** 根据三角不等式，则满足与query距离在n范围内的另一个字符转B，其与A的距离最大为d+n，最小为d-n。

**2、** BK树的构造就过程如下：每个节点有任意个子节点，每条边有个值表示编辑距离。所有子节点到父节点的边上标注n表示编辑距离恰好为n。比如，我们有棵树父节点是”book”和两个子节点”cake”和”books”，”book”到”books”的边标号1，”book”到”cake”的边上标号4。从字典里构造好树后，无论何时你想插入新单词时，计算该单词与根节点的编辑距离，并且查找数值为d(neweord, root)的边。递归得与各子节点进行比较，直到没有子节点，你就可以创建新的子节点并将新单词保存在那。比如，插入”boo”到刚才上述例子的树中，我们先检查根节点，查找d(“book”, “boo”) = 1的边，然后检查标号为1的边的子节点，得到单词”books”。我们再计算距离d(“books”, “boo”)=2，则将新单词插在”books”之后，边标号为2。

**3、** 查询相似词如下：计算单词与根节点的编辑距离d，然后递归查找每个子节点标号为d-n到d+n（包含）的边。假如被检查的节点与搜索单词的距离d小于n，则返回该节点并继续查询。比如输入cape且最大容忍距离为1，则先计算和根的编辑距离d(“book”, “cape”)=4，然后接着找和根节点之间编辑距离为3到5的，这个就找到了cake这个节点，计算d(“cake”, “cape”)=1，满足条件所以返回**cake**，然后再找和cake节点编辑距离是0到2的，分别找到cape和cart节点，这样就得到**cape**这个满足条件的结果。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0820/02/img_7.png#alt=img%5C_7.png)


### [5、介绍下你们电商搜索的整体技术架构。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#5介绍下你们电商搜索的整体技术架构。)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0820/02/img_3.png#alt=img%5C_3.png)


### [6、Elasticsearch在部署时，对Linux的设置有哪些优化方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#6elasticsearch在部署时对linux的设置有哪些优化方法)  


**1、** 64 GB 内存的机器是非常理想的， 但是32 GB 和16 GB 机器也是很常见的。少于8 GB 会适得其反。

**2、** 如果你要在更快的 CPUs 和更多的核心之间选择，选择更多的核心更好。多个内核提供的额外并发远胜过稍微快一点点的时钟频率。

**3、** 如果你负担得起 SSD，它将远远超出任何旋转介质。 基于 SSD 的节点，查询和索引性能都有提升。如果你负担得起，SSD 是一个好的选择。

**4、** 即使数据中心们近在咫尺，也要避免集群跨越多个数据中心。绝对要避免集群跨越大的地理距离。

**5、** 请确保运行你应用程序的 JVM 和服务器的 JVM 是完全一样的。 在 Elasticsearch 的几个地方，使用 Java 的本地序列化。

**6、** 通过设置gateway.recover_after_nodes、gateway.expected_nodes、gateway.recover_after_time可以在集群重启的时候避免过多的分片交换，这可能会让数据恢复从数个小时缩短为几秒钟。

**7、** Elasticsearch 默认被配置为使用单播发现，以防止节点无意中加入集群。只有在同一台机器上运行的节点才会自动组成集群。最好使用单播代替组播。

**8、** 不要随意修改垃圾回收器（CMS）和各个线程池的大小。

**9、** 把你的内存的（少于）一半给 Lucene（但不要超过 32 GB！），通过ES_HEAP_SIZE 环境变量设置。

**10、** 内存交换到磁盘对服务器性能来说是致命的。如果内存交换到磁盘上，一个 100 微秒的操作可能变成 10 毫秒。 再想想那么多 10 微秒的操作时延累加起来。 不难看出 swapping 对于性能是多么可怕。

**11、** Lucene 使用了_大量的_文件。同时，Elasticsearch 在节点和 HTTP 客户端之间进行通信也使用了大量的套接字。 所有这一切都需要足够的文件描述符。你应该增加你的文件描述符，设置一个很大的值，如 64,000。

**补充：索引阶段性能提升方法**

**1、** 使用批量请求并调整其大小：每次批量数据 5–15 MB 大是个不错的起始点。

**2、** 存储：使用 SSD

**3、** 段和合并：Elasticsearch 默认值是 20 MB/s，对机械磁盘应该是个不错的设置。如果你用的是 SSD，可以考虑提高到 100–200 MB/s。如果你在做批量导入，完全不在意搜索，你可以彻底关掉合并限流。另外还可以增加 index.translog.flush_threshold_size 设置，从默认的 512 MB 到更大一些的值，比如 1 GB，这可以在一次清空触发的时候在事务日志里积累出更大的段。

**4、** 如果你的搜索结果不需要近实时的准确度，考虑把每个索引的index.refresh_interval 改到30s。

**5、** 如果你在做大批量导入，考虑通过设置index.number_of_replicas: 0 关闭副本。


### [7、REST API在 Elasticsearch 方面有哪些优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#7rest-api在-elasticsearch-方面有哪些优势)  


REST API是使用超文本传输协议的系统之间的通信，该协议以 XML 和 JSON格式传输数据请求。

REST 协议是无状态的，并且与带有服务器和存储数据的用户界面分开，从而增强了用户界面与任何类型平台的可移植性。它还提高了可伸缩性，允许独立实现组件，因此应用程序变得更加灵活。

REST API与平台和语言无关，只是用于数据交换的语言是XML或JSON。

借助：REST API 查看集群信息或者排查问题都非常方便。


### [8、ElasticSearch如何避免脑裂？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#8elasticsearch如何避免脑裂)  


可以通过设置最少投票通过数量（discovery.zen.minimum_master_nodes）超过所有候选节点一半以上，来解决脑裂问题。


### [9、elasticsearch 全文检索](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#9elasticsearch-全文检索)  


(1) 客户端使用RestFul API向对应的node发送查询请求

(2)协调节点将请求转发到所有节点（primary或者replica）所有节点将对应的数据查询之后返回对应的doc id 返回给协调节点

(3)协调节点将doc进行排序聚合

(4) 协调节点再根据doc id 把查询请求发送到对应shard的node，返回document


### [10、定义副本、创建副本的好处是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#10定义副本创建副本的好处是什么)  


副本是 分片的对应副本，用在极端负载条件下提高查询吞吐量或实现高可用性。

所谓高可用主要指：如果某主分片1出了问题，对应的副本分片1会提升为主分片，保证集群的高可用。


### [11、介绍一下你们的个性化搜索方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#11介绍一下你们的个性化搜索方案)  

### [12、Elasticsearch 对于大数据量（上亿量级）的聚合如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#12elasticsearch-对于大数据量上亿量级的聚合如何实现)  

### [13、elasticsearch 数据预热](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#13elasticsearch-数据预热)  

### [14、Elasticsearch 对于大数据量（上亿量级）的聚合如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#14elasticsearch-对于大数据量上亿量级的聚合如何实现)  

### [15、对于GC方面，在使用Elasticsearch时要注意什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#15对于gc方面在使用elasticsearch时要注意什么)  

### [16、Elasticsearch是如何实现Master选举的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#16elasticsearch是如何实现master选举的)  

### [17、简要介绍一下Elasticsearch？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#17简要介绍一下elasticsearch)  

### [18、在 Elasticsearch 中删除索引的语法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#18在-elasticsearch-中删除索引的语法是什么)  

### [19、你之前公司的ElasticSearch集群，一个Node一般会分配几个分片？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#19你之前公司的elasticsearch集群一个node一般会分配几个分片)  

### [20、详细描述一下 Elasticsearch 搜索的过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#20详细描述一下-elasticsearch-搜索的过程)  

### [21、如何使用 Elasticsearch Tokenizer？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#21如何使用-elasticsearch-tokenizer)  

### [22、详细说明ELK Stack及其内容？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#22详细说明elk-stack及其内容)  

### [23、如何使用 Elastic Reporting ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#23如何使用-elastic-reporting-)  

### [24、Master 节点和 候选 Master节点有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#24master-节点和-候选-master节点有什么区别)  

### [25、详细描述一下 Elasticsearch 索引文档的过程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Elasticsearch/Elasticsearch中级面试题汇总及答案（2021年Elasticsearch面试题及答案大全）.md#25详细描述一下-elasticsearch-索引文档的过程。)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
