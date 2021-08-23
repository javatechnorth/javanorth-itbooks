# Kafka面试题带答案（2021年Kafka面试题及答案大汇总）

Kafka面试题及答案【最新版】Kafka高级面试题大全(2021版)，发现网上很多Kafka面试题及答案整理都没有答案，所以花了很长时间搜集，本套Kafka面试题大全，Kafka面试题大汇总，有大量经典的Kafka面试题以及答案，包含Kafka语言常见面试题、Kafka工程师高级面试题及一些大厂Kafka开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Kafka面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Kafka面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、讲讲Kafka维护消费状态跟踪的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#1讲讲kafka维护消费状态跟踪的方法)  


**1、** 大部分消息系统在broker端的维护消息被消费的记录：一个消息被分发到consumer后broker就马上进行标记或者等待customer的通知后进行标记。这样也可以在消息在消费后立马就删除以减少空间占用。

**2、** 但是这样会不会有什么问题呢？如果一条消息发送出去之后就立即被标记为消费过的，一旦consumer处理消息时失败了（比如程序崩溃）消息就丢失了。为了解决这个问题，很多消息系统提供了另外一个个功能：当消息被发送出去之后仅仅被标记为已发送状态，当接到consumer已经消费成功的通知后才标记为已被消费的状态。这虽然解决了消息丢失的问题，但产生了新问题，首先如果consumer处理消息成功了但是向broker发送响应时失败了，这条消息将被消费两次。第二个问题时，broker必须维护每条消息的状态，并且每次都要先锁住消息然后更改状态然后释放锁。这样麻烦又来了，且不说要维护大量的状态数据，比如如果消息发送出去但没有收到消费成功的通知，这条消息将一直处于被锁定的状态，

**3、** Kafka采用了不同的策略。Topic被分成了若干分区，每个分区在同一时间只被一个consumer消费。这意味着每个分区被消费的消息在日志中的位置仅仅是一个简单的整数：offset。这样就很容易标记每个分区消费状态就很容易了，仅仅需要一个整数而已。这样消费状态的跟踪就很简单了。

**4、** 这带来了另外一个好处：consumer可以把offset调成一个较老的值，去重新消费老的消息。这对传统的消息系统来说看起来有些不可思议，但确实是非常有用的，谁规定了一条消息只能被消费一次呢？


### [2、副本长时间不在ISR中，这意味着什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#2副本长时间不在isr中这意味着什么)  


意味着 follower 不能像 leader 收集数据那样快速地获取数据。


### [3、Kafka中的数据日志是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#3kafka中的数据日志是什么)  


我们知道，在Kafka中，消息会保留相当长的时间。此外，消费者还可以根据自己的方便进行阅读。尽管如此，有一种可能的情况是，如果将Kafka配置为将消息保留24小时，并且消费者可能停机超过24小时，则消费者可能会丢失这些消息。但是，我们仍然可以从上次已知的偏移中读取这些消息，但仅限于消费者的部分停机时间仅为60分钟的情况。此外，关于消费者从一个话题中读到什么，Kafka不会保持状态。


### [4、：11,13,14,16,17,18,19Apache Kafka对于有经验的人的面试](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#4：11,13,14,16,17,18,19apache-kafka对于有经验的人的面试)  

### [5、解释术语“主题复制因子”。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#5解释术语“主题复制因子。)  


在设计Kafka系统时，考虑主题复制是非常重要的。


### [6、Kafka为何这么快](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#6kafka为何这么快)  


Kafka 实现了零拷贝原理来快速移动数据，避免了内核之间的切换。Kafka 可以将数据记录分批发送，从生产者到文件系统（Kafka 主题日志）到消费者，可以端到端的查看这些批次的数据。

批处理能够进行更有效的数据压缩并减少 I/O 延迟，Kafka 采取顺序写入磁盘的方式，避免了随机磁盘寻址的浪费，更多关于磁盘寻址的了解，请参阅 程序员需要了解的硬核知识之磁盘 。总结一下其实就是四个要点

顺序读写

零拷贝

消息压缩

分批发送


### [7、：3,5,6](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#7：3,5,6)  



### [8、：31, 32, 33, 34, 38, 39, 40Apache Kafka对于有经验的人的面试](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#8：31,-32,-33,-34,-38,-39,-40apache-kafka对于有经验的人的面试)  

### [9、怎么解决rebalance中遇到的问题呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#9怎么解决rebalance中遇到的问题呢)  


要避免 Rebalance，还是要从 Rebalance 发生的时机入手。我们在前面说过，Rebalance 主要发生的时机有三个：

组成员数量发生变化

订阅主题数量发生变化

订阅主题的分区数发生变化

后两个我们大可以人为的避免，发生rebalance最常见的原因是消费组成员的变化。

消费者成员正常的添加和停掉导致rebalance，这种情况无法避免，但是时在某些情况下，Consumer 实例会被 Coordinator 错误地认为 “已停止” 从而被“踢出”Group。从而导致rebalance。

当 Consumer Group 完成 Rebalance 之后，每个 Consumer 实例都会定期地向 Coordinator 发送心跳请求，表明它还存活着。如果某个 Consumer 实例不能及时地发送这些心跳请求，Coordinator 就会认为该 Consumer 已经 “死” 了，从而将其从 Group 中移除，然后开启新一轮 Rebalance。这个时间可以通过Consumer 端的参数 session.timeout.ms进行配置。默认值是 10 秒。

除了这个参数，Consumer 还提供了一个控制发送心跳请求频率的参数，就是 heartbeat.interval.ms。这个值设置得越小，Consumer 实例发送心跳请求的频率就越高。频繁地发送心跳请求会额外消耗带宽资源，但好处是能够更加快速地知晓当前是否开启 Rebalance，因为，目前 Coordinator 通知各个 Consumer 实例开启 Rebalance 的方法，就是将 REBALANCE_NEEDED 标志封装进心跳请求的响应体中。

除了以上两个参数，Consumer 端还有一个参数，用于控制 Consumer 实际消费能力对 Rebalance 的影响，即 max.poll.interval.ms 参数。它限定了 Consumer 端应用程序两次调用 poll 方法的最大时间间隔。它的默认值是 5 分钟，表示你的 Consumer 程序如果在 5 分钟之内无法消费完 poll 方法返回的消息，那么 Consumer 会主动发起 “离开组” 的请求，Coordinator 也会开启新一轮 Rebalance。

通过上面的分析，我们可以看一下那些rebalance是可以避免的：

第一类非必要 Rebalance 是因为未能及时发送心跳，导致 Consumer 被 “踢出”Group 而引发的。这种情况下我们可以设置 session.timeout.ms 和 heartbeat.interval.ms 的值，来尽量避免rebalance的出现。（以下的配置是在网上找到的最佳实践，暂时还没测试过）

设置 session.timeout.ms = 6s。设置 heartbeat.interval.ms = 2s。要保证 Consumer 实例在被判定为 “dead” 之前，能够发送至少 3 轮的心跳请求，即 session.timeout.ms >= 3 * heartbeat.interval.ms。将 session.timeout.ms 设置成 6s 主要是为了让 Coordinator 能够更快地定位已经挂掉的 Consumer，早日把它们踢出 Group。

第二类非必要 Rebalance 是 Consumer 消费时间过长导致的。此时，max.poll.interval.ms 参数值的设置显得尤为关键。如果要避免非预期的 Rebalance，你最好将该参数值设置得大一点，比你的下游最大处理时间稍长一点。

总之，要为业务处理逻辑留下充足的时间。这样，Consumer 就不会因为处理这些消息的时间太长而引发 Rebalance 。


### [10、什么是消费者组？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#10什么是消费者组)  


**1、** 消费者组是Kafka独有的概念，如果面试官问这个，就说明他对此是有一定了解的。

**2、** 胡大给的标准答案是：官网上的介绍言简意赅，即消费者组是Kafka提供的可扩展且具有容错性的消费者机制。

**3、** 但实际上，消费者组（Consumer Group）其实包含两个概念，作为队列，消费者组允许你分割数据处理到一组进程集合上（即一个消费者组中可以包含多个消费者进程，他们共同消费该topic的数据），这有助于你的消费能力的动态调整；作为-订阅模型（publish-subscribe），Kafka允许你将同一份消息广播到多个消费者组里，以此来丰富多种数据使用场景。

**4、** 需要注意的是：在消费者组中，多个实例共同订阅若干个主题，实现共同消费。同一个组下的每个实例都配置有相同的组ID，被分配不同的订阅分区。当某个实例挂掉的时候，其他实例会自动地承担起它负责消费的分区。因此，消费者组在一定程度上也保证了消费者程序的高可用性。

注意：消费者组的题目，能够帮你在某种程度上掌控下面的面试方向。

**1、** 如果你擅长位移值原理（Offset），就不妨再提一下消费者组的位移提交机制；

**2、** 如果你擅长Kafka Broker，可以提一下消费者组与Broker之间的交互；

**3、** 如果你擅长与消费者组完全不相关的Producer，那么就可以这么说：“消费者组要消费的数据完全来自于Producer端生产的消息，我对Producer还是比较熟悉的。”

总之，你总得对consumer group相关的方向有一定理解，然后才能像面试官表名你对某一块很理解。


### [11、Zookeeper对于Kafka的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#11zookeeper对于kafka的作用是什么)  

### [12、监控Kafka的框架都有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#12监控kafka的框架都有哪些)  

### [13、如何设置Kafka能接收的最大消息的大小？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#13如何设置kafka能接收的最大消息的大小)  

### [14、解释领导者和追随者的概念。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#14解释领导者和追随者的概念。)  

### [15、数据传输的事务定义有哪三种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#15数据传输的事务定义有哪三种)  

### [16、Kafka集群中保留期的目的是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#16kafka集群中保留期的目的是什么)  

### [17、偏移的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#17偏移的作用是什么)  

### [18、消费者故障，出现活锁问题如何解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#18消费者故障出现活锁问题如何解决)  

### [19、你能用Kafka做什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#19你能用kafka做什么)  

### [20、Kafka 如何判断节点是否存活](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#20kafka-如何判断节点是否存活)  

### [21、能说一下leader选举过程吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#21能说一下leader选举过程吗)  

### [22、Leader和Follower的概念是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#22leader和follower的概念是什么)  

### [23、说明Kafka的一个最佳特征。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#23说明kafka的一个最佳特征。)  

### [24、数据有序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#24数据有序)  

### [25、分区Leader选举策略有几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#25分区leader选举策略有几种)  

### [26、Kafka 与传统MQ消息系统之间有三个关键区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#26kafka-与传统mq消息系统之间有三个关键区别)  

### [27、：24, 22](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#27：24,-22)  

### [28、如果副本长时间不在ISR中，这意味着什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题带答案（2021年Kafka面试题及答案大汇总）.md#28如果副本长时间不在isr中这意味着什么)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
