# Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）

Dubbo面试题及答案【最新版】Dubbo高级面试题大全(2021版)，发现网上很多Dubbo面试题及答案整理都没有答案，所以花了很长时间搜集，本套Dubbo面试题大全，Dubbo面试题大汇总，有大量经典的Dubbo面试题以及答案，包含Dubbo语言常见面试题、Dubbo工程师高级面试题及一些大厂Dubbo开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Dubbo面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Dubbo面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Dubbo支持服务多协议吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#1dubbo支持服务多协议吗)  


Dubbo 允许配置多协议，在不同服务上支持不同协议或者同一服务上同时支持多种协议。


### [2、PRC架构组件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#2prc架构组件)  


一个基本的RPC架构里面应该至少包含以下4个组件：

**1、** 客户端（Client）:服务调用方（服务消费者）

**2、** 客户端存根（Client Stub）:存放服务端地址信息，将客户端的请求参数数据信息打包成网络消息，再通过网络传输发送给服务端

**3、** 服务端存根（Server Stub）:接收客户端发送过来的请求消息并进行解包，然后再调用本地服务进行处理4、服务端（Server）:服务的真正提供者

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/026/54/80_4.png#alt=80%5C_4.png)

- 具体调用过程：

**1、** 服务消费者（client客户端）通过调用本地服务的方式调用需要消费的服务；

**2、** 客户端存根（client stub）接收到调用请求后负责将方法、入参等信息序列化（组装）成能够进行网络传输的消息体；

**3、** 客户端存根（client stub）找到远程的服务地址，并且将消息通过网络发送给服务端；

**4、** 服务端存根（server stub）收到消息后进行解码（反序列化操作）；

**5、** 服务端存根（server stub）根据解码结果调用本地的服务进行相关处理；

**6、** 本地服务执行具体业务逻辑并将处理结果返回给服务端存根（server stub）；

**7、** 服务端存根（server stub）将返回结果重新打包成消息（序列化）并通过网络发送至消费方；

**8、** 客户端存根（client stub）接收到消息，并进行解码（反序列化）；

**9、** 服务消费方得到最终结果；

`而RPC框架的实现目标则是将上面的第2-10步完好地封装起来，也就是把调用、编码/解码的过程给封装起来，让用户感觉上像调用本地服务一样的调用远程服务。`


### [3、dubbo 通信协议 dubbo 协议为什么采用异步单一长连接](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#3dubbo-通信协议-dubbo-协议为什么采用异步单一长连接)  


因为服务的现状大都是服务提供者少，通常只有几台机器，而服务的消费者多，可能整个网站都在访问该服务，比如 Morgan 的提供者只有 6 台提供者，却有上百台消费者，每天有 1.5 亿次调用，如果采用常规的 hessian 服务，服务提供者很容易就被压跨，通过单一连接，保证单一消费者不会压死提供者，长连接，减少连接握手验证等，并使用异步 IO，复用线程池，防止 C10K 问题。


### [4、Dubbo 服务注册与发现的流程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#4dubbo-服务注册与发现的流程)  


**流程说明：**

**1、** Provider(提供者)绑定指定端口并启动服务

**2、** 指供者连接注册中心，并发本机 IP、端口、应用信息和提供服务信息发送至注册中心存储

**3、** Consumer(消费者），连接注册中心 ，并发送应用信息、所求服务信息至注册中心

**4、** 注册中心根据 消费 者所求服务信息匹配对应的提供者列表发送至Consumer 应用缓存。

**5、** Consumer 在发起远程调用时基于缓存的消费者列表择其一发起调用。

**6、** Provider 状态变更会实时通知注册中心、在由注册中心实时推送至Consumer

**设计的原因：**

**1、** Consumer 与 Provider 解偶，双方都可以横向增减节点数。

**2、** 注册中心对本身可做对等集群，可动态增减节点，并且任意一台宕掉后，将自动切换到另一台

**3、** 去中心化，双方不直接依懒注册中心，即使注册中心全部宕机短时间内也不会影响服务的调用

**4、** 服务提供者无状态，任意一台宕掉后，不影响使用


### [5、说说核心的配置有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#5说说核心的配置有哪些)  


核心配置有：

**1、** dubbo:service/

**2、** dubbo:reference/

**3、** dubbo:protocol/

**4、** dubbo:registry/

**5、** dubbo:application/

**6、** dubbo:provider/

**7、** dubbo:consumer/

**8、** dubbo:method/


### [6、默认使用什么序列化框架，你知道的还有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#6默认使用什么序列化框架你知道的还有哪些)  


推荐使用Hessian序列化，还有Duddo、FastJson、Java自带序列化。


### [7、你还了解别的分布式框架吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#7你还了解别的分布式框架吗)  


别的还有spring的spring cloud，facebook的thrift，twitter的finagle等。


### [8、服务提供者能实现失效踢出的是什么原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#8服务提供者能实现失效踢出的是什么原理)  


服务失效踢出基于zookeeper的临时节点原理。


### [9、Dubbo 和 Spring Cloud 有什么哪些区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#9dubbo-和-spring-cloud-有什么哪些区别)  


Dubbo 底层是使用 Netty 这样的 NIO 框架，是基于 TCP 协议传输的，配合以 Hession 序列化完成 RPC 通信。

Spring Cloud 是基于 Http 协议 Rest 接口调用远程过程的通信，相对来说 Http 请求会有更大的报文，占的带宽也会更多。但是 REST 相比 RPC 更为灵活，服务提供方和调用方的依赖只依靠一纸契约，不存在代码级别的强依赖，这在强调快速演化的微服务环境下，显得更为合适，至于注重通信速度还是方便灵活性，具体情况具体考虑。


### [10、为什么要有RPC](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#10为什么要有rpc)  


**1、** http接口是在接口不多、系统与系统交互较少的情况下，解决信息孤岛初期常使用的一种通信手段；优点就是简单、直接、开发方便。利用现成的http协议进行传输。但是如果是一个大型的网站，内部子系统较多、接口非常多的情况下，RPC框架的好处就显示出来了，首先就是长链接，不必每次通信都要像http一样去3次握手什么的，减少了网络开销；其次就是RPC框架一般都有注册中心，有丰富的监控管理；发布、下线接口、动态扩展等，对调用方来说是无感知、统一化的操作。第三个来说就是安全性。最后就是最近流行的服务化架构、服务化治理，RPC框架是一个强力的支撑。

**2、** socket只是一个简单的网络通信方式，只是创建通信双方的通信通道，而要实现rpc的功能，还需要对其进行封装，以实现更多的功能。

**3、** RPC一般配合netty框架、spring自定义注解来编写轻量级框架，其实netty内部是封装了socket的，较新的jdk的IO一般是NIO，即非阻塞IO，在高并发网站中，RPC的优势会很明显


### [11、画一画服务注册与发现的流程图？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#11画一画服务注册与发现的流程图)  

### [12、默认使用什么序列化框架，你知道的还有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#12默认使用什么序列化框架你知道的还有哪些)  

### [13、Dubbo 支持哪些序列化方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#13dubbo-支持哪些序列化方式)  

### [14、Dubbo 服务器注册与发现的流程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#14dubbo-服务器注册与发现的流程)  

### [15、Dubbo telnet 命令能做什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#15dubbo-telnet-命令能做什么)  

### [16、服务调用超时问题怎么解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#16服务调用超时问题怎么解决)  

### [17、Dubbo 可以对结果进行缓存吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#17dubbo-可以对结果进行缓存吗)  

### [18、默认使用的是什么通信框架，还有别的选择吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#18默认使用的是什么通信框架还有别的选择吗)  

### [19、Dubbo 和 Spring Cloud 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#19dubbo-和-spring-cloud-的区别)  

### [20、Dubbo 和 Spring Cloud 有什么哪些区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#20dubbo-和-spring-cloud-有什么哪些区别)  

### [21、Dubbo 核心组件有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#21dubbo-核心组件有哪些)  

### [22、RPC使用了哪些关键技术，服务注册中心](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#22rpc使用了哪些关键技术服务注册中心)  

### [23、Dubbo 使用的是什么通信框架?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#23dubbo-使用的是什么通信框架)  

### [24、服务提供者能实现失效踢出是什么原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#24服务提供者能实现失效踢出是什么原理)  

### [25、Dubbo 的整体架构设计有哪些分层?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#25dubbo-的整体架构设计有哪些分层)  

### [26、RPC使用了哪些关键技术，序列化和反序列化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#26rpc使用了哪些关键技术序列化和反序列化)  

### [27、什么是RPC](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#27什么是rpc)  

### [28、当一个服务接口有多种实现时怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#28当一个服务接口有多种实现时怎么做)  

### [29、RPC使用了哪些关键技术，Avro](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#29rpc使用了哪些关键技术avro)  

### [30、dubbo是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#30dubbo是什么)  

### [31、Dubbo有哪几种负载均衡策略，默认是哪种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题带答案（2021年Dubbo面试题及答案大汇总）.md#31dubbo有哪几种负载均衡策略默认是哪种)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
