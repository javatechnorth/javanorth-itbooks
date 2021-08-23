# Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、SpringBoot 自动配置原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#1springboot-自动配置原理是什么)  


注解 @EnableAutoConfiguration, @Configuration, [@ConditionalOnClass ](/ConditionalOnClass ) 就是自动配置的核心，首先它得是一个配置文件，其次根据类路径下是否有这个类去自动配置。


### [2、ApplicationContext通常的实现是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#2applicationcontext通常的实现是什么)  


**1、** FileSystemXmlApplicationContext ：此容器从一个XML文件中加载beans的定义，XML Bean 配置文件的全路径名必须提供给它的构造函数。

**2、** ClassPathXmlApplicationContext：此容器也从一个XML文件中加载beans的定义，这里，你需要正确设置classpath因为这个容器将在classpath里找bean配置。

**3、** WebXmlApplicationContext：此容器加载一个XML文件，此文件定义了一个WEB应用的所有bean。


### [3、SpringBoot中的监视器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#3springboot中的监视器是什么)  


Spring boot actuator是spring启动框架中的重要功能之一。Spring boot监视器可帮助您访问生产环境中正在运行的应用程序的当前状态。有几个指标必须在生产环境中进行检查和监控。即使一些外部应用程序可能正在使用这些服务来向相关人员触发警报消息。监视器模块公开了一组可直接作为HTTP URL访问的REST端点来检查状态。


### [4、shiro和oauth还有cas他们之间的关系是什么？问下您公司权限是如何设计，还有就是这几个概念的区别。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#4shiro和oauth还有cas他们之间的关系是什么问下您公司权限是如何设计还有就是这几个概念的区别。)  


cas和oauth是一个解决单点登录的组件，shiro主要是负责权限安全方面的工作，所以功能点不一致。但往往需要单点登陆和权限控制一起来使用，所以就有 cas+shiro或者oauth+shiro这样的组合。

token一般是客户端登录后服务端生成的令牌，每次访问服务端会进行校验，一般保存到内存即可，也可以放到其他介质；Redis可以做Session共享，如果前端web服务器有几台负载，但是需要保持用户登录的状态，这场景使用比较常见。

我们公司使用oauth+shiro这样的方式来做后台权限的管理，oauth负责多后台统一登录认证，shiro负责给登录用户赋予不同的访问权限。


### [5、AOP 有哪些实现方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#5aop-有哪些实现方式)  


**实现 AOP 的技术，主要分为两大类：**

**静态代理**

指使用 AOP 框架提供的命令进行编译，从而在编译阶段就可生成 AOP 代理类，因此也称为编译时增强；

编译时编织（特殊编译器实现）

类加载时编织（特殊的类加载器实现）。

**动态代理**

在运行时在内存中“临时”生成 AOP 动态代理类，因此也被称为运行时增强。

**JDK 动态代理**

**CGLIB**


### [6、你如何理解 SpringBoot 配置加载顺序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#6你如何理解-springboot-配置加载顺序)  


在 SpringBoot 里面，可以使用以下几种方式来加载配置。

**1、** properties文件；

**2、** YAML文件；

**3、** 系统环境变量；

**4、** 命令行参数；


### [7、如何在不使用BasePACKAGE过滤器的情况下排除程序包？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#7如何在不使用basepackage过滤器的情况下排除程序包)  


过滤程序包的方法不尽相同。但是弹簧启动提供了一个更复杂的选项，可以在不接触组件扫描的情况下实现这一点。在使用注释@ SpringBootApplication时，可以使用排除属性。请参阅下面的代码片段：

@SpringBootApplication(exclude= {Employee.class})

public class FooAppConfiguration {}


### [8、Ribbon和Feign的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#8ribbon和feign的区别)  


**1、** Ribbon都是调用其他服务的，但方式不同。

**2、** 启动类注解不同，Ribbon是[@RibbonClient ](/RibbonClient ) feign的是[@EnableFeignClients ](/EnableFeignClients )

**3、** 服务指定的位置不同，Ribbon是在@RibbonClient注解上声明，Feign则是在定义抽象方法的接口中使用@FeignClient声明。

**4、** 调用方式不同，Ribbon需要自己构建http请求，模拟http请求然后使用RestTemplate发送给其他服务，步骤相当繁琐。Feign需要将调用的方法定义成抽象方法即可。


### [9、创建一个 SpringBoot Project 的最简单的方法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#9创建一个-springboot-project-的最简单的方法是什么)  


Spring Initializr是启动 SpringBoot Projects 的一个很好的工具。

**我们需要做一下几步：**

**1、** 登录 Spring Initializr，按照以下方式进行选择：

**2、** 选择 com.in28minutes.SpringBoot 为组

**3、** 选择 studet-services 为组件

**4、** 选择下面的依赖项

Web

Actuator

DevTools

**5、** 点击生 GenerateProject

**6、** 将项目导入 Eclipse。文件 - 导入 - 现有的 Maven 项目


### [10、SpringBoot 配置文件的加载顺序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#10springboot-配置文件的加载顺序)  


由jar包外向jar包内进行寻找;

优先加载带profile

jar包外部的application-{profile}.properties或application.yml(带spring.profile配置文件

jar包内部的application-{profile}.properties或application.yml(带spring.profile配置文件

再来加载不带profile

jar包外部的application.properties或application.yml(不带spring.profile配置文件

jar包内部的application.properties或application.yml(不带spring.profile配置文件


### [11、[@RequestMapping ](/RequestMapping ) 注解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#11[@requestmapping-]/requestmapping--注解)  

### [12、Spring Cloud Consul](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#12spring-cloud-consul)  

### [13、如何给静态变量赋值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#13如何给静态变量赋值)  

### [14、如何集成SpringBoot和ActiveMQ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#14如何集成springboot和activemq)  

### [15、如何实现 SpringBoot 应用程序的安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#15如何实现-springboot-应用程序的安全性)  

### [16、什么是微服务架构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#16什么是微服务架构)  

### [17、@Controller注解的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#17@controller注解的作用)  

### [18、当 SpringBoot 应用程序作为 Java 应用程序运行时，后台会发生什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#18当-springboot-应用程序作为-java-应用程序运行时后台会发生什么)  

### [19、什么是 spring 的内部 bean？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#19什么是-spring-的内部-bean)  

### [20、Spring MVC的优点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#20spring-mvc的优点)  

### [21、什么是Netflix Feign？它的优点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#21什么是netflix-feign它的优点是什么)  

### [22、创建一个 SpringBoot Project 的最简单的方法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#22创建一个-springboot-project-的最简单的方法是什么)  

### [23、如何重新加载 SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#23如何重新加载-springboot上的更改而无需重新启动服务器)  

### [24、SpringCloud限流：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#24springcloud限流：)  

### [25、自动装配有什么局限？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#25自动装配有什么局限)  

### [26、什么是 AOP切点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#26什么是-aop切点)  

### [27、SpringBoot 2.X 有什么新特性？与 1.X 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#27springboot-2x-有什么新特性与-1x-有什么区别)  

### [28、列举 spring 支持的事务管理类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#28列举-spring-支持的事务管理类型)  

### [29、[@RequestMapping ](/RequestMapping ) 注解有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#29[@requestmapping-]/requestmapping--注解有什么用)  

### [30、什么是编织（Weaving）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#30什么是编织weaving)  

### [31、如何在SpringBoot中禁用Actuator端点安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题汇总及答案（2021年Spring面试题及答案大全）.md#31如何在springboot中禁用actuator端点安全性)  





