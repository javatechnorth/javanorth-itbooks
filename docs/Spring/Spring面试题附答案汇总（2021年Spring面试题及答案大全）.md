# Spring面试题附答案汇总（2021年Spring面试题及答案大全）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、分布式配置中心有那些框架？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#1分布式配置中心有那些框架)  


Apollo、zookeeper、springcloud config。


### [2、什么是 AOP 代理?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#2什么是-aop-代理)  


代理是通知目标对象后创建的对象。从客户端的角度看，代理对象和目标对象是一样的。


### [3、PACT在微服务架构中的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#3pact在微服务架构中的用途是什么)  


PACT是一个开源工具，允许测试服务提供者和消费者之间的交互，与合同隔离，从而提高微服务集成的可靠性。

微服务中的用法

用于在微服务中实现消费者驱动的合同。

测试微服务的消费者和提供者之间的消费者驱动的合同。

查看即将到来的批次


### [4、什么是凝聚力？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#4什么是凝聚力)  


模块内部元素所属的程度被认为是凝聚力。


### [5、微服务之间是如何独立通讯的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#5微服务之间是如何独立通讯的)  


**1、** 远程调用，比如feign调用，直接通过远程过程调用来访问别的service。 2.消息中间件


### [6、SpringBoot 支持哪些日志框架？推荐和默认的日志框架是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#6springboot-支持哪些日志框架推荐和默认的日志框架是哪个)  


SpringBoot 支持 Java Util Logging, Log4j2, Lockback 作为日志框架，如果你使用 Starters 启动器，SpringBoot 将使用 Logback 作为默认日志框架.


### [7、什么是客户证书？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#7什么是客户证书)  


客户端系统用于向远程服务器发出经过身份验证的请求的一种数字证书称为**客户端证书**。客户端证书在许多相互认证设计中起着非常重要的作用，为请求者的身份提供了强有力的保证。


### [8、什么是Spring Initializer?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#8什么是spring-initializer)  


这个问题并不难，但面试官总是以此测试候选人的专业知识。

Spring Initializer是一个网络应用程序，它可以生成一个SpringBoot项目，包含快速启动所需的一切。和往常一样，我们需要一个好的项目框架；它有助于你正确创建项目结构/框架。


### [9、Springboot 有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#9springboot-有哪些优点)  


**1、** 快速创建独立运行的spring项目与主流框架集成

**2、** 使用嵌入式的servlet容器，应用无需打包成war包

**3、** starters自动依赖与版本控制

**4、** 大量的自动配置，简化开发，也可修改默认值

**5、** 准生产环境的运行应用监控

**6、** 与云计算的天然集成


### [10、什么是Spring Cloud Bus?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#10什么是spring-cloud-bus)  


spring cloud bus 将分布式的节点用轻量的消息代理连接起来，它可以用于广播配置文件的更改或者服务直接的通讯，也可用于监控。

如果修改了配置文件，发送一次请求，所有的客户端便会重新读取配置文件。

**使用:**

**1、** 添加依赖

**2、** 配置rabbimq


### [11、什么是断路器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#11什么是断路器)  

### [12、Spring MVC的主要组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#12spring-mvc的主要组件)  

### [13、描述一下 DispatcherServlet 的工作流程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#13描述一下-dispatcherservlet-的工作流程)  

### [14、如何理解 Spring 中的代理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#14如何理解-spring-中的代理)  

### [15、什么是 Spring Data REST?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#15什么是-spring-data-rest)  

### [16、什么是客户证书？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#16什么是客户证书)  

### [17、Spring Cloud Security](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#17spring-cloud-security)  

### [18、什么是金丝雀释放？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#18什么是金丝雀释放)  

### [19、什么是微服务中的反应性扩展？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#19什么是微服务中的反应性扩展)  

### [20、怎么样把ModelMap里面的数据放入Session里面？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#20怎么样把modelmap里面的数据放入session里面)  

### [21、@RestController和@Controller的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#21@restcontroller和@controller的区别)  

### [22、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#22springboot-的核心注解是哪个它主要由哪几个注解组成的)  

### [23、如何使用SpringBoot实现分页和排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#23如何使用springboot实现分页和排序)  

### [24、如何在 spring 中启动注解装配？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#24如何在-spring-中启动注解装配)  

### [25、我们如何监视所有 SpringBoot 微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#25我们如何监视所有-springboot-微服务)  

### [26、什么是微服务架构中的DRY？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#26什么是微服务架构中的dry)  

### [27、什么是starter?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#27什么是starter)  

### [28、如何在自定义端口上运行 SpringBoot 应用程序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#28如何在自定义端口上运行-springboot-应用程序)  

### [29、[@Required ](/Required ) 注解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#29[@required-]/required--注解)  

### [30、如何启用/禁用执行器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#30如何启用/禁用执行器)  

### [31、SpringBoot Starter 的工作原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案汇总（2021年Spring面试题及答案大全）.md#31springboot-starter-的工作原理是什么)  





