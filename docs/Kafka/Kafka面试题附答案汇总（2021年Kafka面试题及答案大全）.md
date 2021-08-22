# Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）

Kafka面试题及答案【最新版】Kafka高级面试题大全(2021版)，发现网上很多Kafka面试题及答案整理都没有答案，所以花了很长时间搜集，本套Kafka面试题大全，Kafka面试题大汇总，有大量经典的Kafka面试题以及答案，包含Kafka语言常见面试题、Kafka工程师高级面试题及一些大厂Kafka开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Kafka面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Kafka面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Kafka 高效文件存储设计特点：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#1kafka-高效文件存储设计特点：)  


**1、** Kafka 把 topic 中一个 parition 大文件分成多个小文件段，通过多个小文件段，就容易定

**2、** 期清除或删除已经消费完文件，减少磁盘占用。

**3、** 通过索引信息可以快速定位 message 和确定 response 的最大大小。

**4、** 通过 index 元数据全部映射到 memory，可以避免 segment file 的 IO 磁盘操作。

**5、** 通过索引文件稀疏存储，可以大幅降低 index 文件元数据占用空间大小。


### [2、partition 的数据如何保存到硬盘](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#2partition-的数据如何保存到硬盘)  


topic 中的多个 partition 以文件夹的形式保存到 broker，每个分区序号从 0 递增，

且消息有序

Partition 文件下有多个 segment（xxx.index，xxx.log）

segment 文件里的 大小和配置文件大小一致可以根据要求修改 默认为 1g

如果大小大于 1g 时，会滚动一个新的 segment 并且以上一个 segment 最后一条消息的偏移

量命名


### [3、当ack为-1时，什么情况下，Leader 认为一条消息 Commit了？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#3当ack为-1时什么情况下leader-认为一条消息-commit了)  


当ISR中所有Replica都向Leader发送ACK时，leader才commit，这时候producer才能认为一个请求中的消息都commit了。


### [4、为什么Kafka的复制至关重要？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#4为什么kafka的复制至关重要)  


由于复制，我们可以确保的消息不会丢失，并且可以在发生任何机器错误、程序错误或频繁的软件升级时使用。


### [5、Kafa consumer 是否可以消费指定分区消息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#5kafa-consumer-是否可以消费指定分区消息)  


Kafa consumer 消费消息时，向 broker 发出"fetch"请求去消费特定分区的消息，consumer

指定消息在日志中的偏移量（offset），就可以消费从这个位置开始的消息，customer 拥有

了 offset 的控制权，可以向后回滚去重新消费之前的消息，这是很有意义的


### [6、Broker的Heap Size如何设置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#6broker的heap-size如何设置)  


**1、** 其实对于SRE还是送分题，因为目前来讲大部分公司的业务系统都是使用Java开发，因此SRE对于基本的JVM相关的参数应该至少都是非常了解的，核心就在于JVM的配置以及GC相关的知识。

**2、** 标准答案：任何Java进程JVM堆大小的设置都需要仔细地进行考量和测试。一个常见的做法是，以默认的初始JVM堆大小运行程序，当系统达到稳定状态后，手动触发一次Full GC，然后通过JVM工具查看GC后的存活对象大小。之后，将堆大小设置成存活对象总大小的1.5~2倍。对于Kafka而言，这个方法也是适用的。不过，业界有个最佳实践，那就是将Broker的Heap Size固定为6GB。经过很多公司的验证，这个大小是足够且良好的。


### [7、什么是消费者或用户？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#7什么是消费者或用户)  


Kafka消费者订阅一个主题，并读取和处理来自该主题的消息。此外，有了消费者组的名字，消费者就给自己贴上了标签。换句话说，在每个订阅使用者组中，到主题的每个记录都传递到一个使用者实例。确保使用者实例可能位于单独的进程或单独的计算机上。


### [8、Kafka 如何实现延迟队列?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#8kafka-如何实现延迟队列)  


Kafka并没有使用JDK自带的Timer或者DelayQueue来实现延迟的功能，而是**基于时间轮自定义了一个用于实现延迟功能的定时器（SystemTimer）**。JDK的Timer和DelayQueue插入和删除操作的平均时间复杂度为O(nlog(n))，并不能满足Kafka的高性能要求，而基于时间轮可以将插入和删除操作的时间复杂度都降为**O(1)**。时间轮的应用并非Kafka独有，其应用场景还有很多，在Netty、Akka、Quartz、Zookeeper等组件中都存在时间轮的踪影。

底层使用数组实现，数组中的每个元素可以存放一个TimerTaskList对象。TimerTaskList是一个环形双向链表，在其中的链表项TimerTaskEntry中封装了真正的定时任务TimerTask.

Kafka中到底是怎么推进时间的呢？Kafka中的定时器借助了JDK中的DelayQueue来协助推进时间轮。具体做法是对于每个使用到的TimerTaskList都会加入到DelayQueue中。**Kafka中的TimingWheel专门用来执行插入和删除TimerTaskEntry的操作，而DelayQueue专门负责时间推进的任务**。再试想一下，DelayQueue中的第一个超时任务列表的expiration为200ms，第二个超时任务为840ms，这里获取DelayQueue的队头只需要O(1)的时间复杂度。如果采用每秒定时推进，那么获取到第一个超时的任务列表时执行的200次推进中有199次属于“空推进”，而获取到第二个超时任务时有需要执行639次“空推进”，这样会无故空耗机器的性能资源，这里采用DelayQueue来辅助以少量空间换时间，从而做到了“精准推进”。Kafka中的定时器真可谓是“知人善用”，用TimingWheel做最擅长的任务添加和删除操作，而用DelayQueue做最擅长的时间推进工作，相辅相成。



### [9、什么是Kafka？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#9什么是kafka)  


Kafka是**分布式-订阅消息系统**，它最初是由LinkedIn公司开发的，之后成为Apache项目的一部分，Kafka是一个分布式，可划分的，冗余备份的持久性的日志服务，它主要用于处理流式数据。


### [10、Kafka判断一个节点是否还活着有那两个条件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#10kafka判断一个节点是否还活着有那两个条件)  


**1、** 节点必须可以维护和ZooKeeper的连接，Zookeeper通过心跳机制检查每个节点的连接

**2、** 如果节点是个follower,他必须能及时的同步leader的写操作，延时不能太久


### [11、什么是Apache Kafka?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#11什么是apache-kafka)  

### [12、没有zookeeper可以使用Kafka吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#12没有zookeeper可以使用kafka吗)  

### [13、副本和ISR扮演什么角色？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#13副本和isr扮演什么角色)  

### [14、什么情况下一个 Broker 会从ISR中踢出去?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#14什么情况下一个-broker-会从isr中踢出去)  

### [15、简述Follower副本消息同步的完整流程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#15简述follower副本消息同步的完整流程)  

### [16、Kafka 的消费者如何消费数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#16kafka-的消费者如何消费数据)  

### [17、Java Consumer为什么采用单线程来获取消息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#17java-consumer为什么采用单线程来获取消息)  

### [18、消息队列的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#18消息队列的作用)  

### [19、Kafka的主要API有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#19kafka的主要api有哪些)  

### [20、Kafka 判断一个节点是否还活着有那两个条件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#20kafka-判断一个节点是否还活着有那两个条件)  

### [21、consumer_offsets是做什么用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#21consumer_offsets是做什么用的)  

### [22、没有ZooKeeper可以使用Kafka吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#22没有zookeeper可以使用kafka吗)  

### [23、Kafka中的 zookeeper 起到什么作用？可以不用zookeeper吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#23kafka中的-zookeeper-起到什么作用可以不用zookeeper吗)  

### [24、简单说一下ack机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#24简单说一下ack机制)  

### [25、Kafka和Flume之间的主要区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#25kafka和flume之间的主要区别是什么)  

### [26、Kafka中的 Broker 是干什么的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#26kafka中的-broker-是干什么的)  

### [27、Kafka的message格式是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Kafka/Kafka面试题附答案汇总（2021年Kafka面试题及答案大全）.md#27kafka的message格式是什么)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
