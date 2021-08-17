# Spring高级面试题大汇总（2021年Spring面试题大全带答案）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、SpringBoot 支持哪些日志框架？推荐和默认的日志框架是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#1springboot-支持哪些日志框架推荐和默认的日志框架是哪个)  


SpringBoot 支持 Java Util Logging, Log4j2, Lockback 作为日志框架，如果你使用 Starters 启动器，SpringBoot 将使用 Logback 作为默认日志框架，但是不管是那种日志框架他都支持将配置文件输出到控制台或者文件中。


### [2、什么是SpringBoot](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#2什么是springboot)  


**1、** 用来简化spring应用的初始搭建以及开发过程 使用特定的方式来进行配置（properties或yml文件）

**2、** 创建独立的spring引用程序 main方法运行

**3、** 嵌入的Tomcat 无需部署war文件

**4、** 简化maven配置


### [3、DiscoveryClient的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#3discoveryclient的作用)  


可以从注册中心中根据服务别名获取注册的服务器信息。


### [4、什么是Spring MVC？简单介绍下你对Spring MVC的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#4什么是spring-mvc简单介绍下你对spring-mvc的理解)  


Spring MVC是一个基于Java的实现了MVC设计模式的请求驱动类型的轻量级Web框架，通过把模型-视图-控制器分离，将web层进行职责解耦，把复杂的web应用分成逻辑清晰的几部分，简化开发，减少出错，方便组内开发人员之间的配合。


### [5、spring DAO 有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#5spring-dao-有什么用)  


Spring DAO 使得 JDBC，Hibernate 或 JDO 这样的数据访问技术更容易以一种统一的方式工作。 这使得用户容易在持久性技术之间切换。 它还允许您在编写代码时，无需考虑捕获每种技术不同的异常。


### [6、什么是基于Java的Spring注解配置? 给一些注解的例子.](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#6什么是基于java的spring注解配置-给一些注解的例子)  


基于Java的配置，允许你在少量的Java注解的帮助下，进行你的大部分Spring配置而非通过XML文件。

以[@Configuration ](/Configuration ) 注解为例，它用来标记类可以当做一个bean的定义，被Spring IOC容器使用。另一个例子是@Bean注解，它表示此方法将要返回一个对象，作为一个bean注册进Spring应用上下文。


### [7、SpringBoot 有哪几种读取配置的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#7springboot-有哪几种读取配置的方式)  


SpringBoot 可以通过 @PropertySource,@Value,@Environment, @ConfigurationProperties 来绑定变量。


### [8、SpringBoot的配置文件有哪几种格式？区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#8springboot的配置文件有哪几种格式区别是什么)  


.properties和.yml，它们的区别主要是书写格式不同。yml采取的是缩进的格式 不支持@PerpertySource注解导入配置


### [9、Spring Cloud Netflix](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#9spring-cloud-netflix)  


Netflix OSS 开源组件集成，包括Eureka、Hystrix、Ribbon、Feign、Zuul等核心组件。

**1、** Eureka：服务治理组件，包括服务端的注册中心和客户端的服务发现机制；

**2、** Ribbon：负载均衡的服务调用组件，具有多种负载均衡调用策略；

**3、** Hystrix：服务容错组件，实现了断路器模式，为依赖服务的出错和延迟提供了容错能力；

**4、** Feign：基于Ribbon和Hystrix的声明式服务调用组件；

**5、** Zuul：API网关组件，对请求提供路由及过滤功能。


### [10、什么是Spring Cloud？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#10什么是spring-cloud)  


在微服务中，SpringCloud是一个提供与外部系统集成的系统。它是一个敏捷的框架，可以短平快构建应用程序。与有限数量的数据处理相关联，它在微服务体系结构中起着非常重要的作用。 **以下为 Spring Cloud 的核心特性**：

**1、** 版本化/分布式配置。

**2、** 服务注册和发现。

**3、** 服务和服务之间的调用。

**4、** 路由。

**5、** 断路器和负载平衡。

**6、** 分布式消息传递。


### [11、spring-boot-starter-parent 有什么用 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#11spring-boot-starter-parent-有什么用-)  

### [12、XMLBeanFactory](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#12xmlbeanfactory)  

### [13、介绍一下 WebApplicationContext](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#13介绍一下-webapplicationcontext)  

### [14、eureka缓存机制：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#14eureka缓存机制：)  

### [15、什么是 Spring Framework？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#15什么是-spring-framework)  

### [16、Spring Cloud Gateway](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#16spring-cloud-gateway)  

### [17、解释基于XML Schema方式的切面实现。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#17解释基于xml-schema方式的切面实现。)  

### [18、如何禁用特定的自动配置类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#18如何禁用特定的自动配置类)  

### [19、YAML 配置的优势在哪里 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#19yaml-配置的优势在哪里-)  

### [20、您使用了哪些 starter maven 依赖项？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#20您使用了哪些-starter-maven-依赖项)  

### [21、什么是 AOP什么是引入?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#21什么是-aop什么是引入)  

### [22、什么是微服务](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#22什么是微服务)  

### [23、谈谈服务雪崩效应](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#23谈谈服务雪崩效应)  

### [24、什么是依赖注入？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#24什么是依赖注入)  

### [25、负载均衡的意义是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#25负载均衡的意义是什么)  

### [26、什么是Spring Cloud Bus？我们需要它吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#26什么是spring-cloud-bus我们需要它吗)  

### [27、[@Controller ](/Controller ) 注解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#27[@controller-]/controller--注解)  

### [28、SpringBoot事物的使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#28springboot事物的使用)  

### [29、列举 Spring Framework 的优点。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#29列举-spring-framework-的优点。)  

### [30、介绍一下 WebApplicationContext](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题大汇总（2021年Spring面试题大全带答案）.md#30介绍一下-webapplicationcontext)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
