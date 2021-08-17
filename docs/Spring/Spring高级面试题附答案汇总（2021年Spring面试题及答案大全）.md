# Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、什么是嵌入式服务器？我们为什么要使用嵌入式服务器呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#1什么是嵌入式服务器我们为什么要使用嵌入式服务器呢)  


思考一下在你的虚拟机上部署应用程序需要些什么。

第一步：安装 Java

第二部：安装 Web 或者是应用程序的服务器（Tomat/Wbesphere/Weblogic 等等）

第三部：部署应用程序 war 包

如果我们想简化这些步骤，应该如何做呢？

让我们来思考如何使服务器成为应用程序的一部分？

你只需要一个安装了 Java 的虚拟机，就可以直接在上面部署应用程序了，

是不是很爽？

这个想法是嵌入式服务器的起源。

当我们创建一个可以部署的应用程序的时候，我们将会把服务器（例如，tomcat）嵌入到可部署的服务器中。

例如，对于一个 SpringBoot 应用程序来说，你可以生成一个包含 Embedded Tomcat 的应用程序 jar。你就可以像运行正常 Java 应用程序一样来运行 web 应用程序了。

嵌入式服务器就是我们的可执行单元包含服务器的二进制文件（例如，tomcat.jar）。


### [2、什么是Spring Cloud Zuul（服务网关）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#2什么是spring-cloud-zuul服务网关)  


Zuul是对SpringCloud提供的成熟对的路由方案，他会根据请求的路径不同，网关会定位到指定的微服务，并代理请求到不同的微服务接口，他对外隐蔽了微服务的真正接口地址。

三个重要概念：动态路由表，路由定位，反向代理：

**1、** 动态路由表：Zuul支持Eureka路由，手动配置路由，这俩种都支持自动更新

**2、** 路由定位：根据请求路径，Zuul有自己的一套定位服务规则以及路由表达式匹配

**3、** 反向代理：客户端请求到路由网关，网关受理之后，在对目标发送请求，拿到响应之后在 给客户端它可以和Eureka,Ribbon,Hystrix等组件配合使用，

**Zuul的应用场景：**

对外暴露，权限校验，服务聚合，日志审计等


### [3、如何使用 SpringBoot 自动重装我的应用程序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#3如何使用-springboot-自动重装我的应用程序)  


使用 SpringBoot 开发工具。

把 SpringBoot 开发工具添加进入你的项目是简单的。

把下面的依赖项添加至你的 SpringBoot Project pom.xml 中

重启应用程序，然后就可以了。

同样的，如果你想自动装载页面，有可以看看 FiveReload

```
http://www.logicbig.com/tutorials/spring-framework/spring-boot/boot-live-reload/.
```

在我测试的时候，发现了 LiveReload 漏洞，如果你测试时也发现了，请一定要告诉我们。


### [4、SpringBoot 2.X 有什么新特性？与 1.X 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#4springboot-2x-有什么新特性与-1x-有什么区别)  


**1、** 依赖 JDK 版本升级：2.x 里面的许多方法应用了 JDK 8 的许多高级新特性，至少需要 JDK 8 的支持；

**2、** 第三方类库升：2.x 对第三方类库升级了所有能升级的稳定版本，例如：Spring Framework 5+、Tomcat 8.5+、Hibernate 5.2+、Thymeleaf 3+；

**3、** 响应式 Spring 编程：2.x 通过启动器和自动配置全面支持 Spring 的响应式编程，响应式编程是完全异步和非阻塞的，它是基于事件驱动模型，而不是传统的线程模型；

**4、** 连接池：2.x 默认使用 HikariCP 连接池；

**5、** json：提供了一个 spring-boot-starter-json 启动器对 JSON 读写的支持；

**6、** Quartz：2.x 提供了一个 spring-boot-starter-quartz 启动器对定时任务框架 Quartz 的支持；

**7、** HTTP/2 支持：提供对HTTP/2 的支持，如：Tomcat, Undertow, Jetty；

**8、** Actuator加强：在 2.x 中，对执行器端点进行了许多改进，所有的 HTTP 执行端点现在都暴露在 /actuator路径下，并对 JSON 结果集也做了改善。


### [5、Spring MVC怎么和AJAX相互调用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#5spring-mvc怎么和ajax相互调用的)  


通过Jackson框架就可以把Java里面的对象直接转化成Js可以识别的Json对象。具体步骤如下 ：

**1、** 加入Jackson.jar

**2、** 在配置文件中配置json的映射

**3、** 在接受Ajax方法里面可以直接返回Object,List等,但方法前面要加上@ResponseBody注解。


### [6、REST 和RPC对比](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#6rest-和rpc对比)  


**1、** RPC主要的缺陷是服务提供方和调用方式之间的依赖太强，需要对每一个微服务进行接口的定义，并通过持续继承发布，严格版本控制才不会出现冲突。

**2、** REST是轻量级的接口，服务的提供和调用不存在代码之间的耦合，只需要一个约定进行规范。


### [7、核心容器（应用上下文) 模块。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#7核心容器应用上下文-模块。)  


这是基本的Spring模块，提供spring 框架的基础功能，BeanFactory 是 任何以spring为基础的应用的核心。Spring 框架建立在此模块之上，它使Spring成为一个容器。


### [8、Spring框架的事务管理有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#8spring框架的事务管理有哪些优点)  


**1、** 它为不同的事务API 如 JTA，JDBC，Hibernate，JPA 和JDO，提供一个不变的编程模式。

**2、** 它为编程式事务管理提供了一套简单的API而不是一些复杂的事务API如

**3、** 它支持声明式事务管理。

**4、** 它和Spring各种数据访问抽象层很好得集成。


### [9、什么是bean的自动装配？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#9什么是bean的自动装配)  


Spring 容器能够自动装配相互合作的bean，这意味着容器不需要和配置，能通过Bean工厂自动处理bean之间的协作。


### [10、Spring Framework 有哪些不同的功能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#10spring-framework-有哪些不同的功能)  


**1、** 轻量级 - Spring 在代码量和透明度方面都很轻便。

**2、** IOC - 控制反转

**3、** AOP - 面向切面编程可以将应用业务逻辑和系统服务分离，以实现高内聚。

**4、** 容器 - Spring 负责创建和管理对象（Bean）的生命周期和配置。

**5、** MVC - 对 web 应用提供了高度可配置性，其他框架的集成也十分方便。

**6、** 事务管理 - 提供了用于事务管理的通用抽象层。 Spring 的事务支持也可用于容器较少的环境。

**7、** JDBC 异常 - Spring 的 JDBC 抽象层提供了一个异常层次结构，简化了错误处理策略。4、Spring Framework 中有多少个模块，它们分别是什么？

**1、** Spring 核心容器 – 该层基本上是 Spring Framework 的核心。它包含以下模块：

**2、** Spring Core

**3、** Spring Bean

**4、** SpEL (Spring Expression Language)

**5、** Spring Context

**数据访问/集成 – 该层提供与数据库交互的支持。 它包含以下模块：**

**1、** JDBC (Java DataBase Connectivity)

**2、** ORM (Object Relational Mapping)

**3、** OXM (Object XML Mappers)

**4、** JMS (Java Messaging Service)

**5、** Transaction

**1、** Web – 该层提供了创建 Web 应用程序的支持。它包含以下模块：AOP – 该层支持面向切面编程

**2、** Web

**3、** Web – Servlet

**4、** Web – Socket

**5、** Web – Portlet

**6、** Instrumentation – 该层为类检测和类加载器实现提供支持。

**7、** Test – 该层为使用 JUnit 和 TestNG 进行测试提供支持

**几个杂项模块:**

Messaging – 该模块为 STOMP 提供支持。它还支持注解编程模型，该模型用于从 WebSocket 客户端路由和处理 STOMP 消息。

Aspects – 该模块为与 AspectJ 的集成提供支持。


### [11、什么是 Spring Profiles？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#11什么是-spring-profiles)  

### [12、SpringBoot如何实现打包](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#12springboot如何实现打包)  

### [13、什么是CSRF攻击？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#13什么是csrf攻击)  

### [14、解释AOP模块](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#14解释aop模块)  

### [15、SpringBoot 怎么用好自动配置，精髓:](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#15springboot-怎么用好自动配置精髓:)  

### [16、Spring MVC怎么样设定重定向和转发的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#16spring-mvc怎么样设定重定向和转发的)  

### [17、Zuul网关如何搭建集群](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#17zuul网关如何搭建集群)  

### [18、@RequestMapping注解的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#18@requestmapping注解的作用)  

### [19、列举 IoC 的一些好处](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#19列举-ioc-的一些好处)  

### [20、您对Mike Cohn的测试金字塔了解多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#20您对mike-cohn的测试金字塔了解多少)  

### [21、RequestMapping 和 GetMapping 的不同之处在哪里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#21requestmapping-和-getmapping-的不同之处在哪里)  

### [22、SpringBoot和springcloud认识](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#22springboot和springcloud认识)  

### [23、SpringBoot 中的 starter 到底是什么 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#23springboot-中的-starter-到底是什么-)  

### [24、如何实现 SpringBoot应用程序的安全性?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#24如何实现-springboot应用程序的安全性)  

### [25、如何实现SpringBoot应用程序的安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#25如何实现springboot应用程序的安全性)  

### [26、MVC是什么？MVC设计模式的好处有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#26mvc是什么mvc设计模式的好处有哪些)  

### [27、SpingMvc中的控制器的注解一般用哪个,有没有别的注解可以替代？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#27spingmvc中的控制器的注解一般用哪个,有没有别的注解可以替代)  

### [28、SpringBoot 还提供了其它的哪些 Starter Project Options？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#28springboot-还提供了其它的哪些-starter-project-options)  

### [29、我们如何监视所有 SpringBoot 微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#29我们如何监视所有-springboot-微服务)  

### [30、什么是不同类型的双因素身份认证？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#30什么是不同类型的双因素身份认证)  

### [31、SpringBoot常用的starter有哪些?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题附答案汇总（2021年Spring面试题及答案大全）.md#31springboot常用的starter有哪些)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
