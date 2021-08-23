# SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）

SpringCloud面试题及答案【最新版】SpringCloud高级面试题大全(2021版)，发现网上很多SpringCloud面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringCloud面试题大全，SpringCloud面试题大汇总，有大量经典的SpringCloud面试题以及答案，包含SpringCloud语言常见面试题、SpringCloud工程师高级面试题及一些大厂SpringCloud开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringCloud面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringCloud面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是Spring Cloud Bus?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#1什么是spring-cloud-bus)  


spring cloud bus 将分布式的节点用轻量的消息代理连接起来，它可以用于广播配置文件的更改或者服务直接的通讯，也可用于监控。

如果修改了配置文件，发送一次请求，所有的客户端便会重新读取配置文件。

**使用:**

**1、** 添加依赖

**2、** 配置rabbimq


### [2、微服务限流 dubbo限流：dubbo提供了多个和请求相关的filter：ActiveLimitFilter ExecuteLimitFilter TPSLimiterFilter](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#2微服务限流-dubbo限流：dubbo提供了多个和请求相关的filter：activelimitfilter-executelimitfilter-tpslimiterfilter)  


**1、** ActiveLimitFilter：

```
@Activate(group = Constants.CONSUMER, value = Constants.ACTIVES_KEY)
```

**作⽤于客户端，主要作⽤是控制客户端⽅法的并发度；**

当超过了指定的active值之后该请求将等待前⾯的请求完成【何时结束呢？依赖于该⽅法的timeout 如果没有设置timeout的话可能就是多个请求⼀直被阻塞然后等待随机唤醒。

**2、** ExecuteLimitFilter：

```
@Activate(group = Constants.PROVIDER, value = Constants.EXECUTES_KEY)
```

作⽤于服务端，⼀旦超出指定的数⽬直接报错 其实是指在服务端的并⾏度【需要注意这些都是指的是在单台服务上⽽不是整个服务集群】

**3、** TPSLimiterFilter：

```
@Activate(group = Constants.PROVIDER, value = Constants.TPS_LIMIT_RATE_KEY)
```

**1、** 作⽤于服务端，控制⼀段时间内的请求数；

**2、** 默认情况下取得tps.interval字段表示请求间隔 如果⽆法找到则使⽤60s 根据tps字段表示允许调⽤次数。

**3、** 使⽤AtomicInteger表示允许调⽤的次数 每次调⽤减少1次当结果⼩于0之后返回不允许调⽤


### [3、微服务设计的基础是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#3微服务设计的基础是什么)  


这可能是最常见的微服务面试问题之一。在回答这个问题时，你需要记住以下内容：

**1、** 定义范围。

**2、** 结合低耦合和高内聚。

**3、** 创建一个有唯一标识的服务，唯一标识将充当识别源，非常像数据库表中的唯一键。

**4、** 创建正确的API并在集成过程中特别注意。

**5、** 限制对数据的访问并将其限制到所需级别。

**6、** 在请求和响应之间保持顺畅的流程。

**7、** 自动化大多数流程，以减少时间复杂性。

**8、** 将表的数量保持在最低水平，以减少空间复杂性。

**9、** 不断监控架构，发现缺陷及时修复。

**10、**  每个微服务的数据存储应该分开。

**11、**  对于每个微服务，都应该有一个独立的构建。

**12、**  将微服务部署到容器中。

**13、**  服务器应被视为无状态。


### [4、eureka服务注册与发现原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#4eureka服务注册与发现原理)  


**1、** 每30s发送⼼跳检测重新进⾏租约，如果客户端不能多次更新租约，它将在90s内从服务器注册中⼼移除。

**2、** 注册信息和更新会被复制到其他Eureka 节点，来⾃任何区域的客户端可以查找到注册中⼼信息，每30s发⽣⼀次复制来定位他们的服务，并进⾏远程调⽤。

**3、** 客户端还可以缓存⼀些服务实例信息，所以即使Eureka全挂掉，客户端也是可以定位到服务地址的。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_4.png#alt=45%5C_4.png)


### [5、为什么在微服务中需要Reports报告和Dashboards仪表板？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#5为什么在微服务中需要reports报告和dashboards仪表板)  


报告和仪表板主要用于监视和维护微服务。有多种工具可以帮助实现此目的。报告 和仪表板可用于： 找出哪些微服务公开了哪些资源。 找出组件发生变化时受影响的服务。 提供一个简单的点，只要需要文档，就可以访问它。 部署的组件的版本。


### [6、列举微服务技术栈](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#6列举微服务技术栈)  


**1、** 服务⽹关Zuul

**2、** 服务注册发现Eureka+Ribbon

**3、** 服务配置中⼼Apollo

**4、** 认证授权中⼼Spring Security OAuth2

**5、** 服务框架SpringBoot

**6、** 数据总线Kafka

**7、** ⽇志监控ELK

**8、** 调⽤链监控CAT

**9、** Metrics监控KairosDB

**10、** 健康检查和告警ZMon

**11、** 限流熔断和流聚合Hystrix/Turbine


### [7、什么是Eureka的自我保护模式，](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#7什么是eureka的自我保护模式)  


默认情况下，如果Eureka Service在一定时间内没有接收到某个微服务的心跳，Eureka Service会进入自我保护模式，在该模式下Eureka Service会保护服务注册表中的信息，不在删除注册表中的数据，当网络故障恢复后，Eureka Servic 节点会自动退出自我保护模式


### [8、微服务有哪些特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#8微服务有哪些特点)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_3.png#alt=img%5C_3.png)

图3：微服务的 特点 – 微服务访谈问题

解耦 – 系统内的服务很大程度上是分离的。因此，整个应用程序可以轻松构建，更改和扩展

组件化 – 微服务被视为可以轻松更换和升级的独立组件

业务能力 – 微服务非常简单，专注于单一功能

自治 – 开发人员和团队可以彼此独立工作，从而提高速度

持续交付 – 通过软件创建，测试和批准的系统自动化，允许频繁发布软件

责任 – 微服务不关注应用程序作为项目。相反，他们将应用程序视为他们负责的产品

分散治理 – 重点是使用正确的工具来做正确的工作。这意味着没有标准化模式或任何技术模式。开发人员可以自由选择最有用的工具来解决他们的问题

敏捷 – 微服务支持敏捷开发。任何新功能都可以快速开发并再次丢弃


### [9、为什么人们会犹豫使用微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#9为什么人们会犹豫使用微服务)  


我见过许多开发者在这个问题上摸索。毕竟，在面试微服务架构师角色时，他们会被问到这个问题，所以承认它的缺点可能有点棘手。以下是一些很好的答案：

它们需要大量协作 - 微服务需要大量的合作。不同的微服务模块，可能分散在不同的团队，团队之间需要始终保持良好的同步。

他们需要建立繁重的架构 - 系统是分布式的，架构涉及很多。 他们需要过多的计划来处理操作开销 - 如果您计划使用微服务架构，则需要为操作开销做好准备。 需要熟练的专业人员，他们可以支持异构分布的微服务。


### [10、Spring Cloud和各子项目版本对应关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#10spring-cloud和各子项目版本对应关系)  


**1、** Edgware.SR6：我理解为最低版本号

**2、** Greenwich.SR2 :我理解为最高版本号

**3、** Greenwich.BUILD-SNAPSHOT（快照）：是一种特殊的版本，指定了某个当前的开发进度的副本。不同于常规的版本，几乎每天都要提交更新的版本，如果每次提交都申明一个版本号那不是版本号都不够用？

| Component | Edgware.SR6 | Greenwich.SR2 | Greenwich.BUILD-SNAPSHOT |
| --- | --- | --- | --- |
| spring-cloud-aws | 1.2.4.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-bus | 1.3.4.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-cli | 1.4.1.RELEASE | 2.0.0.RELEASE | 2.0.1.BUILD-SNAPSHOT |
| spring-cloud-commons | 1.3.6.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-contract | 1.2.7.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-config | 1.4.7.RELEASE | 2.1.3.RELEASE | 2.1.4.BUILD-SNAPSHOT |
| spring-cloud-netflix | 1.4.7.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-security | 1.2.4.RELEASE | 2.1.3.RELEASE | 2.1.4.BUILD-SNAPSHOT |
| spring-cloud-cloudfoundry | 1.1.3.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-consul | 1.3.6.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-sleuth | 1.3.6.RELEASE | 2.1.1.RELEASE | 2.1.2.BUILD-SNAPSHOT |
| spring-cloud-stream | Ditmars.SR5 | Fishtown.SR3 | Fishtown.BUILD-SNAPSHOT |
| spring-cloud-zookeeper | 1.2.3.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-boot | 1.5.21.RELEASE | 2.1.5.RELEASE | 2.1.8.BUILD-SNAPSHOT |
| spring-cloud-task | 1.2.4.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-vault | 1.1.3.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-gateway | 1.0.3.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-openfeign | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |  |
| spring-cloud-function | 1.0.2.RELEASE | 2.0.2.RELEASE | 2.0.3.BUILD-SNAPSHOT |


### [11、Spring Cloud和SpringBoot版本对应关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#11spring-cloud和springboot版本对应关系)  

### [12、Spring Cloud Gateway](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#12spring-cloud-gateway)  

### [13、微服务之间是如何独⽴通讯的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#13微服务之间是如何独⽴通讯的)  

### [14、eureka和zookeeper都可以提供服务注册与发现的功能，请说说两个的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#14eureka和zookeeper都可以提供服务注册与发现的功能请说说两个的区别)  

### [15、什么是Spring Cloud？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#15什么是spring-cloud)  

### [16、我们如何在测试中消除非决定论？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#16我们如何在测试中消除非决定论)  

### [17、服务网关的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#17服务网关的作用)  

### [18、多个消费者调⽤同⼀接⼝，eruka默认的分配⽅式是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#18多个消费者调⽤同⼀接⼝eruka默认的分配⽅式是什么)  

### [19、SpringBoot和springcloud认识](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#19springboot和springcloud认识)  

### [20、谈一下领域驱动设计](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#20谈一下领域驱动设计)  

### [21、SpringCloud主要项目](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#21springcloud主要项目)  

### [22、为什么我们需要微服务容器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#22为什么我们需要微服务容器)  

### [23、什么是不同类型的双因素身份认证？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#23什么是不同类型的双因素身份认证)  

### [24、什么是领域驱动设计？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#24什么是领域驱动设计)  

### [25、缓存机制：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#25缓存机制：)  

### [26、Mock或Stub有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#26mock或stub有什么区别)  

### [27、合同测试你懂什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#27合同测试你懂什么)  

### [28、Spring Cloud Security](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#28spring-cloud-security)  

### [29、Spring Cloud的版本关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#29spring-cloud的版本关系)  

### [30、DiscoveryClient的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#30discoveryclient的作用)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
