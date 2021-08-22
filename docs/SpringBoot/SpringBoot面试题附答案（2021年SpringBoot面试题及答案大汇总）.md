# SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）

SpringBoot面试题及答案【最新版】SpringBoot高级面试题大全(2021版)，发现网上很多SpringBoot面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringBoot面试题大全，SpringBoot面试题大汇总，有大量经典的SpringBoot面试题以及答案，包含SpringBoot语言常见面试题、SpringBoot工程师高级面试题及一些大厂SpringBoot开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringBoot面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringBoot面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、SpringBoot 配置加载顺序?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#1springboot-配置加载顺序)  


**1、** properties文件 2、YAML文件 3、系统环境变量 4、命令行参数


### [2、SpringBoot 自动配置原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#2springboot-自动配置原理是什么)  


注解 @EnableAutoConfiguration, @Configuration, [@ConditionalOnClass ](/ConditionalOnClass ) 就是自动配置的核心，首先它得是一个配置文件，其次根据类路径下是否有这个类去自动配置。


### [3、SpringBoot 支持哪些日志框架？推荐和默认的日志框架是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#3springboot-支持哪些日志框架推荐和默认的日志框架是哪个)  


SpringBoot 支持 Java Util Logging, Log4j2, Lockback 作为日志框架，如果你使用 Starters 启动器，SpringBoot 将使用 Logback 作为默认日志框架.


### [4、SpringBoot 实现热部署有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#4springboot-实现热部署有哪几种方式)  


热部署就是可以不用重新运行SpringBoot项目可以实现操作后台代码自动更新到以运行的项目中

主要有两种方式：

Spring Loaded

Spring-boot-devtools


### [5、为什么我们需要 spring-boot-maven-plugin?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#5为什么我们需要-spring-boot-maven-plugin)  


spring-boot-maven-plugin 提供了一些像 jar 一样打包或者运行应用程序的命令。

spring-boot:run 运行你的 SpringBooty 应用程序。

spring-boot：repackage 重新打包你的 jar 包或者是 war 包使其可执行

spring-boot：start 和 spring-boot：stop 管理 SpringBoot 应用程序的生命周期（也可以说是为了集成测试）。

spring-boot:build-info 生成执行器可以使用的构造信息。


### [6、比较一下 Spring Security 和 Shiro 各自的优缺点 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#6比较一下-spring-security-和-shiro-各自的优缺点-)  


由于 SpringBoot 官方提供了大量的非常方便的开箱即用的 Starter ，包括 Spring Security 的 Starter ，使得在 SpringBoot 中使用 Spring Security 变得更加容易，甚至只需要添加一个依赖就可以保护所有的接口，所以，如果是 SpringBoot 项目，一般选择 Spring Security 。当然这只是一个建议的组合，单纯从技术上来说，无论怎么组合，都是没有问题的。Shiro 和 Spring Security 相比

**主要有如下一些特点：**

**1、** Spring Security 是一个重量级的安全管理框架；Shiro 则是一个轻量级的安全管理框架

**2、** Spring Security 概念复杂，配置繁琐；Shiro 概念简单、配置简单

**3、** Spring Security 功能强大；Shiro 功能简单


### [7、什么是JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#7什么是javaconfig)  


Spring JavaConfig是Spring社区的产品，它提供了配置Spring IoC容器的纯Java方法。因此它有助于避免使用XML配置。使用JavaConfig的优点在于：

**1、** 面向对象的配置。由于配置被定义为JavaConfig中的类，因此用户可以充分利用Java中的面向对象功能。一个配置类可以继承另一个，重写它的@Bean方法等。

**2、** 减少或消除XML配置。基于依赖注入原则的外化配置的好处已被证明。但是，许多开发人员不希望在XML和Java之间来回切换。JavaConfig为开发人员提供了一种纯Java方法来配置与XML配置概念相似的Spring容器。从技术角度来讲，只使用JavaConfig配置类来配置容器是可行的，但实际上很多人认为将JavaConfig与XML混合匹配是理想的。

**3、** 类型安全和重构友好。JavaConfig提供了一种类型安全的方法来配置Spring容器。由于Java 5.0对泛型的支持，现在可以按类型而不是按名称检索bean，不需要任何强制转换或基于字符串的查找。


### [8、SpringBoot 2.X 有什么新特性？与 1.X 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#8springboot-2x-有什么新特性与-1x-有什么区别)  


配置变更

JDK 版本升级

第三方类库升级

响应式 Spring 编程支持

HTTP/2 支持

配置属性绑定

更多改进与加强…


### [9、JPA 和 Hibernate 有哪些区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#9jpa-和-hibernate-有哪些区别)  


简而言之

JPA 是一个规范或者接口

Hibernate 是 JPA 的一个实现

当我们使用 JPA 的时候，我们使用 javax.persistence 包中的注释和接口时，不需要使用 hibernate 的导入包。

我们建议使用 JPA 注释，因为哦我们没有将其绑定到 Hibernate 作为实现。后来（我知道 - 小于百分之一的几率），我们可以使用另一种 JPA 实现。


### [10、YAML 配置的优势在哪里 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#10yaml-配置的优势在哪里-)  


YAML 现在可以算是非常流行的一种配置文件格式了，无论是前端还是后端，都可以见到 YAML 配置。那么 YAML 配置和传统的 properties 配置相比到底有哪些优势呢？

**1、** 配置有序，在一些特殊的场景下，配置有序很关键

**2、** 支持数组，数组中的元素可以是基本数据类型也可以是对象

3、简洁

相比 properties 配置文件，YAML 还有一个缺点，就是不支持 [@PropertySource ](/PropertySource ) 注解导入自定义的 YAML 配置。


### [11、SpringBoot 日志框架：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#11springboot-日志框架：)  

### [12、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#12springboot-的核心配置文件有哪几个它们的区别是什么)  

### [13、开启 SpringBoot 特性有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#13开启-springboot-特性有哪几种方式)  

### [14、什么是嵌入式服务器？我们为什么要使用嵌入式服务器呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#14什么是嵌入式服务器我们为什么要使用嵌入式服务器呢)  

### [15、SpringBoot自动配置的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#15springboot自动配置的原理是什么)  

### [16、SpringBoot 有哪几种读取配置的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#16springboot-有哪几种读取配置的方式)  

### [17、SpringBoot中的监视器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#17springboot中的监视器是什么)  

### [18、可以在SpringBoot application中禁用默认的Web服务器吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#18可以在springboot-application中禁用默认的web服务器吗)  

### [19、什么是 SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#19什么是-springboot)  

### [20、spring boot初始化环境变量流程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#20spring-boot初始化环境变量流程)  

### [21、SpringBoot 提供了哪些核心功能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#21springboot-提供了哪些核心功能)  

### [22、什么是 Spring Profiles？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#22什么是-spring-profiles)  

### [23、SpringBoot 有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#23springboot-有哪些优点)  

### [24、path=”users”, collectionResourceRel=”users” 如何与 Spring Data Rest 一起使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#24path=users,-collectionresourcerel=users-如何与-spring-data-rest-一起使用)  

### [25、什么是 Spring Batch?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#25什么是-spring-batch)  

### [26、如何重新加载SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#26如何重新加载springboot上的更改而无需重新启动服务器)  

### [27、什么是 CSRF 攻击？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#27什么是-csrf-攻击)  

### [28、SpringBoot 自动配置原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#28springboot-自动配置原理)  

### [29、SpringBoot 需要独立的容器运行吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#29springboot-需要独立的容器运行吗)  

### [30、SpringBoot性能如何优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#30springboot性能如何优化)  

### [31、如何使用SpringBoot实现异常处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案（2021年SpringBoot面试题及答案大汇总）.md#31如何使用springboot实现异常处理)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
