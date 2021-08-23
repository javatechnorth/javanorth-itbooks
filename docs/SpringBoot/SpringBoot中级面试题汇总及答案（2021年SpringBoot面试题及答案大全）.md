# SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）

SpringBoot面试题及答案【最新版】SpringBoot高级面试题大全(2021版)，发现网上很多SpringBoot面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringBoot面试题大全，SpringBoot面试题大汇总，有大量经典的SpringBoot面试题以及答案，包含SpringBoot语言常见面试题、SpringBoot工程师高级面试题及一些大厂SpringBoot开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringBoot面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringBoot面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、SpringBoot Starter 的工作原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#1springboot-starter-的工作原理是什么)  


SpringBoot 在启动的时候会干这几件事情：

**1、** SpringBoot 在启动时会去依赖的 Starter 包中寻找 resources/META-INF/spring.factories 文件，然后根据文件中配置的 Jar 包去扫描项目所依赖的 Jar 包。

**2、** 根据 spring.factories 配置加载 AutoConfigure 类

**3、** 根据 [@Conditional ](/Conditional ) 注解的条件，进行自动配置并将 Bean 注入 Spring Context

总结一下，其实就是 SpringBoot 在启动的时候，按照约定去读取 SpringBoot Starter 的配置信息，再根据配置信息对资源进行初始化，并注入到 Spring 容器中。这样 SpringBoot 启动完毕后，就已经准备好了一切资源，使用过程中直接注入对应 Bean 资源即可。

这只是简单的三连环问答，不知道有多少同学能够完整的回答出来。

其实 SpringBoot 中有很多的技术点可以挖掘，今天给大家整理了十个高频 SpringBoot 面试题，希望可以在后期的面试中帮助到大家。


### [2、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#2springboot-的核心配置文件有哪几个它们的区别是什么)  


SpringBoot 的核心配置文件是 application 和 bootstrap 配置文件。

application 配置文件这个容易理解，主要用于 SpringBoot 项目的自动化配置。

bootstrap 配置文件有以下几个应用场景。

使用 Spring Cloud Config 配置中心时，这时需要在 bootstrap 配置文件中添加连接到配置中心的配置属性来加载外部配置中心的配置信息；

一些固定的不能被覆盖的属性；

一些加密/解密的场景；


### [3、Spring、SpringBoot、SpringMVC的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#3springspringbootspringmvc的区别)  


**1、** Spring框架就像一个家族，有众多衍生产品，例如boot、mvc、jpa等等。但他们的基础都是Spring的ioc、aop。ioc提供了依赖注入的容器，aop解决了面向横切面编程，然后在此两者的基础上实现了其它延伸产品的高级功能；

**2、** springMVC是基于Servlet的一个MVC框架主要解决WEB开发的问题；

**3、** 为了简化开发的使用，从而创造性地推出了SpringBoot框架，默认优于配置


### [4、SpringBoot的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#4springboot的核心注解是哪个它主要由哪几个注解组成的)  


启动类上面的注解是@SpringBootApplication，它也是SpringBoot的核心注解，主要组合包含了以下3个注解：

**1、** @SpringBootConfiguration：组合了@Configuration注解，实现配置文件的功能。

**2、** @EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：SpringBootApplication(exclude={DataSourceAutoConfiguration.class})

**3、** @ComponentScan：Spring组件扫描


### [5、SpringBoot 配置文件的加载顺序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#5springboot-配置文件的加载顺序)  


由jar包外向jar包内进行寻找;

优先加载带profile

jar包外部的application-{profile}.properties或application.yml(带spring.profile配置文件

jar包内部的application-{profile}.properties或application.yml(带spring.profile配置文件

再来加载不带profile

jar包外部的application.properties或application.yml(不带spring.profile配置文件

jar包内部的application.properties或application.yml(不带spring.profile配置文件


### [6、如何在 SpringBoot 中添加通用的 JS 代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#6如何在-springboot-中添加通用的-js-代码)  


在源文件夹下，创建一个名为 static 的文件夹。然后，你可以把你的静态的内容放在这里面。

例如，myapp.js 的路径是 resources\static\js\myapp.js

**

你可以参考它在 jsp 中的使用方法：**

错误：HAL browser gives me unauthorized error - Full authenticaition is required to access this resource.

该如何来修复这个错误呢？

两种方法：

方法 1：关闭安全验证

application.properties

```
management.security.enabled:FALSE
```

方法二：在日志中搜索密码并传递至请求标头中


### [7、SpringBoot 中如何实现定时任务 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#7springboot-中如何实现定时任务-)  


在 SpringBoot 中使用定时任务主要有两种不同的方式，一个就是使用 Spring 中的 [@Scheduled ](/Scheduled ) 注解，另一-个则是使用第三方框架 Quartz。

使用 Spring 中的 [@Scheduled ](/Scheduled ) 的方式主要通过 [@Scheduled ](/Scheduled ) 注解来实现。


### [8、如何在SpringBoot中禁用Actuator端点安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#8如何在springboot中禁用actuator端点安全性)  


默认情况下，所有敏感的HTTP端点都是安全的，只有具有ACTUATOR角色的用户才能访问它们。

安全性是使用标准的HttpServletRequest.isUserInRole方法实施的。 我们可以使用management.security.enabled = false 来禁用安全性。只有在执行机构端点在防火墙后访问时，才建议禁用安全性。

如何在自定义端口上运行SpringBoot应用程序？ 为了在自定义端口上运行SpringBoot应用程序，您可以在application.properties中指定端口。 server.port = 8090


### [9、Async异步调用方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#9async异步调用方法)  


在SpringBoot中使用异步调用是很简单的，只需要在方法上使用@Async注解即可实现方法的异步调用。 注意：需要在启动类加入@EnableAsync使异步调用@Async注解生效。


### [10、什么是自动配置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#10什么是自动配置)  


Spring 和 SpringMVC 的问题在于需要配置大量的参数。

我们能否带来更多的智能？当一个 MVC JAR 添加到应用程序中的时候，我们能否自动配置一些 beans？

Spring 查看（CLASSPATH 上可用的框架）已存在的应用程序的配置。在此基础上，SpringBoot 提供了配置应用程序和框架所需要的基本配置。这就是自动配置。


### [11、是否可以在SpringBoot中覆盖或替换嵌入式Tomcat？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#11是否可以在springboot中覆盖或替换嵌入式tomcat)  

### [12、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#12springboot-的核心注解是哪个它主要由哪几个注解组成的)  

### [13、什么是Apache Kafka？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#13什么是apache-kafka)  

### [14、什么是SpringBoot ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#14什么是springboot-)  

### [15、SpringData 项目所支持的关系数据存储技术：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#15springdata-项目所支持的关系数据存储技术：)  

### [16、SpringBoot集成mybatis的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#16springboot集成mybatis的过程)  

### [17、RequestMapping 和 GetMapping 的不同之处在哪里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#17requestmapping-和-getmapping-的不同之处在哪里)  

### [18、JPA 和 Hibernate 有哪些区别？JPA 可以支持动态 SQL 吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#18jpa-和-hibernate-有哪些区别jpa-可以支持动态-sql-吗)  

### [19、项目中前后端分离部署，所以需要解决跨域的问题。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#19项目中前后端分离部署所以需要解决跨域的问题。)  

### [20、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#20运行-springboot-有哪几种方式)  

### [21、什么是Spring Initializer?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#21什么是spring-initializer)  

### [22、SpringBoot 还提供了其它的哪些 Starter Project Options？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#22springboot-还提供了其它的哪些-starter-project-options)  

### [23、spring boot扫描流程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#23spring-boot扫描流程)  

### [24、SpringBoot、Spring MVC 和 Spring 有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#24springbootspring-mvc-和-spring-有什么区别)  

### [25、SpringBoot的配置文件有哪几种格式？区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#25springboot的配置文件有哪几种格式区别是什么)  

### [26、为什么我们不建议在实际的应用程序中使用 Spring Data Rest?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#26为什么我们不建议在实际的应用程序中使用-spring-data-rest)  

### [27、您使用了哪些 starter maven 依赖项？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#27您使用了哪些-starter-maven-依赖项)  

### [28、spring boot 核心的两个配置文件：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#28spring-boot-核心的两个配置文件：)  

### [29、什么是Spring Profiles？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#29什么是spring-profiles)  

### [30、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#30springboot-的核心注解是哪个它主要由哪几个注解组成的)  

### [31、SpringBoot如何配置log4j？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#31springboot如何配置log4j)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
