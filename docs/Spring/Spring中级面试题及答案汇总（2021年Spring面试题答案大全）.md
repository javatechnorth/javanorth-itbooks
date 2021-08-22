# Spring中级面试题及答案汇总（2021年Spring面试题答案大全）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、可以通过多少种方式完成依赖注入？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#1可以通过多少种方式完成依赖注入)  


通常，依赖注入可以通过三种方式完成，即：

**1、** 构造函数注入

**2、** setter 注入

**3、** 接口注入

在 Spring Framework 中，仅使用构造函数和 setter 注入。


### [2、Spring AOP and AspectJ AOP 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#2spring-aop-and-aspectj-aop-有什么区别)  


Spring AOP 基于动态代理方式实现；AspectJ 基于静态代理方式实现。Spring AOP 仅支持方法级别的 PointCut；提供了完全的 AOP 支持，它还支持属性级别的 PointCut。


### [3、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#3springboot-的核心配置文件有哪几个它们的区别是什么)  


**1、** SpringBoot 的核心配置文件是 application 和 bootstrap 配置文件。

**2、** application 配置文件这个容易了解，主要用于 SpringBoot 项目的自动化配置。

**3、** bootstrap 配置文件有以下几个应用场景。

**4、** 使用 Spring Cloud Config 配置中心时，这时需要在 bootstrap 配置文件中增加连接到配置中心的配置属性来加载外部配置中心的配置信息；

**5、** 少量固定的不能被覆盖的属性；

**6、** 少量加密/解密的场景；


### [4、微服务之间是如何独立通讯的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#4微服务之间是如何独立通讯的)  


**1、** 远程过程调用（Remote Procedure Invocation）：也就是我们常说的服务的注册与发现，直接通过远程过程调用来访问别的service。

**优点：**

简单，常见,因为没有中间件代理，系统更简单

**缺点：**

**1、** 只支持请求/响应的模式，不支持别的，比如通知、请求/异步响应、发布/订阅、发布/异步响应

**2、** 降低了可用性，因为客户端和服务端在请求过程中必须都是可用的

**2、** 消息：使用异步消息来做服务间通信。服务间通过消息管道来交换消息，从而通信。

**优点:**

**1、** 把客户端和服务端解耦，更松耦合

**2、** 提高可用性，因为消息中间件缓存了消息，直到消费者可以消费

**3、** 支持很多通信机制比如通知、请求/异步响应、发布/订阅、发布/异步响应

**缺点:**

消息中间件有额外的复杂


### [5、SpringBoot有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#5springboot有哪些优点)  


**1、** 快速创建独立运行的spring项目与主流框架集成

**2、** 使用嵌入式的servlet容器，应用无需打包成war包

**3、** starters自动依赖与版本控制

**4、** 大量的自动配置，简化开发，也可修改默认值

**5、** 准生产环境的运行应用监控

**6、** 与云计算的天然集成


### [6、SpringCloud有几种调用接口方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#6springcloud有几种调用接口方式)  


**1、** Feign

**2、** RestTemplate


### [7、@SpringBootApplication注释在内部有什么用处?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#7@springbootapplication注释在内部有什么用处)  


作为Spring引导文档，@SpringBootApplication注释等同于同时使用@Configuration、@EnableAutoConfiguration和@ComponentScan及其默认属性。SpringBoot允许开发人员使用单个注释而不是多个注释。但是，众所周知，Spring提供了松散耦合的特性，我们可以根据项目需要为每个注释使用这些特性。


### [8、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#8springboot-的核心注解是哪个它主要由哪几个注解组成的)  


启动类上面的注解是@SpringBootApplication，它也是 SpringBoot 的核心注解，主要组合包含了以下 3 个注解：

@SpringBootConfiguration：组合了 [@Configuration ](/Configuration ) 注解，实现配置文件的功能。

[@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：@SpringBootApplication(exclude ](/EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：@SpringBootApplication(exclude ) = { DataSourceAutoConfiguration.class })。

@ComponentScan：Spring组件扫描。


### [9、什么是YAML?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#9什么是yaml)  


YAML是一种人类可读的数据序列化语言。它通常用于`配置文件`。 与属性文件相比，如果我们想要在配置文件中添加复杂的属性，YAML文件就更加结构化，而且更少混淆。可以看出YAML具有`分层配置数据`。


### [10、接⼝限流⽅法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#10接⼝限流⽅法)  


**限制 总并发数（⽐如 数据库连接池、线程池）**

**1、** 限制 瞬时并发数（如 nginx 的 limit_conn 模块，⽤来限制 瞬时并发连接数）

**2、** 限制 时间窗⼝内的平均速率（如 Guava 的 RateLimiter、nginx 的 limit_req模块，限制每秒的平均速率）

**3、** 限制 远程接⼝ 调⽤速率

**4、** 限制 MQ 的消费速率

**5、** 可以根据⽹络连接数、⽹络流量、CPU或内存负载等来限流



### [11、哪些是重要的bean生命周期方法？你能重载它们吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#11哪些是重要的bean生命周期方法你能重载它们吗)  

### [12、解释JDBC抽象和DAO模块。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#12解释jdbc抽象和dao模块。)  

### [13、SpringBoot的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#13springboot的核心注解是哪个它主要由哪几个注解组成的)  

### [14、SpringCloud 和 Dubbo 有哪些区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#14springcloud-和-dubbo-有哪些区别)  

### [15、如何重新加载 SpringBoot 上的更改，而无需重新启动服务器？SpringBoot项目如何热部署？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#15如何重新加载-springboot-上的更改而无需重新启动服务器springboot项目如何热部署)  

### [16、可以在SpringBoot application中禁用默认的Web服务器吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#16可以在springboot-application中禁用默认的web服务器吗)  

### [17、SpringBoot 支持哪些日志框架？推荐和默认的日志框架是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#17springboot-支持哪些日志框架推荐和默认的日志框架是哪个)  

### [18、什么是 SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#18什么是-springboot)  

### [19、前后端分离，如何维护接口文档 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#19前后端分离如何维护接口文档-)  

### [20、Spring Cloud Config](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#20spring-cloud-config)  

### [21、什么是织入。什么是织入应用的不同点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#21什么是织入。什么是织入应用的不同点)  

### [22、注解原理是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#22注解原理是什么)  

### [23、什么是Hystrix？它如何实现容错？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#23什么是hystrix它如何实现容错)  

### [24、什么是Spring Cloud Gateway?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#24什么是spring-cloud-gateway)  

### [25、微服务同时调用多个接口，怎么支持事务的啊？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#25微服务同时调用多个接口怎么支持事务的啊)  

### [26、如何在 spring 中启动注解装配？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#26如何在-spring-中启动注解装配)  

### [27、SpringBoot 最大的优势是什么呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#27springboot-最大的优势是什么呢)  

### [28、eureka服务注册与发现原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#28eureka服务注册与发现原理)  

### [29、SpringBoot与SpringCloud 区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#29springboot与springcloud-区别)  

### [30、Spring Cloud Sleuth](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案汇总（2021年Spring面试题答案大全）.md#30spring-cloud-sleuth)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
