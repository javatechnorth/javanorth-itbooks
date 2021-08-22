# Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）

Dubbo面试题及答案【最新版】Dubbo高级面试题大全(2021版)，发现网上很多Dubbo面试题及答案整理都没有答案，所以花了很长时间搜集，本套Dubbo面试题大全，Dubbo面试题大汇总，有大量经典的Dubbo面试题以及答案，包含Dubbo语言常见面试题、Dubbo工程师高级面试题及一些大厂Dubbo开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Dubbo面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Dubbo面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、说说核心的配置有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#1说说核心的配置有哪些)  

| 配置 | 配置说明 |
| --- | --- |
| dubbo:service | 服务配置 |
| dubbo:reference | 引用配置 |
| dubbo:protocol | 协议配置 |
| dubbo:application | 应用配置 |
| dubbo:module | 模块配置 |
| dubbo:registry | 注册中心配置 |
| dubbo:monitor | 监控中心配置 |
| dubbo:provider | 提供方配置 |
| dubbo:consumer | 消费方配置 |
| dubbo:method | 方法配置 |
| dubbo:argument | 参数配置 |



### [2、Dubbo集群提供了哪些负载均衡策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#2dubbo集群提供了哪些负载均衡策略)  


**1、** Random LoadBalance: 随机选取提供者策略，有利于动态调整提供者权重。截面碰撞率高，调用次数越多，分布越均匀。

**2、** RoundRobin LoadBalance: 轮循选取提供者策略，平均分布，但是存在请求累积的问题。

**3、** LeastActive LoadBalance: 最少活跃调用策略，解决慢提供者接收更少的请求。

**4、** ConstantHash LoadBalance: 一致性 Hash 策略，使相同参数请求总是发到同一提供者，一台机器宕机，可以基于虚拟节点，分摊至其他提供者，避免引起提供者的剧烈变动。

`默认为 Random 随机调用。`


### [3、Dubbo 使用的是什么通信框架?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#3dubbo-使用的是什么通信框架)  


默认使用 NIO Netty 框架


### [4、服务调用是阻塞的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#4服务调用是阻塞的吗)  


默认是阻塞的，可以异步调用，没有返回值的可以这么做。

Dubbo 是基于 NIO 的非阻塞实现并行调用，客户端不需要启动多线程即可完成并行调用多个远程服务，相对多线程开销较小，异步调用会返回一个 Future 对象。


### [5、dubbo 在安全机制方面如何解决的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#5dubbo-在安全机制方面如何解决的)  


dubbo 通过 token 令牌防止用户绕过注册中心直连，然后在注册中心管理授权，dubbo 提供了黑白名单，控制服务所允许的调用方。


### [6、Dubbo 超时时间怎样设置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#6dubbo-超时时间怎样设置)  


Dubbo 超时时间设置有两种方式：

服务提供者端设置超时时间，在 Dubbo 的用户文档中，推荐如果能在服务端多配置就尽量多配置，因为服务提供者比消费者更清楚自己提供的服务特性。

服务消费者端设置超时时间，如果在消费者端设置了超时时间，以消费者端为主，即优先级更高。因为服务调用方设置超时时间控制性更灵活。如果消费方超时，服务端线程不会定制，会产生警告。


### [7、Dubbo 的注册中心集群挂掉，者和订阅者之间还能通信么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#7dubbo-的注册中心集群挂掉者和订阅者之间还能通信么)  


可以的，启动 dubbo 时，消费者会从 zookeeper 拉取注册的生产者的地址接口等数据，缓存在本地。

每次调用时，按照本地存储的地址进行调用。


### [8、Dubbo telnet 命令能做什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#8dubbo-telnet-命令能做什么)  


dubbo 服务发布之后，我们可以利用 telnet 命令进行调试、管理。Dubbo2.0.5 以上版本服务提供端口支持 telnet 命令


### [9、你还了解别的分布式框架吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#9你还了解别的分布式框架吗)  


别的还有 spring 的 spring cloud，facebook 的 thrift，twitter 的 finagle 等。冲上云霄，Dubbo Go！GO语言版本都发布了～推荐阅读：Spring Cloud是什么，和Dubbo对比呢？


### [10、在使用过程中都遇到了些什么问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#10在使用过程中都遇到了些什么问题)  


如序列化问题。


### [11、Dubbo 超时时间怎样设置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#11dubbo-超时时间怎样设置)  

### [12、同一个服务多个注册的情况下可以直连某一个服务吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#12同一个服务多个注册的情况下可以直连某一个服务吗)  

### [13、服务调用是阻塞的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#13服务调用是阻塞的吗)  

### [14、Dubbo 和 Spring Cloud 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#14dubbo-和-spring-cloud-的区别)  

### [15、服务读写推荐的容错策略是怎样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#15服务读写推荐的容错策略是怎样的)  

### [16、默认使用的是什么通信框架，还有别的选择吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#16默认使用的是什么通信框架还有别的选择吗)  

### [17、Dubbo 如何优雅停机？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#17dubbo-如何优雅停机)  

### [18、Dubbo 集群容错有几种方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#18dubbo-集群容错有几种方案)  

### [19、Dubbo 服务降级，失败重试怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#19dubbo-服务降级失败重试怎么做)  

### [20、Dubbo 必须依赖的包有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#20dubbo-必须依赖的包有哪些)  

### [21、dubbo和dubbox之间的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#21dubbo和dubbox之间的区别)  

### [22、你觉得用 Dubbo 好还是 Spring Cloud 好？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#22你觉得用-dubbo-好还是-spring-cloud-好)  

### [23、RPC使用了哪些关键技术，反序列化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#23rpc使用了哪些关键技术反序列化)  

### [24、Dubbo 和 Spring Cloud 有什么关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#24dubbo-和-spring-cloud-有什么关系)  

### [25、Dubbo中zookeeper做注册中心，如果注册中心集群都挂掉，者和订阅者之间还能通信么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#25dubbo中zookeeper做注册中心如果注册中心集群都挂掉者和订阅者之间还能通信么)  

### [26、Dubbo SPI 和 Java SPI 区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#26dubbo-spi-和-java-spi-区别)  

### [27、同一个服务多个注册的情况下可以直连某一个服务吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#27同一个服务多个注册的情况下可以直连某一个服务吗)  

### [28、服务调用是阻塞的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#28服务调用是阻塞的吗)  

### [29、RPC使用了哪些关键技术，RPC的实现原理架构图](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#29rpc使用了哪些关键技术rpc的实现原理架构图)  

### [30、Dubbo 集群的负载均衡有哪些策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo高级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#30dubbo-集群的负载均衡有哪些策略)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
