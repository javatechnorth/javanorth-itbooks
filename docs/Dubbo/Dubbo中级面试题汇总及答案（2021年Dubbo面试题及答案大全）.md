# Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）

Dubbo面试题及答案【最新版】Dubbo高级面试题大全(2021版)，发现网上很多Dubbo面试题及答案整理都没有答案，所以花了很长时间搜集，本套Dubbo面试题大全，Dubbo面试题大汇总，有大量经典的Dubbo面试题以及答案，包含Dubbo语言常见面试题、Dubbo工程师高级面试题及一些大厂Dubbo开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Dubbo面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Dubbo面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、dubbo 推荐用什么协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#1dubbo-推荐用什么协议)  


默认使用 dubbo 协议


### [2、Dubbo 核心功能有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#2dubbo-核心功能有哪些)  


**1、** Remoting：网络通信框架，提供对多种NIO框架抽象封装，包括“同步转异步”和“请求-响应”模式的信息交换方式。

**2、** Cluster：服务框架，提供基于接口方法的透明远程过程调用，包括多协议支持，以及软负载均衡，失败容错，地址路由，动态配置等集群支持。

**3、** Registry：服务注册，基于注册中心目录服务，使服务消费方能动态的查找服务提供方，使地址透明，使服务提供方可以平滑增加或减少机器。


### [3、dubbo 推荐用什么协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#3dubbo-推荐用什么协议)  


默认使用 dubbo 协议。


### [4、Dubbo 的主要应用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#4dubbo-的主要应用场景)  


**1、** 透明化的远程方法调用，就像调用本地方法一样调用远程方法，只需简单配置，没有任何 API 侵入。

**2、** 软负载均衡及容错机制，可在内网替代 F5 等硬件负载均衡器，降低成本，减少单点。

**3、** 服务自动注册与发现，不再需要写死服务提供方地址，注册中心基于接口名查询服务提供者的 IP 地址，并且能够平滑添加或删除服务提供者。

Dubbo 的主要应用场景？

Dubbo 的核心功能？

**主要就是如下 3 个核心功能：**

**1、** Remoting：网络通信框架，提供对多种 NIO 框架抽象封装，包括“同步转异步”和“请求-响应”模式的信息交换方式。

**2、** Cluster：服务框架，提供基于接口方法的透明远程过程调用，包括多协议支持，以及软负载均衡，失败容错，地址路由，动态配置等集群支持。

**3、** Registry：服务注册，基于注册中心目录服务，使服务消费方能动态的查找服务提供方，使地址透明，使服务提供方可以平滑增加或减少机器。


### [5、Dubbo服务之间的调用是阻塞的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#5dubbo服务之间的调用是阻塞的吗)  


默认是同步等待结果阻塞的，支持异步调用，Dubbo 是基于 NIO 的非阻塞实现并行调用，客户端不需要启动多线程即可完成并行调用多个远程服务，相对多线程开销较小，异步调用会返回一个 Future 对象。


### [6、dubbo 服务集群配置（集群容错模式）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#6dubbo-服务集群配置集群容错模式)  


在集群调用失败时， Dubbo 提供了多种容错方案，缺省为 failover 重试。可以自行扩展集群容错策略

l Failover Cluster(默认)

失败自动切换，当出现失败，重试其它服务器。(缺省)通常用于读操作，

但重试会带来更长延迟。可通过 retries="2"来设置重试次数(不含第一次)。

```
<dubbo:service retries="2" cluster="failover"/>或：<dubbo:reference retries="2" cluster="failover"/>cluster="failover"可以不用写,因为默认就是 failover
```

**Failfast Cluster**

快速失败，只发起一次调用，失败立即报错。通常用于非幂等性的写操作，

比如新增记录。

```
dubbo:service cluster="failfast" />
```

或：

```
<dubbo:reference cluster="failfast" />

cluster="failfast"和 把 cluster="failover"、 retries="0"是一样的效果,retries="0"就是不重
```

Failsafe Cluster失败安全，出现异常时，直接忽略。通常用于写入审计日志等操作。

```
<dubbo:service cluster="failsafe" />
```

或：

```
<dubbo:reference cluster="failsafe" />
```

**Failback Cluster**

失败自动恢复，后台记录失败请求，定时重发。通常用于消息通知操作。

```
<dubbo:service cluster="failback" />
```

或：

```
<dubbo:reference cluster="failback" />
```

Forking Cluster并行调用多个服务器，只要一个成功即返回。通常用于实时性要求较高的读

操作，但需要浪费更多服务资源。可通过 forks="2"来设置最大并行数。

```
<dubbo:service cluster=“forking" forks="2"/>
```

或：

```
<dubbo:reference cluster=“forking" forks="2"/>
```


### [7、Dubbo 默认采用注册中心？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#7dubbo-默认采用注册中心)  


采用 Zookeeper


### [8、Dubbo 支持服务降级吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#8dubbo-支持服务降级吗)  


以通过 dubbo:reference 中设置 mock=“return null”。mock 的值也可以修改为 true，然后再跟接口同一个路径下实现一个 Mock 类，命名规则是 “接口名称+Mock” 后缀。然后在 Mock 类里实现自己的降级逻辑


### [9、RPC使用了哪些关键技术，主流RPC框架有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#9rpc使用了哪些关键技术主流rpc框架有哪些)  



### [10、Dubbo的管理控制台能做什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#10dubbo的管理控制台能做什么)  


管理控制台主要包含：路由规则，动态配置，服务降级，访问控制，权重调整，负载均衡，等管理功能


### [11、如何解决服务调用链过长的问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#11如何解决服务调用链过长的问题)  

### [12、Dubbo 用到哪些设计模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#12dubbo-用到哪些设计模式)  

### [13、如何解决服务调用链过长的问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#13如何解决服务调用链过长的问题)  

### [14、Dubbo 类似的分布式框架还有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#14dubbo-类似的分布式框架还有哪些)  

### [15、Dubbo 能集成 SpringBoot 吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#15dubbo-能集成-springboot-吗)  

### [16、Dubbo 支持哪些协议，它们的优缺点有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#16dubbo-支持哪些协议它们的优缺点有哪些)  

### [17、集群容错怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#17集群容错怎么做)  

### [18、RPC使用了哪些关键技术，服务寻址](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#18rpc使用了哪些关键技术服务寻址)  

### [19、为什么需要服务治理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#19为什么需要服务治理)  

### [20、dubbo推荐用什么协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#20dubbo推荐用什么协议)  

### [21、Dubbo 集群提供了哪些负载均衡策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#21dubbo-集群提供了哪些负载均衡策略)  

### [22、dubbo 和 dubbox 之间的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#22dubbo-和-dubbox-之间的区别)  

### [23、RPC使用了哪些关键技术，Hessian](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#23rpc使用了哪些关键技术hessian)  

### [24、RPC使用了哪些关键技术，protobuf-rpc-pro](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#24rpc使用了哪些关键技术protobuf-rpc-pro)  

### [25、Dubbo 支持服务降级吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#25dubbo-支持服务降级吗)  

### [26、Dubbo 超时设置有哪些方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#26dubbo-超时设置有哪些方式)  

### [27、Dubbo 和 Dubbox 之间的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#27dubbo-和-dubbox-之间的区别)  

### [28、为什么要用Dubbo？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#28为什么要用dubbo)  

### [29、Dubbo集群提供了哪些负载均衡策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#29dubbo集群提供了哪些负载均衡策略)  

### [30、一般使用什么注册中心？还有别的选择吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo中级面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#30一般使用什么注册中心还有别的选择吗)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
