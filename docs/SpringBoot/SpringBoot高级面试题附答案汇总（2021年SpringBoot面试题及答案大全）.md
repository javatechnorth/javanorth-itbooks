# SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）

SpringBoot面试题及答案【最新版】SpringBoot高级面试题大全(2021版)，发现网上很多SpringBoot面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringBoot面试题大全，SpringBoot面试题大汇总，有大量经典的SpringBoot面试题以及答案，包含SpringBoot语言常见面试题、SpringBoot工程师高级面试题及一些大厂SpringBoot开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringBoot面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringBoot面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、使用 SpringBoot 启动连接到内存数据库 H2 的 JPA 应用程序需要哪些依赖项？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#1使用-springboot-启动连接到内存数据库-h2-的-jpa-应用程序需要哪些依赖项)  


在 SpringBoot 项目中，当你确保下面的依赖项都在类路里面的时候，你可以加载 H2 控制台。

web 启动器

h2

jpa 数据启动器

**其它的依赖项在下面：**

需要注意的一些地方：

一个内部数据内存只在应用程序执行期间存在。这是学习框架的有效方式。

这不是你希望的真是世界应用程序的方式。

在问题“如何连接一个外部数据库？”中，我们解释了如何连接一个你所选择的数据库。


### [2、SpringBoot 中的 starter 到底是什么 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#2springboot-中的-starter-到底是什么-)  


首先，这个 Starter 并非什么新的技术点，基本上还是基于 Spring 已有功能来实现的。首先它提供了一个自动化配置类，一般命名为 `XXXAutoConfiguration` ，在这个配置类中通过条件注解来决定一个配置是否生效（条件注解就是 Spring 中原本就有的），然后它还会提供一系列的默认配置，也允许开发者根据实际情况自定义相关配置，然后通过类型安全的属性(spring、factories)注入将这些配置属性注入进来，新注入的属性会代替掉默认属性。正因为如此，很多第三方框架，我们只需要引入依赖就可以直接使用了。当然，开发者也可以自定义 Starter


### [3、SpringBoot 可以兼容老 Spring 项目吗，如何做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#3springboot-可以兼容老-spring-项目吗如何做)  


可以兼容，使用 [@ImportResource ](/ImportResource ) 注解导入老 Spring 项目配置文件。


### [4、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#4springboot-的核心配置文件有哪几个它们的区别是什么)  


SpringBoot 的核心配置文件是 application 和 bootstrap 配置文件。

application 配置文件这个容易理解，主要用于 SpringBoot 项目的自动化配置。

bootstrap 配置文件有以下几个应用场景。

使用 Spring Cloud Config 配置中心时，这时需要在 bootstrap 配置文件中添加连接到配置中心的配置属性来加载外部配置中心的配置信息； 一些固定的不能被覆盖的属性；一些加密/解密的场景


### [5、spring boot 核心配置文件是什么？bootstrap.properties 和 application.properties 有何区别 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#5spring-boot-核心配置文件是什么bootstrapproperties-和-applicationproperties-有何区别-)  


单纯做 SpringBoot 开发，可能不太容易遇到 bootstrap.properties 配置文件，但是在结合 Spring Cloud 时，这个配置就会经常遇到了，特别是在需要加载一些远程配置文件的时侯。


### [6、如何使用 SpringBoot 实现分页和排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#6如何使用-springboot-实现分页和排序)  


使用 SpringBoot 实现分页非常简单。使用 Spring Data-JPA 可以实现将可分页的传递给存储库方法。


### [7、如何集成SpringBoot和ActiveMQ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#7如何集成springboot和activemq)  


对于集成SpringBoot和ActiveMQ，我们使用spring-boot-starter-activemq 依赖关系。 它只需要很少的配置，并且不需要样板代码。


### [8、如何在 SpringBoot 启动的时候运行一些特定的代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#8如何在-springboot-启动的时候运行一些特定的代码)  


可以实现接口 ApplicationRunner 或者 CommandLineRunner，这两个接口实现方式一样，它们都只提供了一个 run 方法，实现上述接口的类加入IOC容器即可生效。


### [9、SpringBoot 自动配置原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#9springboot-自动配置原理是什么)  


注解 @EnableAutoConfiguration, @Configuration, [@ConditionalOnClass ](/ConditionalOnClass ) 就是自动配置的核心，

@EnableAutoConfiguration 给容器导入META-INF/spring.factories 里定义的自动配置类。

筛选有效的自动配置类。

每一个自动配置类结合对应的 xxxProperties.java 读取配置文件进行自动配置功能


### [10、SpringBoot事物的使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#10springboot事物的使用)  


SpringBoot的事物很简单，首先使用注解EnableTransactionManagement开启事物之后，然后在Service方法上添加注解Transactional便可。


### [11、SpringBoot 2、X 有什么新特性？与 1、X 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#11springboot-2x-有什么新特性与-1x-有什么区别)  

### [12、如何重新加载SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#12如何重新加载springboot上的更改而无需重新启动服务器)  

### [13、SpringBoot 实现热部署有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#13springboot-实现热部署有哪几种方式)  

### [14、微服务同时调用多个接口，怎么支持事务的啊？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#14微服务同时调用多个接口怎么支持事务的啊)  

### [15、什么是Spring Actuator？它有什么优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#15什么是spring-actuator它有什么优势)  

### [16、创建一个 SpringBoot Project 的最简单的方法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#16创建一个-springboot-project-的最简单的方法是什么)  

### [17、Spring Initializr 是创建 SpringBoot Projects 的唯一方法吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#17spring-initializr-是创建-springboot-projects-的唯一方法吗)  

### [18、什么是starter?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#18什么是starter)  

### [19、如何使用 SpringBoot 自动重装我的应用程序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#19如何使用-springboot-自动重装我的应用程序)  

### [20、SpringBoot 打成的 jar 和普通的 jar 有什么区别 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#20springboot-打成的-jar-和普通的-jar-有什么区别-)  

### [21、如何重新加载 SpringBoot 上的更改，而无需重新启动服务器？SpringBoot项目如何热部署？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#21如何重新加载-springboot-上的更改而无需重新启动服务器springboot项目如何热部署)  

### [22、什么是 Spring Data ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#22什么是-spring-data-)  

### [23、如何实现 SpringBoot应用程序的安全性?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#23如何实现-springboot应用程序的安全性)  

### [24、如何集成SpringBoot和ActiveMQ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#24如何集成springboot和activemq)  

### [25、SpringBoot 有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#25springboot-有哪些优点)  

### [26、如何在 SpringBoot 中禁用 Actuator 端点安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#26如何在-springboot-中禁用-actuator-端点安全性)  

### [27、你如何理解 SpringBoot 配置加载顺序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#27你如何理解-springboot-配置加载顺序)  

### [28、SpringBoot默认支持的日志框架有哪些？可以进行哪些设置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#28springboot默认支持的日志框架有哪些可以进行哪些设置)  

### [29、如何在自定义端口上运行SpringBoot应用程序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#29如何在自定义端口上运行springboot应用程序)  

### [30、如何禁用特定的自动配置类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#30如何禁用特定的自动配置类)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
