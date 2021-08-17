# Spring高级面试题及答案汇总（2021年Spring面试题答案大全）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、是否可以在Spring boot中更改嵌入式Tomcat服务器的端口?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#1是否可以在spring-boot中更改嵌入式tomcat服务器的端口)  


是的，更改端口是可行的。可以使用application.properties文件更改端口。但需要提到“server.port”（即server.port=8081）。确保项目类路径中有application.properties；后续工作将由REST Spring框架接手。如果提到server.port=0，那么它将自动分配任何可用的端口。


### [2、什么是嵌入式服务器？我们为什么要使用嵌入式服务器呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#2什么是嵌入式服务器我们为什么要使用嵌入式服务器呢)  


思考一下在你的虚拟机上部署应用程序需要些什么。

**第一步：**安装 Java

**第二步：**安装 Web 或者是应用程序的服务器（Tomat/Wbesphere/Weblogic 等等）

**第三步：**部署应用程序 war 包

如果我们想简化这些步骤，应该如何做呢？

让我们来思考如何使服务器成为应用程序的一部分？

你只需要一个安装了 Java 的虚拟机，就可以直接在上面部署应用程序了，

这个想法是嵌入式服务器的起源。

当我们创建一个可以部署的应用程序的时候，我们将会把服务器（例如，tomcat）嵌入到可部署的服务器中。

例如，对于一个 SpringBoot 应用程序来说，你可以生成一个包含 Embedded Tomcat 的应用程序 jar。你就可以想运行正常 Java 应用程序一样来运行 web 应用程序了。

嵌入式服务器就是我们的可执行单元包含服务器的二进制文件（例如，tomcat.jar）。


### [3、如何使用 SpringBoot 实现全局异常处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#3如何使用-springboot-实现全局异常处理)  


Spring 提供了一种使用 ControllerAdvice 处理异常的非常有用的方法。 我们通过实现一个 ControlerAdvice 类，来处理控制器类抛出的所有异常。


### [4、SpringBoot 打成的 jar 和普通的 jar 有什么区别 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#4springboot-打成的-jar-和普通的-jar-有什么区别-)  


SpringBoot 项目最终打包成的 jar 是可执行 jar ，这种 jar 可以直接通过 `java -jar xxx、jar` 命令来运行，这种 jar 不可以作为普通的 jar 被其他项目依赖，即使依赖了也无法使用其中的类。

SpringBoot 的 jar 无法被其他项目依赖，主要还是他和普通 jar 的结构不同。普通的 jar 包，解压后直接就是包名，包里就是我们的代码，而 SpringBoot 打包成的可执行 jar 解压后，在 `\BOOT-INF\classes` 目录下才是我们的代码，因此无法被直接引用。如果非要引用，可以在 pom、xml 文件中增加配置，将 SpringBoot 项目打包成两个 jar ，一个可执行，一个可引用。


### [5、什么是Spring的内部bean？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#5什么是spring的内部bean)  


当一个bean仅被用作另一个bean的属性时，它能被声明为一个内部bean，为了定义inner bean，在Spring 的 基于XML的 配置元数据中，可以在 或  元素内使用 元素，内部bean通常是匿名的，它们的Scope一般是prototype。


### [6、怎样开启注解装配？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#6怎样开启注解装配)  


注解装配在默认情况下是不开启的，为了使用注解装配，我们必须在Spring配置文件中配置 [context:annotation-config/]()元素。


### [7、链路跟踪Sleuth](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#7链路跟踪sleuth)  


当我们项目中引入Spring Cloud Sleuth后，每次链路请求都会添加一串追踪信息，格式是[server-name, main-traceId,sub-spanId,boolean]：

**1、** server-name：服务结点名称。

**2、** main-traceId：一条链路唯一的ID，为TraceID。

**3、** sub-spanId：链路中每一环的ID，为SpanID。

**4、** boolean：是否将信息输出到Zipkin等服务收集和展示。

Sleuth的实现是基于HTTP的，为了在数据的收集过程中不能影响到正常业务，Sleuth会在每个请求的Header上添加跟踪需求的重要信息。这样在数据收集时，只需要将Header上的相关信息发送给对应的图像工具即可，图像工具根据上传的数据，按照Span对应的逻辑进行分析、展示。



### [8、有几种不同类型的自动代理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#8有几种不同类型的自动代理)  


BeanNameAutoProxyCreator

DefaultAdvisorAutoProxyCreator

Metadata autoproxying


### [9、如何使用 SpringBoot 实现异常处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#9如何使用-springboot-实现异常处理)  


Spring 提供了一种使用 ControllerAdvice 处理异常的非常有用的方法。我们通过实现一个 ControlerAdvice 类，来处理控制器类抛出的所有异常。


### [10、为什么我们需要 spring-boot-maven-plugin?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#10为什么我们需要-spring-boot-maven-plugin)  


spring-boot-maven-plugin 提供了一些像 jar 一样打包或者运行应用程序的命令。

spring-boot:run 运行你的 SpringBooty 应用程序。

spring-boot：repackage 重新打包你的 jar 包或者是 war 包使其可执行

spring-boot：start 和 spring-boot：stop 管理 SpringBoot 应用程序的生命周期（也可以说是为了集成测试）。

spring-boot:build-info 生成执行器可以使用的构造信息。


### [11、Spring Cloud的版本关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#11spring-cloud的版本关系)  

### [12、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#12运行-springboot-有哪几种方式)  

### [13、什么是 Spring IOC 容器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#13什么是-spring-ioc-容器)  

### [14、什么是REST / RESTful以及它的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#14什么是rest-/-restful以及它的用途是什么)  

### [15、单片，SOA和微服务架构有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#15单片soa和微服务架构有什么区别)  

### [16、什么是SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#16什么是springboot)  

### [17、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#17运行-springboot-有哪几种方式)  

### [18、什么是双因素身份验证？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#18什么是双因素身份验证)  

### [19、SpringBoot自动配置的原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#19springboot自动配置的原理)  

### [20、SpringCloud的优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#20springcloud的优缺点)  

### [21、如何使用SpringBoot实现分页和排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#21如何使用springboot实现分页和排序)  

### [22、微服务架构如何运作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#22微服务架构如何运作)  

### [23、YAML 配置的优势在哪里 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#23yaml-配置的优势在哪里-)  

### [24、spring-boot-starter-parent 有什么用 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#24spring-boot-starter-parent-有什么用-)  

### [25、什么是端到端微服务测试？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#25什么是端到端微服务测试)  

### [26、什么是FreeMarker模板？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#26什么是freemarker模板)  

### [27、保护 SpringBoot 应用有哪些方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#27保护-springboot-应用有哪些方法)  

### [28、比较一下 Spring Security 和 Shiro 各自的优缺点 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#28比较一下-spring-security-和-shiro-各自的优缺点-)  

### [29、什么是 JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#29什么是-javaconfig)  

### [30、如何实现动态Zuul网关路由转发](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案汇总（2021年Spring面试题答案大全）.md#30如何实现动态zuul网关路由转发)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
