# SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）

SpringBoot面试题及答案【最新版】SpringBoot高级面试题大全(2021版)，发现网上很多SpringBoot面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringBoot面试题大全，SpringBoot面试题大汇总，有大量经典的SpringBoot面试题以及答案，包含SpringBoot语言常见面试题、SpringBoot工程师高级面试题及一些大厂SpringBoot开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringBoot面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringBoot面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Spring Cache 三种常用的缓存注解和意义？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#1spring-cache-三种常用的缓存注解和意义)  


**1、** [@Cacheable ](/Cacheable ) ，用来声明方法是可缓存，将结果存储到缓存中以便后续使用相同参数调用时不需执行实际的方法，直接从缓存中取值。

**2、** @CachePut，使用 [@CachePut ](/CachePut ) 标注的方法在执行前，不会去检查缓存中是否存在之前执行过的结果，而是每次都会执行该方法，并将执行结果以键值对的形式存入指定的缓存中。

**3、** @CacheEvict，是用来标注在需要清除缓存元素的方法或类上的，当标记在一个类上时表示其中所有的方法的执行都会触发缓存的清除操作。


### [2、SpringBoot有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#2springboot有哪些优点)  


减少开发，测试时间和努力。

使用JavaConfig有助于避免使用XML。

避免大量的Maven导入和各种版本冲突。

提供意见发展方法。

通过提供默认值快速开始开发。

没有单独的Web服务器需要。这意味着你不再需要启动Tomcat，Glassfish或其他任何东西。

需要更少的配置 因为没有web.xml文件。只需添加用@ Configuration注释的类，然后添加用@Bean注释的方法，Spring将自动加载对象并像以前一样对其进行管理。您甚至可以将@Autowired添加到bean方法中，以使Spring自动装入需要的依赖关系中。基于环境的配置 使用这些属性，您可以将您正在使用的环境传递到应用程序：-Dspring.profiles.active = {enviornment}。在加载主应用程序属性文件后，Spring将在（application{environment} .properties）中加载后续的应用程序属性文件。


### [3、什么是CSRF攻击？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#3什么是csrf攻击)  


CSRF代表跨站请求伪造。这是一种攻击，迫使最终用户在当前通过身份验证的Web应用程序上执行不需要的操作。CSRF攻击专门针对状态改变请求，而不是数据窃取，因为攻击者无法查看对伪造请求的响应。


### [4、SpringBoot 2.X 有什么新特性？与 1.X 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#4springboot-2x-有什么新特性与-1x-有什么区别)  


**1、** 配置变更

**2、** JDK 版本升级

**3、** 第三方类库升级

**4、** 响应式 Spring 编程支持

**5、** HTTP/2 支持

**6、** 配置属性绑定

**7、** 更多改进与加强…


### [5、你如何理解 SpringBoot 配置加载顺序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#5你如何理解-springboot-配置加载顺序)  


在 SpringBoot 里面，可以使用以下几种方式来加载配置。

**1、** properties文件；

**2、** YAML文件；

**3、** 系统环境变量；

**4、** 命令行参数；


### [6、SpringBoot的缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#6springboot的缺点)  


我觉得是为难人，SpringBoot在目前我觉得没有什么缺点，非要找一个出来我觉得就是

由于不用自己做的配置，报错时很难定位。


### [7、微服务中如何实现 session 共享 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#7微服务中如何实现-session-共享-)  


在微服务中，一个完整的项目被拆分成多个不相同的独立的服务，各个服务独立部署在不同的服务器上，各自的 session 被从物理空间上隔离开了，但是经常，我们需要在不同微服务之间共享 session ，常见的方案就是 Spring Session + Redis 来实现 session 共享。将所有微服务的 session 统一保存在 Redis 上，当各个微服务对 session 有相关的读写操作时，都去操作 Redis 上的 session 。这样就实现了 session 共享，Spring Session 基于 Spring 中的代理过滤器实现，使得 session 的同步操作对开发人员而言是透明的，非常简便。


### [8、SpringBoot 是否可以使用 XML 配置 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#8springboot-是否可以使用-xml-配置-)  


SpringBoot 推荐使用 Java 配置而非 XML 配置，但是 SpringBoot 中也可以使用 XML 配置，通过 [@ImportResource ](/ImportResource ) 注解可以引入一个 XML 配置。


### [9、什么是 JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#9什么是-javaconfig)  


Spring JavaConfig 是 Spring 社区的产品，它提供了配置 Spring IoC 容器的纯Java 方法。因此它有助于避免使用 XML 配置。使用 JavaConfig 的优点在于：

**1、** 面向对象的配置。由于配置被定义为 JavaConfig 中的类，因此用户可以充分利用 Java 中的面向对象功能。一个配置类可以继承另一个，重写它的[@Bean ](/Bean ) 方法等。

**2、** 减少或消除 XML 配置。基于依赖注入原则的外化配置的好处已被证明。但是，许多开发人员不希望在 XML 和 Java 之间来回切换。JavaConfig 为开发人员提供了一种纯 Java 方法来配置与 XML 配置概念相似的 Spring 容器。从技术角度来讲，只使用 JavaConfig 配置类来配置容器是可行的，但实际上很多人认为将JavaConfig 与 XML 混合匹配是理想的。

**3、** 类型安全和重构友好。JavaConfig 提供了一种类型安全的方法来配置 Spring容器。由于 Java 5.0 对泛型的支持，现在可以按类型而不是按名称检索 bean，不需要任何强制转换或基于字符串的查找。


### [10、各服务之间通信，对Restful和Rpc这2种方式如何做选择？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#10各服务之间通信对restful和rpc这2种方式如何做选择)  


在传统的SOA治理中，使用rpc的居多；Spring Cloud默认使用restful进行服务之间的通讯。rpc通讯效率会比restful要高一些，但是对于大多数公司来讲，这点效率影响甚微。我建议使用restful这种方式，易于在不同语言实现的服务之间通讯。


### [11、SpringBoot运行项目的几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#11springboot运行项目的几种方式)  

### [12、什么是JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#12什么是javaconfig)  

### [13、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#13springboot-的核心注解是哪个它主要由哪几个注解组成的)  

### [14、SpringBoot 怎么用好自动配置，精髓:](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#14springboot-怎么用好自动配置精髓:)  

### [15、SpringBoot 的配置文件有哪几种格式？它们有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#15springboot-的配置文件有哪几种格式它们有什么区别)  

### [16、保护 SpringBoot 应用有哪些方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#16保护-springboot-应用有哪些方法)  

### [17、我们如何监视所有SpringBoot微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#17我们如何监视所有springboot微服务)  

### [18、如何重新加载SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#18如何重新加载springboot上的更改而无需重新启动服务器)  

### [19、什么是 Spring Profiles？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#19什么是-spring-profiles)  

### [20、SpringBoot、Spring MVC 和 Spring 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#20springbootspring-mvc-和-spring-有什么区别)  

### [21、保护 SpringBoot 应用有哪些方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#21保护-springboot-应用有哪些方法)  

### [22、SpringBoot自动配置的原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#22springboot自动配置的原理)  

### [23、SpringBoot Starter的工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#23springboot-starter的工作原理)  

### [24、如何在 SpringBoot 启动的时候运行一些特定的代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#24如何在-springboot-启动的时候运行一些特定的代码)  

### [25、YAML 配置的优势在哪里 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#25yaml-配置的优势在哪里-)  

### [26、如何使用 SpringBoot 实现全局异常处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#26如何使用-springboot-实现全局异常处理)  

### [27、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#27运行-springboot-有哪几种方式)  

### [28、Springboot 有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#28springboot-有哪些优点)  

### [29、如何重新加载 SpringBoot 上的更改，而无需重新启动服务器？SpringBoot项目如何热部署？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#29如何重新加载-springboot-上的更改而无需重新启动服务器springboot项目如何热部署)  

### [30、如何在 SpringBoot中禁用 Actuator端点安全性?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#30如何在-springboot中禁用-actuator端点安全性)  

### [31、@SpringBootApplication注释在内部有什么用处?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringBoot/SpringBoot面试题附答案汇总（2021年SpringBoot面试题及答案大全）.md#31@springbootapplication注释在内部有什么用处)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
