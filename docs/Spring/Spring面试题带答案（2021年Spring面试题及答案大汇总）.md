# Spring面试题带答案（2021年Spring面试题及答案大汇总）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何在SpringBoot应用程序中实现Spring安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#1如何在springboot应用程序中实现spring安全性)  


实施需要最少的配置。您需要做的就是spring-boot-starter-security在pom.xml文件中添加starter。您还需要创建一个Spring配置类，它将覆盖所需的方法，同时扩展 WebSecurityConfigurerAdapter 应用程序中的安全性。这是一些示例代码：

```
package com.gkatzioura.security.securityendpoints.config;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;@
Configuration
public class SecurityConfig extends WebSecurityConfigurerAdapter {@
    Override
    protected void configure(HttpSecurity http) throws Exception {
        http.
        authorizeRequests().
        antMatchers("/welcome").
        permitAll().anyRequest().
        authenticated().and().
        formLogin().
        permitAll().
        and().
        logout().
        permitAll();
    }
}
```


### [2、spring 支持哪些 ORM 框架](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#2spring-支持哪些-orm-框架)  


**1、** Hibernate

**2、** iBatis

**3、** JPA

**4、** JDO

**5、** OJB


### [3、Spring Cloud解决了哪些问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#3spring-cloud解决了哪些问题)  


在使用SpringBoot开发分布式微服务时，我们面临的问题很少由Spring Cloud解决。

与分布式系统相关的复杂性 – 包括网络问题，延迟开销，带宽问题，安全问题。

处理服务发现的能力 – 服务发现允许集群中的进程和服务找到彼此并进行通信。

解决冗余问题 – 冗余问题经常发生在分布式系统中。

负载平衡 – 改进跨多个计算资源（例如计算机集群，网络链接，中央处理单元）的工作负载分布。

减少性能问题 – 减少因各种操作开销导致的性能问题。


### [4、SpringBoot、Spring MVC 和 Spring 有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#4springbootspring-mvc-和-spring-有什么区别)  


**1、** Spring 是一个“引擎”，

**2、** Spring MVC是基于Spring的一个 MVC 框架，

**3、** SpringBoot是基于 Spring的一套快速开发整合包


### [5、SpringBoot 是否可以使用 XML 配置 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#5springboot-是否可以使用-xml-配置-)  


SpringBoot 推荐使用 Java 配置而非 XML 配置，但是 SpringBoot 中也可以使用 XML 配置，通过 [@ImportResource ](/ImportResource ) 注解可以引入一个 XML 配置。


### [6、什么是 WebSockets？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#6什么是-websockets)  


WebSocket 是一种计算机通信协议，通过单个 TCP 连接提供全双工通信信道。

**1、** WebSocket 是双向的 -使用 WebSocket 客户端或服务器可以发起消息发送。

**2、** WebSocket 是全双工的 -客户端和服务器通信是相互独立的。

**3、** 单个 TCP 连接 -初始连接使用 HTTP，然后将此连接升级到基于套接字的连接。然后这个单一连接用于所有未来的通信

**4、** Light -与 http 相比，WebSocket 消息数据交换要轻得多。


### [7、Spring支持的事务管理类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#7spring支持的事务管理类型)  


Spring支持两种类型的事务管理：

**1、** 编程式事务管理：这意味你通过编程的方式管理事务，给你带来极大的灵活性，但是难维护。

**2、** 声明式事务管理：这意味着你可以将业务代码和事务管理分离，你只需用注解和XML配置来管理事务。


### [8、什么是幂等性?它是如何使用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#8什么是幂等性它是如何使用的)  


幂等性指的是这样一种场景:您重复执行一项任务，但最终结果保持不变或类似。 幂等性主要用作数据源或远程服务，当它接收一组以上指令时，它只处理一组指令。



### [9、[@Autowired ](/Autowired ) 注解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#9[@autowired-]/autowired--注解)  


[@Autowired ](/Autowired ) 注解提供了更细粒度的控制，包括在何处以及如何完成自动装配。它的用法和@Required一样，修饰setter方法、构造器、属性或者具有任意名称和/或多个参数的PN方法。


### [10、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#10springboot-的核心注解是哪个它主要由哪几个注解组成的)  


启动类上面的注解是@SpringBootApplication，它也是 SpringBoot 的核心注解，主要组合包含了以下 3 个注解：

@SpringBootConfiguration：组合了 [@Configuration ](/Configuration ) 注解，实现配置文件的功能。

@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项，如关闭数据源自动配置功能：

[@SpringBootApplication(exclude ](/SpringBootApplication(exclude ) = { DataSourceAutoConfiguration.class })。

@ComponentScan：Spring组件扫描。


### [11、什么是 Spring Profiles？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#11什么是-spring-profiles)  

### [12、SpringBoot 中如何解决跨域问题 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#12springboot-中如何解决跨域问题-)  

### [13、如何使用SpringBoot实现分页和排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#13如何使用springboot实现分页和排序)  

### [14、什么是 FreeMarker 模板？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#14什么是-freemarker-模板)  

### [15、一个Spring的应用看起来象什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#15一个spring的应用看起来象什么)  

### [16、SpringBoot中的监视器是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#16springboot中的监视器是什么)  

### [17、如何使用SpringBoot实现异常处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#17如何使用springboot实现异常处理)  

### [18、您将如何在微服务上执行安全测试？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#18您将如何在微服务上执行安全测试)  

### [19、什么是 Apache Kafka？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#19什么是-apache-kafka)  

### [20、解释不同方式的自动装配](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#20解释不同方式的自动装配)  

### [21、Spring Framework 中有多少个模块，它们分别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#21spring-framework-中有多少个模块它们分别是什么)  

### [22、解释WEB 模块。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#22解释web-模块。)  

### [23、@Component, @Controller, @Repository, [@Service ](/Service ) 有何区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#23@component,-@controller,-@repository,-[@service-]/service--有何区别)  

### [24、使用 SpringBoot 启动连接到内存数据库 H2 的 JPA 应用程序需要哪些依赖项？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#24使用-springboot-启动连接到内存数据库-h2-的-jpa-应用程序需要哪些依赖项)  

### [25、使用Spring通过什么方式访问Hibernate?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#25使用spring通过什么方式访问hibernate)  

### [26、什么是 Hystrix？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#26什么是-hystrix)  

### [27、22。你能否给出关于休息和微服务的要点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#2722。你能否给出关于休息和微服务的要点)  

### [28、什么是 spring 装配](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#28什么是-spring-装配)  

### [29、什么是 JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#29什么是-javaconfig)  

### [30、什么是Spring Actuator？它有什么优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#30什么是spring-actuator它有什么优势)  

### [31、SpringBoot 需要独立的容器运行吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题带答案（2021年Spring面试题及答案大汇总）.md#31springboot-需要独立的容器运行吗)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
