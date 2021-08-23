# Spring面试题大汇总（2021年Spring面试题大全带答案）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、微服务的缺点：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#1微服务的缺点：)  


**1、** 复杂度⾼：服务调⽤要考虑被调⽤⽅故障、过载、消息丢失等各种异常情况，代码逻辑更加复杂；对于微服务间的事务性操作，因为不同的微服务采⽤了不同的数据库，将⽆法利⽤数据库本身的事务机制保证⼀致性，需要引⼊⼆阶段提交等技术。

**2、** 运维复杂：系统由多个独⽴运⾏的微服务构成，需要⼀个设计良好的监控系统对各个微服务的运⾏状态进⾏监控。运维⼈员需要对系统有细致的了解才对够更好的运维系统。

**3、** 通信延迟：微服务之间调⽤会有时间损耗，造成通信延迟。


### [2、什么是 Spring Framework？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#2什么是-spring-framework)  


**1、** Spring 是一个开源应用框架，旨在降低应用程序开发的复杂度。

**2、** 它是轻量级、松散耦合的。

**3、** 它具有分层体系结构，允许用户选择组件，同时还为 J2EE 应用程序开发提供了一个有凝聚力的框架。

**4、** 它可以集成其他框架，如 Structs、Hibernate、EJB 等，所以又称为框架的框架。


### [3、各服务之间通信，对Restful和Rpc这2种方式如何做选择？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#3各服务之间通信对restful和rpc这2种方式如何做选择)  


在传统的SOA治理中，使用rpc的居多；Spring Cloud默认使用restful进行服务之间的通讯。rpc通讯效率会比restful要高一些，但是对于大多数公司来讲，这点效率影响甚微。我建议使用restful这种方式，易于在不同语言实现的服务之间通讯。


### [4、如何给Spring 容器提供配置元数据?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#4如何给spring-容器提供配置元数据)  


这里有三种重要的方法给Spring 容器提供配置元数据。

**1、** XML配置文件。

**2、** 基于注解的配置。

**3、** 基于java的配置。


### [5、哪些是重要的bean生命周期方法？ 你能重载它们吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#5哪些是重要的bean生命周期方法-你能重载它们吗)  


有两个重要的bean 生命周期方法，第一个是setup ， 它是在容器加载bean的时候被调用。第二个方法是 teardown 它是在容器卸载类的时候被调用。

The bean 标签有两个重要的属性（init-method和destroy-method）。用它们你可以自己定制初始化和注销方法。它们也有相应的注解（@PostConstruct和@PreDestroy）。


### [6、如何在 SpringBoot 中禁用 Actuator 端点安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#6如何在-springboot-中禁用-actuator-端点安全性)  


默认情况下，所有敏感的 HTTP 端点都是安全的，只有具有 ACTUATOR 角色的用户才能访问它们。安全性是使用标准的 HttpServletRequest.isUserInRole 方法实施的。我们可以使用来禁用安全性。只有在执行机构端点在防火墙后访问时，才建议禁用安全性。


### [7、一个Spring的应用看起来象什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#7一个spring的应用看起来象什么)  


**1、** 一个定义了一些功能的接口。

**2、** 这实现包括属性，它的Setter ， getter 方法和函数等。

**3、** Spring AOP。

**4、** Spring 的XML 配置文件。

**5、** 使用以上功能的客户端程序。


### [8、第⼆层缓存：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#8第⼆层缓存：)  


readWriteCacheMap，本质上是Guava缓存：此处存放的是最终的缓存， 当服务下线，过期，注册，状态变更，都会来清除这个缓存⾥⾯的数据。 然后通过CacheLoader进⾏缓存加载，在进⾏readWriteCacheMap.get(key)的时候，⾸先看这个缓存⾥⾯有没有该数据，如果没有则通过CacheLoader的load⽅法去加载，加载成功之后将数据放⼊缓存，同时返回数据。 readWriteCacheMap 缓存过期时间，默认为 180 秒 。

#
### [9、自动装配有哪些局限性 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#9自动装配有哪些局限性-)  


自动装配的局限性是：

**1、** 重写：你仍需用 和  配置来定义依赖，意味着总要重写自动装配。

**2、** 基本数据类型：你不能自动装配简单的属性，如基本数据类型，String字符串，和类。

**3、** 模糊特性：自动装配不如显式装配精确，如果有可能，建议使用显式装配。


### [10、Spring MVC与Struts2区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#10spring-mvc与struts2区别)  


**相同点**

都是基于mvc的表现层框架，都用于web项目的开发。

**不同点**

**1、** 前端控制器不一样。Spring MVC的前端控制器是servlet：DispatcherServlet。struts2的前端控制器是filter：StrutsPreparedAndExcutorFilter。

**2、** 请求参数的接收方式不一样。Spring MVC是使用方法的形参接收请求的参数，基于方法的开发，线程安全，可以设计为单例或者多例的开发，推荐使用单例模式的开发（执行效率更高），默认就是单例开发模式。struts2是通过类的成员变量接收请求的参数，是基于类的开发，线程不安全，只能设计为多例的开发。

**3、** Struts采用值栈存储请求和响应的数据，通过OGNL存取数据，Spring MVC通过参数解析器是将request请求内容解析，并给方法形参赋值，将数据和视图封装成ModelAndView对象，最后又将ModelAndView中的模型数据通过reques域传输到页面。Jsp视图解析器默认使用jstl。

**4、** 与spring整合不一样。Spring MVC是spring框架的一部分，不需要整合。在企业项目中，Spring MVC使用更多一些。


### [11、[@RequestMapping ](/RequestMapping ) 注解有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#11[@requestmapping-]/requestmapping--注解有什么用)  

### [12、SpringBoot多数据源拆分的思路](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#12springboot多数据源拆分的思路)  

### [13、SpringBoot 的配置文件有哪几种格式？它们有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#13springboot-的配置文件有哪几种格式它们有什么区别)  

### [14、Spring MVC 框架有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#14spring-mvc-框架有什么用)  

### [15、使用 SpringBoot 开发分布式微服务时，我们面临什么问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#15使用-springboot-开发分布式微服务时我们面临什么问题)  

### [16、您对Distributed Transaction有何了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#16您对distributed-transaction有何了解)  

### [17、什么是feigin？它的优点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#17什么是feigin它的优点是什么)  

### [18、如何设计一套API接口](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#18如何设计一套api接口)  

### [19、SpringBoot的缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#19springboot的缺点)  

### [20、为什么在微服务中需要Reports报告和Dashboards仪表板？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#20为什么在微服务中需要reports报告和dashboards仪表板)  

### [21、解释基于注解的切面实现](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#21解释基于注解的切面实现)  

### [22、为什么要用SpringBoot](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#22为什么要用springboot)  

### [23、SOA和微服务架构之间的主要区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#23soa和微服务架构之间的主要区别是什么)  

### [24、BeanFactory – BeanFactory 实现举例。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#24beanfactory-–-beanfactory-实现举例。)  

### [25、eureka的缺点：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#25eureka的缺点：)  

### [26、在Spring框架中如何更有效地使用JDBC?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#26在spring框架中如何更有效地使用jdbc)  

### [27、[@Qualifier ](/Qualifier ) 注解有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#27[@qualifier-]/qualifier--注解有什么用)  

### [28、SpringBoot集成mybatis的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#28springboot集成mybatis的过程)  

### [29、Spring MVC中函数的返回值是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#29spring-mvc中函数的返回值是什么)  

### [30、SpringBoot 支持哪些日志框架？推荐和默认的日志框架是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大汇总（2021年Spring面试题大全带答案）.md#30springboot-支持哪些日志框架推荐和默认的日志框架是哪个)  





