# Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）

Dubbo面试题及答案【最新版】Dubbo高级面试题大全(2021版)，发现网上很多Dubbo面试题及答案整理都没有答案，所以花了很长时间搜集，本套Dubbo面试题大全，Dubbo面试题大汇总，有大量经典的Dubbo面试题以及答案，包含Dubbo语言常见面试题、Dubbo工程师高级面试题及一些大厂Dubbo开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Dubbo面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Dubbo面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、RPC使用了哪些关键技术，建立通信](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#1rpc使用了哪些关键技术建立通信)  


首先要解决通讯的问题：即A机器想要调用B机器，首先得建立起通信连接。

主要是通过在客户端和服务器之间建立TCP连接，远程过程调用的所有交换的数据都在这个连接里传输。连接可以是按需连接，调用结束后就断掉，也可以是长连接，多个远程过程调用共享同一个连接。

通常这个连接可以是按需连接（需要调用的时候就先建立连接，调用结束后就立马断掉），也可以是长连接（客户端和服务器建立起连接之后保持长期持有，不管此时有无数据包的发送，可以配合心跳检测机制定期检测建立的连接是否存活有效），多个远程过程调用共享同一个连接。


### [2、服务上线怎么不影响旧版本？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#2服务上线怎么不影响旧版本)  


采用多版本开发，不影响旧版本。在配置中添加version来作为版本区分


### [3、RPC使用了哪些关键技术，从调用者的角度看：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#3rpc使用了哪些关键技术从调用者的角度看：)  


服务的调用者启动的时候根据自己订阅的服务向服务注册中心查找服务提供者的地址等信息；

当服务调用者消费的服务上线或者下线的时候，注册中心会告知该服务的调用者；

服务调用者下线的时候，则取消订阅。


### [4、你还了解别的分布式框架吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#4你还了解别的分布式框架吗)  


别的还有spring的spring cloud，facebook的thrift，twitter的finagle等



### [5、如何解决服务调用链过长的问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#5如何解决服务调用链过长的问题)  


可以结合 zipkin 实现分布式服务追踪。


### [6、Dubbo 配置文件是如何加载到 Spring 中的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#6dubbo-配置文件是如何加载到-spring-中的)  


Spring 容器在启动的时候，会读取到 Spring 默认的一些 schema 以及 Dubbo 自定义的 schema，每个 schema 都会对应一个自己的 NamespaceHandler，NamespaceHandler 里面通过 BeanDefinitionParser 来解析配置信息并转化为需要加载的 bean 对象！


### [7、Dubbo服务降级，失败重试怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#7dubbo服务降级失败重试怎么做)  


可以通过dubbo:reference 中设置mock="return null"。mock的值也可以修改为true，然后在跟接口同一个路径下实现一个Mock类，命名规则是"接口名称+Mock"后缀。然后在Mock类里实现自己的降级逻辑。



### [8、在使用过程中都遇到了些什么问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#8在使用过程中都遇到了些什么问题)  


Dubbo 的设计目的是为了满足高并发小数据量的 rpc 调用，在大数据量下的性能表现并不好，建议使用 rmi 或 http 协议。


### [9、集群容错怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#9集群容错怎么做)  


读操作建议使用Failover失败自动切换，默认重试两次其他服务器。写操作建议使用Failfast快速失败，发一次调用失败就立即报错。


### [10、Dubbo 在安全机制方面是如何解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#10dubbo-在安全机制方面是如何解决)  


Dubbo 通过 Token 令牌防止用户绕过注册中心直连，然后在注册中心上管理授权。Dubbo 还提供服务黑白名单，来控制服务所允许的调用方。


### [11、同一个服务多个注册的情况下可以直连某一个服务吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#11同一个服务多个注册的情况下可以直连某一个服务吗)  

### [12、默认使用什么序列化框架，你知道的还有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#12默认使用什么序列化框架你知道的还有哪些)  

### [13、在使用过程中都遇到了些什么问题？ 如何解决的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#13在使用过程中都遇到了些什么问题-如何解决的)  

### [14、Dubbo 配置文件是如何加载到Spring中的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#14dubbo-配置文件是如何加载到spring中的)  

### [15、Dubbo 超时设置有哪些方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#15dubbo-超时设置有哪些方式)  

### [16、服务上线怎么不影响旧版本？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#16服务上线怎么不影响旧版本)  

### [17、Dubbo Monitor 实现原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#17dubbo-monitor-实现原理)  

### [18、Dubbo 推荐什么协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#18dubbo-推荐什么协议)  

### [19、Dubbo 和 Spring Cloud 的关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#19dubbo-和-spring-cloud-的关系)  

### [20、同一个服务多个注册的情况下可以直连某一个服务吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#20同一个服务多个注册的情况下可以直连某一个服务吗)  

### [21、Dubbo 在安全方面有哪些措施？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#21dubbo-在安全方面有哪些措施)  

### [22、Dubbo 使用过程中都遇到了些什么问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#22dubbo-使用过程中都遇到了些什么问题)  

### [23、Dubbo 服务降级，失败重试怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#23dubbo-服务降级失败重试怎么做)  

### [24、RPC使用了哪些关键技术，NIO通信](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#24rpc使用了哪些关键技术nio通信)  

### [25、同一个服务多个注册的情况下可以直连某一个服务吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#25同一个服务多个注册的情况下可以直连某一个服务吗)  

### [26、服务调用超时问题怎么解决](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#26服务调用超时问题怎么解决)  

### [27、Dubbo 使用过程中都遇到了些什么问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#27dubbo-使用过程中都遇到了些什么问题)  

### [28、服务提供者能实现失效踢出是什么原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#28服务提供者能实现失效踢出是什么原理)  

### [29、Dubbo 支持分布式事务吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#29dubbo-支持分布式事务吗)  

### [30、Dubbo 可以对结果进行缓存吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Dubbo/Dubbo面试题附答案汇总（2021年Dubbo面试题及答案大全）.md#30dubbo-可以对结果进行缓存吗)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
