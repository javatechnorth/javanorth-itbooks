# Spring面试题及答案汇总（2021年Spring面试题答案大全）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是通知（Advice）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#1什么是通知advice)  


特定 JoinPoint 处的 Aspect 所采取的动作称为 Advice。Spring AOP 使用一个 Advice 作为拦截器，在 JoinPoint “周围”维护一系列的拦截器。


### [2、第⼀层缓存：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#2第⼀层缓存：)  


readOnlyCacheMap，本质上是ConcurrentHashMap：这是⼀个JVM的CurrentHashMap只读缓存，这个主要是为了供客户端获取注册信息时使⽤，其缓存更新，依赖于定时器的更新，通过和readWriteCacheMap 的值做对⽐，如果数据不⼀致，则以readWriteCacheMap 的数据为准。readOnlyCacheMap 缓存更新的定时器时间间隔，默认为30秒

#
### [3、什么是 Aspect 切面](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#3什么是-aspect-切面)  


AOP核心就是切面，它将多个类的通用行为封装成可重用的模块，该模块含有一组API提供横切功能。比如，一个日志模块可以被称作日志的AOP切面。根据需求的不同，一个应用程序可以有若干切面。在Spring AOP中，切面通过带有@Aspect注解的类实现。


### [4、JPA 和 Hibernate 有哪些区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#4jpa-和-hibernate-有哪些区别)  


简而言之

JPA 是一个规范或者接口

Hibernate 是 JPA 的一个实现

当我们使用 JPA 的时候，我们使用 javax.persistence 包中的注释和接口时，不需要使用 hibernate 的导入包。

我们建议使用 JPA 注释，因为哦我们没有将其绑定到 Hibernate 作为实现。后来（我知道 - 小于百分之一的几率），我们可以使用另一种 JPA 实现。


### [5、SpringCloud Config 可以实现实时刷新吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#5springcloud-config-可以实现实时刷新吗)  


springcloud config实时刷新采用SpringCloud Bus消息总线。


### [6、什么是Eureka](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#6什么是eureka)  


Eureka作为SpringCloud的服务注册功能服务器，他是服务注册中心，系统中的其他服务使用Eureka的客户端将其连接到Eureka Service中，并且保持心跳，这样工作人员可以通过Eureka Service来监控各个微服务是否运行正常。


### [7、什么是消费者驱动的合同（CDC）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#7什么是消费者驱动的合同cdc)  


这基本上是用于开发微服务的模式，以便它们可以被外部系统使用。当我们处理微服务时，有一个特定的提供者构建它，并且有一个或多个使用微服务的消费者。

通常，提供程序在XML文档中指定接口。但在消费者驱动的合同中，每个服务消费者都传达了提供商期望的接口。


### [8、Spring支持的ORM](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#8spring支持的orm)  


Spring支持以下ORM：

**1、** Hibernate

**2、** iBatis

**3、** JPA (Java Persistence API)

**4、** TopLink

**5、** JDO (Java Data Objects)

**6、** OJB


### [9、什么是 SpringBoot Stater ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#9什么是-springboot-stater-)  


启动器是一套方便的依赖没描述符，它可以放在自己的程序中。你可以一站式的获取你所需要的 Spring 和相关技术，而不需要依赖描述符的通过示例代码搜索和复制黏贴的负载。

例如，如果你想使用 Sping 和 JPA 访问数据库，只需要你的项目包含 spring-boot-starter-data-jpa 依赖项，你就可以完美进行。


### [10、什么是服务降级](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#10什么是服务降级)  


consumer 端：consumer 如果发现某个provider出现异常情况，⽐如，经常超时(可能是熔断引起的降级)，数据错误，这时，consumer可以采取⼀定的策略，降级provider的逻辑，基本的有直接返回固定的数据。

provider 端：当provider 发现流量激增的时候，为了保护⾃身的稳定性，也可能考虑降级服务。

**1、** 直接给consumer返回固定数据

**2、** 需要实时写⼊数据库的，先缓存到队列⾥，异步写⼊数据库。


### [11、spring DAO 有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#11spring-dao-有什么用)  

### [12、Spring Cloud Config](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#12spring-cloud-config)  

### [13、我们如何监视所有 SpringBoot 微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#13我们如何监视所有-springboot-微服务)  

### [14、什么是Idempotence以及它在哪里使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#14什么是idempotence以及它在哪里使用)  

### [15、如何在自定义端口上运行SpringBoot应用程序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#15如何在自定义端口上运行springboot应用程序)  

### [16、SpringBoot 有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#16springboot-有哪些优点)  

### [17、一个 Spring Bean 定义 包含什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#17一个-spring-bean-定义-包含什么)  

### [18、IOC的优点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#18ioc的优点是什么)  

### [19、区分 BeanFactory 和 ApplicationContext。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#19区分-beanfactory-和-applicationcontext。)  

### [20、Spring Cloud Task](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#20spring-cloud-task)  

### [21、如何使用 SpringBoot 部署到不同的服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#21如何使用-springboot-部署到不同的服务器)  

### [22、我们如何监视所有SpringBoot微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#22我们如何监视所有springboot微服务)  

### [23、如何覆盖SpringBoot项目的默认属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#23如何覆盖springboot项目的默认属性)  

### [24、什么是Spring beans?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#24什么是spring-beans)  

### [25、什么是持续集成（CI）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#25什么是持续集成ci)  

### [26、Ribbon底层实现原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#26ribbon底层实现原理)  

### [27、缓存机制：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#27缓存机制：)  

### [28、WebApplicationContext](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#28webapplicationcontext)  

### [29、Spring Cloud Gateway](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#29spring-cloud-gateway)  

### [30、多个消费者调⽤同⼀接⼝，eruka默认的分配⽅式是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案汇总（2021年Spring面试题答案大全）.md#30多个消费者调⽤同⼀接⼝eruka默认的分配⽅式是什么)  





