# Kafka面试题附答案（2021年Kafka面试题及答案大汇总）

Kafka面试题及答案【最新版】Kafka高级面试题大全(2021版)，发现网上很多Kafka面试题及答案整理都没有答案，所以花了很长时间搜集，本套Kafka面试题大全，Kafka面试题大汇总，有大量经典的Kafka面试题以及答案，包含Kafka语言常见面试题、Kafka工程师高级面试题及一些大厂Kafka开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Kafka面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Kafka面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Kafka和Flume之间的主要区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#1kafka和flume之间的主要区别是什么)  


**工具类型**

Apache Kafka 是面向多个生产商和消费者的通用工具。

Apache Flume 是特定应用程序的专用工具。

**复制功能**

Apache Kafka 可以复制事件；

Apache Flume 不复制事件。


### [2、消费者提交消费位移时提交的是当前消费到的最新消息的offset还是offset+1?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#2消费者提交消费位移时提交的是当前消费到的最新消息的offset还是offset+1)  


offset+1


### [3、消费者API的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#3消费者api的作用是什么)  


允许应用程序订阅一个或多个主题并处理生成给它们的记录流的API，我们称之为消费者API。


### [4、生产者和消费者的命令行是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#4生产者和消费者的命令行是什么)  


**生产者在主题上发布消息：**

**1、** bin/Kafka-console-producer.sh --broker-list 192.168.43.49:9092 --topic Hello-Kafka

**2、** 注意这里的IP是server.properties中的listeners的配置。接下来每个新行就是输入一条新消息。

**3、** 消费者接受消息：

**4、** bin/Kafka-console-consumer.sh --zookeeper localhost:2181 --topic Hello-Kafka --from-beginning


### [5、如何获取topic主题的列表](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#5如何获取topic主题的列表)  


bin/Kafka-topics.sh --list --zookeeper localhost:2181


### [6、消费者负载均衡策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#6消费者负载均衡策略)  


一个消费者组中的一个分片对应一个消费者成员，他能保证每个消费者成员都能访问，如

果组中成员太多会有空闲的成员


### [7、Kafka 的设计时什么样的呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#7kafka-的设计时什么样的呢)  


**1、** Kafka 将消息以 topic 为单位进行归纳

**2、** 将向 Kafka topic 发布消息的程序成为 producers.

**3、** 将预订 topics 并消费消息的程序成为 consumer.

**4、** Kafka 以集群的方式运行，可以由一个或多个服务组成，每个服务叫做一个 broker.

**5、** producers 通过网络将消息发送到 Kafka 集群，集群向消费者提供消息


### [8、解释多租户是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#8解释多租户是什么)  


我们可以轻松地将Kafka部署为多租户解决方案。但是，通过配置主题可以生成或使用数据，可以启用多租户。此外，它还为配额提供操作支持。


### [9、Kafka 与传统消息系统之间有三个关键区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#9kafka-与传统消息系统之间有三个关键区别)  


**1、** Kafka 持久化日志，这些日志可以被重复读取和无限期保留

**2、** Kafka 是一个分布式系统：它以集群的方式运行，可以灵活伸缩，在内部通过复制数据

**3、** 提升容错能力和高可用性

**4、** Kafka 支持实时的流式处理


### [10、启动Kafka服务器的过程是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#10启动kafka服务器的过程是什么)  


初始化ZooKeeper服务器是非常重要的一步，因为Kafka使用ZooKeeper，所以启动Kafka服务器的过程是：要启动ZooKeeper服务器：>bin/zooKeeper-server-start.sh config/zooKeeper.properties接下来，启动Kafka服务器：>bin/Kafka-server-start.sh config/server.properties


### [11、Apache Kafka的缺陷](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#11apache-kafka的缺陷)  

### [12、解释生产者是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#12解释生产者是什么)  

### [13、Kafka什么情况下会rebalance](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#13kafka什么情况下会rebalance)  

### [14、Kafka中有哪几个组件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#14kafka中有哪几个组件)  

### [15、解释Kafka可以接收的消息最大为多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#15解释kafka可以接收的消息最大为多少)  

### [16、Apache Kafka是分布式流处理平台吗？如果是，你能用它做什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#16apache-kafka是分布式流处理平台吗如果是你能用它做什么)  

### [17、Kafka分布式（不是单机）的情况下，如何保证消息的顺序消费?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#17kafka分布式不是单机的情况下如何保证消息的顺序消费)  

### [18、解释Apache Kafka用例？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#18解释apache-kafka用例)  

### [19、传统的消息传递方法有哪些类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#19传统的消息传递方法有哪些类型)  

### [20、在生产者中，何时发生QueueFullException？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#20在生产者中何时发生queuefullexception)  

### [21、：41, 42, 43, 44, 45, 47, 49Apache Kafka对于有经验的人的面试](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#21：41,-42,-43,-44,-45,-47,-49apache-kafka对于有经验的人的面试)  

### [22、Kafka中有哪几个组件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#22kafka中有哪几个组件)  

### [23、consumer是推还是拉？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#23consumer是推还是拉)  

### [24、讲一讲Kafka的ack的三种机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#24讲一讲kafka的ack的三种机制)  

### [25、在Kafka集群中保留期的目的是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#25在kafka集群中保留期的目的是什么)  

### [26、数据传输的事物定义有哪三种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#26数据传输的事物定义有哪三种)  

### [27、Controller发生网络分区（Network Partitioning）时，Kafka会怎么样？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#27controller发生网络分区network-partitioning时kafka会怎么样)  

### [28、Kafka提供的保证是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案（2021年Kafka面试题及答案大汇总）.md#28kafka提供的保证是什么)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
