# Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）

Kafka面试题及答案【最新版】Kafka高级面试题大全(2021版)，发现网上很多Kafka面试题及答案整理都没有答案，所以花了很长时间搜集，本套Kafka面试题大全，Kafka面试题大汇总，有大量经典的Kafka面试题以及答案，包含Kafka语言常见面试题、Kafka工程师高级面试题及一些大厂Kafka开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Kafka面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Kafka面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Kafka为什么那么快?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#1kafka为什么那么快)  


1. Cache Filesystem Cache PageCache缓存
2. 顺序写 由于现代的操作系统提供了预读和写技术，磁盘的顺序写大多数情况下比随机写内存还要快。
3. Zero-copy 零拷技术减少拷贝次数
4. Batching of Messages 批量量处理。合并小的请求，然后以流的方式进行交互，直顶网络上限。
5. Pull 拉模式 使用拉模式进行消息的获取消费，与消费端处理能力相符。


### [2、Kafka 消息是采用 Pull 模式，还是 Push 模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#2kafka-消息是采用-pull-模式还是-push-模式)  


Kafka 最初考虑的问题是，customer 应该从 brokes 拉取消息还是 brokers 将消息推送到

consumer，也就是 pull 还 push。在这方面，Kafka 遵循了一种大部分消息系统共同的传统

的设计：

producer 将消息推送到 broker，consumer 从 broker 拉取消息

一些消息系统比如 Scribe 和 Apache Flume 采用了 push 模式，将消息推送到下游的

consumer。

这样做有好处也有坏处：由 broker 决定消息推送的速率，对于不同消费速率的

consumer 就不太好处理了。消息系统都致力于让 consumer 以最大的速率最快速的消费消

息，但不幸的是，push 模式下，当 broker 推送的速率远大于 consumer 消费的速率时，

consumer 恐怕就要崩溃了。最终 Kafka 还是选取了传统的 pull 模式

Pull 模式的另外一个好处是 consumer 可以自主决定是否批量的从 broker 拉取数据。Push

模式必须在不知道下游 consumer 消费能力和消费策略的情况下决定是立即推送每条消息还

是缓存之后批量推送。如果为了避免 consumer 崩溃而采用较低的推送速率，将可能导致一

次只推送较少的消息而造成浪费。Pull 模式下，consumer 就可以根据自己的消费能力去决

定这些策略

Pull 有个缺点是，如果 broker 没有可供消费的消息，将导致 consumer 不断在循环中轮询，

直到新消息到 t 达。为了避免这点，Kafka 有个参数可以让 consumer 阻塞知道新消息到达

(当然也可以阻塞知道消息的数量达到某个特定的量这样就可以批量发


### [3、Kafka Producer 写数据，ACK 为 0，1，-1 时分别代表什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#3kafka-producer-写数据ack-为-01-1-时分别代表什么)  


1（默认） 数据发送到Kafka后，经过leader成功接收消息的的确认，就算是发送成功了。在这种情况下，如果leader宕机了，则会丢失数据。

0 生产者将数据发送出去就不管了，不去等待任何返回。这种情况下数据传输效率最高，但是数据可靠性确是最低的。

-1 producer需要等待ISR中的所有follower都确认接收到数据后才算一次发送完成，可靠性最高。


### [4、ISR在Kafka环境中代表什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#4isr在kafka环境中代表什么)  


ISR指的是同步副本。这些通常被分类为一组消息副本，它们被同步为领导者。


### [5、Kafka的一些最显著的应用。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#5kafka的一些最显著的应用。)  


Netflix，Mozilla，Oracle


### [6、kafaka 生产数据时数据的分组策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#6kafaka-生产数据时数据的分组策略)  


**1、** 生产者决定数据产生到集群的哪个 partition 中

**2、** 每一条消息都是以（key，value）格式

**3、** Key 是由生产者发送数据传入

**4、** 所以生产者（key）决定了数据产生到集群的哪个 partition


### [7、Leader总是-1，怎么破？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#7leader总是-1怎么破)  


**1、** 对于有经验的SRE来讲，早期的Kafka版本应该多多少少都遇到过该种情况，通常情况下就是Controller不工作了，导致无法分配leader，那既然知道问题后，解决方案也就很简单了。重启Controller节点上的Kafka进程，让其他节点重新注册Controller角色，但是如上面ZooKeeper的作用，你要知道为什么Controller可以自动注册。

**2、** 当然了，当你知道controller的注册机制后，你也可以说：删除ZooKeeper节点/controller，触发Controller重选举。Controller重选举能够为所有主题分区重刷分区状态，可以有效解决因不一致导致的 Leader 不可用问题。但是，需要注意的是，直接操作ZooKeeper是一件风险很大的操作，就好比在Linux中执行了rm -rf /xxx一样，如果在/和xxx之间不小心多了几个空格，那”恭喜你”，今年白干了。


### [8、Java在Apache Kafka中的重要性是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#8java在apache-kafka中的重要性是什么)  


为了满足Kafka标准的高处理速率需求，我们可以使用java语言。此外，对于Kafka的消费者客户，Java也提供了良好的社区支持。所以，我们可以说在Java中实现Kafka是一个正确的选择。


### [9、什么是消费者组？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#9什么是消费者组)  


消费者组的概念是Apache Kafka独有的。基本上，每个Kafka消费群体都由一个或多个共同消费一组订阅主题的消费者组成。


### [10、为什么需要消息系统，MySQL不能满足需求吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#10为什么需要消息系统mysql不能满足需求吗)  


**1、** 解耦：

允许你独立的扩展或修改两边的处理过程，只要确保它们遵守同样的接口约束。

**2、** 冗余：

消息队列把数据进行持久化直到它们已经被完全处理，通过这一方式规避了数据丢失风险。许多消息队列所采用的”插入-获取-删除”范式中，在把一个消息从队列中删除之前，需要你的处理系统明确的指出该消息已经被处理完毕，从而确保你的数据被安全的保存直到你使用完毕。

**3、** 扩展性：

因为消息队列解耦了你的处理过程，所以增大消息入队和处理的频率是很容易的，只要另外增加处理过程即可。

**4、** 灵活性 & 峰值处理能力：

在访问量剧增的情况下，应用仍然需要继续发挥作用，但是这样的突发流量并不常见。如果为以能处理这类峰值访问为标准来投入资源随时待命无疑是巨大的浪费。使用消息队列能够使关键组件顶住突发的访问压力，而不会因为突发的超负荷的请求而完全崩溃。

**5、** 可恢复性：

系统的一部分组件失效时，不会影响到整个系统。消息队列降低了进程间的耦合度，所以即使一个处理消息的进程挂掉，加入队列中的消息仍然可以在系统恢复后被处理。

**6、** 顺序保证：

在大多使用场景下，数据处理的顺序都很重要。大部分消息队列本来就是排序的，并且能保证数据会按照特定的顺序来处理。（Kafka 保证一个 Partition 内的消息的有序性）

**7、** 缓冲：

有助于控制和优化数据流经过系统的速度，解决生产消息和消费消息的处理速度不一致的情况。

**8、** 异步通信：

很多时候，用户不想也不需要立即处理消息。消息队列提供了异步处理机制，允许用户把一个消息放入队列，但并不立即处理它。想向队列中放入多少消息就放多少，然后在需要的时候再去处理它们。


### [11、如何调优Kafka？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#11如何调优kafka)  

### [12、解释术语“Log Anatomy”](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#12解释术语“log-anatomy)  

### [13、如果 Leader Crash 时，ISR为空怎么办](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#13如果-leader-crash-时isr为空怎么办)  

### [14、Kafka为什么不支持读写分离？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#14kafka为什么不支持读写分离)  

### [15、Kafka 存储在硬盘上的消息格式是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#15kafka-存储在硬盘上的消息格式是什么)  

### [16、：12,15,20](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#16：12,15,20)  

### [17、Kafka的哪些场景中使用了零拷贝（Zero Copy）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#17kafka的哪些场景中使用了零拷贝zero-copy)  

### [18、为什么要使用 Kafka？为什么要使用消息队列？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#18为什么要使用-kafka为什么要使用消息队列)  

### [19、Kafka中的 ISR、AR 又代表什么？ISR 的伸缩又指什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#19kafka中的-israr-又代表什么isr-的伸缩又指什么)  

### [20、如何控制消费的位置](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#20如何控制消费的位置)  

### [21、什么是生产者？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#21什么是生产者)  

### [22、在Kafka中，ZooKeeper的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#22在kafka中zookeeper的作用是什么)  

### [23、是什么确保了Kafka中服务器的负载平衡？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#23是什么确保了kafka中服务器的负载平衡)  

### [24、：35, 36, 37](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#24：35,-36,-37)  

### [25、Kafka可以接收的消息最大为多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#25kafka可以接收的消息最大为多少)  

### [26、解释Kafka Producer API的作用。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#26解释kafka-producer-api的作用。)  

### [27、：21, 23, 25, 26, 27, 28, 29, 30Apache Kafka对于有经验的人的面试](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#27：21,-23,-25,-26,-27,-28,-29,-30apache-kafka对于有经验的人的面试)  

### [28、什么是多租户？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka中级面试题汇总及答案（2021年Kafka面试题及答案大全）.md#28什么是多租户)  





