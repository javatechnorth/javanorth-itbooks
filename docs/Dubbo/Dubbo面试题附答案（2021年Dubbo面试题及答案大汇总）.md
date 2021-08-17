# Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）

Dubbo面试题及答案【最新版】Dubbo高级面试题大全(2021版)，发现网上很多Dubbo面试题及答案整理都没有答案，所以花了很长时间搜集，本套Dubbo面试题大全，Dubbo面试题大汇总，有大量经典的Dubbo面试题以及答案，包含Dubbo语言常见面试题、Dubbo工程师高级面试题及一些大厂Dubbo开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Dubbo面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Dubbo面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、dubbo 通信协议 dubbo 协议适用范围和适用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#1dubbo-通信协议-dubbo-协议适用范围和适用场景)  


适用范围：传入传出参数数据包较小（建议小于 100K），消费者比提供者个数多，单一消费者无法压满提供者，尽量不要用 dubbo 协议传输大文件或超大字符串。

适用场景：常规远程服务方法调用

dubbo 协议补充：

连接个数：单连接

连接方式：长连接

传输协议：TCP

传输方式：NIO 异步传输

序列化：Hessian 二进制序列化


### [2、Dubbo 核心组件有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#2dubbo-核心组件有哪些)  


**1、** Provider：暴露服务的服务提供方

**2、** Consumer：调用远程服务消费方

**3、** Registry：服务注册与发现注册中心

**4、** Monitor：监控中心和访问调用统计

**5、** Container：服务运行容器


### [3、Dubbo SPI 和 Java SPI 区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#3dubbo-spi-和-java-spi-区别)  


**JDK SPI：**

JDK 标准的 SPI 会一次性加载所有的扩展实现，如果有的扩展很耗时，但也没用上，很浪费资源。所以只希望加载某个的实现，就不现实了

**DUBBO SPI：**

**1、** 对 Dubbo 进行扩展，不需要改动 Dubbo 的源码

**2、** 延迟加载，可以一次只加载自己想要加载的扩展实现。

**3、** 增加了对扩展点 IOC 和 AOP 的支持，一个扩展点可以直接 setter 注入其它扩展点。

**4、** Dubbo 的扩展机制能很好的支持第三方 IoC 容器，默认支持 Spring Bean。


### [4、Dubbo 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#4dubbo-是什么)  


Dubbo 是一个分布式、高性能、透明化的 RPC 服务框架，提供服务自动注册、自动发现等高效服务治理方案， 可以和Spring 框架无缝集成


### [5、Dubbo 支持哪些协议，每种协议的应用场景，优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#5dubbo-支持哪些协议每种协议的应用场景优缺点)  


dubbo： 单一长连接和 NIO 异步通讯，适合大并发小数据量的服务调用，以及消费者远大于提供者。传输协议 TCP，异步，Hessian 序列化；

rmi： 采用 JDK 标准的 rmi 协议实现，传输参数和返回参数对象需要实现 Serializable 接口，使用 java 标准序列化机制，使用阻塞式短连接，传输数据包大小混合，消费者和提供者个数差不多，可传文件，传输协议 TCP。 多个短连接，TCP 协议传输，同步传输，适用常规的远程服务调用和 rmi 互操作。在依赖低版本的 Common-Collections 包，java 序列化存在安全漏洞；

webservice:基于 WebService 的远程调用协议，集成 CXF 实现，提供和原生 WebService 的互操作。多个短连接，基于 HTTP 传输，同步传输，适用系统集成和跨语言调用；http： 基于 Http 表单提交的远程调用协议，使用 Spring 的 HttpInvoke 实现。多个短连接，传输协议 HTTP，传入参数大小混合，提供者个数多于消费者，需要给应用程序和浏览器 JS 调用； hessian： 集成 Hessian 服务，基于 HTTP 通讯，采用 Servlet 暴露服务，Dubbo 内嵌 Jetty 作为服务器时默认实现，提供与 Hession 服务互操作。多个短连接，同步 HTTP 传输，Hessian 序列化，传入参数较大，提供者大于消费者，提供者压力较大，可传文件；

memcache： 基于 Memcached 实现的 RPC 协议 Redis： 基于 Redis 实现的 RPC 协议


### [6、Dubbo 的整体架构设计有哪些分层?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#6dubbo-的整体架构设计有哪些分层)  


**接口服务层（Service）**：该层与业务逻辑相关，根据 provider 和 consumer 的业务设计对应的接口和实现

**配置层（Config）**：对外配置接口，以 ServiceConfig 和 ReferenceConfig 为中心

**服务代理层（Proxy）**：服务接口透明代理，生成服务的客户端 Stub 和 服务端的 Skeleton，以 ServiceProxy 为中心，扩展接口为 ProxyFactory

**服务注册层（Registry）**：封装服务地址的注册和发现，以服务 URL 为中心，扩展接口为 RegistryFactory、Registry、RegistryService

**路由层（Cluster）**：封装多个提供者的路由和负载均衡，并桥接注册中心，以Invoker 为中心，扩展接口为 Cluster、Directory、Router和LoadBlancce

**监控层（Monitor）**：RPC调用次数和调用时间监控，以 Statistics 为中心，扩展接口为 MonitorFactory、Monitor和MonitorService

**远程调用层（Protocal）**：封装 RPC 调用，以 Invocation 和 Result 为中心，扩展接口为 Protocal、Invoker和Exporter

**信息交换层（Exchange**）：封装请求响应模式，同步转异步。以 Request 和 Response 为中心，扩展接口为 Exchanger、ExchangeChannel、ExchangeClient和ExchangeServer

**网络传输层（Transport）**：抽象 mina 和 netty 为统一接口，以 Message 为中心，扩展接口为Channel、Transporter、Client、Server和Codec

**数据序列化层（Serialize）**：可复用的一些工具，扩展接口为Serialization、 ObjectInput、ObjectOutput和ThreadPool


### [7、Dubbo 集群的负载均衡有哪些策略?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#7dubbo-集群的负载均衡有哪些策略)  


Dubbo 提供了常见的集群策略实现，并预扩展点予以自行实现。

**1、** Random LoadBalance: 随机选取提供者策略，有利于动态调整提供者权重。截面碰撞率高，调用次数越多，分布越均匀；

**2、** RoundRobin LoadBalance: 轮循选取提供者策略，平均分布，但是存在请求累积的问题；

**3、** LeastActive LoadBalance: 最少活跃调用策略，解决慢提供者接收更少的请求；

**4、** ConstantHash LoadBalance: 一致性 Hash 策略，使相同参数请求总是发到同一提供者，一台机器宕机，可以基于虚拟节点，分摊至其他提供者，避免引起提供者的剧烈变动；


### [8、Dubbo 有哪些注册中心？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#8dubbo-有哪些注册中心)  


**1、** Multicast 注册中心：Multicast 注册中心不需要任何中心节点，只要广播地址，就能进行服务注册和发现,基于网络中组播传输实现。

**2、** Zookeeper 注册中心：基于分布式协调系统 Zookeeper 实现，采用 Zookeeper 的 watch 机制实现数据变更。

**3、** Redis 注册中心：基于 Redis 实现，采用 key/map 存储，key 存储服务名和类型，map 中 key 存储服务 url，value 服务过期时间。基于 Redis 的发布/订阅模式通知数据变更。

**4、** Simple 注册中心。


### [9、Dubbo 的使用场景有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#9dubbo-的使用场景有哪些)  


**1、** 透明化的远程方法调用：就像调用本地方法一样调用远程方法，只需简单配置，没有任何API侵入。

**2、** 软负载均衡及容错机制：可在内网替代 F5 等硬件负载均衡器，降低成本，减少单点。

**3、** 服务自动注册与发现：不再需要写死服务提供方地址，注册中心基于接口名查询服务提供者的IP地址，并且能够平滑添加或删除服务提供者。


### [10、Dubbo必须依赖的包有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#10dubbo必须依赖的包有哪些)  


Dubbo 必须依赖 JDK，其他为可选。


### [11、RPC使用了哪些关键技术，服务调用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#11rpc使用了哪些关键技术服务调用)  

### [12、为什么要用 Dubbo？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#12为什么要用-dubbo)  

### [13、服务调用超时会怎么样？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#13服务调用超时会怎么样)  

### [14、Dubbo可以对结果进行缓存吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#14dubbo可以对结果进行缓存吗)  

### [15、Dubbo 推荐用什么协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#15dubbo-推荐用什么协议)  

### [16、Dubbo 与 Spring 的关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#16dubbo-与-spring-的关系)  

### [17、Dubbo 支持哪些协议，它们的优缺点有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#17dubbo-支持哪些协议它们的优缺点有哪些)  

### [18、RPC和SOA、SOAP、REST的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#18rpc和soasoaprest的区别)  

### [19、dubbo能做什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#19dubbo能做什么)  

### [20、Dubbo 服务器注册与发现的流程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#20dubbo-服务器注册与发现的流程)  

### [21、Dubbo 的默认集群容错方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#21dubbo-的默认集群容错方案)  

### [22、RPC使用了哪些关键技术，动态代理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#22rpc使用了哪些关键技术动态代理)  

### [23、dubbo 服务负载均衡策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#23dubbo-服务负载均衡策略)  

### [24、Dubbo的集群容错方案有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#24dubbo的集群容错方案有哪些)  

### [25、Dubbo 和 Dubbox 之间的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#25dubbo-和-dubbox-之间的区别)  

### [26、默认使用什么序列化框架，你知道的还有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#26默认使用什么序列化框架你知道的还有哪些)  

### [27、RPC使用了哪些关键技术，RMI](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#27rpc使用了哪些关键技术rmi)  

### [28、Dubbo 的注册中心集群挂掉，发布者和订阅者之间还能通信么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#28dubbo-的注册中心集群挂掉发布者和订阅者之间还能通信么)  

### [29、Dubbo的集群容错方案有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#29dubbo的集群容错方案有哪些)  

### [30、RPC使用了哪些关键技术，序列化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#30rpc使用了哪些关键技术序列化)  

### [31、Dubbo 支持哪些序列化方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案（2021年Dubbo面试题及答案大汇总）.md#31dubbo-支持哪些序列化方式)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
