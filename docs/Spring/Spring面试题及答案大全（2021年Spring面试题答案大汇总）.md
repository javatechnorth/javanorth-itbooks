# Spring面试题及答案大全（2021年Spring面试题答案大汇总）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、网关与过滤器有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#1网关与过滤器有什么区别)  


网关是对所有服务的请求进行分析过滤，过滤器是对单个服务而言。


### [2、spring 支持集中 bean scope？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#2spring-支持集中-bean-scope)  


Spring bean 支持 5 种 scope：

**Singleton**

**1、** 每个 Spring IoC 容器仅有一个单实例。Prototype

**2、** 每次请求都会产生一个新的实例。Request

**3、** 每一次 HTTP 请求都会产生一个新的实例，并且该 bean 仅在当前 HTTP 请求内有效。Session

**4、** 每一次 HTTP 请求都会产生一个新的 bean，同时该 bean 仅在当前 HTTP session 内有效。Global-session

**5、** 类似于标准的 HTTP Session 作用域，不过它仅仅在基于 portlet 的 web 应用中才有意义。Portlet 规范定义了全局 Session 的概念，它被所有构成某个 portlet web 应用的各种不同的 portlet 所共享。在 global session 作用域中定义的 bean 被限定于全局 portlet Session 的生命周期范围内。如果你在 web 中使用 global session 作用域来标识 bean，那么 web 会自动当成 session 类型来使用。

仅当用户使用支持 Web 的 ApplicationContext 时，最后三个才可用。


### [3、保护 SpringBoot 应用有哪些方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#3保护-springboot-应用有哪些方法)  


在生产中使用HTTPS 使用Snyk检查你的依赖关系 升级到最新版本 启用CSRF保护 使用内容安全策略防止XSS攻击



### [4、架构师在微服务架构中的角色是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#4架构师在微服务架构中的角色是什么)  


微服务架构中的架构师扮演以下角色：

决定整个软件系统的布局。

帮助确定组件的分区。因此，他们确保组件相互粘合，但不紧密耦合。

与开发人员共同编写代码，了解日常生活中面临的挑战。

为开发微服务的团队提供某些工具和技术的建议。

提供技术治理，以便技术开发团队遵循微服务原则。


### [5、spring JDBC API 中存在哪些类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#5spring-jdbc-api-中存在哪些类)  


**1、** JdbcTemplate

**2、** SimpleJdbcTemplate

**3、** NamedParameterJdbcTemplate

**4、** SimpleJdbcInsert

**5、** SimpleJdbcCall



### [6、Spring配置文件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#6spring配置文件)  


Spring配置文件是个XML 文件，这个文件包含了类信息，描述了如何配置它们，以及如何相互调用。


### [7、为什么要使用 Spring Cloud 熔断器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#7为什么要使用-spring-cloud-熔断器)  


当一个服务调用另一个服务，由于网络原因或者自身原因出现问题时 ，调用者就会等待被调者的响应，当更多的服务请求到这些资源时，导致更多的请求等待，这样就会发生连锁效应，断路器就是解决这一问题的。

**断路器的状态有以下几种：**

**1、** 完全打开：一定时间内，达到一定的次数无法调用，并且多次检测没有恢复的迹象，断路器完全打开，那么下次的请求不会请求到该服务。

**2、** 半开：短时间内有恢复迹象，断路器会将部分请求发送给服务，当能正常调用时，断路器关闭。

**3、** 关闭：服务一直处于正常状态，能正常调用，断路器关闭。


### [8、什么是 Swagger？你用 SpringBoot 实现了它吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#8什么是-swagger你用-springboot-实现了它吗)  


Swagger 广泛用于可视化 API，使用 Swagger UI 为前端开发人员提供在线沙箱。Swagger 是用于生成 RESTful Web 服务的可视化表示的工具，规范和完整框架实现。它使文档能够以与服务器相同的速度更新。当通过 Swagger 正确定义时，消费者可以使用最少量的实现逻辑来理解远程服务并与其进行交互。因此，Swagger消除了调用服务时的猜测。


### [9、SpringBoot 如何设置支持跨域请求？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#9springboot-如何设置支持跨域请求)  


现代浏览器出于安全的考虑， HTTP 请求时必须遵守同源策略，否则就是跨域的 HTTP 请求，默认情况下是被禁止的，IP（域名）不同、或者端口不同、协议不同（比如 HTTP、HTTPS）都会造成跨域问题。

**一般前端的解决方案有：**

**1、** 使用 JSONP 来支持跨域的请求，JSONP 实现跨域请求的原理简单的说，就是动态创建`<script>`标签，然后利用`<script>`的 SRC 不受同源策略约束来跨域获取数据。缺点是需要后端配合输出特定的返回信息。

**2、** 利用反应代理的机制来解决跨域的问题，前端请求的时候先将请求发送到同源地址的后端，通过后端请求转发来避免跨域的访问。

后来 HTML5 支持了 CORS 协议。CORS 是一个 W3C 标准，全称是”跨域资源共享”（Cross-origin resource sharing），允许浏览器向跨源服务器，发出 XMLHttpRequest 请求，从而克服了 AJAX 只能同源使用的限制。它通过服务器增加一个特殊的 Header[Access-Control-Allow-Origin]来告诉客户端跨域的限制，如果浏览器支持 CORS、并且判断 Origin 通过的话，就会允许 XMLHttpRequest 发起跨域请求。

前端使用了 CORS 协议，就需要后端设置支持非同源的请求，SpringBoot 设置支持非同源的请求有两种方式。

第一，配置 CorsFilter。

```

@Configuration
public class GlobalCorsConfig {
    @Bean
    public CorsFilter corsFilter() {
        CorsConfiguration config = new CorsConfiguration();
          config.addAllowedOrigin("*");
          config.setAllowCredentials(true);
          config.addAllowedMethod("*");
          config.addAllowedHeader("*");
          config.addExposedHeader("*");

        UrlBasedCorsConfigurationSource configSource = new UrlBasedCorsConfigurationSource();
        configSource.registerCorsConfiguration("/**", config);

        return new CorsFilter(configSource);
    }
}
```

需要配置上述的一段代码。第二种方式稍微简单一些。

第二，在启动类上添加：

```

public class Application extends WebMvcConfigurerAdapter {

    @Override
    public void addCorsMappings(CorsRegistry registry) {

        registry.addMapping("/**")
                .allowCredentials(true)
                .allowedHeaders("*")
                .allowedOrigins("*")
                .allowedMethods("*");

    }
}
```


### [10、你对SpringBoot有什么了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#10你对springboot有什么了解)  


事实上，随着新功能的增加，弹簧变得越来越复杂。如果必须启动新的spring项目，则必须添加构建路径或添加maven依赖项，配置应用程序服务器，添加spring配置。所以一切都必须从头开始。

SpringBoot是解决这个问题的方法。使用spring boot可以避免所有样板代码和配置。因此，基本上认为自己就好像你正在烘烤蛋糕一样，春天就像制作蛋糕所需的成分一样，弹簧靴就是你手中的完整蛋糕。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_12.png#alt=img%5C_12.png)

图10：  SpringBoot的因素 – 微服务面试问题


### [11、Eureka怎么实现高可用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#11eureka怎么实现高可用)  

### [12、如何使用SpringBoot实现异常处理?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#12如何使用springboot实现异常处理)  

### [13、什么是SpringBoot ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#13什么是springboot-)  

### [14、解释对象/关系映射集成模块。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#14解释对象/关系映射集成模块。)  

### [15、什么是 Aspect？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#15什么是-aspect)  

### [16、使用 Spring 有哪些方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#16使用-spring-有哪些方式)  

### [17、Spring Cloud Sleuth](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#17spring-cloud-sleuth)  

### [18、Container在微服务中的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#18container在微服务中的用途是什么)  

### [19、微服务有哪些特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#19微服务有哪些特点)  

### [20、Async异步调用方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#20async异步调用方法)  

### [21、Spring Cloud 是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#21spring-cloud-是什么)  

### [22、如何使用 SpringBoot 实现分页和排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#22如何使用-springboot-实现分页和排序)  

### [23、SpringBoot 的核心配置文件有哪几个？它们的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#23springboot-的核心配置文件有哪几个它们的区别是什么)  

### [24、Bean 工厂和 Application contexts 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#24bean-工厂和-application-contexts-有什么区别)  

### [25、有哪些不同类型的IOC（依赖注入）方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#25有哪些不同类型的ioc依赖注入方式)  

### [26、为什么要选择微服务架构？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#26为什么要选择微服务架构)  

### [27、SpringBoot 有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#27springboot-有哪些优点)  

### [28、什么是Oauth？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#28什么是oauth)  

### [29、为什么我们不建议在实际的应用程序中使用 Spring Data Rest?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#29为什么我们不建议在实际的应用程序中使用-spring-data-rest)  

### [30、什么是Spring的MVC框架？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#30什么是spring的mvc框架)  

### [31、列举 Spring DAO 抛出的异常。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring面试题及答案大全（2021年Spring面试题答案大汇总）.md#31列举-spring-dao-抛出的异常。)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
