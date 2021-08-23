# Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）

Kafka面试题及答案【最新版】Kafka高级面试题大全(2021版)，发现网上很多Kafka面试题及答案整理都没有答案，所以花了很长时间搜集，本套Kafka面试题大全，Kafka面试题大汇总，有大量经典的Kafka面试题以及答案，包含Kafka语言常见面试题、Kafka工程师高级面试题及一些大厂Kafka开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Kafka面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Kafka面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Kafka存在那些局限性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#1kafka存在那些局限性)  


**1、** 没有完整的监控工具集

**2、** 消息调整的问题

**3、** 不支持通配符主题选择

**4、** 速度问题


### [2、Kafka Follower如何与Leader同步数据?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#2kafka-follower如何与leader同步数据)  


Kafka 的复制机制既不是完全的同步复制，也不是单纯的异步复制。完全同步复制要求 All Alive Follower 都复制完，这条消息才会被认为 commit，这种复制方式极大的影响了吞吐率。而异步复制方式下，Follower 异步的从 Leader 复制数据，数据只要被 Leader 写入 log 就被认为已经 commit，这种情况下，如果 leader 挂掉，会丢失数据，Kafka 使用 ISR 的方式很好的均衡了确保数据不丢失以及吞吐率。Follower 可以批量的从 Leader 复制数据，而且 Leader 充分利用磁盘顺序读以及 send file(zero copy) 机制，这样极大的提高复制性能，内部批量写磁盘，大幅减少了 Follower 与 Leader 的消息量差。


### [3、系统工具有哪些类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#3系统工具有哪些类型)  


系统工具有三种类型：1.Kafka迁移工具：它有助于将代理从一个版本迁移到另一个版本。2.Mirror Maker：Mirror Maker工具有助于将一个Kafka集群的镜像提供给另一个。3.消费者检查:对于指定的主题集和消费者组，它显示主题，分区，所有者。


### [4、生产者中，什么情况下会发生 QueueFullException？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#4生产者中什么情况下会发生-queuefullexception)  


每当Kafka生产者试图以代理的身份在当时无法处理的速度发送消息时，通常都会发生QueueFullException。但是，为了协作处理增加的负载，用户需要添加足够的代理，因为生产者不会阻止。


### [5、什么是消费者或用户？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#5什么是消费者或用户)  


Kafka消费者订阅一个主题，并读取和处理来自该主题的消息。此外，有了消费者组的名字，消费者就给自己贴上了标签。换句话说，在每个订阅使用者组中，发布到主题的每个记录都传递到一个使用者实例。确保使用者实例可能位于单独的进程或单独的计算机上。Apache Kafka对于新手的面试
### [6、能简单说一下rebalance过程吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#6能简单说一下rebalance过程吗)  


主要的流程如下：

发送GCR请求寻找Coordinator：这个过程主要会向集群中负载最小的broker发起请求，等待成功返回后，那么该Broker将作为Coordinator，尝试连接该Coordinator

发送JGR请求加入该组：当成功找到Coordinator后，那么就要发起加入group的请求，表示该consumer是该组的成员，Coordinator会接收到该请求，会给集群分配一个Leader（通常是第一个），让其负责partition的分配

发送SGR请求：JGR请求成功后，如果发现当前Consumer是leader，那么会进行partition的分配，并发起SGR请求将分配结果发送给Coordinator;如果不是leader，那么也会发起SGR请求，不过分配结果为空


### [7、producer 是否直接将数据发送到 broker 的 leader(主节点)？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#7producer-是否直接将数据发送到-broker-的-leader主节点)  


producer 直接将数据发送到 broker 的 leader(主节点)，不需要在多个节点进行分发，为了

帮助 producer 做到这点，所有的 Kafka 节点都可以及时的告知:哪些节点是活动的，目标

topic 目标分区的 leader 在哪。这样 producer 就可以直接将消息发送到目的地了


### [8、流API的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#8流api的作用是什么)  


一种允许应用程序充当流处理器的API，它还使用一个或多个主题的输入流，并生成一个输出流到一个或多个输出主题，此外，有效地将输入流转换为输出流，我们称之为流API。


### [9、Kafka 创建 Topic 时如何将分区放置到不同的 Broker 中](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#9kafka-创建-topic-时如何将分区放置到不同的-broker-中)  


副本因子不能大于 Broker 的个数；

**1、** 第一个分区（编号为 0）的第一个副本放置位置是随机从 brokerList 选择的；

**2、** 其他分区的第一个副本放置位置相对于第 0 个分区依次往后移。也就是如果我们有 5 个

**3、** Broker，5 个分区，假设第一个分区放在第四个 Broker 上，那么第二个分区将会放在第五

**4、** 个 Broker 上；第三个分区将会放在第一个 Broker 上；第四个分区将会放在第二个

**5、** Broker 上，依次类推；

**6、** 剩余的副本相对于第一个副本放置位置其实是由 nextReplicaShift 决定的，而这个数也是

**7、** 随机产生的


### [10、什么是Kafka中的地域复制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#10什么是kafka中的地域复制)  


对于我们的集群，Kafka MirrorMaker提供地理复制。基本上，消息是通过MirrorMaker跨多个数据中心或云区域复制的。因此，它可以在主动/被动场景中用于备份和恢复；也可以将数据放在离用户更近的位置，或者支持数据位置要求。


### [11、什么是复制工具及其类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#11什么是复制工具及其类型)  

### [12、为什么Kafka的复制至关重要？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#12为什么kafka的复制至关重要)  

### [13、Rebalance有什么影响](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#13rebalance有什么影响)  

### [14、消费者如何不自动提交偏移量，由应用提交？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#14消费者如何不自动提交偏移量由应用提交)  

### [15、Apache Kafka是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#15apache-kafka是什么)  

### [16、如何估算Kafka集群的机器数量？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#16如何估算kafka集群的机器数量)  

### [17、Kafka 中 Consumer Group 是什么概念？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#17kafka-中-consumer-group-是什么概念)  

### [18、解释偏移的作用。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#18解释偏移的作用。)  

### [19、为什么Kafka不支持读写分离？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#19为什么kafka不支持读写分离)  

### [20、解释下Kafka中位移（offset）的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#20解释下kafka中位移offset的作用)  

### [21、Kafka一次reblance大概要多久](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#21kafka一次reblance大概要多久)  

### [22、3.不支持通配符主题选择4.速度###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#223不支持通配符主题选择4速度###)  

### [23、比较RabbitMQ与Apache Kafka](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#23比较rabbitmq与apache-kafka)  

### [24、Kafka的流处理是什么意思？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#24kafka的流处理是什么意思)  

### [25、副本和 ISR 扮演什么角色？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#25副本和-isr-扮演什么角色)  

### [26、解释流API的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#26解释流api的作用)  

### [27、解释一些Kafka流实时用例。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#27解释一些kafka流实时用例。)  

### [28、LEO、LSO、AR、ISR、HW都表示什么含义？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题汇总及答案（2021年Kafka面试题及答案大全）.md#28leolsoarisrhw都表示什么含义)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
