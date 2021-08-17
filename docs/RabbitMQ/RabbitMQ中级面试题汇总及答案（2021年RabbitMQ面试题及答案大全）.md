# RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）

RabbitMQ面试题及答案【最新版】RabbitMQ高级面试题大全(2021版)，发现网上很多RabbitMQ面试题及答案整理都没有答案，所以花了很长时间搜集，本套RabbitMQ面试题大全，RabbitMQ面试题大汇总，有大量经典的RabbitMQ面试题以及答案，包含RabbitMQ语言常见面试题、RabbitMQ工程师高级面试题及一些大厂RabbitMQ开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套RabbitMQ面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个RabbitMQ面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、RabbitMQ有那些基本概念？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#1rabbitmq有那些基本概念)  


**1、** Broker：简单来说就是消息队列服务器实体

**2、** Exchange：消息交换机，它指定消息按什么规则，路由到哪个队列

**3、** Queue：消息队列载体，每个消息都会被投入到一个或多个队列

**4、** Binding：绑定，它的作用就是把exchange和queue按照路由规则绑定起来

**5、** Routing Key：路由关键字，exchange根据这个关键字进行消息投递

**6、** VHost：vhost 可以理解为虚拟 broker ，即 mini-RabbitMQ server。其内部均含有独立的 queue、exchange 和 binding 等，但最最重要的是，其拥有独立的权限系统，可以做到 vhost 范围的用户控制。当然，从 RabbitMQ 的全局角度，vhost 可以作为不同权限隔离的手段（一个典型的例子就是不同的应用可以跑在不同的 vhost 中）。

**7、** Producer：消息生产者，就是投递消息的程序

**8、** Consumer：消息消费者，就是接受消息的程序

**9、** Channel：消息通道，在客户端的每个连接里，可建立多个channel，每个channel代表一个会话任务

由`Exchange`、`Queue`、`RoutingKey`三个才能决定一个从Exchange到Queue的唯一的线路。


### [2、交换器无法根据自身类型和路由键找到符合条件队列时，有哪些处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#2交换器无法根据自身类型和路由键找到符合条件队列时有哪些处理)  


mandatory ：true 返回消息给生产者。

mandatory: false 直接丢弃。


### [3、RabbitMQ是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#3rabbitmq是什么)  


RabbitMQ是实现了高级消息队列协议（AMQP）的开源消息代理软件（亦称面向消息的中间件）。RabbitMQ服务器是用Erlang语言编写的，而群集和故障转移是构建在开放电信平台框架上的。所有主要的编程语言均有与代理接口通讯的客户端库。


### [4、RabbitMQ 包括哪些要素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#4rabbitmq-包括哪些要素)  


1. 生产者 ：消息的创建者，发送到RabbitMQ
2. 消费者 ：连接到RabbitMQ，订阅到队列上，消费消息，持续订阅（basicConsumer）和单条订阅（basicGet）
3. 消息 ：包含有效载荷和标签，有效载荷指要传输的数据，标签描述了有效载荷，并且RabbitMQ用它来决定谁获得消息，消费者只能拿到有效载荷，并不知道生产者是谁。


### [5、RabbitMQ routing路由模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#5rabbitmq-routing路由模式)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/030/5/35_7.png#alt=35%5C_7.png)

**1、** 消息生产者将消息发送给交换机按照路由判断,路由是字符串(info) 当前产生的消息携带路由字符(对象的方法),交换机根据路由的key,只能匹配上路由key对应的消息队列,对应的消费者才能消费消息;

**2、** 根据业务功能定义路由字符串

**3、** 从系统的代码逻辑中获取对应的功能字符串,将消息任务扔到对应的队列中。

**4、** 业务场景:error 通知;EXCEPTION;错误通知的功能;传统意义的错误通知;客户通知;利用key路由,可以将程序中的错误封装成消息传入到消息队列中,开发者可以自定义消费者,实时接收错误;


### [6、什么是Broker服务节点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#6什么是broker服务节点)  


Broker可以看做RabbitMQ的服务节点。一般请下一个Broker可以看做一个RabbitMQ服务器。


### [7、如何确保消息正确地发送至RabbitMQ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#7如何确保消息正确地发送至rabbitmq)  


RabbitMQ使用发送方确认模式，确保消息正确地发送到RabbitMQ。发送方确认模式：将信道设置成`confirm`模式（发送方确认模式），则所有在信道上的消息都会被指派一个唯一的ID。一旦消息被投递到目的队列后，或者消息被写入磁盘后（可持久化的消息），信道会发送一个确认给生产者（包含消息唯一ID）。如果`RabbitMQ`发生内部错误从而导致消息丢失，会发送一条`nack`（not acknowledged，未确认）消息。发送方确认模式是异步的，生产者应用程序在等待确认的同时，可以继续发送消息。当确认消息到达生产者应用程序，生产者应用程序的回调方法就会被触发来处理确认消息。


### [8、如何确保消息不丢失？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#8如何确保消息不丢失)  


消息持久化，当然前提是队列必须持久化

RabbitMQ 确保持久性消息能从服务器重启中恢复的方式是，将它们写入磁盘上的一个持久化日志文件，当一条持久性消息到持久交换器上时，RabbitMQ 会在消息提交到日志文件后才发送响应。

一旦消费者从持久队列中消费了一条持久化消息，RabbitMQ 会在持久化日志中把这条消息标记为等待垃圾收集。如果持久化消息在被消费之前 RabbitMQ 重启，那么 RabbitMQ 会自动重建交换器和队列（以及绑定），并重新持久化日志文件中的消息到合适的队列。


### [9、Basic.Reject 的用法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#9basicreject-的用法是什么)  


该信令可用于 consumer 对收到的 message 进行 reject 。若在该信令中设置

requeue=true，则当 RabbitMQ server 收到该拒绝信令后，会将该 message 重新发送到下一个处于 consume 状态的 consumer 处（理论上仍可能将该消息发送给当前consumer）。若设置 requeue=false ，则 RabbitMQ server 在收到拒绝信令后，将直接将该message 从 queue 中移除。

另外一种移除 queue 中 message 的小技巧是，consumer 回复 Basic.Ack 但不对获取到的message 做任何处理。而 Basic.Nack 是对 Basic.Reject 的扩展，以支持一次拒绝多条 message 的能力。



### [10、MQ 有哪些常见问题？如何解决这些问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#10mq-有哪些常见问题如何解决这些问题)  


MQ 的常见问题有：

**1、** 消息的顺序问题

**2、** 消息的重复问题

**消息的顺序问题**

消息有序指的是可以按照消息的发送顺序来消费。

假如生产者产生了 2 条消息：M1、M2，假定 M1 发送到 S1，M2 发送到 S2，如果要保证 M1 先于 M2 被消费，怎么做？

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/030/5/35_2.png#alt=35%5C_2.png)

**解决方案：**

**1、** 保证生产者 - MQServer - 消费者是一对一对一的关系

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/030/5/35_3.png#alt=35%5C_3.png)

**缺陷：**

**1、** 并行度就会成为消息系统的瓶颈（吞吐量不够）

**2、** 更多的异常处理，比如：只要消费端出现问题，就会导致整个处理流程阻塞，我们不得不花费更多的精力来解决阻塞的问题。 （2）通过合理的设计或者将问题分解来规避。

**3、** 不关注乱序的应用实际大量存在

**4、** 队列无序并不意味着消息无序 所以从业务层面来保证消息的顺序而不仅仅是依赖于消息系统，是一种更合理的方式。

**消息的重复问题**

造成消息重复的根本原因是：网络不可达。

**1、** 所以解决这个问题的办法就是绕过这个问题。那么问题就变成了：如果消费端收到两条一样的消息，应该怎样处理？

**2、** 消费端处理消息的业务逻辑保持幂等性。只要保持幂等性，不管来多少条重复消息，最后处理的结果都一样。保证每条消息都有唯一编号且保证消息处理成功与去重表的日志同时出现。利用一张日志表来记录已经处理成功的消息的 ID，如果新到的消息 ID 已经在日志表中，那么就不再处理这条消息。


### [11、生产者Producer?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#11生产者producer)  

### [12、AMQP是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#12amqp是什么)  

### [13、如何解决RabbitMQ丢数据的问题?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#13如何解决rabbitmq丢数据的问题)  

### [14、使用RabbitMQ有什么好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#14使用rabbitmq有什么好处)  

### [15、什么是消费者Consumer?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#15什么是消费者consumer)  

### [16、消息在什么时候会变成死信?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#16消息在什么时候会变成死信)  

### [17、RabbitMQ的工作模式有几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#17rabbitmq的工作模式有几种)  

### [18、Consumer Cancellation Notification 机制用于什么场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#18consumer-cancellation-notification-机制用于什么场景)  

### [19、什么是Queue队列？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#19什么是queue队列)  

### [20、无法被路由的消息去了哪里?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#20无法被路由的消息去了哪里)  

### [21、优先级队列？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#21优先级队列)  

### [22、在单 node 系统和多 node 构成的 cluster 系统中声明 queue、exchange ，以及进行 binding 会有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#22在单-node-系统和多-node-构成的-cluster-系统中声明-queueexchange-以及进行-binding-会有什么不同)  

### [23、AMQP模型的几大组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#23amqp模型的几大组件)  

### [24、如何保证消息不被重复消费？或者说，如何保证消息消费时的幂等性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#24如何保证消息不被重复消费或者说如何保证消息消费时的幂等性)  

### [25、为什么不应该对所有的 message 都使用持久化机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#25为什么不应该对所有的-message-都使用持久化机制)  

### [26、RAM node 和 disk node 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#26ram-node-和-disk-node-的区别)  

### [27、RabbitMQ publish/subscribe发布订阅(共享资源)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/RabbitMQ/RabbitMQ中级面试题汇总及答案（2021年RabbitMQ面试题及答案大全）.md#27rabbitmq-publish/subscribe发布订阅共享资源)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
