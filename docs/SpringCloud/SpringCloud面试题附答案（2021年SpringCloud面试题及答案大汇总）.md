# SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）

SpringCloud面试题及答案【最新版】SpringCloud高级面试题大全(2021版)，发现网上很多SpringCloud面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringCloud面试题大全，SpringCloud面试题大汇总，有大量经典的SpringCloud面试题以及答案，包含SpringCloud语言常见面试题、SpringCloud工程师高级面试题及一些大厂SpringCloud开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringCloud面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringCloud面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、@LoadBalanced注解的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#1@loadbalanced注解的作用)  


开启客户端负载均衡。


### [2、什么是Spring Cloud？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#2什么是spring-cloud)  


在微服务中，SpringCloud是一个提供与外部系统集成的系统。它是一个敏捷的框架，可以短平快构建应用程序。与有限数量的数据处理相关联，它在微服务体系结构中起着非常重要的作用。 **以下为 Spring Cloud 的核心特性**：

**1、** 版本化/分布式配置。

**2、** 服务注册和发现。

**3、** 服务和服务之间的调用。

**4、** 路由。

**5、** 断路器和负载平衡。

**6、** 分布式消息传递。


### [3、Spring Cloud Bus](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#3spring-cloud-bus)  


用于传播集群状态变化的消息总线，使用轻量级消息代理链接分布式系统中的节点，可以用来动态刷新集群中的服务配置信息。

简单来说就是修改了配置文件，发送一次请求，所有客户端便会重新读取配置文件。

需要利用中间插件MQ


### [4、负载平衡的意义什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#4负载平衡的意义什么)  


**1、** 简单来说： 先将集群，集群就是把一个的事情交给多个人去做，假如要做1000个产品给一个人做要10天，我叫10个人做就是一天，这就是集群，负载均衡的话就是用来控制集群，他把做的最多的人让他慢慢做休息会，把做的最少的人让他加量让他做多点。

**2、** 在计算中，负载平衡可以改善跨计算机，计算机集群，网络链接，中央处理单元或磁盘驱动器等多种计算资源的工作负载分布。负载平衡旨在优化资源使用，最大化吞吐量，最小化响应时间并避免任何单一资源的过载。使用多个组件进行负载平衡而不是单个组件可能会通过冗余来提高可靠性和可用性。负载平衡通常涉及专用软件或硬件，例如多层交换机或域名系统服务器进程。


### [5、Web，RESTful API在微服务中的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#5webrestful-api在微服务中的作用是什么)  


微服务架构基于一个概念，其中所有服务应该能够彼此交互以构建业务功能。因此，要实现这一点，每个微服务必须具有接口。这使得Web API成为微服务的一个非常重要的推动者。RESTful API基于Web的开放网络原则，为构建微服务架构的各个组件之间的接口提供了最合理的模型。


### [6、什么是Spring Cloud Zuul（服务网关）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#6什么是spring-cloud-zuul服务网关)  


Zuul是对SpringCloud提供的成熟对的路由方案，他会根据请求的路径不同，网关会定位到指定的微服务，并代理请求到不同的微服务接口，他对外隐蔽了微服务的真正接口地址。

三个重要概念：动态路由表，路由定位，反向代理：

**1、** 动态路由表：Zuul支持Eureka路由，手动配置路由，这俩种都支持自动更新

**2、** 路由定位：根据请求路径，Zuul有自己的一套定位服务规则以及路由表达式匹配

**3、** 反向代理：客户端请求到路由网关，网关受理之后，在对目标发送请求，拿到响应之后在 给客户端它可以和Eureka,Ribbon,Hystrix等组件配合使用，

**Zuul的应用场景：**

对外暴露，权限校验，服务聚合，日志审计等


### [7、过渡到微服务时的常见错误](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#7过渡到微服务时的常见错误)  


不仅在开发上，而且在方面流程也经常发生错误。一些常见错误是：

**1、** 通常开发人员无法概述当前的挑战。

**2、** 重写已经存在的程序。

**3、** 职责、时间线和界限没有明确定义。

**4、** 未能从一开始就实施和确定自动化的范围。


### [8、微服务之间如何独立通讯的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#8微服务之间如何独立通讯的)  


同步通信：dobbo通过 RPC 远程过程调用、springcloud通过 REST 接口json调用 等。

异步：消息队列，如：RabbitMq、ActiveM、Kafka 等。


### [9、什么是Spring Cloud Gateway?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#9什么是spring-cloud-gateway)  


Spring Cloud Gateway是Spring Cloud官方推出的第二代网关框架，取代Zuul网关。网关作为流量的，在微服务系统中有着非常作用，网关常见的功能有路由转发、权限校验、限流控制等作用。

使用了一个RouteLocatorBuilder的bean去创建路由，除了创建路由RouteLocatorBuilder可以让你添加各种predicates和filters，predicates断言的意思，顾名思义就是根据具体的请求的规则，由具体的route去处理，filters是各种过滤器，用来对请求做各种判断和修改。


### [10、Spring Cloud Config](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#10spring-cloud-config)  


集中配置管理工具，分布式系统中统一的外部配置管理，默认使用Git来存储配置，可以支持客户端配置的刷新及加密、解密操作。


### [11、谈谈服务雪崩效应](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#11谈谈服务雪崩效应)  

### [12、第⼆层缓存：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#12第⼆层缓存：)  

### [13、你对SpringBoot有什么了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#13你对springboot有什么了解)  

### [14、微服务之间是如何独立通讯的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#14微服务之间是如何独立通讯的)  

### [15、Spring Cloud Zookeeper](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#15spring-cloud-zookeeper)  

### [16、使用Spring Cloud有什么优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#16使用spring-cloud有什么优势)  

### [17、什么是Hystrix?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#17什么是hystrix)  

### [18、使⽤中碰到的坑](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#18使⽤中碰到的坑)  

### [19、springcloud和dubbo有哪些区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#19springcloud和dubbo有哪些区别)  

### [20、服务雪崩？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#20服务雪崩)  

### [21、如何覆盖SpringBoot项目的默认属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#21如何覆盖springboot项目的默认属性)  

### [22、Spring Cloud 和dubbo区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#22spring-cloud-和dubbo区别)  

### [23、Container在微服务中的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#23container在微服务中的用途是什么)  

### [24、康威定律是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#24康威定律是什么)  

### [25、Docker的目的是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#25docker的目的是什么)  

### [26、Nginx与Ribbon的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#26nginx与ribbon的区别)  

### [27、使用 SpringBoot 开发分布式微服务时，我们面临什么问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#27使用-springboot-开发分布式微服务时我们面临什么问题)  

### [28、ZuulFilter常用有那些方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#28zuulfilter常用有那些方法)  

### [29、服务注册和发现是什么意思？Spring Cloud 如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#29服务注册和发现是什么意思spring-cloud-如何实现)  

### [30、Spring Cloud Config](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案（2021年SpringCloud面试题及答案大汇总）.md#30spring-cloud-config)  





