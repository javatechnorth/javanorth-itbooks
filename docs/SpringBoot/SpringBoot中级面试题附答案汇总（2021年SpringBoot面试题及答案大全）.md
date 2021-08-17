# SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）

SpringBoot面试题及答案【最新版】SpringBoot高级面试题大全(2021版)，发现网上很多SpringBoot面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringBoot面试题大全，SpringBoot面试题大汇总，有大量经典的SpringBoot面试题以及答案，包含SpringBoot语言常见面试题、SpringBoot工程师高级面试题及一些大厂SpringBoot开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringBoot面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringBoot面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、什么是 Spring Data？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#1什么是-spring-data)  


来自：[//projects.spring.io/spring-](//projects.spring.io/spring-) data/

Spring Data 的使命是在保证底层数据存储特殊性的前提下，为数据访问提供一个熟悉的，一致性的，基于 Spring 的编程模型。这使得使用数据访问技术，关系数据库和非关系数据库，map-reduce 框架以及基于云的数据服务变得很容易。

为了让它更简单一些，Spring Data 提供了不受底层数据源限制的 Abstractions 接口。

你可以定义一简单的库，用来插入，更新，删除和检索代办事项，而不需要编写大量的代码。


### [2、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#2运行-springboot-有哪几种方式)  


**1、** 打包用命令或者者放到容器中运行

**2、** 用 Maven/ Gradle 插件运行

**3、** 直接执行 main 方法运行


### [3、什么是Swagger？你用SpringBoot实现了它吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#3什么是swagger你用springboot实现了它吗)  


Swagger广泛用于可视化API，使用Swagger UI为前端开发人员提供在线沙箱。Swagger是用于生成RESTful Web服务的可视化表示的工具，规范和完整框架实现。它使文档能够以与服务器相同的速度更新。当通过Swagger正确定义时，消费者可以使用最少量的实现逻辑来理解远程服务并与其进行交互。因此，Swagger消除了调用服务时的猜测。


### [4、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#4springboot-的核心注解是哪个它主要由哪几个注解组成的)  


启动类上面的注解是@SpringBootApplication，它也是 SpringBoot 的核心注解 主要组合包含了以下 3 个注解：

@SpringBootConfiguration：组合了 [@Configuration ](/Configuration ) 注解，实现配置文件的功能。

@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能： [@SpringBootApplication(exclude ](/SpringBootApplication(exclude ) = { DataSourceAutoConfiguration.class })。

@ComponentScan：Spring组件扫描。


### [5、什么是 YAML？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#5什么是-yaml)  


YAML 是一种人类可读的数据序列化语言。它通常用于配置文件。与属性文件相比，如果我们想要在配置文件中添加复杂的属性，YAML 文件就更加结构化，而且更少混淆。可以看出 YAML 具有分层配置数据。


### [6、如何在自定义端口上运行 SpringBoot应用程序?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#6如何在自定义端口上运行-springboot应用程序)  


在 `application.properties`中指定端口`serverport=8090`。


### [7、当 SpringBoot 应用程序作为 Java 应用程序运行时，后台会发生什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#7当-springboot-应用程序作为-java-应用程序运行时后台会发生什么)  


如果你使用 Eclipse IDE，Eclipse maven 插件确保依赖项或者类文件的改变一经添加，就会被编译并在目标文件中准备好！在这之后，就和其它的 Java 应用程序一样了。

当你启动 java 应用程序的时候，spring boot 自动配置文件就会魔法般的启用了。

当 SpringBoot 应用程序检测到你正在开发一个 web 应用程序的时候，它就会启动 tomcat。


### [8、我们如何连接一个像 MySQL 或者Orcale 一样的外部数据库？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#8我们如何连接一个像-mysql-或者orcale-一样的外部数据库)  


让我们以 MySQL 为例来思考这个问题：

**第一步** - 把 MySQL 连接器的依赖项添加至 pom.xml

**第二步** - 从 pom.xml 中移除 H2 的依赖项

或者至少把它作为测试的范围。

**第三步** - 安装你的 MySQL 数据库

更多的来看看这里 -[https://github.com/in28minutes/jpa-with-hibernate#installing-and-setting-up-MySQL](https://github.com/in28minutes/jpa-with-hibernate#installing-and-setting-up-MySQL)

**第四步** - 配置你的 MySQL 数据库连接

配置 application.properties

```
spring.jpa.hibernate.ddl-auto=none spring.datasource.url=jdbc:MySQL://localhost:3306/todo_example
spring.datasource.username=todouser spring.datasource.password=YOUR_PASSWORD
```

**第五步** - 重新启动，你就准备好了！

就是这么简单！


### [9、SpringBoot、Spring MVC 和 Spring 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#9springbootspring-mvc-和-spring-有什么区别)  


**1、** Spring

Spring最重要的特征是依赖注入。所有 SpringModules 不是依赖注入就是 IOC 控制反转。

当我们恰当的使用 DI 或者是 IOC 的时候，我们可以开发松耦合应用。松耦合应用的单元测试可以很容易的进行。

**2、** Spring MVC

Spring MVC 提供了一种分离式的方法来开发 Web 应用。通过运用像 DispatcherServelet，MoudlAndView 和 ViewResolver 等一些简单的概念，开发 Web 应用将会变的非常简单。

**3、** SpringBoot

Spring 和 SpringMVC 的问题在于需要配置大量的参数。

SpringBoot 通过一个自动配置和启动的项来目解决这个问题。为了更快的构建产品就绪应用程序，SpringBoot 提供了一些非功能性特征。


### [10、SpringBoot常用的starter有哪些?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#10springboot常用的starter有哪些)  


**1、** `spring-boot-starter-web` (嵌入tomcat和web开发需要servlet与jsp支持)

**2、** `spring-boot-starter-data-jpa` (数据库支持)

**3、** `spring-boot-starter-data-Redis` (Redis数据库支持)

**4、** `spring-boot-starter-data-solr` (solr搜索应用框架支持)

**5、** `mybatis-spring-boot-starter` (第三方的mybatis集成starter)


### [11、什么是嵌入式服务器？我们为什么要使用嵌入式服务器呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#11什么是嵌入式服务器我们为什么要使用嵌入式服务器呢)  

### [12、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#12springboot-的核心注解是哪个它主要由哪几个注解组成的)  

### [13、如何在不使用BasePACKAGE过滤器的情况下排除程序包？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#13如何在不使用basepackage过滤器的情况下排除程序包)  

### [14、什么是WebSockets？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#14什么是websockets)  

### [15、SpringBoot 支持哪些日志框架？推荐和默认的日志框架是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#15springboot-支持哪些日志框架推荐和默认的日志框架是哪个)  

### [16、我们如何监视所有 SpringBoot 微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#16我们如何监视所有-springboot-微服务)  

### [17、为什么我们需要 spring-boot-maven-plugin?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#17为什么我们需要-spring-boot-maven-plugin)  

### [18、SpringBoot 常用的 Starter 有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#18springboot-常用的-starter-有哪些)  

### [19、如何集成SpringBoot和ActiveMQ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#19如何集成springboot和activemq)  

### [20、是否可以在Spring boot中更改嵌入式Tomcat服务器的端口?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#20是否可以在spring-boot中更改嵌入式tomcat服务器的端口)  

### [21、如何启用/禁用执行器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#21如何启用/禁用执行器)  

### [22、开启SpringBoot特性有哪几种方式？（创建SpringBoot项目的两种方式）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#22开启springboot特性有哪几种方式创建springboot项目的两种方式)  

### [23、shiro和oauth还有cas他们之间的关系是什么？问下您公司权限是如何设计，还有就是这几个概念的区别。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#23shiro和oauth还有cas他们之间的关系是什么问下您公司权限是如何设计还有就是这几个概念的区别。)  

### [24、创建一个 SpringBoot Project 的最简单的方法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#24创建一个-springboot-project-的最简单的方法是什么)  

### [25、SpringBoot支持什么前端模板，](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#25springboot支持什么前端模板)  

### [26、如何使用SpringBoot实现分页和排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#26如何使用springboot实现分页和排序)  

### [27、SpringBoot中的监视器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#27springboot中的监视器是什么)  

### [28、什么是 JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#28什么是-javaconfig)  

### [29、SpringBoot 中的监视器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#29springboot-中的监视器是什么)  

### [30、SpringBoot 有哪几种读取配置的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#30springboot-有哪几种读取配置的方式)  

### [31、什么是JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot中级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#31什么是javaconfig)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
