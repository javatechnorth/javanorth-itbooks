# Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）

Dubbo面试题及答案【最新版】Dubbo高级面试题大全(2021版)，发现网上很多Dubbo面试题及答案整理都没有答案，所以花了很长时间搜集，本套Dubbo面试题大全，Dubbo面试题大汇总，有大量经典的Dubbo面试题以及答案，包含Dubbo语言常见面试题、Dubbo工程师高级面试题及一些大厂Dubbo开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Dubbo面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Dubbo面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、RPC框架需要解决的问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#1rpc框架需要解决的问题)  


**1、** 如何确定客户端和服务端之间的通信协议？

**2、** 如何更高效地进行网络通信？

**3、** 服务端提供的服务如何暴露给客户端？

**4、** 客户端如何发现这些暴露的服务？

**5、** 如何更高效地对请求对象和响应结果进行序列化和反序列化操作？


### [2、Dubbo 支持哪些协议，每种协议的应用场景，优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#2dubbo-支持哪些协议每种协议的应用场景优缺点)  


**1、** dubbo：单一长连接和 NIO 异步通讯，适合大并发小数据量的服务调用，以及消费者远大于提供者。传输协议 TCP，异步， Hessian 序列化；

**2、** rmi：采用 JDK 标准的 rmi 协议实现，传输参数和返回参数对象需要实现Serializable 接口，使用 java 标准序列化机制，使用阻塞式短连接，传输数据包大小混合，消费者和提供者个数差不多，可传文件，传输协议 TCP。多个短连接， TCP 协议传输，同步传输，适用常规的远程服务调用和 rmi 互操作。在依赖低版本的 Common-Collections 包， java 序列化存在安全漏洞；

**3、** http：基于 Http 表单提交的远程调用协议，使用 Spring 的 HttpInvoke 实现。多个短连接，传输协议 HTTP，传入参数大小混合，提供者个数多于消费者，需要给应用程序和浏览器 JS 调用；

**4、** webservice：基于 WebService 的远程调用协议，集成 CXF 实现，提供和原生 WebService 的互操作。多个短连接，基于 HTTP 传输，同步传输，适用系统集成和跨语言调用；

**5、** hessian：集成 Hessian 服务，基于 HTTP 通讯，采用 Servlet 暴露服务，Dubbo 内嵌 Jetty 作为服务器时默认实现，提供与 Hession 服务互操作。多个短连接，同步 HTTP 传输， Hessian 序列化，传入参数较大，提供者大于消费者，提供者压力较大，可传文件；

**6、** Redis：基于 Redis 实现的 RPC 协议


### [3、dubbo 通信协议 dubbo 协议为什么不能传大包；](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#3dubbo-通信协议-dubbo-协议为什么不能传大包；)  


因 dubbo 协议采用单一长连接，如果每次请求的数据包大小为 500KByte，假设网络为千兆网卡(1024Mbit=128MByte)，每条连接最大 7MByte(不同的环境可能不一样，供参考)，单个服务提供者的 TPS(每秒处理事务数)最大为：128MByte / 500KByte = 262。

单个消费者调用单个服务提供者的 TPS(每秒处理事务数)最大为：7MByte / 500KByte = 14。

如果能接受，可以考虑使用，否则网络将成为瓶颈。


### [4、一般使用什么注册中心？还有别的选择吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#4一般使用什么注册中心还有别的选择吗)  


推荐使用 Zookeeper 作为注册中心，还有 Redis、Multicast、Simple 注册中心，但不推荐。


### [5、Dubbo 在安全机制方面是如何解决的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#5dubbo-在安全机制方面是如何解决的)  


Dubbo 通过 Token 令牌防止用户绕过注册中心直连，然后在注册中心上管理授权。Dubbo 还提供服务黑白名单，来控制服务所允许的调用方。


### [6、Dubbo有哪几种集群容错方案，默认是哪种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#6dubbo有哪几种集群容错方案默认是哪种)  


**1、** Failover Cluster 失败自动切换，自动重试其他服务器(默认)

**2、** Failfast Cluster 快速失败，立即报错，只发起一次调用

**3、** Failsafe Cluster 失败安全，出现异常时，直接忽略

**4、** Failback Cluster 失败自动回复，记录失败请求，定时请求

**5、** Forking Cluster  并行调用多个服务器，只要一个成功即返回

**6、** Broadcast Cluster 广播逐个调用所有提供者，任意一个报错则报错


### [7、Dubbo 支持哪些协议，每种协议的应用场景，优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#7dubbo-支持哪些协议每种协议的应用场景优缺点)  


**1、** dubbo：单一长连接和 NIO 异步通讯，适合大并发小数据量的服务调用，以及消费者远大于提供者。传输协议 TCP，异步， Hessian 序列化；

**2、** rmi：采用 JDK 标准的 rmi 协议实现，传输参数和返回参数对象需要实现 Serializable 接口，使用 java 标准序列化机制，使用阻塞式短连接，传输数据包大小混合，消费者和提供者个数差不多，可传文件，传输协议 TCP。多个短连接， TCP 协议传输，同步传输，适用常规的远程服务调用和rmi 互操作。在依赖低版本的 Common-Collections包， java 序列化存在安全漏洞；

**3、** webservice：基于 WebService 的远程调用协议，集成 CXF 实现，提供和原生 WebService 的互操作。多个短连接，基于 HTTP 传输，同步传输，适用系统集成和跨语言调用；

**4、** http：基于 Http 表单提交的远程调用协议，使用 Spring 的HttpInvoke 实现。多个短连接，传输协议 HTTP，传入参数大小混合，提供者个数多于消费者，需要给应用程序和浏览器 JS 调用；

**5、** hessian：集成 Hessian 服务，基于 HTTP 通讯，采用 Servlet 暴露服务， Dubbo 内嵌 Jetty 作为服务器时默认实现，提供与 Hession 服务互操作。多个短连接，同步 HTTP 传输， Hessian 序列化，传入参数较大，提供者大于消费者，提供者压力较大，可传文件；

**6、** memcache：基于 Memcached 实现的 RPC 协议

**7、** Redis：基于 Redis 实现的 RPC 协议


### [8、Dubbo 如何优雅停机？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#8dubbo-如何优雅停机)  


Dubbo 是通过 JDK 的 ShutdownHook 来完成优雅停机的，所以如果使用 kill -9 PID 等强制关闭指令，是不会执行优雅停机的，只有通过 kill PID 时，才会执行。


### [9、RPC使用了哪些关键技术，从服务提供者的角度看：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#9rpc使用了哪些关键技术从服务提供者的角度看：)  


当服务提供者启动的时候，需要将自己提供的服务注册到指定的注册中心，以便服务消费者能够通过服务注册中心进行查找；

当服务提供者由于各种原因致使提供的服务停止时，需要向注册中心注销停止的服务；

服务的提供者需要定期向服务注册中心发送心跳检测，服务注册中心如果一段时间未收到来自服务提供者的心跳后，认为该服务提供者已经停止服务，则将该服务从注册中心上去掉。


### [10、注册了多个同一样的服务，如果测试指定的某一个服务呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#10注册了多个同一样的服务如果测试指定的某一个服务呢)  


可以配置环境点对点直连，绕过注册中心，将以服务接口为单位，忽略注册中心的提供者列表。


### [11、Dubbo 支持分布式事务吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#11dubbo-支持分布式事务吗)  

### [12、Dubbo 的集群容错方案有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#12dubbo-的集群容错方案有哪些)  

### [13、Dubbo 的架构设计](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#13dubbo-的架构设计)  

### [14、说说 Dubbo 服务暴露的过程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#14说说-dubbo-服务暴露的过程。)  

### [15、说说核心的配置有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#15说说核心的配置有哪些)  

### [16、服务上线怎么兼容旧版本？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#16服务上线怎么兼容旧版本)  

### [17、说说核心的配置有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#17说说核心的配置有哪些)  

### [18、Dubbo 用到哪些设计模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#18dubbo-用到哪些设计模式)  

### [19、你还了解别的分布式框架吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#19你还了解别的分布式框架吗)  

### [20、dubbo 通信协议 dubbo 协议为什么要消费者比提供者个数多？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#20dubbo-通信协议-dubbo-协议为什么要消费者比提供者个数多)  

### [21、RPC使用了哪些关键技术，Thrift](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#21rpc使用了哪些关键技术thrift)  

### [22、Dubbo 有些哪些注册中心？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#22dubbo-有些哪些注册中心)  

### [23、Dubbo 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#23dubbo-是什么)  

### [24、一般使用什么注册中心？还有别的选择吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#24一般使用什么注册中心还有别的选择吗)  

### [25、Dubbo 有哪些注册中心？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#25dubbo-有哪些注册中心)  

### [26、RPC使用了哪些关键技术，Dubbo](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#26rpc使用了哪些关键技术dubbo)  

### [27、RPC的实现基础？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#27rpc的实现基础)  

### [28、Dubbo Monitor 实现原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#28dubbo-monitor-实现原理)  

### [29、服务提供者能实现失效踢出是什么原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#29服务提供者能实现失效踢出是什么原理)  

### [30、dubbo 连接注册中心和直连的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题汇总及答案（2021年Dubbo面试题及答案大全）.md#30dubbo-连接注册中心和直连的区别)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
