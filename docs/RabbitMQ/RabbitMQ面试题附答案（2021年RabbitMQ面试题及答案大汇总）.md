# RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）

RabbitMQ面试题及答案【最新版】RabbitMQ高级面试题大全(2021版)，发现网上很多RabbitMQ面试题及答案整理都没有答案，所以花了很长时间搜集，本套RabbitMQ面试题大全，RabbitMQ面试题大汇总，有大量经典的RabbitMQ面试题以及答案，包含RabbitMQ语言常见面试题、RabbitMQ工程师高级面试题及一些大厂RabbitMQ开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套RabbitMQ面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个RabbitMQ面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何避免消息重复投递或重复消费?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#1如何避免消息重复投递或重复消费)  


在消息生产时，MQ内部针对每条生产者发送的消息生成一个`inner-msg-id`，作为去重和幂等的依据（消息投递失败并重传），避免重复的消息进入队列；在消息消费时，要求消息体中必须要有一个`bizId`（对于同一业务全局唯一，如支付ID、订单ID、帖子ID等）作为去重和幂等的依据，避免同一条消息被重复消费。

这个问题针对业务场景来答分以下几点：

**1、** 拿到这个消息做数据库的insert操作。然后给这个消息做一个唯一主键，那么就算出现重复消费的情况，就会导致主键冲突，避免数据库出现脏数据。

**2、** 拿到这个消息做Redis的set的操作，因为你无论set几次结果都是一样的，set操作本来就算幂等操作。

**3、** 如果上面两种情况还不行。准备一个第三方介质,来做消费记录。以Redis为例，给消息分配一个全局id，只要消费过该消息，将<id,message>以K-V形式写入Redis。那消费者开始消费前，先去Redis中查询有没消费记录即可。


### [2、RabbitMQ 允许发送的 message 最大可达多大？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#2rabbitmq-允许发送的-message-最大可达多大)  


根据 AMQP 协议规定，消息体的大小由 64-bit 的值来指定，所以你就可以知道到底能发多大的数据了。


### [3、vhost 是什么？起什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#3vhost-是什么起什么作用)  


vhost 可以理解为虚拟 broker ，即 mini-RabbitMQ server。其内部均含有独立的queue、exchange 和 binding 等，但最最重要的是，其拥有独立的权限系统，可以做到vhost 范围的用户控制。

当然，从 RabbitMQ 的全局角度，vhost 可以作为不同权限隔离的手段（一个典型的例子就是不同的应用可以跑在不同的 vhost 中）。


### [4、发送确认机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#4发送确认机制)  


生产者把信道设置为confirm确认模式,设置后，所有再改信道发布的消息都会被指定一个唯一的ID，一旦消息被投递到所有匹配的队列之后，RabbitMQ就会发送一个确认（Basic.Ack)给生产者（包含消息的唯一ID)，这样生产者就知道消息到达对应的目的地了。


### [5、生产者消息如何运转？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#5生产者消息如何运转)  


**1、** Producer先连接到Broker,建立连接Connection,开启一个信道(Channel)。

**2、** Producer声明一个交换器并设置好相关属性。

**3、** Producer声明一个队列并设置好相关属性。

**4、** Producer通过路由键将交换器和队列绑定起来。

**5、** Producer发送消息到Broker,其中包含路由键、交换器等信息。

**6、** 相应的交换器根据接收到的路由键查找匹配的队列。

**7、** 如果找到，将消息存入对应的队列，如果没有找到，会根据生产者的配置丢弃或者退回给生产者。

**8、** 关闭信道。

**9、** 管理连接。


### [6、如何保证RabbitMQ消息的顺序性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#6如何保证rabbitmq消息的顺序性)  


**1、** 拆分多个 queue(消息队列)，每个 queue(消息队列) 一个 consumer(消费者)，就是多一些 queue (消息队列)而已，确实是麻烦点；

**2、** 或者就一个 queue (消息队列)但是对应一个 consumer(消费者)，然后这个 consumer(消费者)内部用内存队列做排队，然后分发给底层不同的 worker 来处理。


### [7、消息怎么路由？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#7消息怎么路由)  


**1、** 消息提供方->路由->一至多个队列

**2、** 消息发布到交换器时，消息将拥有一个路由键（routing key），在消息创建时设定。

**3、** 通过队列路由键，可以把队列绑定到交换器上。

**4、** 消息到达交换器后，RabbitMQ会将消息的路由键与队列的路由键进行匹配（针对不同的交换器有不同的路由规则）；

**常用的交换器主要分为一下三种**

**1、** fanout：如果交换器收到消息，将会广播到所有绑定的队列上

**2、** direct：如果路由键完全匹配，消息就被投递到相应的队列

**3、** topic：可以使来自不同源头的消息能够到达同一个队列。 使用topic交换器时，可以使用通配符


### [8、如何保证RabbitMQ不被重复消费？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#8如何保证rabbitmq不被重复消费)  


1. 正常情况下，消费者在消费消息的时候，消费完毕后，会发送一个确认信息给消息队列，消息队列就知道该消息被消费了，就会将该消息从消息队列中删除。
2. 但是因为网络传输等故障，确认信息没有传送到消息队列，导致消息队列不知道自己已经消费过该消息了，再次将消息分发给其他的消费者。

**解决思路：**

1. 保证消息的唯一性，就算是多次传输，不要让消息的多次消费带来影响；
2. 保证消息幂等性；
3. 比如：在写入消息队列的数据做唯一标识，消费消息时，根据唯一标识判断该消息是否被消费过。


### [9、什么是元数据？元数据分为哪些类型？包括哪些内容？与 cluster 相关的元数据有哪些？元数据是如何保存的？元数据在 cluster 中是如何分布的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#9什么是元数据元数据分为哪些类型包括哪些内容与-cluster-相关的元数据有哪些元数据是如何保存的元数据在-cluster-中是如何分布的)  


在非 cluster 模式下，元数据主要分为 Queue 元数据（queue 名字和属性等）、Exchange 元数据（exchange 名字、类型和属性等）、Binding 元数据（存放路由关系的查找表）、Vhost 元数据（vhost 范围内针对前三者的名字空间约束和安全属性设置）。

在cluster 模式下，还包括 cluster 中 node 位置信息和 node 关系信息。元数据按照 erlangnode 的类型确定是仅保存于 RAM 中，还是同时保存在 RAM 和 disk 上。元数据在cluster 中是全 node 分布的。


### [10、Exchange交换器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#10exchange交换器)  


Exchange:生产者将消息发送到交换器，有交换器将消息路由到一个或者多个队列中。当路由不到时，或返回给生产者或直接丢弃。


### [11、你们公司生产环境用的是什么消息中间件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#11你们公司生产环境用的是什么消息中间件)  

### [12、消费者某些原因无法处理当前接受的消息如何来拒绝？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#12消费者某些原因无法处理当前接受的消息如何来拒绝)  

### [13、如何解决消息队列的延时以及过期失效问题？消息队列满了以后该怎么处理？有几百万消息持续积压几小时，怎么办？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#13如何解决消息队列的延时以及过期失效问题消息队列满了以后该怎么处理有几百万消息持续积压几小时怎么办)  

### [14、如何避免消息重复投递或重复消费？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#14如何避免消息重复投递或重复消费)  

### [15、消费者Consumer?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#15消费者consumer)  

### [16、如何保证消息的顺序性?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#16如何保证消息的顺序性)  

### [17、如何防止出现 blackholed 问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#17如何防止出现-blackholed-问题)  

### [18、消息基于什么传输?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#18消息基于什么传输)  

### [19、Queue队列？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#19queue队列)  

### [20、RabbitMQ的特点?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#20rabbitmq的特点)  

### [21、RabbitMQ work工作模式(资源的竞争)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#21rabbitmq-work工作模式资源的竞争)  

### [22、什么情况下会出现 blackholed 问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#22什么情况下会出现-blackholed-问题)  

### [23、RabbitMQ 中的 broker 是指什么？cluster 又是指什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#23rabbitmq-中的-broker-是指什么cluster-又是指什么)  

### [24、如何保证RabbitMQ消息的可靠传输？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#24如何保证rabbitmq消息的可靠传输)  

### [25、导致的死信的几种原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#25导致的死信的几种原因)  

### [26、cluster 中 node 的失效会对 consumer 产生什么影响？若是在 cluster 中创建了mirrored queue ，这时 node 失效会对 consumer 产生什么影响？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#26cluster-中-node-的失效会对-consumer-产生什么影响若是在-cluster-中创建了mirrored-queue-这时-node-失效会对-consumer-产生什么影响)  

### [27、如何保证高可用的？RabbitMQ 的集群](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#27如何保证高可用的rabbitmq-的集群)  

### [28、能够在地理上分开的不同数据中心使用 RabbitMQ cluster 么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题附答案（2021年RabbitMQ面试题及答案大汇总）.md#28能够在地理上分开的不同数据中心使用-rabbitmq-cluster-么)  





