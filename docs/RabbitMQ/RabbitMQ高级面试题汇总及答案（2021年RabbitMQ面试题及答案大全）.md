# RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）

RabbitMQ面试题及答案【最新版】RabbitMQ高级面试题大全(2021版)，发现网上很多RabbitMQ面试题及答案整理都没有答案，所以花了很长时间搜集，本套RabbitMQ面试题大全，RabbitMQ面试题大汇总，有大量经典的RabbitMQ面试题以及答案，包含RabbitMQ语言常见面试题、RabbitMQ工程师高级面试题及一些大厂RabbitMQ开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套RabbitMQ面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个RabbitMQ面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Binding绑定？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#1binding绑定)  


通过绑定将交换器和队列关联起来，一般会指定一个BindingKey,这样RabbitMq就知道如何正确路由消息到队列了。


### [2、什么是RabbitMQ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#2什么是rabbitmq)  


RabbitMQ是一款开源的，Erlang编写的，消息中间件； 最大的特点就是消费并不需要确保提供方存在,实现了服务之间的高度解耦 可以用它来：解耦、异步、削峰。


### [3、什么情况下 producer 不主动创建 queue 是安全的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#3什么情况下-producer-不主动创建-queue-是安全的)  


1.message 是允许丢失的；2.实现了针对未处理消息的 republish 功能（例如采用Publisher Confirm 机制）。


### [4、消息如何保证幂等性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#4消息如何保证幂等性)  


生产者方面：可以对每条消息生成一个msgID，以控制消息重复投递

```
AMQP.BasicProperties properties = new AMQP.BasicProperties.Builder()
porperties.messageId(String.valueOF(UUID.randomUUID()))
```

消费者方面：消息体中必须携带一个业务ID，如银行流水号，消费者可以根据业务ID去重，避免重复消费


### [5、解耦、异步、削峰是什么？。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#5解耦异步削峰是什么。)  


- MQ 解耦

A 系统发送数据到 BCD 三个系统，通过接口调用发送。如果 E 系统也要这个数据呢？那如果 C 系统现在不需要了呢？A 系统负责人几乎崩溃…A 系统跟其它各种乱七八糟的系统严重耦合，A 系统产生一条比较关键的数据，很多系统都需要 A 系统将这个数据发送过来。如果使用 MQ，A 系统产生一条数据，发送到 MQ 里面去，哪个系统需要数据自己去 MQ 里面消费。如果新系统需要数据，直接从 MQ 里消费即可；如果某个系统不需要这条数据了，就取消对 MQ 消息的消费即可。这样下来，A 系统压根儿不需要去考虑要给谁发送数据，不需要维护这个代码，也不需要考虑人家是否调用成功、失败超时等情况。

就是一个系统或者一个模块，调用了多个系统或者模块，互相之间的调用很复杂，维护起来很麻烦。但是其实这个调用是不需要直接同步调用接口的，如果用 MQ 给它异步化解耦。

- 异步

A 系统接收一个请求，需要在自己本地写库，还需要在 BCD 三个系统写库，自己本地写库要 3ms，BCD 三个系统分别写库要 300ms、450ms、200ms。最终请求总延时是 3 + 300 + 450 + 200 = 953ms，接近 1s，用户感觉搞个什么东西，慢死了慢死了。用户通过浏览器发起请求。如果使用 MQ，那么 A 系统连续发送 3 条消息到 MQ 队列中，假如耗时 5ms，A 系统从接受一个请求到返回响应给用户，总时长是 3 + 5 = 8ms。

- 削峰

减少高峰时期对服务器压力。


### [6、RabbitMQ 概念里的 channel、exchange 和 queue 这些东东是逻辑概念，还是对应着进程实体？这些东东分别起什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#6rabbitmq-概念里的-channelexchange-和-queue-这些东东是逻辑概念还是对应着进程实体这些东东分别起什么作用)  


queue 具有自己的 erlang 进程；exchange 内部实现为保存 binding 关系的查找表；channel 是实际进行路由工作的实体，即负责按照 routing_key 将 message 投递给queue 。由 AMQP 协议描述可知，channel 是真实 TCP 连接之上的虚拟连接，所有AMQP 命令都是通过 channel 发送的，且每一个 channel 有唯一的 ID。

一个 channel 只能被单独一个操作系统线程使用，故投递到特定 channel 上的 message 是有顺序的。但一个操作系统线程上允许使用多个 channel 。channel 号为 0 的 channel 用于处理所有对于当前 connection 全局有效的帧，而 1-65535 号 channel 用于处理和特定 channel 相关的帧。AMQP 协议给出的 channel ，其中每一个 channel 运行在一个独立的线程上，多线程共享同一个 socket。


### [7、什么是MQ](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#7什么是mq)  


MQ就是消息队列。是软件和软件进行通信的中间件产品


### [8、RabbitMQ中消息可能有的几种状态?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#8rabbitmq中消息可能有的几种状态)  


alpha: 消息内容(包括消息体、属性和 headers) 和消息索引都存储在内存中 。

beta: 消息内容保存在磁盘中，消息索引保存在内存中。

gamma: 消息内容保存在磁盘中，消息索引在磁盘和内存中都有 。

delta: 消息内容和索引都在磁盘中 。



### [9、消息基于什么传输？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#9消息基于什么传输)  


由于 TCP 连接的创建和销毁开销较大，且并发数受系统资源限制，会造成性能瓶颈。RabbitMQ 使用信道的方式来传输数据。信道是建立在真实的 TCP 连接内的虚拟连接，且每条 TCP 连接上的信道数量没有限制。


### [10、向不存在的 exchange 发 publish 消息会发生什么？向不存在的 queue 执行consume 动作会发生什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#10向不存在的-exchange-发-publish-消息会发生什么向不存在的-queue-执行consume-动作会发生什么)  


都会收到 Channel.Close 信令告之不存在（内含原因 404 NOT_FOUND）。


### [11、设计MQ思路](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#11设计mq思路)  

### [12、RabbitMQ特点?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#12rabbitmq特点)  

### [13、vhost 是什么? 起什么作用?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#13vhost-是什么-起什么作用)  

### [14、MQ的优点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#14mq的优点)  

### [15、消费者接收消息过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#15消费者接收消息过程)  

### [16、Kafka、ActiveMQ、RabbitMQ、RocketMQ 有什么优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#16kafkaactivemqrabbitmqrocketmq-有什么优缺点)  

### [17、为什么要使用rabbitmq](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#17为什么要使用rabbitmq)  

### [18、RabbitMQ队列结构？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#18rabbitmq队列结构)  

### [19、如何确保消息正确地发送至 RabbitMQ？ 如何确保消息接收方消费了消息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#19如何确保消息正确地发送至-rabbitmq-如何确保消息接收方消费了消息)  

### [20、延迟队列？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#20延迟队列)  

### [21、RabbitMQ中消息可能有的几种状态?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#21rabbitmq中消息可能有的几种状态)  

### [22、客户端连接到 cluster 中的任意 node 上是否都能正常工作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#22客户端连接到-cluster-中的任意-node-上是否都能正常工作)  

### [23、消费者某些原因无法处理当前接受的消息如何来拒绝？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#23消费者某些原因无法处理当前接受的消息如何来拒绝)  

### [24、什么是Binding绑定？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#24什么是binding绑定)  

### [25、如何自动删除长时间没有消费的消息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#25如何自动删除长时间没有消费的消息)  

### [26、消息传输保证层级？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#26消息传输保证层级)  

### [27、RabbitMQ消息确认过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ高级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#27rabbitmq消息确认过程)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
