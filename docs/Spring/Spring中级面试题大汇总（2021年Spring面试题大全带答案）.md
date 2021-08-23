# Spring中级面试题大汇总（2021年Spring面试题大全带答案）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如果在拦截请求中，我想拦截get方式提交的方法,怎么配置](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#1如果在拦截请求中我想拦截get方式提交的方法,怎么配置)  




可以在@RequestMapping注解里面加上method=RequestMethod.GET。


### [2、什么是Spring MVC框架的控制器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#2什么是spring-mvc框架的控制器)  


控制器提供一个访问应用程序的行为，此行为通常通过服务接口实现。控制器解析用户输入并将其转换为一个由视图呈现给用户的模型。Spring用一个非常抽象的方式实现了一个控制层，允许用户创建多种用途的控制器。


### [3、SpringBoot运行项目的几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#3springboot运行项目的几种方式)  


打包用命令或者放到容器中运行

**1、** 打成jar包，使用java -jar xxx.jar运行

**2、** 打成war包，放到tomcat里面运行

直接用maven插件运行   maven spring-boot：run

直接执行main方法运行


### [4、服务降级底层是如何实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#4服务降级底层是如何实现的)  


Hystrix实现服务降级的功能是通过重写HystrixCommand中的getFallback()方法，当Hystrix的run方法或construct执行发生错误时转而执行getFallback()方法。


### [5、SpringBoot 有哪几种读取配置的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#5springboot-有哪几种读取配置的方式)  


- `@PropertySource`
- `@Value`
- `@Environment`
- `@ConfigurationPropertie`


### [6、@LoadBalanced注解的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#6@loadbalanced注解的作用)  


开启客户端负载均衡。


### [7、SpringBoot 中的监视器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#7springboot-中的监视器是什么)  


Spring boot actuator 是 spring 启动框架中的重要功能之一。Spring boot 监视器可帮助您访问生产环境中正在运行的应用程序的当前状态。有几个指标必须在生产环境中进行检查和监控。即使一些外部应用程序可能正在使用这些服务来向相关人员触发警报消息。监视器模块公开了一组可直接作为 HTTP URL 访问的REST 端点来检查状态。


### [8、有哪些不同类型的IOC（依赖注入）方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#8有哪些不同类型的ioc依赖注入方式)  


**1、** 构造器依赖注入：构造器依赖注入通过容器触发一个类的构造器来实现的，该类有一系列参数，每个参数代表一个对其他类的依赖。

**2、** Setter方法注入：Setter方法注入是容器通过调用无参构造器或无参static工厂 方法实例化bean之后，调用该bean的setter方法，即实现了基于setter的依赖注入。


### [9、请描述Spring MVC的工作流程？描述一下 DispatcherServlet 的工作流程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#9请描述spring-mvc的工作流程描述一下-dispatcherservlet-的工作流程)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/042/38/80_1.png#alt=80%5C_1.png)

**1、** 用户发送请求至前端控制器DispatcherServlet；

**2、** DispatcherServlet收到请求后，调用HandlerMapping处理器映射器，请求获取Handle；

**3、** 处理器映射器根据请求url找到具体的处理器，生成处理器对象及处理器拦截器(如果有则生成)一并返回给DispatcherServlet；

**4、** DispatcherServlet 调用 HandlerAdapter处理器适配器；

**5、** HandlerAdapter 经过适配调用 具体处理器(Handler，也叫后端控制器)；

**6、** Handler执行完成返回ModelAndView；

**7、** HandlerAdapter将Handler执行结果ModelAndView返回给DispatcherServlet；

**8、** DispatcherServlet将ModelAndView传给ViewResolver视图解析器进行解析；

**9、** ViewResolver解析后返回具体View；

**10、** DispatcherServlet对View进行渲染视图（即将模型数据填充至视图中）

**11、** DispatcherServlet响应用户。


### [10、如何重新加载SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#10如何重新加载springboot上的更改而无需重新启动服务器)  


这可以使用DEV工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式tomcat将重新启动。

SpringBoot有一个开发工具（DevTools）模块，它有助于提高开发人员的生产力。Java开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务器。

开发人员可以重新加载SpringBoot上的更改，而无需重新启动服务器。这将消除每次手动部署更改的需要。SpringBoot在它的第一个版本时没有这个功能。

这是开发人员最需要的功能。DevTools模块完全满足开发人员的需求。该模块将在生产环境中被禁用。它还提供H2数据库控制台以更好地测试应用程序。

org.springframework.boot

spring-boot-devtools

true


### [11、RequestMapping 和 GetMapping 的不同之处在哪里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#11requestmapping-和-getmapping-的不同之处在哪里)  

### [12、eureka和zookeeper都可以提供服务注册与发现的功能，请说说两个的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#12eureka和zookeeper都可以提供服务注册与发现的功能请说说两个的区别)  

### [13、你更倾向用那种事务管理类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#13你更倾向用那种事务管理类型)  

### [14、微服务架构的优缺点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#14微服务架构的优缺点是什么)  

### [15、你能否举一个以 ReadOnly 为事务管理的例子？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#15你能否举一个以-readonly-为事务管理的例子)  

### [16、Eureka如何 保证AP](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#16eureka如何-保证ap)  

### [17、Ribbon是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#17ribbon是什么)  

### [18、eureka和zookeeper都可以提供服务注册与发现的功能，请说说两个的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#18eureka和zookeeper都可以提供服务注册与发现的功能请说说两个的区别)  

### [19、Spring Framework 有哪些不同的功能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#19spring-framework-有哪些不同的功能)  

### [20、什么是Swagger？你用SpringBoot实现了它吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#20什么是swagger你用springboot实现了它吗)  

### [21、什么是 YAML？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#21什么是-yaml)  

### [22、Spring Cloud 实现服务注册和发现的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#22spring-cloud-实现服务注册和发现的原理是什么)  

### [23、什么是SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#23什么是springboot)  

### [24、使用Spring框架的好处是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#24使用spring框架的好处是什么)  

### [25、如何在SpringBoot中禁用Actuator端点安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#25如何在springboot中禁用actuator端点安全性)  

### [26、springcloud核⼼组件及其作⽤，以及springcloud⼯作原理：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#26springcloud核⼼组件及其作⽤以及springcloud⼯作原理：)  

### [27、SpringBoot 可以兼容老 Spring 项目吗，如何做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#27springboot-可以兼容老-spring-项目吗如何做)  

### [28、什么是Apache Kafka？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#28什么是apache-kafka)  

### [29、你可以在Spring中注入一个null 和一个空字符串吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#29你可以在spring中注入一个null-和一个空字符串吗)  

### [30、Spring Cloud Bus](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大汇总（2021年Spring面试题大全带答案）.md#30spring-cloud-bus)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
