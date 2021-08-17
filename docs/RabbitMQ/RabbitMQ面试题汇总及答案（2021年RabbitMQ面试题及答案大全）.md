# RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）

RabbitMQ面试题及答案【最新版】RabbitMQ高级面试题大全(2021版)，发现网上很多RabbitMQ面试题及答案整理都没有答案，所以花了很长时间搜集，本套RabbitMQ面试题大全，RabbitMQ面试题大汇总，有大量经典的RabbitMQ面试题以及答案，包含RabbitMQ语言常见面试题、RabbitMQ工程师高级面试题及一些大厂RabbitMQ开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套RabbitMQ面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个RabbitMQ面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、消息基于什么传输？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#1消息基于什么传输)  


由于TCP连接的创建和销毁开销较大，且并发数受系统资源限制，会造成性能瓶颈。RabbitMQ使用信道的方式来传输数据。信道是建立在真实的TCP连接内的虚拟连接，且每条TCP连接上的信道数量没有限制。


### [2、多个消费者监听一个队列时，消息如何分发?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#2多个消费者监听一个队列时消息如何分发)  


轮询: 默认的策略，消费者轮流，平均地接收消息

公平分发: 根据消费者的能力来分发消息，给空闲的消费者发送更多消息

**当消费者有x条消息没有响应ACK时，不再给这个消费者发送消息**

```
channel.basicQos(int x)
```


### [3、交换器4种类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#3交换器4种类型)  


主要有以下4种。

fanout:把所有发送到该交换器的消息路由到所有与该交换器绑定的队列中。

direct:把消息路由到BindingKey和RoutingKey完全匹配的队列中。

topic:

匹配规则：

RoutingKey 为一个 点号'.': 分隔的字符串。 比如: java.xiaoka.show

BindingKey和RoutingKey一样也是点号“.“分隔的字符串。

BindingKey可使用 _ 和 # 用于做模糊匹配，_匹配一个单词，#匹配多个或者0个

headers:不依赖路由键匹配规则路由消息。是根据发送消息内容中的headers属性进行匹配。性能差，基本用不到。


### [4、Broker服务节点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#4broker服务节点)  


Broker可以看做RabbitMQ的服务节点。一般请下一个Broker可以看做一个RabbitMQ服务器。


### [5、什么是生产者Producer?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#5什么是生产者producer)  


消息生产者，就是投递消息的一方。

消息一般包含两个部分：`消息体`（payload)和`标签`(Label)。


### [6、消息如何分发？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#6消息如何分发)  


若该队列至少有一个消费者订阅，消息将以循环（round-robin）的方式发送给消费者。每条消息只会分发给一个订阅的消费者（前提是消费者能够正常处理消息并进行确认）。通过路由可实现多消费的功能


### [7、消息如何被优先消费？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#7消息如何被优先消费)  


生产者

```
Map<String, Object> argss = new HashMap<String, Object>();
argss.put("x-max-priority",10);
```

消费者

```
AMQP.BasicProperties properties = new AMQP.BasicProperties.Builder()
    .priority(5) // 优先级，默认为5，配合队列的 x-max-priority 属性使用
```


### [8、消费者接收消息过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#8消费者接收消息过程)  


1.Producer先连接到Broker,建立连接Connection,开启一个信道(Channel)。

2.向Broker请求消费响应的队列中消息，可能会设置响应的回调函数。

3.等待Broker回应并投递相应队列中的消息，接收消息。

4.消费者确认收到的消息,ack。

5.RabbitMq从队列中删除已经确定的消息。

6.关闭信道。

7.关闭连接。


### [9、RabbitMQ 什么是信道？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#9rabbitmq-什么是信道)  


信道：是生产者、消费者与RabbitMQ通信的渠道，生产者publish或是消费者subscribe一个队列都是通过信道来通信的。信道是建立在TCP连接上的虚拟连接。就是说RabbitMQ在一条TCP上建立成百上千个信道来达到多个线程处理，这个TCP被多个线程共享，每个线程对应一个信道，信道在RabbitMQ都有一个唯一的ID，保证了信道私有性，对应上唯一的线程使用。

**疑问：为什么不建立多个TCP连接？**

原因是RabbitMQ需要保证性能，系统为每个线程开辟一个TCP是非常消耗性能的，美妙成百上千的建立销毁TCP会严重消耗系统性能；所以RabbitMQ选择建立多个信道（建立在TCP的虚拟连接）连接到RabbitMQ上


### [10、RabbitMQ概念里的channel、exchange 和 queue是逻辑概念，还是对应着进程实体？作用分别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#10rabbitmq概念里的channelexchange-和-queue是逻辑概念还是对应着进程实体作用分别是什么)  


queue 具有自己的 erlang 进程；

exchange 内部实现为保存 binding 关系的查找表；

channel 是实际进行路由工作的实体，负责按照 routing_key 将 message投递给queue。

由 AMQP 协议描述可知，channel 是真实TCP连接之上的 虚拟连接 ， 所有AMQP 命令都是通过 channel 发送的，且每一个 channel 有 唯一的ID 。一个 channel 只能被单独一个操作系统线程使用，所以投递到特定的 channel 上的 message 是有顺序的。单一个操作系统线程上允许使用多个channel。


### [11、使用RabbitMQ有什么好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#11使用rabbitmq有什么好处)  

### [12、如何确保消息正确地发送至RabbitMQ？ 如何确保消息接收方消费了消息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#12如何确保消息正确地发送至rabbitmq-如何确保消息接收方消费了消息)  

### [13、为什么说保证 message 被可靠持久化的条件是 queue 和 exchange 具有durable 属性，同时 message 具有 persistent 属性才行？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#13为什么说保证-message-被可靠持久化的条件是-queue-和-exchange-具有durable-属性同时-message-具有-persistent-属性才行)  

### [14、rabbitmq 的使用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#14rabbitmq-的使用场景)  

### [15、RabbitMQ如何实现延时队列?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#15rabbitmq如何实现延时队列)  

### [16、什么是RoutingKey路由键？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#16什么是routingkey路由键)  

### [17、事务机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#17事务机制)  

### [18、使用rabbitmq的场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#18使用rabbitmq的场景)  

### [19、如何保证RabbitMQ消息的可靠传输？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#19如何保证rabbitmq消息的可靠传输)  

### [20、RabbitMQ事务机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#20rabbitmq事务机制)  

### [21、消息怎么路由？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#21消息怎么路由)  

### [22、如何确保消息接收方消费了消息?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#22如何确保消息接收方消费了消息)  

### [23、RoutingKey路由键？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#23routingkey路由键)  

### [24、RabbitMQ topic 主题模式(路由模式的一种)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#24rabbitmq-topic-主题模式路由模式的一种)  

### [25、RabbitMQ 上的一个 queue 中存放的 message 是否有数量限制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#25rabbitmq-上的一个-queue-中存放的-message-是否有数量限制)  

### [26、RabbitMQ 中的 Broker 是指什么？Cluster 又是指什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#26rabbitmq-中的-broker-是指什么cluster-又是指什么)  

### [27、RabbitMQ simple模式（即最简单的收发模式）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#27rabbitmq-simple模式即最简单的收发模式)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
