# Spring面试题附答案（2021年Spring面试题及答案大汇总）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何在 SpringBoot 启动的时候运行一些特定的代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#1如何在-springboot-启动的时候运行一些特定的代码)  


可以实现接口 ApplicationRunner 或者 CommandLineRunner，这两个接口实现方式一样，它们都只提供了一个 run 方法，实现上述接口的类加入IOC容器即可生效。


### [2、Spring Cloud OpenFeign](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#2spring-cloud-openfeign)  


Feign是一个声明性的Web服务客户端。它使编写Web服务客户端变得更容易。要使用Feign，我们可以将调用的服务方法定义成抽象方法保存在本地添加一点点注解就可以了，不需要自己构建Http请求了，直接调用接口就行了，不过要注意，调用方法要和本地抽象方法的签名完全一致。


### [3、常用网关框架有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#3常用网关框架有那些)  


Nginx、Zuul、Gateway


### [4、如何重新加载SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#4如何重新加载springboot上的更改而无需重新启动服务器)  


这可以使用DEV工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式tomcat将重新启动。

SpringBoot有一个开发工具（DevTools）模块，它有助于提高开发人员的生产力。Java开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务器。

开发人员可以重新加载SpringBoot上的更改，而无需重新启动服务器。这将消除每次手动部署更改的需要。SpringBoot在发布它的第一个版本时没有这个功能。

这是开发人员最需要的功能。DevTools模块完全满足开发人员的需求。该模块将在生产环境中被禁用。它还提供H2数据库控制台以更好地测试应用程序。


### [5、如何集成SpringBoot和ActiveMQ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#5如何集成springboot和activemq)  


对于集成SpringBoot和ActiveMQ，我们使用

依赖关系。 它只需要很少的配置，并且不需要样板代码。


### [6、SpringBoot有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#6springboot有哪些优点)  


**1、** 减少开发，测试时间和努力。

**2、** 使用JavaConfig有助于避免使用XML。

**3、** 避免大量的Maven导入和各种版本冲突。

**4、** 提供意见发展方法。

**5、** 通过提供默认值快速开始开发。

**6、** 没有单独的Web服务器需要。这意味着你不再需要启动Tomcat，Glassfish或其他任何东西。

**7、** 需要更少的配置 因为没有web.xml文件。只需添加用@ Configuration注释的类，然后添加用@Bean注释的方法，Spring将自动加载对象并像以前一样对其进行管理。您甚至可以将@Autowired添加到bean方法中，以使Spring自动装入需要的依赖关系中。

**8、** 基于环境的配置 使用这些属性，您可以将您正在使用的环境传递到应用程序：-Dspring.profiles.active = {enviornment}。在加载主应用程序属性文件后，Spring将在（application{environment} .properties）中加载后续的应用程序属性文件。


### [7、SpringBoot 提供了哪些核心功能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#7springboot-提供了哪些核心功能)  


**1、** 独立运行 Spring 项目

**2、** 内嵌 Servlet 容器

SpringBoot 可以选择内嵌 Tomcat、Jetty 或者 Undertow，这样我们无须以 war 包形式部署项目。

**3、** 提供 Starter 简化 Maven 配置

例如，当你使用了 spring-boot-starter-web ，会自动加入如下依赖：`spring-boot-starter-web` 的 pom 文件

**4、** 自动配置 Spring Bean

SpringBoot 检测到特定类的存在，就会针对这个应用做一定的配置，进行自动配置 Bean ，这样会极大地减少我们要使用的配置。

**5、** 准生产的应用监控

SpringBoot 提供基于 HTTP、JMX、SSH 对运行时的项目进行监控。

**6、** 无代码生成和 XML 配置

SpringBoot 没有引入任何形式的代码生成，它是使用的 Spring 4.0 的条件 [@Condition ](/Condition ) 注解以实现根据条件进行配置。同时使用了 Maven /Gradle 的依赖传递解析机制来实现 Spring 应用里面的自动配置。


### [8、如何集成 SpringBoot 和 ActiveMQ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#8如何集成-springboot-和-activemq)  


对于集成 SpringBoot 和 ActiveMQ，我们使用依赖关系。它只需要很少的配置，并且不需要样板代码。


### [9、什么是Spring Profiles？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#9什么是spring-profiles)  


Spring Profiles允许用户根据配置文件（dev，test，prod等）来注册bean。因此，当应用程序在开发中运行时，只有某些bean可以加载，而在PRODUCTION中，某些其他bean可以加载。假设我们的要求是Swagger文档仅适用于QA环境，并且禁用所有其他文档。这可以使用配置文件来完成。SpringBoot使得使用配置文件非常简单。


### [10、什么是Eureka的自我保护模式，](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#10什么是eureka的自我保护模式)  


默认情况下，如果Eureka Service在一定时间内没有接收到某个微服务的心跳，Eureka Service会进入自我保护模式，在该模式下Eureka Service会保护服务注册表中的信息，不在删除注册表中的数据，当网络故障恢复后，Eureka Servic 节点会自动退出自我保护模式


### [11、Spring Cloud和SpringBoot版本对应关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#11spring-cloud和springboot版本对应关系)  

### [12、SpringBoot常用的starter有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#12springboot常用的starter有哪些)  

### [13、spring 支持集中 bean scope？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#13spring-支持集中-bean-scope)  

### [14、什么是代理?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#14什么是代理)  

### [15、网关的作用是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#15网关的作用是什么)  

### [16、什么是JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#16什么是javaconfig)  

### [17、SpringBoot和SpringCloud的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#17springboot和springcloud的区别)  

### [18、Spring Initializr 是创建 SpringBoot Projects 的唯一方法吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#18spring-initializr-是创建-springboot-projects-的唯一方法吗)  

### [19、什么是YAML？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#19什么是yaml)  

### [20、Spring MVC的控制器是不是单例模式,如果是,有什么问题,怎么解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#20spring-mvc的控制器是不是单例模式,如果是,有什么问题,怎么解决)  

### [21、不同版本的 Spring Framework 有哪些主要功能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#21不同版本的-spring-framework-有哪些主要功能)  

### [22、解释不同方式的自动装配 。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#22解释不同方式的自动装配-。)  

### [23、如何配置SpringBoot应用程序日志记录？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#23如何配置springboot应用程序日志记录)  

### [24、你怎样定义类的作用域?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#24你怎样定义类的作用域)  

### [25、SpringBoot的自动配置原理是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#25springboot的自动配置原理是什么)  

### [26、访问RESTful微服务的方法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#26访问restful微服务的方法是什么)  

### [27、Spring MVC用什么对象从后台向前台传递数据的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#27spring-mvc用什么对象从后台向前台传递数据的)  

### [28、Bean 工厂和 Application contexts 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#28bean-工厂和-application-contexts-有什么区别)  

### [29、微服务限流 dubbo限流：dubbo提供了多个和请求相关的filter：ActiveLimitFilter ExecuteLimitFilter TPSLimiterFilter](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#29微服务限流-dubbo限流：dubbo提供了多个和请求相关的filter：activelimitfilter-executelimitfilter-tpslimiterfilter)  

### [30、微服务之间如何独立通讯的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#30微服务之间如何独立通讯的)  

### [31、什么是切点（JoinPoint）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题附答案（2021年Spring面试题及答案大汇总）.md#31什么是切点joinpoint)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
