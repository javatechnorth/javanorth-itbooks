# Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是Spring的依赖注入？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#1什么是spring的依赖注入)  


依赖注入，是IOC的一个方面，是个通常的概念，它有多种解释。这概念是说你不用创建对象，而只需要描述它如何被创建。你不在代码里直接组装你的组件和服务，但是要在配置文件里描述哪些组件需要哪些服务，之后一个容器（IOC容器）负责把他们组装起来。


### [2、什么是 AOP？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#2什么是-aop)  


AOP(Aspect-Oriented Programming), 即 面向切面编程, 它与 OOP( Object-Oriented Programming, 面向对象编程) 相辅相成, 提供了与 OOP 不同的抽象软件结构的视角、在 OOP 中, 我们以类(class)作为我们的基本单元, 而 AOP 中的基本单元是 Aspect(切面)


### [3、什么是有界上下文？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#3什么是有界上下文)  


有界上下文是域驱动设计的核心模式。DDD战略设计部门的重点是处理大型模型和团队。DDD通过将大型模型划分为不同的有界上下文并明确其相互关系来处理大型模型。


### [4、列举 Spring Framework 的优点。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#4列举-spring-framework-的优点。)  


**1、** 由于 Spring Frameworks 的分层架构，用户可以自由选择自己需要的组件。

**2、** Spring Framework 支持 POJO(Plain Old Java Object) 编程，从而具备持续集成和可测试性。

**3、** 由于依赖注入和控制反转，JDBC 得以简化。

**4、** 它是开源免费的。


### [5、什么是Feign？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#5什么是feign)  


**1、** Feign 是一个声明web服务客户端，这使得编写web服务客户端更容易

**2、** 他将我们需要调用的服务方法定义成抽象方法保存在本地就可以了，不需要自己构建Http请求了，直接调用接口就行了，不过要注意，调用方法要和本地抽象方法的签名完全一致。


### [6、什么是 CSRF 攻击？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#6什么是-csrf-攻击)  


CSRF 代表跨站请求伪造。这是一种攻击，迫使最终用户在当前通过身份验证的Web 应用程序上执行不需要的操作。CSRF 攻击专门针对状态改变请求，而不是数据窃取，因为攻击者无法查看对伪造请求的响应。


### [7、哪种依赖注入方式你建议使用，构造器注入，还是 Setter方法注入？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#7哪种依赖注入方式你建议使用构造器注入还是-setter方法注入)  


你两种依赖方式都可以使用，构造器注入和Setter方法注入。最好的解决方案是用构造器参数实现强制依赖，setter方法实现可选依赖。


### [8、path=”users”, collectionResourceRel=”users” 如何与 Spring Data Rest 一起使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#8path=users,-collectionresourcerel=users-如何与-spring-data-rest-一起使用)  


path- 这个资源要导出的路径段。

collectionResourceRel- 生成指向集合资源的链接时使用的 rel 值。在生成 HATEOAS 链接时使用。


### [9、Spring Cloud Zookeeper](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#9spring-cloud-zookeeper)  


SpringCloud支持三种注册方式Eureka， Consul(go语言编写)，zookeeper

Spring Cloud Zookeeper是基于Apache Zookeeper的服务治理组件。


### [10、[@Autowired ](/Autowired ) 注解有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#10[@autowired-]/autowired--注解有什么用)  


[@Autowired ](/Autowired ) 可以更准确地控制应该在何处以及如何进行自动装配。此注解用于在 setter 方法，构造函数，具有任意名称或多个参数的属性或方法上自动装配 bean。默认情况下，它是类型驱动的注入。

```
public class Employee {
    private String name;
    @Autowired
    public void setName(String name) {
        this.name=name;
    }
    public string getName(){
        return name;
    }
}
```


### [11、spring boot 核心的两个配置文件：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#11spring-boot-核心的两个配置文件：)  

### [12、什么是 AOP什么是目标对象?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#12什么是-aop什么是目标对象)  

### [13、解释Spring框架中bean的生命周期。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#13解释spring框架中bean的生命周期。)  

### [14、如何通过HibernateDaoSupport将Spring和Hibernate结合起来？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#14如何通过hibernatedaosupport将spring和hibernate结合起来)  

### [15、康威定律是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#15康威定律是什么)  

### [16、Docker的目的是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#16docker的目的是什么)  

### [17、Zuul与Nginx有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#17zuul与nginx有什么区别)  

### [18、什么是基于注解的容器配置](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#18什么是基于注解的容器配置)  

### [19、什么是Spring引导的执行器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#19什么是spring引导的执行器)  

### [20、开启 SpringBoot 特性有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#20开启-springboot-特性有哪几种方式)  

### [21、spring bean 容器的生命周期是什么样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#21spring-bean-容器的生命周期是什么样的)  

### [22、什么是Semantic监控？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#22什么是semantic监控)  

### [23、保护 SpringBoot 应用有哪些方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#23保护-springboot-应用有哪些方法)  

### [24、SpringBoot 中的 starter 到底是什么 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#24springboot-中的-starter-到底是什么-)  

### [25、SpringBoot有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#25springboot有哪些优点)  

### [26、自动装配有哪些方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#26自动装配有哪些方式)  

### [27、开启 SpringBoot 特性有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#27开启-springboot-特性有哪几种方式)  

### [28、什么是 Spring IOC 容器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#28什么是-spring-ioc-容器)  

### [29、什么是 AOP 连接点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#29什么是-aop-连接点)  

### [30、SpringBoot 有哪几种读取配置的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#30springboot-有哪几种读取配置的方式)  

### [31、21、在Spring MVC应用程序中使用WebMvcTest注释有什么用处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题及答案大全（2021年Spring面试题答案大汇总）.md#3121在spring-mvc应用程序中使用webmvctest注释有什么用处)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
