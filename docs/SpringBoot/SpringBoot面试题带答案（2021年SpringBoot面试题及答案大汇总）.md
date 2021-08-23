# SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）

SpringBoot面试题及答案【最新版】SpringBoot高级面试题大全(2021版)，发现网上很多SpringBoot面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringBoot面试题大全，SpringBoot面试题大汇总，有大量经典的SpringBoot面试题以及答案，包含SpringBoot语言常见面试题、SpringBoot工程师高级面试题及一些大厂SpringBoot开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringBoot面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringBoot面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、SpringBoot 如何设置支持跨域请求？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#1springboot-如何设置支持跨域请求)  


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


### [2、SpringBoot多数据源拆分的思路](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#2springboot多数据源拆分的思路)  


先在properties配置文件中配置两个数据源，创建分包mapper，使用@ConfigurationProperties读取properties中的配置，使用@MapperScan注册到对应的mapper包中


### [3、SpringBoot 2.X 有什么新特性？与 1.X 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#3springboot-2x-有什么新特性与-1x-有什么区别)  


**1、** 依赖 JDK 版本升级：2.x 里面的许多方法应用了 JDK 8 的许多高级新特性，至少需要 JDK 8 的支持；

**2、** 第三方类库升：2.x 对第三方类库升级了所有能升级的稳定版本，例如：Spring Framework 5+、Tomcat 8.5+、Hibernate 5.2+、Thymeleaf 3+；

**3、** 响应式 Spring 编程：2.x 通过启动器和自动配置全面支持 Spring 的响应式编程，响应式编程是完全异步和非阻塞的，它是基于事件驱动模型，而不是传统的线程模型；

**4、** 连接池：2.x 默认使用 HikariCP 连接池；

**5、** json：提供了一个 spring-boot-starter-json 启动器对 JSON 读写的支持；

**6、** Quartz：2.x 提供了一个 spring-boot-starter-quartz 启动器对定时任务框架 Quartz 的支持；

**7、** HTTP/2 支持：提供对HTTP/2 的支持，如：Tomcat, Undertow, Jetty；

**8、** Actuator加强：在 2.x 中，对执行器端点进行了许多改进，所有的 HTTP 执行端点现在都暴露在 /actuator路径下，并对 JSON 结果集也做了改善。


### [4、SpringBoot有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#4springboot有哪些优点)  


**1、** 快速创建独立运行的spring项目与主流框架集成

**2、** 使用嵌入式的servlet容器，应用无需打包成war包

**3、** starters自动依赖与版本控制

**4、** 大量的自动配置，简化开发，也可修改默认值

**5、** 准生产环境的运行应用监控

**6、** 与云计算的天然集成


### [5、RequestMapping 和 GetMapping 的不同之处在哪里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#5requestmapping-和-getmapping-的不同之处在哪里)  


RequestMapping 具有类属性的，可以进行 GET,POST,PUT 或者其它的注释中具有的请求方法。

GetMapping 是 GET 请求方法中的一个特例。它只是 ResquestMapping 的一个延伸，目的是为了提高清晰度。


### [6、如何实现 SpringBoot 应用程序的安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#6如何实现-springboot-应用程序的安全性)  


为了实现 SpringBoot 的安全性，我们使用 spring-boot-starter-security 依赖项，并且必须添加安全配置。它只需要很少的代码。配置类将必须扩展WebSecurityConfigurerAdapter 并覆盖其方法。


### [7、你能否举一个以 ReadOnly 为事务管理的例子？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#7你能否举一个以-readonly-为事务管理的例子)  


当你从数据库读取内容的时候，你想把事物中的用户描述或者是其它描述设置为只读模式，以便于 Hebernate 不需要再次检查实体的变化。这是非常高效的。


### [8、SpringBoot读取配置文件的方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#8springboot读取配置文件的方式)  


SpringBoot默认读取配置文件为application.properties或者是application.yml


### [9、您使用了哪些 starter maven 依赖项？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#9您使用了哪些-starter-maven-依赖项)  


使用了下面的一些依赖项：

spring-boot-starter-activemq

spring-boot-starter-security

这有助于增加更少的依赖关系，并减少版本的冲突。


### [10、SpringBoot有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#10springboot有哪些优点)  


**1、** 减少开发，测试时间和努力。

**2、** 使用JavaConfig有助于避免使用XML。

**3、** 避免大量的Maven导入和各种版本冲突。

**4、** 提供意见发展方法。

**5、** 通过提供默认值快速开始开发。

**6、** 没有单独的Web服务器需要。这意味着你不再需要启动Tomcat，Glassfish或其他任何东西。

**7、** 需要更少的配置 因为没有web.xml文件。只需添加用@ Configuration注释的类，然后添加用@Bean注释的方法，Spring将自动加载对象并像以前一样对其进行管理。您甚至可以将@Autowired添加到bean方法中，以使Spring自动装入需要的依赖关系中。

**8、** 基于环境的配置 使用这些属性，您可以将您正在使用的环境传递到应用程序：-Dspring.profiles.active = {enviornment}。在加载主应用程序属性文件后，Spring将在（application{environment} .properties）中加载后续的应用程序属性文件。


### [11、如何在SpringBoot中禁用Actuator端点安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#11如何在springboot中禁用actuator端点安全性)  

### [12、什么是YAML？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#12什么是yaml)  

### [13、Spring 、SpringBoot 和 Spring Cloud 的关系?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#13spring-springboot-和-spring-cloud-的关系)  

### [14、SpringBoot 实现热部署有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#14springboot-实现热部署有哪几种方式)  

### [15、spring boot 核心配置文件是什么？bootstrap、properties 和 application、properties 有何区别 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#15spring-boot-核心配置文件是什么bootstrapproperties-和-applicationproperties-有何区别-)  

### [16、保护 SpringBoot 应用有哪些方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#16保护-springboot-应用有哪些方法)  

### [17、SpringBoot 的配置文件有哪几种格式？它们有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#17springboot-的配置文件有哪几种格式它们有什么区别)  

### [18、什么是 Spring Data REST?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#18什么是-spring-data-rest)  

### [19、您使用了哪些starter maven依赖项？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#19您使用了哪些starter-maven依赖项)  

### [20、spring-boot-starter-parent 有什么用 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#20spring-boot-starter-parent-有什么用-)  

### [21、SpringBoot 有哪几种读取配置的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#21springboot-有哪几种读取配置的方式)  

### [22、什么是FreeMarker模板？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#22什么是freemarker模板)  

### [23、SpringBoot微服务中如何实现 session 共享 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#23springboot微服务中如何实现-session-共享-)  

### [24、SpringBoot如何实现打包](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#24springboot如何实现打包)  

### [25、如何使用 SpringBoot 实现异常处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#25如何使用-springboot-实现异常处理)  

### [26、什么是 SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#26什么是-springboot)  

### [27、SpringBoot有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#27springboot有哪些优点)  

### [28、@RestController和@Controller的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#28@restcontroller和@controller的区别)  

### [29、如何给静态变量赋值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#29如何给静态变量赋值)  

### [30、SpringBoot需要独立的容器运行？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#30springboot需要独立的容器运行)  

### [31、如何使用SpringBoot实现异常处理?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题带答案（2021年SpringBoot面试题及答案大汇总）.md#31如何使用springboot实现异常处理)  





