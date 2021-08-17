# Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#1springboot-的核心注解是哪个它主要由哪几个注解组成的)  


启动类上面的注解是@SpringBootApplication，它也是 SpringBoot 的核心注解，主要组合包含了以下 3 个注解：

@SpringBootConfiguration：组合了 [@Configuration ](/Configuration ) 注解，实现配置文件的功能。

@EnableAutoConfiguration：打开自动配置的功能，也可以关闭某个自动配置的选项， 例如：`java 如关闭数据源自动配置功能： @SpringBootApplication(exclude = { DataSourceAutoConfiguration、class })。`

@ComponentScan：Spring组件扫描。


### [2、SpringBoot 2、X 有什么新特性？与 1、X 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#2springboot-2x-有什么新特性与-1x-有什么区别)  


**1、**  配置变更

**2、**  JDK 版本升级

**3、**  第三方类库升级

**4、**  响应式 Spring 编程支持

**5、**  HTTP/2 支持

**6、**  配置属性绑定

**7、**  更多改进与加强


### [3、SpringBoot如何配置log4j？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#3springboot如何配置log4j)  


在引用log4j之前，需要先排除项目创建时候带的日志，因为那个是Logback，然后再引入log4j的依赖，引入依赖之后，去src/main/resources目录下的log4j-spring.properties配置文件，就可以开始对应用的日志进行配置使用。


### [4、spring 中有多少种 IOC 容器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#4spring-中有多少种-ioc-容器)  


BeanFactory - BeanFactory 就像一个包含 bean 集合的工厂类。它会在客户端要求时实例化 bean。

ApplicationContext - ApplicationContext 接口扩展了 BeanFactory 接口。它在 BeanFactory 基础上提供了一些额外的功能。


### [5、SpringCloud由什么组成](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#5springcloud由什么组成)  


这就有很多了，我讲几个开发中最重要的

**1、** Spring Cloud Eureka：服务注册与发现

**2、** Spring Cloud Zuul：服务网关

**3、** Spring Cloud Ribbon：客户端负载均衡

**4、** Spring Cloud Feign：声明性的Web服务客户端

**5、** Spring Cloud Hystrix：断路器

**6、** Spring Cloud Config：分布式统一配置管理

**7、** 等20几个框架，开源一直在更新


### [6、什么是bean装配?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#6什么是bean装配)  


装配，或bean 装配是指在Spring 容器中把bean组装到一起，前提是容器需要知道bean的依赖关系，如何通过依赖注入来把它们装配到一起。


### [7、[@RequestMapping ](/RequestMapping ) 注解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#7[@requestmapping-]/requestmapping--注解)  


该注解是用来映射一个URL到一个类或一个特定的方处理法上。



### [8、什么是依赖注入？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#8什么是依赖注入)  


在依赖注入中，您不必创建对象，但必须描述如何创建它们。 您不是直接在代码中将组件和服务连接在一起，而是描述配置文件中哪些组件需要哪些服务。 由 IoC 容器将它们装配在一起。


### [9、什么是耦合和凝聚力？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#9什么是耦合和凝聚力)  


组件之间依赖关系强度的度量被认为是**耦合**。一个好的设计总是被认为具有**高内聚力和低耦合性**。 面试官经常会问起凝聚力。它也是另一个测量单位。更像是一个模块内部的元素保持结合的程度。 必须记住，设计微服务的一个重要关键是低耦合和高内聚的组合。当低耦合时，服务对其他服务的依赖很少。这样可以保持服务的完整性。在高内聚性中，将所有相关逻辑保存在服务中成为可能。否则，服务将尝试彼此通信，从而影响整体性能。


### [10、[@Required ](/Required ) 注解有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#10[@required-]/required--注解有什么用)  


[@Required ](/Required ) 应用于 bean 属性 setter 方法。此注解仅指示必须在配置时使用 bean 定义中的显式属性值或使用自动装配填充受影响的 bean 属性。如果尚未填充受影响的 bean 属性，则容器将抛出 BeanInitializationException。

示例：

```
public class Employee {
    private String name;
    @Required
    public void setName(String name){
        this.name=name;
    }
    public string getName(){
        return name;
    }
}
```


### [11、spring boot 核心配置文件是什么？bootstrap.properties 和 application.properties 有何区别 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#11spring-boot-核心配置文件是什么bootstrapproperties-和-applicationproperties-有何区别-)  

### [12、您使用了哪些 starter maven 依赖项？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#12您使用了哪些-starter-maven-依赖项)  

### [13、SpringData 项目所支持的关系数据存储技术：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#13springdata-项目所支持的关系数据存储技术：)  

### [14、什么是Spring Cloud？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#14什么是spring-cloud)  

### [15、Spring Cloud Bus](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#15spring-cloud-bus)  

### [16、什么是 AOP 目标对象?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#16什么是-aop-目标对象)  

### [17、什么是JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#17什么是javaconfig)  

### [18、什么是 SpringBoot 启动类注解：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#18什么是-springboot-启动类注解：)  

### [19、什么是Netflix Feign？它的优点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#19什么是netflix-feign它的优点是什么)  

### [20、什么是耦合？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#20什么是耦合)  

### [21、什么是 AOP 通知](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#21什么是-aop-通知)  

### [22、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#22运行-springboot-有哪几种方式)  

### [23、Spring支持的事务管理类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#23spring支持的事务管理类型)  

### [24、SpringBoot 自动配置原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#24springboot-自动配置原理是什么)  

### [25、您对微服务架构中的语义监控有何了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#25您对微服务架构中的语义监控有何了解)  

### [26、服务注册和发现是什么意思？Spring Cloud如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#26服务注册和发现是什么意思spring-cloud如何实现)  

### [27、SpringBoot 的配置文件有哪几种格式？它们有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#27springboot-的配置文件有哪几种格式它们有什么区别)  

### [28、为什么需要学习Spring Cloud](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#28为什么需要学习spring-cloud)  

### [29、spring boot扫描流程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#29spring-boot扫描流程)  

### [30、你所知道微服务的技术栈有哪些？列举一二](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#30你所知道微服务的技术栈有哪些列举一二)  

### [31、使⽤中碰到的坑](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题附答案汇总（2021年Spring面试题及答案大全）.md#31使⽤中碰到的坑)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
