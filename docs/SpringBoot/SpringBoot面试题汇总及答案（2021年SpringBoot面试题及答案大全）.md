# SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）

SpringBoot面试题及答案【最新版】SpringBoot高级面试题大全(2021版)，发现网上很多SpringBoot面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringBoot面试题大全，SpringBoot面试题大汇总，有大量经典的SpringBoot面试题以及答案，包含SpringBoot语言常见面试题、SpringBoot工程师高级面试题及一些大厂SpringBoot开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringBoot面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringBoot面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何不通过任何配置来选择 Hibernate 作为 JPA 的默认实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#1如何不通过任何配置来选择-hibernate-作为-jpa-的默认实现)  


因为 SpringBoot 是自动配置的。

**下面是我们添加的依赖项:**

spring-boot-stater-data-jpa 对于 Hibernate 和 JPA 有过渡依赖性。

当 SpringBoot 在类路径中检测到 Hibernate 中，将会自动配置它为默认的 JPA 实现。


### [2、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#2springboot-的核心注解是哪个它主要由哪几个注解组成的)  


启动类上面的注解是@SpringBootApplication，它也是 SpringBoot 的核心注解，主要组合包含了以下 3 个注解：

@SpringBootConfiguration：组合了 [@Configuration ](/Configuration ) 注解，实现配置文件的功能。

@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：

[@SpringBootApplication(exclude ](/SpringBootApplication(exclude ) = { DataSourceAutoConfiguration.class })。

@ComponentScan：Spring组件扫描。


### [3、什么是 WebSockets？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#3什么是-websockets)  


WebSocket 是一种计算机通信协议，通过单个 TCP 连接提供全双工通信信道。

**1、** WebSocket 是双向的 -使用 WebSocket 客户端或服务器可以发起消息发送。

**2、** WebSocket 是全双工的 -客户端和服务器通信是相互独立的。

**3、** 单个 TCP 连接 -初始连接使用 HTTP，然后将此连接升级到基于套接字的连接。然后这个单一连接用于所有未来的通信

**4、** Light -与 http 相比，WebSocket 消息数据交换要轻得多。


### [4、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#4运行-springboot-有哪几种方式)  


打包用命令或者放到容器中运行

用 Maven/ Gradle 插件运行

直接执行 main 方法运行


### [5、什么是执行器停机？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#5什么是执行器停机)  


关机是允许应用程序正常关机的端点。默认情况下，此功能不启用。你可以在应用程序属性文件中使用management . endpoint . shut down . enabled = true来启用此选项。但是该方法请谨慎使用。


### [6、我们如何监视所有 SpringBoot 微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#6我们如何监视所有-springboot-微服务)  


SpringBoot 提供监视器端点以监控各个微服务的度量。这些端点对于获取有关应用程序的信息（如它们是否已启动）以及它们的组件（如数据库等）是否正常运行很有帮助。但是，使用监视器的一个主要缺点或困难是，我们必须单独打开应用程序的知识点以了解其状态或健康状况。想象一下涉及 50 个应用程序的微服务，管理员将不得不击中所有 50 个应用程序的执行终端。为了帮助我们处理这种情况，我们将使用位于的开源项目。它建立在 SpringBoot Actuator 之上，它提供了一个 Web UI，使我们能够可视化多个应用程序的度量。


### [7、如何使用SpringBoot实现分页和排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#7如何使用springboot实现分页和排序)  


使用SpringBoot实现分页非常简单。使用Spring Data-JPA可以实现将可分页的

传递给存储库方法。


### [8、什么是 JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#8什么是-javaconfig)  


**1、** `面向对象的配置`。由于配置被定义为 JavaConfig 中的类，因此用户可以充分利用 Java 中的面向对象功能。一个配置类可以继承另一个，重写它的[@Bean ](/Bean ) 方法等。

**2、** `减少或消除 XML 配置`。基于依赖注入原则的外化配置的好处已被证明。但是，许多开发人员不希望在 XML 和 Java 之间来回切换。JavaConfig 为开发人员提供了一种纯 Java 方法来配置与 XML 配置概念相似的 Spring 容器。从技术角度来讲，只使用 JavaConfig 配置类来配置容器是可行的，但实际上很多人认为将JavaConfig 与 XML 混合匹配是理想的。

**3、** `类型安全和重构友好`。JavaConfig 提供了一种类型安全的方法来配置 Spring容器。由于 Java 5.0 对泛型的支持，现在可以按类型而不是按名称检索 bean，不需要任何强制转换或基于字符串的查找。


### [9、如何实现SpringBoot应用程序的安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#9如何实现springboot应用程序的安全性)  


为了实现SpringBoot的安全性，我们使用 spring-boot-starter-security依赖项，并且必须添加安全配置。它只需要很少的代码。配置类将必须扩展WebSecurityConfigurerAdapter并覆盖其方法。


### [10、比较一下 Spring Security 和 Shiro 各自的优缺点 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#10比较一下-spring-security-和-shiro-各自的优缺点-)  


由于 SpringBoot 官方提供了大量的非常方便的开箱即用的 Starter ，包括 Spring Security 的 Starter ，使得在 SpringBoot 中使用 Spring Security 变得更加容易，甚至只需要添加一个依赖就可以保护所有的接口，所以，如果是 SpringBoot 项目，一般选择 Spring Security 。当然这只是一个建议的组合，单纯从技术上来说，无论怎么组合，都是没有问题的。Shiro 和 Spring Security 相比，主要有如下一些特点：

Spring Security 是一个重量级的安全管理框架；Shiro 则是一个轻量级的安全管理框架

Spring Security 概念复杂，配置繁琐；Shiro 概念简单、配置简单

Spring Security 功能强大；Shiro 功能简单


### [11、什么是SpringBoot](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#11什么是springboot)  

### [12、如何使用SpringBoot实现分页和排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#12如何使用springboot实现分页和排序)  

### [13、什么是SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#13什么是springboot)  

### [14、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#14springboot-的核心注解是哪个它主要由哪几个注解组成的)  

### [15、什么是 Swagger？你用 SpringBoot 实现了它吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#15什么是-swagger你用-springboot-实现了它吗)  

### [16、SpringBoot 最大的优势是什么呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#16springboot-最大的优势是什么呢)  

### [17、spring-boot-starter-parent有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#17spring-boot-starter-parent有什么用)  

### [18、如何重新加载SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#18如何重新加载springboot上的更改而无需重新启动服务器)  

### [19、SpringBoot多数据源事务如何管理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#19springboot多数据源事务如何管理)  

### [20、SpringBoot 打成的 jar 和普通的 jar 有什么区别 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#20springboot-打成的-jar-和普通的-jar-有什么区别-)  

### [21、开启 SpringBoot 特性有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#21开启-springboot-特性有哪几种方式)  

### [22、我们如何监视所有 SpringBoot 微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#22我们如何监视所有-springboot-微服务)  

### [23、你如何理解 SpringBoot 中的 Starters？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#23你如何理解-springboot-中的-starters)  

### [24、SpringBoot 中如何解决跨域问题 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#24springboot-中如何解决跨域问题-)  

### [25、怎么设计无状态服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#25怎么设计无状态服务)  

### [26、为什么要用SpringBoot](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#26为什么要用springboot)  

### [27、能否举一个例子来解释更多 Staters 的内容？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#27能否举一个例子来解释更多-staters-的内容)  

### [28、什么是 SpringBoot 启动类注解：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#28什么是-springboot-启动类注解：)  

### [29、什么是Spring Batch？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#29什么是spring-batch)  

### [30、如何使用 SpringBoot 生成一个 WAR 文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#30如何使用-springboot-生成一个-war-文件)  

### [31、bootstrap.yml和application.yml有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#31bootstrapyml和applicationyml有什么区别)  





