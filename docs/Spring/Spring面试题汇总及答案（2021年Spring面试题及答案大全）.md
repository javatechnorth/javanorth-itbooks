# Spring面试题汇总及答案（2021年Spring面试题及答案大全）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何在 SpringBoot 中添加通用的 JS 代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#1如何在-springboot-中添加通用的-js-代码)  


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


### [2、什么是Spring Cloud？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#2什么是spring-cloud)  


spring cloud 是一系列框架的有序集合。它利用 spring boot 的开发便利性巧妙地简化了分布式系统基础设施的开发，如服务发现注册、配置中心、消息总线、负载均衡、断路器、数据监控等，都可以用 spring boot 的开发风格做到一键启动和部署。


### [3、Spring Cloud OpenFeign](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#3spring-cloud-openfeign)  


基于Ribbon和Hystrix的声明式服务调用组件，可以动态创建基于Spring MVC注解的接口实现用于服务调用，在Spring Cloud 2.0中已经取代Feign成为了一等公民。

Spring Cloud的版本关系

Spring Cloud是一个由许多子项目组成的综合项目，各子项目有不同的发布节奏。为了管理Spring Cloud与各子项目的版本依赖关系，发布了一个清单，其中包括了某个Spring Cloud版本对应的子项目版本。

为了避免Spring Cloud版本号与子项目版本号混淆，Spring Cloud版本采用了名称而非版本号的命名，这些版本的名字采用了伦敦地铁站的名字，根据字母表的顺序来对应版本时间顺序，例如Angel是第一个版本，Brixton是第二个版本。

当Spring Cloud的发布内容积累到临界点或者一个重大BUG被解决后，会发布一个"service releases"版本，简称SRX版本，比如Greenwich.SR2就是Spring Cloud发布的Greenwich版本的第2个SRX版本。目前Spring Cloud的最新版本是Hoxton。


### [4、SpringBoot Starter的工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#4springboot-starter的工作原理)  


`我个人理解SpringBoot就是由各种Starter组合起来的，我们自己也可以开发Starter`

在sprinBoot启动时由@SpringBootApplication注解会自动去maven中读取每个starter中的spring、factories文件,该文件里配置了所有需要被创建spring容器中的bean，并且进行自动配置把bean注入SpringContext中 //（SpringContext是Spring的配置文件）


### [5、Spring Cloud和SpringBoot版本对应关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#5spring-cloud和springboot版本对应关系)  

| Spring Cloud Version | SpringBoot Version |
| --- | --- |
| Hoxton | 2.2.x |
| Greenwich | 2.1.x |
| Finchley | 2.0.x |
| Edgware | 1.5.x |
| Dalston | 1.5.x |



### [6、如何不通过任何配置来选择 Hibernate 作为 JPA 的默认实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#6如何不通过任何配置来选择-hibernate-作为-jpa-的默认实现)  


因为 SpringBoot 是自动配置的。

**下面是我们添加的依赖项:**

spring-boot-stater-data-jpa 对于 Hibernate 和 JPA 有过渡依赖性。

当 SpringBoot 在类路径中检测到 Hibernate 中，将会自动配置它为默认的 JPA 实现。


### [7、什么是SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#7什么是springboot)  


用来简化spring应用的初始搭建以及开发过程，使用特定的方式来进行配置（`properties`或`yml`文件）创建独立的spring引用程序 main方法运行，嵌入的Tomcat 无需部署war文件，简化maven配置，自动配置spring添加对应功能starter自动化配置


### [8、Spring对DAO的支持](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#8spring对dao的支持)  


Spring对数据访问对象（DAO）的支持旨在简化它和数据访问技术如JDBC，Hibernate or JDO 结合使用。这使我们可以方便切换持久层。编码时也不用担心会捕获每种技术特有的异常。


### [9、SpringBoot 2.X 有什么新特性？与 1.X 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#9springboot-2x-有什么新特性与-1x-有什么区别)  


配置变更

JDK 版本升级

第三方类库升级

响应式 Spring 编程支持

HTTP/2 支持

配置属性绑定

更多改进与加强…


### [10、谈一下领域驱动设计](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#10谈一下领域驱动设计)  


主要关注核心领域逻辑。基于领域的模型检测复杂设计。这涉及与公司层面领域方面的专家定期合作，以解决与领域相关的问题并改进应用程序的模型。在回答这个微服务面试问题时，您还需要提及DDD的核心基础知识。他们是：

**1、** DDD主要关注领域逻辑和领域本身。

**2、** 复杂的设计完全基于领域的模型。

**3、** 为了改进模型的设计并解决任何新出现的问题，DDD不断与公司领域方面的专家合作。


### [11、可以通过多少种方式完成依赖注入？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#11可以通过多少种方式完成依赖注入)  

### [12、Nginx与Ribbon的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#12nginx与ribbon的区别)  

### [13、我们可以用微服务创建状态机吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#13我们可以用微服务创建状态机吗)  

### [14、过渡到微服务时的常见错误](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#14过渡到微服务时的常见错误)  

### [15、JdbcTemplate](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#15jdbctemplate)  

### [16、SpringBoot 中如何实现定时任务 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#16springboot-中如何实现定时任务-)  

### [17、您使用了哪些starter maven依赖项？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#17您使用了哪些starter-maven依赖项)  

### [18、服务雪崩效应产生的原因](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#18服务雪崩效应产生的原因)  

### [19、spring JDBC API 中存在哪些类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#19spring-jdbc-api-中存在哪些类)  

### [20、Spring 应用程序有哪些不同组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#20spring-应用程序有哪些不同组件)  

### [21、微服务的端到端测试意味着什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#21微服务的端到端测试意味着什么)  

### [22、[@Autowired ](/Autowired ) 注解有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#22[@autowired-]/autowired--注解有什么用)  

### [23、SpringBoot 实现热部署有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#23springboot-实现热部署有哪几种方式)  

### [24、什么是 Spring 配置文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#24什么是-spring-配置文件)  

### [25、服务网关的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#25服务网关的作用)  

### [26、什么是Hystrix断路器？我们需要它吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#26什么是hystrix断路器我们需要它吗)  

### [27、Spring Cloud Zookeeper](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#27spring-cloud-zookeeper)  

### [28、Mock或Stub有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#28mock或stub有什么区别)  

### [29、SpringBoot 配置加载顺序?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#29springboot-配置加载顺序)  

### [30、SpringBoot多数据源事务如何管理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#30springboot多数据源事务如何管理)  

### [31、什么是持续监测？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题汇总及答案（2021年Spring面试题及答案大全）.md#31什么是持续监测)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
