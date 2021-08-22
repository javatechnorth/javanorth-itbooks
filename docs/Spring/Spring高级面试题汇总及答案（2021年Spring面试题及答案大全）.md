# Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何重新加载SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#1如何重新加载springboot上的更改而无需重新启动服务器)  


这可以使用DEV工具来实现。通过这种依赖关系，您可以节省任何更改，嵌入式tomcat将重新启动。

SpringBoot有一个开发工具（DevTools）模块，它有助于提高开发人员的生产力。Java开发人员面临的一个主要挑战是将文件更改自动部署到服务器并自动重启服务器。

开发人员可以重新加载SpringBoot上的更改，而无需重新启动服务器。这将消除每次手动部署更改的需要。SpringBoot在它的第一个版本时没有这个功能。

这是开发人员最需要的功能。DevTools模块完全满足开发人员的需求。该模块将在生产环境中被禁用。它还提供H2数据库控制台以更好地测试应用程序。


### [2、能否举一个例子来解释更多 Staters 的内容？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#2能否举一个例子来解释更多-staters-的内容)  


让我们来思考一个 Stater 的例子 -SpringBoot Stater Web。

如果你想开发一个 web 应用程序或者是公开 REST 服务的应用程序。SpringBoot Start Web 是首选。让我们使用 Spring Initializr 创建一个 SpringBoot Start Web 的快速项目。

**依赖项可以被分为：**

**1、** Spring - core，beans，context，aop

**2、** Web MVC - （Spring MVC）

**3、** Jackson - for JSON Binding

**4、** Validation - Hibernate,Validation API

**5、** Enbedded Servlet Container - Tomcat

**6、** Logging - logback,slf4j

任何经典的 Web 应用程序都会使用所有这些依赖项。SpringBoot Starter Web 预先打包了这些依赖项。

作为一个开发者，我不需要再担心这些依赖项和它们的兼容版本。


### [3、微服务限流 http限流：我们使⽤nginx的limitzone来完成：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#3微服务限流-http限流：我们使⽤nginx的limitzone来完成：)  


```
//这个表示使⽤ip进⾏限流 zone名称为req_one 分配了10m 空间使⽤漏桶算法 每秒钟允许1个请求
limit_req_zone $binary_remote_addr zone=req_one:10m rate=1r/s; //这边burst表示可以瞬间超过20个请求 由于没有noDelay参数因此需要排队 如果超过这20个那么直接返回503
limit_req zone=req_three burst=20;
```


### [4、Spring MVC里面拦截器是怎么写的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#4spring-mvc里面拦截器是怎么写的)  


有两种写法,一种是实现HandlerInterceptor接口，另外一种是继承适配器类，接着在接口方法当中，实现处理逻辑；然后在Spring MVC的配置文件中配置拦截器即可：

```
<!-- 配置Spring MVC的拦截器 -->
< mvc: interceptors >
<!-- 配置一个拦截器的Bean就可以了 默认是对所有请求都拦截 -->
< bean id = "myInterceptor"
class = "com.zwp.action.MyHandlerInterceptor" > < /bean>
<!-- 只针对部分请求拦截 -->
<mvc:interceptor>
   <mvc:mapping path="/modelMap.do " />
   <bean class="
com.
zwp.action.MyHandlerInterceptorAdapter " />
</mvc:interceptor>
</mvc:interceptors>
```


### [5、什么是无所不在的语言？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#5什么是无所不在的语言)  


如果您必须定义泛在语言（UL），那么它是特定域的开发人员和用户使用的通用语言，通过该语言可以轻松解释域。

无处不在的语言必须非常清晰，以便它将所有团队成员放在同一页面上，并以机器可以理解的方式进行翻译。


### [6、[@Required ](/Required ) 注解有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#6[@required-]/required--注解有什么用)  


[@Required ](/Required ) 应用于 bean 属性 setter 方法。 此注解仅指示必须在配置时使用 bean 定义中的显式属性值或使用自动装配填充受影响的 bean 属性。 如果尚未填充受影响的 bean 属性，则容器将抛出 BeanInitializationException。


### [7、Spring、SpringBoot、SpringMVC的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#7springspringbootspringmvc的区别)  


**1、** Spring框架就像一个家族，有众多衍生产品，例如boot、mvc、jpa等等。但他们的基础都是Spring的ioc、aop。ioc提供了依赖注入的容器，aop解决了面向横切面编程，然后在此两者的基础上实现了其它延伸产品的高级功能；

**2、** springMVC是基于Servlet的一个MVC框架主要解决WEB开发的问题；

**3、** 为了简化开发的使用，从而创造性地推出了SpringBoot框架，默认优于配置


### [8、微服务的优点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#8微服务的优点)  


**单⼀职责：**

每个微服务仅负责⾃⼰业务领域的功能；

**⾃治：**

⼀个微服务就是⼀个独⽴的实体，它可以独⽴部署、升级，服务与服务之间通过REST等形式的标准接⼝进⾏通信，并且⼀个微服务实例可以被替换成另⼀种实现，⽽对其它的微服务不产⽣影响。

**逻辑清晰：**

微服务单⼀职责特性使微服务看起来逻辑清晰，易于维护。

**简化部署：**

单系统中修改⼀处需要部署整个系统，⽽微服务中修改⼀处可单独部署⼀个服务

**可扩展：**

应对系统业务增⻓的⽅法通常采⽤横向（Scale out）或纵向（Scale up）的⽅向进⾏扩展。分布式系统中通常要采⽤Scale out的⽅式进⾏扩展。

**灵活组合：**

**技术异构：**

不同的服务之间，可以根据⾃⼰的业务特点选择不通的技术架构，如数据库等。


### [9、我们如何在测试中消除非决定论？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#9我们如何在测试中消除非决定论)  


非确定性测试（NDT）基本上是不可靠的测试。所以，有时可能会发生它们通过，显然有时它们也可能会失败。当它们失败时，它们会重新运行通过。

从测试中删除非确定性的一些方法如下：

**1、**   隔离

**2、**   异步

**3、**   远程服务

**4、**   隔离

**5、**   时间

**6、**   资源泄漏


### [10、什么是 JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#10什么是-javaconfig)  


**1、** `面向对象的配置`。由于配置被定义为 JavaConfig 中的类，因此用户可以充分利用 Java 中的面向对象功能。一个配置类可以继承另一个，重写它的[@Bean ](/Bean ) 方法等。

**2、** `减少或消除 XML 配置`。基于依赖注入原则的外化配置的好处已被证明。但是，许多开发人员不希望在 XML 和 Java 之间来回切换。JavaConfig 为开发人员提供了一种纯 Java 方法来配置与 XML 配置概念相似的 Spring 容器。从技术角度来讲，只使用 JavaConfig 配置类来配置容器是可行的，但实际上很多人认为将JavaConfig 与 XML 混合匹配是理想的。

**3、** `类型安全和重构友好`。JavaConfig 提供了一种类型安全的方法来配置 Spring容器。由于 Java 5.0 对泛型的支持，现在可以按类型而不是按名称检索 bean，不需要任何强制转换或基于字符串的查找。


### [11、解释Spring支持的几种bean的作用域。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#11解释spring支持的几种bean的作用域。)  

### [12、SpringBoot需要独立的容器运行？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#12springboot需要独立的容器运行)  

### [13、是否可以在SpringBoot中覆盖或替换嵌入式Tomcat？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#13是否可以在springboot中覆盖或替换嵌入式tomcat)  

### [14、Eureka和ZooKeeper都可以提供服务注册与发现的功能,请说说两个的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#14eureka和zookeeper都可以提供服务注册与发现的功能,请说说两个的区别)  

### [15、使用Spring Cloud有什么优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#15使用spring-cloud有什么优势)  

### [16、使用Spring通过什么方式访问Hibernate?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#16使用spring通过什么方式访问hibernate)  

### [17、SpringBoot 实现热部署有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#17springboot-实现热部署有哪几种方式)  

### [18、什么是 Spring 配置文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#18什么是-spring-配置文件)  

### [19、SpringBoot自动配置的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#19springboot自动配置的原理是什么)  

### [20、微服务设计的基础是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#20微服务设计的基础是什么)  

### [21、在 Spring中如何注入一个java集合？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#21在-spring中如何注入一个java集合)  

### [22、什么是Spring IOC 容器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#22什么是spring-ioc-容器)  

### [23、SpringBoot有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#23springboot有哪些优点)  

### [24、如何给Spring 容器提供配置元数据?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#24如何给spring-容器提供配置元数据)  

### [25、@PathVariable和@RequestParam的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#25@pathvariable和@requestparam的区别)  

### [26、Zookeeper如何 保证CP](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#26zookeeper如何-保证cp)  

### [27、spring 中有多少种 IOC 容器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#27spring-中有多少种-ioc-容器)  

### [28、springcloud和dubbo有哪些区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#28springcloud和dubbo有哪些区别)  

### [29、区分构造函数注入和 setter 注入。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#29区分构造函数注入和-setter-注入。)  

### [30、Spring Cloud抛弃了Dubbo 的RPC通信，采用的是基于HTTP的REST方式。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#30spring-cloud抛弃了dubbo-的rpc通信采用的是基于http的rest方式。)  

### [31、什么是 Spring Batch？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题汇总及答案（2021年Spring面试题及答案大全）.md#31什么是-spring-batch)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
