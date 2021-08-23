# Spring面试题及答案整理（2021年Spring面试题答案大汇总）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、解释AOP](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#1解释aop)  


面向切面的编程，或AOP， 是一种编程技术，允许程序模块化横向切割关注点，或横切典型的责任划分，如日志和事务管理。


### [2、Spring Cloud和各子项目版本对应关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#2spring-cloud和各子项目版本对应关系)  


**1、** Edgware.SR6：我理解为最低版本号

**2、** Greenwich.SR2 :我理解为最高版本号

**3、** Greenwich.BUILD-SNAPSHOT（快照）：是一种特殊的版本，指定了某个当前的开发进度的副本。不同于常规的版本，几乎每天都要提交更新的版本，如果每次提交都申明一个版本号那不是版本号都不够用？

| Component | Edgware.SR6 | Greenwich.SR2 | Greenwich.BUILD-SNAPSHOT |
| --- | --- | --- | --- |
| spring-cloud-aws | 1.2.4.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-bus | 1.3.4.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-cli | 1.4.1.RELEASE | 2.0.0.RELEASE | 2.0.1.BUILD-SNAPSHOT |
| spring-cloud-commons | 1.3.6.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-contract | 1.2.7.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-config | 1.4.7.RELEASE | 2.1.3.RELEASE | 2.1.4.BUILD-SNAPSHOT |
| spring-cloud-netflix | 1.4.7.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-security | 1.2.4.RELEASE | 2.1.3.RELEASE | 2.1.4.BUILD-SNAPSHOT |
| spring-cloud-cloudfoundry | 1.1.3.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-consul | 1.3.6.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-sleuth | 1.3.6.RELEASE | 2.1.1.RELEASE | 2.1.2.BUILD-SNAPSHOT |
| spring-cloud-stream | Ditmars.SR5 | Fishtown.SR3 | Fishtown.BUILD-SNAPSHOT |
| spring-cloud-zookeeper | 1.2.3.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-boot | 1.5.21.RELEASE | 2.1.5.RELEASE | 2.1.8.BUILD-SNAPSHOT |
| spring-cloud-task | 1.2.4.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-vault | 1.1.3.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-gateway | 1.0.3.RELEASE | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |
| spring-cloud-openfeign | 2.1.2.RELEASE | 2.1.3.BUILD-SNAPSHOT |  |
| spring-cloud-function | 1.0.2.RELEASE | 2.0.2.RELEASE | 2.0.3.BUILD-SNAPSHOT |


### [3、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#3运行-springboot-有哪几种方式)  


**1、** 打包用命令或者放到容器中运行

**2、** 用 Maven/ Gradle 插件运行

**3、** 直接执行 main 方法运行


### [4、什么是Spring Cloud？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#4什么是spring-cloud)  


根据Spring Cloud的官方网站，Spring Cloud为开发人员提供了快速构建分布式系统中一些常见模式的工具（例如配置管理，服务发现，断路器，智能路由，领导选举，分布式会话，集群状态）。


### [5、有哪些类型的通知（Advice）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#5有哪些类型的通知advice)  


**1、** Before - 这些类型的 Advice 在 joinpoint 方法之前执行，并使用 [@Before ](/Before ) 注解标记进行配置。

**2、** After Returning - 这些类型的 Advice 在连接点方法正常执行后执行，并使用[@AfterReturning ](/AfterReturning ) 注解标记进行配置。

**3、** After Throwing - 这些类型的 Advice 仅在 joinpoint 方法通过抛出异常退出并使用 [@AfterThrowing ](/AfterThrowing ) 注解标记配置时执行。

**4、** After (finally) - 这些类型的 Advice 在连接点方法之后执行，无论方法退出是正常还是异常返回，并使用 [@After ](/After ) 注解标记进行配置。

**5、** Around - 这些类型的 Advice 在连接点之前和之后执行，并使用 [@Around ](/Around ) 注解标记进行配置。


### [6、为什么我们需要 spring-boot-maven-plugin?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#6为什么我们需要-spring-boot-maven-plugin)  


spring-boot-maven-plugin 提供了一些像 jar 一样打包或者运行应用程序的命令。

**1、** spring-boot:run 运行你的 SpringBooty 应用程序。

**2、** spring-boot：repackage 重新打包你的 jar 包或者是 war 包使其可执行

**3、** spring-boot：start 和 spring-boot：stop 管理 SpringBoot 应用程序的生命周期（也可以说是为了集成测试）。

**4、** spring-boot:build-info 生成执行器可以使用的构造信息。


### [7、比较一下 Spring Security 和 Shiro 各自的优缺点 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#7比较一下-spring-security-和-shiro-各自的优缺点-)  


由于 SpringBoot 官方提供了大量的非常方便的开箱即用的 Starter ，包括 Spring Security 的 Starter ，使得在 SpringBoot 中使用 Spring Security 变得更加容易，甚至只需要添加一个依赖就可以保护所有的接口，所以，如果是 SpringBoot 项目，一般选择 Spring Security 。当然这只是一个建议的组合，单纯从技术上来说，无论怎么组合，都是没有问题的。Shiro 和 Spring Security 相比

**主要有如下一些特点：**

**1、** Spring Security 是一个重量级的安全管理框架；Shiro 则是一个轻量级的安全管理框架

**2、** Spring Security 概念复杂，配置繁琐；Shiro 概念简单、配置简单

**3、** Spring Security 功能强大；Shiro 功能简单


### [8、合同测试你懂什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#8合同测试你懂什么)  


根据Martin Flower的说法，合同测试是在外部服务边界进行的测试，用于验证其是否符合消费服务预期的合同。

此外，合同测试不会深入测试服务的行为。更确切地说，它测试该服务调用的输入＆输出包含所需的属性和所述响应延迟，吞吐量是允许的限度内。


### [9、使用Spring框架的好处是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#9使用spring框架的好处是什么)  


**1、** 轻量：Spring 是轻量的，基本的版本大约2MB。

**2、** 控制反转：Spring通过控制反转实现了松散耦合，对象们给出它们的依赖，而不是创建或查找依赖的对象们。

**3、** 面向切面的编程(AOP)：Spring支持面向切面的编程，并且把应用业务逻辑和系统服务分开。

**4、** 容器：Spring 包含并管理应用中对象的生命周期和配置。

**5、** MVC框架：Spring的WEB框架是个精心设计的框架，是Web框架的一个很好的替代品。

**6、** 事务管理：Spring 提供一个持续的事务管理接口，可以扩展到上至本地事务下至全局事务（JTA）。

**7、** 异常处理：Spring 提供方便的API把具体技术相关的异常（比如由JDBC，Hibernate or JDO抛出的）转化为一致的unchecked 异常。


### [10、spring boot初始化环境变量流程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#10spring-boot初始化环境变量流程)  


**1、** 调用`prepareEnvironment`方法去设置环境变量

**2、** 接下来有三个方法`getOrCreateEnvironment`，`configureEnvironment`，`environmentPrepared`

**3、** `getOrCreateEnvironment`去初始化系统环境变量

**4、** `configureEnvironment`去初始化命令行参数

**5、** `environmentPrepared`当广播到来的时候调用`onApplicationEnvironmentPreparedEvent`方法去使用`postProcessEnvironment`方法`load yml`和`properties变量`


### [11、SpringBoot中的监视器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#11springboot中的监视器是什么)  

### [12、负载平衡的意义什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#12负载平衡的意义什么)  

### [13、什么是领域驱动设计？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#13什么是领域驱动设计)  

### [14、如何设置服务发现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#14如何设置服务发现)  

### [15、怎样在方法里面得到Request,或者Session？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#15怎样在方法里面得到request,或者session)  

### [16、微服务测试的主要障碍是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#16微服务测试的主要障碍是什么)  

### [17、我们如何进行跨功能测试？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#17我们如何进行跨功能测试)  

### [18、spring 提供了哪些配置方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#18spring-提供了哪些配置方式)  

### [19、开启 SpringBoot 特性有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#19开启-springboot-特性有哪几种方式)  

### [20、SpringBoot 常用的 Starter 有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#20springboot-常用的-starter-有哪些)  

### [21、什么是Spring Batch？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#21什么是spring-batch)  

### [22、什么是JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#22什么是javaconfig)  

### [23、Spring Cloud Security](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#23spring-cloud-security)  

### [24、什么是 AOP Aspect 切面](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#24什么是-aop-aspect-切面)  

### [25、如果前台有很多个参数传入,并且这些参数都是一个对象的,那么怎么样快速得到这个对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#25如果前台有很多个参数传入,并且这些参数都是一个对象的,那么怎么样快速得到这个对象)  

### [26、Spring Cloud Stream](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#26spring-cloud-stream)  

### [27、在 Spring Initializer 中，如何改变一个项目的包名字？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#27在-spring-initializer-中如何改变一个项目的包名字)  

### [28、熔断的原理，以及如何恢复？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#28熔断的原理以及如何恢复)  

### [29、Actuator在SpringBoot中的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#29actuator在springboot中的作用)  

### [30、服务雪崩？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案整理（2021年Spring面试题答案大汇总）.md#30服务雪崩)  





