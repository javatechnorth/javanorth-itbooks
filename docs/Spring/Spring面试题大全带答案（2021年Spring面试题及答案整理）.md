# Spring面试题大全带答案（2021年Spring面试题及答案整理）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、@ResponseBody注解的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#1@responsebody注解的作用)  


**作用：**

该注解用于将Controller的方法返回的对象，通过适当的HttpMessageConverter转换为指定格式后，写入到Response对象的body数据区。

**使用时机：**

返回的数据不是html标签的页面，而是其他某种格式的数据时（如json、xml等）使用；


### [2、项目中前后端分离部署，所以需要解决跨域的问题。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#2项目中前后端分离部署所以需要解决跨域的问题。)  


我们使用cookie存放用户登录的信息，在spring拦截器进行权限控制，当权限不符合时，直接返回给用户固定的json结果。

当用户登录以后，正常使用；当用户退出登录状态时或者token过期时，由于拦截器和跨域的顺序有问题，出现了跨域的现象。

我们知道一个http请求，先走filter，到达servlet后才进行拦截器的处理，如果我们把cors放在filter里，就可以优先于权限拦截器执行。

```
@Configuration
public class CorsConfig {

    @Bean
    public CorsFilter corsFilter() {
        CorsConfiguration corsConfiguration = new CorsConfiguration();
        corsConfiguration.addAllowedOrigin("*");
        corsConfiguration.addAllowedHeader("*");
        corsConfiguration.addAllowedMethod("*");
        corsConfiguration.setAllowCredentials(true);
        UrlBasedCorsConfigurationSource urlBasedCorsConfigurationSource = new UrlBasedCorsConfigurationSource();
        urlBasedCorsConfigurationSource.registerCorsConfiguration("/**", corsConfiguration);
        return new CorsFilter(urlBasedCorsConfigurationSource);
    }

}
```


### [3、Spring Cloud Netflix(重点，这些组件用的最多)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#3spring-cloud-netflix重点这些组件用的最多)  


Netflix OSS 开源组件集成，包括Eureka、Hystrix、Ribbon、Feign、Zuul等核心组件。

**1、** Eureka：服务治理组件，包括服务端的注册中心和客户端的服务发现机制；

**2、** Ribbon：负载均衡的服务调用组件，具有多种负载均衡调用策略；

**3、** Hystrix：服务容错组件，实现了断路器模式，为依赖服务的出错和延迟提供了容错能力；

**4、** Feign：基于Ribbon和Hystrix的声明式服务调用组件；

**5、** Zuul：API网关组件，对请求提供路由及过滤功能。

`我觉得SpringCloud的福音是Netflix，他把人家的组件都搬来进行封装了，使开发者能快速简单安全的使用`


### [4、SpringBoot支持什么前端模板，](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#4springboot支持什么前端模板)  


thymeleaf，freemarker，jsp，官方不推荐JSP会有限制


### [5、负载平衡的意义什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#5负载平衡的意义什么)  


**1、** 简单来说： 先将集群，集群就是把一个的事情交给多个人去做，假如要做1000个产品给一个人做要10天，我叫10个人做就是一天，这就是集群，负载均衡的话就是用来控制集群，他把做的最多的人让他慢慢做休息会，把做的最少的人让他加量让他做多点。

**2、** 在计算中，负载平衡可以改善跨计算机，计算机集群，网络链接，中央处理单元或磁盘驱动器等多种计算资源的工作负载分布。负载平衡旨在优化资源使用，最大化吞吐量，最小化响应时间并避免任何单一资源的过载。使用多个组件进行负载平衡而不是单个组件可能会通过冗余来提高可靠性和可用性。负载平衡通常涉及专用软件或硬件，例如多层交换机或域名系统服务器进程。


### [6、分布式配置中心的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#6分布式配置中心的作用)  


动态变更项目配置信息而不必重新部署项目。


### [7、SpringBoot读取配置文件的方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#7springboot读取配置文件的方式)  


SpringBoot默认读取配置文件为application.properties或者是application.yml


### [8、什么是执行器停机？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#8什么是执行器停机)  


关机是允许应用程序正常关机的端点。默认情况下，此功能不启用。你可以在应用程序属性文件中使用management . endpoint . shut down . enabled = true来启用此选项。但是该方法请谨慎使用。


### [9、Spring Cloud Task](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#9spring-cloud-task)  


Spring Cloud Task的目标是为SpringBoot应用程序提供创建短运行期微服务的功能。在Spring Cloud Task中，我们可以灵活地动态运行任何任务，按需分配资源并在任务完成后检索结果。Tasks是Spring Cloud Data Flow中的一个基础项目，允许用户将几乎任何SpringBoot应用程序作为一个短期任务执行。


### [10、列举微服务技术栈](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#10列举微服务技术栈)  


**1、** 服务⽹关Zuul

**2、** 服务注册发现Eureka+Ribbon

**3、** 服务配置中⼼Apollo

**4、** 认证授权中⼼Spring Security OAuth2

**5、** 服务框架SpringBoot

**6、** 数据总线Kafka

**7、** ⽇志监控ELK

**8、** 调⽤链监控CAT

**9、** Metrics监控KairosDB

**10、** 健康检查和告警ZMon

**11、** 限流熔断和流聚合Hystrix/Turbine


### [11、什么是Spring Cloud Config?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#11什么是spring-cloud-config)  

### [12、DispatcherServlet](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#12dispatcherservlet)  

### [13、什么是DispatcherServlet](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#13什么是dispatcherservlet)  

### [14、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#14springboot-的核心配置文件有哪几个它们的区别是什么)  

### [15、SpringBoot 的自动配置是如何实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#15springboot-的自动配置是如何实现的)  

### [16、SpringBoot默认支持的日志框架有哪些？可以进行哪些设置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#16springboot默认支持的日志框架有哪些可以进行哪些设置)  

### [17、如何在 SpringBoot 启动的时候运行一些特定的代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#17如何在-springboot-启动的时候运行一些特定的代码)  

### [18、Spring Cache 三种常用的缓存注解和意义？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#18spring-cache-三种常用的缓存注解和意义)  

### [19、什么是网关?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#19什么是网关)  

### [20、使用 Spring 访问 Hibernate 的方法有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#20使用-spring-访问-hibernate-的方法有哪些)  

### [21、spring boot 核心配置文件是什么？bootstrap、properties 和 application、properties 有何区别 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#21spring-boot-核心配置文件是什么bootstrapproperties-和-applicationproperties-有何区别-)  

### [22、什么是 SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#22什么是-springboot)  

### [23、什么是 AOP 引入?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#23什么是-aop-引入)  

### [24、什么是YAML？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#24什么是yaml)  

### [25、在微服务中，如何保护服务?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#25在微服务中如何保护服务)  

### [26、SpringBoot的启动器有哪几种?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#26springboot的启动器有哪几种)  

### [27、你如何理解 SpringBoot 中的 Starters？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#27你如何理解-springboot-中的-starters)  

### [28、什么是OAuth？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#28什么是oauth)  

### [29、什么是WebSockets？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#29什么是websockets)  

### [30、为什么我们需要微服务容器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#30为什么我们需要微服务容器)  

### [31、什么是 Spring Batch?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题大全带答案（2021年Spring面试题及答案整理）.md#31什么是-spring-batch)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
