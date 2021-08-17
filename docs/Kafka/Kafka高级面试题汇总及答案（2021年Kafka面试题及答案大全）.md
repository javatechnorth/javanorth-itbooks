# Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）

Kafka面试题及答案【最新版】Kafka高级面试题大全(2021版)，发现网上很多Kafka面试题及答案整理都没有答案，所以花了很长时间搜集，本套Kafka面试题大全，Kafka面试题大汇总，有大量经典的Kafka面试题以及答案，包含Kafka语言常见面试题、Kafka工程师高级面试题及一些大厂Kafka开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Kafka面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Kafka面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、列出所有Apache Kafka业务](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#1列出所有apache-kafka业务)  


Apache Kafka的业务包括：添加和删除Kafka主题如何修改Kafka主题如何关机在Kafka集群之间镜像数据找到消费者的位置扩展您的Kafka群集自动迁移数据退出服务器数据中心


### [2、Kafka 中的消息是否会丢失和重复消费？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#2kafka-中的消息是否会丢失和重复消费)  


要确定Kafka的消息是否丢失或重复，从两个方面分析入手：消息发送和消息消费。

消息发送 Kafka消息发送有两种方式：**同步**（sync）和**异步**（async），默认是同步方式，可通过producer.type属性进行配置。Kafka通过配置request.required.acks属性来确认消息的生产：

综上所述，有6种消息生产的情况，下面分情况来分析消息丢失的场景：

acks=0；不和Kafka集群进行消息接收确认，则当网络异常、缓冲区满了等情况时，消息可能丢失；

acks=1；同步模式下，只有Leader确认接收成功后但挂掉了，副本没有同步，数据可能丢失；

0 表示不进行消息接收是否成功的确认；

1 表示当Leader接收成功时确认；

-1 表示Leader和Follower都接收成功时确认；

消息消费 Kafka消息消费有两个consumer接口，Low-level API和High-level API：

Low-level API：消费者自己维护offset等值，可以实现对Kafka的完全控制；

High-level API：封装了对parition和offset的管理，使用简单；如果使用高级接口High-level API，可能存在一个问题就是当消息消费者从集群中把消息取出来、并提交了新的消息offset值后，还没来得及消费就挂掉了，那么下次再消费时之前没消费成功的消息就“诡异”的消失了；

**解决办法：**

针对消息丢失： **同步模式下**，确认机制设置为-1，即让消息写入Leader和Follower之后再确认消息发送成功； **异步模式下**，为防止缓冲区满，可以在配置文件设置不限制阻塞超时时间，当缓冲区满时让生产者一直处于阻塞状态；

针对消息重复：将消息的唯一标识保存到外部介质中，每次消费时判断是否处理过即可。


### [3、Kafka Producer API的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#3kafka-producer-api的作用是什么)  


允许应用程序将记录流到一个或多个Kafka主题的API就是我们所说的Producer API。


### [4、Kafka中有哪几个组件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#4kafka中有哪几个组件)  


Kafka最重要的元素是：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/1/27/0/9_1.png#alt=9%5C_1.png)

主题：Kafka主题是一堆或一组消息。生产者：在Kafka，生产者发布通信以及向Kafka主题发布消息。消费者：Kafka消费者订阅了一个主题，并且还从主题中读取和处理消息。经纪人：在管理主题中的消息存储时，我们使用Kafka Brokers。


### [5、为什么要使用Apache Kafka集群？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#5为什么要使用apache-kafka集群)  


为了克服收集大量数据和分析收集数据的挑战，我们需要一个消息队列系统。因此Apache Kafka应运而生。其好处是：只需存储/发送事件以进行实时处理，就可以跟踪Web活动。通过这一点，我们可以发出警报并报告操作指标。此外，我们可以将数据转换为标准格式。此外，它允许对主题的流数据进行连续处理。由于它的广泛使用，它秒杀了竞品，如ActiveMQ，RabbitMQ等。


### [6、为什么Kafka技术很重要？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#6为什么kafka技术很重要)  


Kafka有一些优点，因此使用起来很重要：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/1/27/0/9_2.png#alt=9%5C_2.png)

高吞吐量：我们在Kafka中不需要任何大型硬件，因为它能够处理高速和大容量数据。此外，它还可以支持每秒数千条消息的消息吞吐量。低延迟：Kafka可以轻松处理这些消息，具有毫秒级的极低延迟，这是大多数新用例所要求的。容错：Kafka能够抵抗集群中的节点/机器故障。耐久性：由于Kafka支持消息复制，因此消息永远不会丢失。这是耐久性背后的原因之一。可扩展性：卡夫卡可以扩展，而不需要通过添加额外的节点而在运行中造成任何停机。


### [7、Kafka 中是怎么体现消息顺序性的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#7kafka-中是怎么体现消息顺序性的)  


Kafka 每个 partition 中的消息在写入时都是有序的，消费时，每个 partition 只能被每一个 group 中的一个消费者消费，保证了消费时也是有序的。整个 topic 不保证有序。如果为了保证 topic 整个有序，那么将 partition 调整为1.


### [8、Kafka能手动删除消息吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#8kafka能手动删除消息吗)  


**1、** Kafka不需要用户手动删除消息。它本身提供了留存策略，能够自动删除过期消息。当然，它是支持手动删除消息的。

**2、** 对于设置了Key且参数cleanup.policy=compact的主题而言，我们可以构造一条 的消息发送给Broker，依靠Log Cleaner组件提供的功能删除掉该 Key 的消息。

**3、** 对于普通主题而言，我们可以使用Kafka-delete-records命令，或编写程序调用Admin.deleteRecords方法来删除消息。这两种方法殊途同归，底层都是调用Admin的deleteRecords方法，通过将分区Log Start Offset值抬高的方式间接删除消息。


### [9、Kafka Unclean 配置代表什么？会对 spark streaming 消费有什么影响？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#9kafka-unclean-配置代表什么会对-spark-streaming-消费有什么影响)  


unclean.leader.election.enable 为 true 的话，意味着非 ISR 集合的 broker 也可以参与选举，这样有可能就会丢数据，spark streaming在消费过程中拿到的 end offset 会突然变小，导致 spark streaming job 挂掉。如果 unclean.leader.election.enable 参数设置为 true，就有可能发生数据丢失和数据不一致的情况，Kafka 的可靠性就会降低；而如果 unclean.leader.election.enable 参数设置为 false，Kafka 的可用性就会降低。


### [10、比较传统队列系统与Apache Kafka](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#10比较传统队列系统与apache-kafka)  


让我们比较一下传统队列系统与Apache Kafka的功能：消息保留 传统的队列系统 - 它通常从队列末尾处理完成后删除消息。 Apache Kafka中，消息即使在处理后仍然存在。这意味着Kafka中的消息不会因消费者收到消息而被删除。基于逻辑的处理传统队列系统不允许基于类似消息或事件处理逻辑。Apache Kafka允许基于类似消息或事件处理逻辑。


### [11、Apache Kafka是分布式流处理平台吗？如果是，你能用它做什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#11apache-kafka是分布式流处理平台吗如果是你能用它做什么)  

### [12、Kafka 新建的分区会在哪个目录下创建](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#12kafka-新建的分区会在哪个目录下创建)  

### [13、连接器API的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#13连接器api的作用是什么)  

### [14、Kafka的高可用机制是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#14kafka的高可用机制是什么)  

### [15、Kafka系统工具有哪些类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#15kafka系统工具有哪些类型)  

### [16、：46, 48](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#16：46,-48)  

### [17、解释如何调整Kafka以获得最佳性能。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#17解释如何调整kafka以获得最佳性能。)  

### [18、Kafka Producer如何优化写入速度?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#18kafka-producer如何优化写入速度)  

### [19、ZooKeeper在Kafka中的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#19zookeeper在kafka中的作用是什么)  

### [20、阐述下 Kafka 中的领导者副本（Leader Replica）和追随者副本（Follower Replica）的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#20阐述下-kafka-中的领导者副本leader-replica和追随者副本follower-replica的区别)  

### [21、Kafka的优点有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#21kafka的优点有那些)  

### [22、Kafka如何不消费重复数据？比如扣款，我们不能重复的扣。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#22kafka如何不消费重复数据比如扣款我们不能重复的扣。)  

### [23、3.它还可以在记录进入时对其进行处理。Apache Kafka对于新手的面试](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#233它还可以在记录进入时对其进行处理。apache-kafka对于新手的面试)  

### [24、Kafka流的特点。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#24kafka流的特点。)  

### [25、连接器API的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#25连接器api的作用是什么)  

### [26、Kafka 的 ack 机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#26kafka-的-ack-机制)  

### [27、如何保证Kafka顺序消费](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#27如何保证kafka顺序消费)  

### [28、：1,2,4,7,8,9,10Apache Kafka对于有经验的人的面试](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka高级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#28：1,2,4,7,8,9,10apache-kafka对于有经验的人的面试)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
