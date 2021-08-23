# SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）

SpringBoot面试题及答案【最新版】SpringBoot高级面试题大全(2021版)，发现网上很多SpringBoot面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringBoot面试题大全，SpringBoot面试题大汇总，有大量经典的SpringBoot面试题以及答案，包含SpringBoot语言常见面试题、SpringBoot工程师高级面试题及一些大厂SpringBoot开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringBoot面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringBoot面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、SpringBoot 中如何解决跨域问题 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#1springboot-中如何解决跨域问题-)  


跨域可以在前端通过 JSONP 来解决，但是 JSONP 只可以发送 GET 请求，无法发送其他类型的请求，在 RESTful 风格的应用中，就显得非常鸡肋，因此我们推荐在后端通过 （CORS，Cross-origin resource sharing） 来解决跨域问题。这种解决方案并非 SpringBoot 特有的，在传统的 SSM 框架中，就可以通过 CORS 来解决跨域问题，只不过之前我们是在 XML 文件中配置 CORS ，现在可以通过实现WebMvcConfigurer接口然后重写addCorsMappings方法解决跨域问题。

```
  @Configuration
  public class CorsConfig implements WebMvcConfigurer {

  @Override
  public void addCorsMappings(CorsRegistry registry) {
  registry、addMapping("/**")
  、allowedOrigins("*")
  、allowCredentials(true)
  、allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
  、maxAge(3600);
  }

  }
```


### [2、如何集成 SpringBoot 和 ActiveMQ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#2如何集成-springboot-和-activemq)  


对于集成 SpringBoot 和 ActiveMQ，我们使用依赖关系。它只需要很少的配置，并且不需要样板代码。


### [3、什么是 Apache Kafka？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#3什么是-apache-kafka)  


Apache Kafka 是一个分布式发布 - 订阅消息系统。它是一个可扩展的，容错的发布 - 订阅消息系统，它使我们能够构建分布式应用程序。这是一个 Apache 顶级项目。Kafka 适合离线和在线消息消费。


### [4、spring-boot-starter-parent 有什么用 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#4spring-boot-starter-parent-有什么用-)  


我们都知道，新创建一个 SpringBoot 项目，默认都是有 parent 的，这个 parent 就是 spring-boot-starter-parent ，spring-boot-starter-parent 主要有如下作用：

**1、**  定义了 Java 编译版本为 1、8 。

**2、**  使用 UTF-8 格式编码。

**3、**  继承自 spring-boot-dependencies，这个里边定义了依赖的版本，也正是因为继承了这个依赖，所以我们在写依赖时才不需要写版本号。

**4、**  执行打包操作的配置。

**5、**  自动化的资源过滤。

**6、**  自动化的插件配置。

**7、**  针对 application、properties 和 application、yml 的资源过滤，包括通过 profile 定义的不同环境的配置文件，例如 application-dev、properties 和 application-dev、yml。

总结就是打包用的


### [5、SpringBoot与SpringCloud 区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#5springboot与springcloud-区别)  


SpringBoot是快速开发的Spring框架，SpringCloud是完整的微服务框架，SpringCloud依赖于SpringBoot。


### [6、SpringBoot 中的 starter 到底是什么 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#6springboot-中的-starter-到底是什么-)  


首先，这个 Starter 并非什么新的技术点，基本上还是基于 Spring 已有功能来实现的。首先它提供了一个自动化配置类，一般命名为 XXXAutoConfiguration ，在这个配置类中通过条件注解来决定一个配置是否生效（条件注解就是 Spring 中原本就有的），然后它还会提供一系列的默认配置，也允许开发者根据实际情况自定义相关配置，然后通过类型安全的属性注入将这些配置属性注入进来，新注入的属性会代替掉默认属性。正因为如此，很多第三方框架，我们只需要引入依赖就可以直接使用了。当然，开发者也可以自定义 Starter


### [7、spring boot监听器流程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#7spring-boot监听器流程)  


**1、** 通过`app.addListeners`注册进入 2、初始化一个`SpringApplicationRunListeners`进行处理

**3、** 从`spring.factories`中读取监听器处理类`EventPublishingRunListener`

**4、** 通过`createSpringFactoriesInstances`创建监听器处理类实例

**5、** 调用监听器`listeners.starting()`的方法来启动。

**6、** 底层把事件处理交给`线程池`去处理


### [8、SpringBoot 支持哪些日志框架？推荐和默认的日志框架是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#8springboot-支持哪些日志框架推荐和默认的日志框架是哪个)  


SpringBoot 支持 Java Util Logging, Log4j2, Lockback 作为日志框架，如果你使用 Starters 启动器，SpringBoot 将使用 Logback 作为默认日志框架


### [9、什么是SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#9什么是springboot)  


多年来，随着新功能的增加，spring变得越来越复杂。只需访问https://spring.io/projects 页面，我们就会看到可以在我们的应用程序中使用的所有Spring项目的不同功能。如果必须启动一个新的Spring项目，我们必须添加构建路径或添加Maven依赖关系，配置应用程序服务器，添加spring配置。因此，开始一个新的spring项目需要很多努力，因为我们现在必须从头开始做所有事情。

SpringBoot是解决这个问题的方法。SpringBoot已经建立在现有spring框架之上。使用spring启动，我们避免了之前我们必须做的所有样板代码和配置。因此，SpringBoot可以帮助我们以最少的工作量，更加健壮地使用现有的Spring功能。


### [10、SpringBoot常用的starter有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#10springboot常用的starter有哪些)  


**1、** spring-boot-starter-web 嵌入tomcat和web开发需要servlet与jsp支持

**2、** spring-boot-starter-data-jpa 数据库支持

**3、** spring-boot-starter-data-Redis Redis数据库支持

**4、** spring-boot-starter-data-solr solr支持

**5、** mybatis-spring-boot-starter 第三方的mybatis集成starter


### [11、SpringBoot的启动器有哪几种?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#11springboot的启动器有哪几种)  

### [12、SpringBoot 有哪几种读取配置的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#12springboot-有哪几种读取配置的方式)  

### [13、什么是 JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#13什么是-javaconfig)  

### [14、什么是YAML？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#14什么是yaml)  

### [15、什么是 Spring Batch？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#15什么是-spring-batch)  

### [16、SpringBoot 中如何实现定时任务 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#16springboot-中如何实现定时任务-)  

### [17、如何在自定义端口上运行 SpringBoot 应用程序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#17如何在自定义端口上运行-springboot-应用程序)  

### [18、SpringBoot 的自动配置是如何实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#18springboot-的自动配置是如何实现的)  

### [19、SpringBoot 支持哪些日志框架？推荐和默认的日志框架是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#19springboot-支持哪些日志框架推荐和默认的日志框架是哪个)  

### [20、什么是 FreeMarker 模板？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#20什么是-freemarker-模板)  

### [21、在 Spring Initializer 中，如何改变一个项目的包名字？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#21在-spring-initializer-中如何改变一个项目的包名字)  

### [22、前后端分离，如何维护接口文档 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#22前后端分离如何维护接口文档-)  

### [23、如何重新加载 SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#23如何重新加载-springboot上的更改而无需重新启动服务器)  

### [24、开启 SpringBoot 特性有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#24开启-springboot-特性有哪几种方式)  

### [25、如何使用 SpringBoot 部署到不同的服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#25如何使用-springboot-部署到不同的服务器)  

### [26、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#26运行-springboot-有哪几种方式)  

### [27、什么是 SpringBoot Stater ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#27什么是-springboot-stater-)  

### [28、SpringBoot的自动配置原理是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#28springboot的自动配置原理是什么)  

### [29、什么是YAML?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#29什么是yaml)  

### [30、SpringBoot中的监视器是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#30springboot中的监视器是什么)  

### [31、什么是SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot高级面试题汇总及答案（2021年SpringBoot面试题及答案大全）.md#31什么是springboot)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
