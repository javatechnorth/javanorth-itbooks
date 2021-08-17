# RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）

RabbitMQ面试题及答案【最新版】RabbitMQ高级面试题大全(2021版)，发现网上很多RabbitMQ面试题及答案整理都没有答案，所以花了很长时间搜集，本套RabbitMQ面试题大全，RabbitMQ面试题大汇总，有大量经典的RabbitMQ面试题以及答案，包含RabbitMQ语言常见面试题、RabbitMQ工程师高级面试题及一些大厂RabbitMQ开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套RabbitMQ面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个RabbitMQ面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、RabbitMQ消息是如何路由的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#1rabbitmq消息是如何路由的)  


**消息路由必须有三部分：交换器、路由、绑定。**

生产者把消息发布到交换器上，绑定决定了消息如何从路由器路由到特定的队列；消息最终到达队列，并被消费者接收。

1. 消息发布到交换器时，消息将拥有一个 路由键（routing key） ， 在消息创建时设定。
2. 通过队列路由键，可以把队列绑定到交换器上。
3. 消息到达交换器后，RabbitMQ会将消息的路由键与队列的路由键进行匹配（针对不同的交换器有不同的路由规则）。如果能够匹配到队列，则消息会投递到相应队列中；如果不能匹配到任何队列，消息将进入"黑洞"。

**常用的交换器主要分为以下三种：**

1. direct ：如果路由键完全匹配，消息就会被投递到相应的队列；每个AMQP的实现都必须有一个direct交换器，包含一个空白字符串名称的默认交换器。声明一个队列时，会自动绑定到默认交换器，并且以队列名称作为路由键：channel -> basic_public($msg, '', 'queue-name')
2. fanout ： 如果交换器收到消息，将会广播到所有绑定的队列上；
3. topic ：可以使来自不同源头的消息能够到达同一个队列。使用topic交换器时，可以使用通配符，比如："*" 匹配特定位置的任意文本，"." 把路由键分为了几个标识符， "#" 匹配所有规则等。
4. 特别注意：发往topic交换器的消息不能随意的设置选择键（routing_key），必须是有"."隔开的一系列的标识符组成。


### [2、生产者消息运转？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#2生产者消息运转)  


1.Producer先连接到Broker,建立连接Connection,开启一个信道(Channel)。

2.Producer声明一个交换器并设置好相关属性。

3.Producer声明一个队列并设置好相关属性。

4.Producer通过路由键将交换器和队列绑定起来。

5.Producer发送消息到Broker,其中包含路由键、交换器等信息。

6.相应的交换器根据接收到的路由键查找匹配的队列。

7.如果找到，将消息存入对应的队列，如果没有找到，会根据生产者的配置丢弃或者退回给生产者。

8.关闭信道。

9.管理连接。


### [3、为什么 heavy RPC 的使用场景下不建议采用 disk node ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#3为什么-heavy-rpc-的使用场景下不建议采用-disk-node-)  


heavy RPC 是指在业务逻辑中高频调用 RabbitMQ 提供的 RPC 机制，导致不断创建、销毁 reply queue ，进而造成 disk node 的性能问题（因为会针对元数据不断写盘）。所以在使用 RPC 机制时需要考虑自身的业务场景。


### [4、消息队列有什么缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#4消息队列有什么缺点)  


**缺点有以下几个：**

**1、** 系统可用性降低

本来系统运行好好的，现在你非要加入个消息队列进去，那消息队列挂了，你的系统不是呵呵了。因此，系统可用性会降低；

**2、** 系统复杂度提高

加入了消息队列，要多考虑很多方面的问题，比如：一致性问题、如何保证消息不被重复消费、如何保证消息可靠性传输等。因此，需要考虑的东西更多，复杂性增大。

**3、** 一致性问题

A 系统处理完了直接返回成功了，人都以为你这个请求就成功了；但是问题是，要是 BCD 三个系统那里，BD 两个系统写库成功了，结果 C 系统写库失败了，咋整？你这数据就不一致了。

所以消息队列实际是一种非常复杂的架构，你引入它有很多好处，但是也得针对它带来的坏处做各种额外的技术方案和架构来规避掉，做好之后，你会发现，妈呀，系统复杂度提升了一个数量级，也许是复杂了 10 倍。但是关键时刻，用，还是得用的。


### [5、“dead letter”queue 的用途？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#5“dead-letterqueue-的用途)  


当消息被 RabbitMQ server 投递到 consumer 后，但 consumer 却通过 Basic.Reject进行了拒绝时（同时设置 requeue=false），那么该消息会被放入“dead letter”queue 中。该 queue 可用于排查 message 被 reject 或 undeliver 的原因。


### [6、AMQP模型的几大组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#6amqp模型的几大组件)  


**1、** 交换器 (Exchange)：消息代理服务器中用于把消息路由到队列的组件。

**2、** 队列 (Queue)：用来存储消息的数据结构，位于硬盘或内存中。

**3、** 绑定 (Binding)：一套规则，告知交换器消息应该将消息投递给哪个队列。


### [7、routing_key 和 binding_key 的最大长度是多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#7routing_key-和-binding_key-的最大长度是多少)  


255 字节。


### [8、RabbitMQ基本概念](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#8rabbitmq基本概念)  


**1、** Broker： 简单来说就是消息队列服务器实体

**2、** Exchange： 消息交换机，它指定消息按什么规则，路由到哪个队列

**3、** Queue： 消息队列载体，每个消息都会被投入到一个或多个队列

**4、** Binding： 绑定，它的作用就是把exchange和queue按照路由规则绑定起来

**5、** Routing Key： 路由关键字，exchange根据这个关键字进行消息投递

**6、** VHost： vhost 可以理解为虚拟 broker ，即 mini-RabbitMQ server。其内部均含有独立的 queue、exchange 和 binding 等，但最最重要的是，其拥有独立的权限系统，可以做到 vhost 范围的用户控制。当然，从 RabbitMQ 的全局角度，vhost 可以作为不同权限隔离的手段（一个典型的例子就是不同的应用可以跑在不同的 vhost 中）。

**7、** Producer： 消息生产者，就是投递消息的程序

**8、** Consumer： 消息消费者，就是接受消息的程序

**9、** Channel： 消息通道，在客户端的每个连接里，可建立多个channel，每个channel代表一个会话任务

由Exchange、Queue、RoutingKey三个才能决定一个从Exchange到Queue的唯一的线路。


### [9、死信队列？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#9死信队列)  


DLX，全称为 Dead-Letter-Exchange，死信交换器，死信邮箱。当消息在一个队列中变成死信 (dead message) 之后，它能被重新被发送到另一个交换器中，这个交换器就是 DLX，绑定 DLX 的队列就称之为死信队列。


### [10、队列结构？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#10队列结构)  


通常由以下两部分组成？

rabbit_amqqueue_process :负责协议相关的消息处理，即接收生产者发布的消息、向消费者交付消息、处理消息的确认(包括生产端的 confirm 和消费端的 ack) 等。

backing_queue:是消息存储的具体形式和引擎，并向 rabbit amqqueue process 提供相关的接口以供调用。


### [11、如何保证消息的可靠性投递?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#11如何保证消息的可靠性投递)  

### [12、RabbitMQ的集群模式有几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#12rabbitmq的集群模式有几种)  

### [13、消息如何分发?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#13消息如何分发)  

### [14、死信队列和延迟队列的使用?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#14死信队列和延迟队列的使用)  

### [15、AMQP协议3层？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#15amqp协议3层)  

### [16、消息怎么路由？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#16消息怎么路由)  

### [17、消息如何分发？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#17消息如何分发)  

### [18、什么是Exchange交换器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#18什么是exchange交换器)  

### [19、什么是rabbitmq](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#19什么是rabbitmq)  

### [20、AMQP协议3层？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#20amqp协议3层)  

### [21、如何确保消息不丢失？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#21如何确保消息不丢失)  

### [22、消息传输保证层级？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#22消息传输保证层级)  

### [23、消费者获取消息的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#23消费者获取消息的方式)  

### [24、集群中的节点类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#24集群中的节点类型)  

### [25、mq的缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#25mq的缺点)  

### [26、rabbitmq的集群](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#26rabbitmq的集群)  

### [27、集群节点类型有几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#27集群节点类型有几种)  

### [28、vhost?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ面试题带答案（2021年RabbitMQ面试题及答案大汇总）.md#28vhost)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
