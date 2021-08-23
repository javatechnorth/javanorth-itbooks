# Spring中级面试题大全带答案（2021年Spring面试题及答案整理）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、双因素身份验证的凭据类型有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#1双因素身份验证的凭据类型有哪些)  


这三种凭证是：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_15.png#alt=img%5C_15.png)

图12： 双因素认证的证书类型 – 微服务面试问题


### [2、康威定律是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#2康威定律是什么)  


康威定律指出，“设计系统的组织，其产生的设计等同于组织之内、组织之间的沟通结构。” 面试官可能会问反微服务面试问题，比如康威定律与微服务的关系。一些松散耦合的api形成了微服务的体系结构。这种结构非常适合小团队实现自治组件的方式。这种体系结构使组织在重组其工作流程时更加灵活。


### [3、spring 提供了哪些配置方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#3spring-提供了哪些配置方式)  


基于 xml 配置

bean 所需的依赖项和服务在 XML 格式的配置文件中指定。这些配置文件通常包含许多 bean 定义和特定于应用程序的配置选项。它们通常以 bean 标签开头。例如：

```
<bean id="studentbean" class="org.edureka.firstSpring.StudentBean">
 <property name="name" value="Edureka"></property>
</bean>
```

基于注解配置

您可以通过在相关的类，方法或字段声明上使用注解，将 bean 配置为组件类本身，而不是使用 XML 来描述 bean 装配。默认情况下，Spring 容器中未打开注解装配。因此，您需要在使用它之前在 Spring 配置文件中启用它。例如：

```
<beans>
<context:annotation-config/>
<!-- bean definitions go here -->
</beans>
```

基于 Java API 配置

Spring 的 Java 配置是通过使用 [@Bean ](/Bean ) 和 [@Configuration ](/Configuration ) 来实现。

**1、**   [@Bean ](/Bean ) 注解扮演与 `<bean/>` 元素相同的角色。

**2、**   [@Configuration ](/Configuration ) 类允许通过简单地调用同一个类中的其他 [@Bean ](/Bean ) 方法来定义 bean 间依赖关系。

例如：

```
@Configuration
public class StudentConfig {
    @Bean
    public StudentBean myStudent() {
        return new StudentBean();
    }
}
```


### [4、spring cloud 断路器的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#4spring-cloud-断路器的作用是什么)  


在分布式架构中，断路器模式的作用也是类似的，当某个服务单元发生故障（类似用电器发生短路）之后，通过断路器的故障监控（类似熔断保险丝），向调用方返回一个错误响应，而不是长时间的等待。这样就不会使得线程因调用故障服务被长时间占用不释放，避免了故障在分布式系统中的蔓延。


### [5、什么是SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#5什么是springboot)  


Spring boot是微服务面试问题的主要话题。 随着新功能的加入，Spring变得越来越复杂。无论何时启动新项目，都必须添加新的构建路径或Maven依赖项。简而言之，你需要从头开始做每件事。SpringBoot是一种帮助您避免所有代码配置的解决方案。


### [6、如何在自定义端口上运行 SpringBoot应用程序?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#6如何在自定义端口上运行-springboot应用程序)  


在 `application.properties`中指定端口`serverport=8090`。


### [7、我们如何连接一个像 MySQL 或者Orcale 一样的外部数据库？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#7我们如何连接一个像-mysql-或者orcale-一样的外部数据库)  


让我们以 MySQL 为例来思考这个问题：

**第一步** - 把 MySQL 连接器的依赖项添加至 pom.xml

**第二步** - 从 pom.xml 中移除 H2 的依赖项

或者至少把它作为测试的范围。

**第三步** - 安装你的 MySQL 数据库

更多的来看看这里 -[https://github.com/in28minutes/jpa-with-hibernate#installing-and-setting-up-MySQL](https://github.com/in28minutes/jpa-with-hibernate#installing-and-setting-up-MySQL)

**第四步** - 配置你的 MySQL 数据库连接

配置 application.properties

```
spring.jpa.hibernate.ddl-auto=none spring.datasource.url=jdbc:MySQL://localhost:3306/todo_example
spring.datasource.username=todouser spring.datasource.password=YOUR_PASSWORD
```

**第五步** - 重新启动，你就准备好了！

就是这么简单！


### [8、运行 SpringBoot 有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#8运行-springboot-有哪几种方式)  


**1、**  打包用命令或者放到容器中运行

**2、**  用 Maven/ Gradle 插件运行

**3、**  直接执行 main 方法运行


### [9、SpringBoot 打成的 jar 和普通的 jar 有什么区别 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#9springboot-打成的-jar-和普通的-jar-有什么区别-)  


SpringBoot 项目最终打包成的 jar 是可执行 jar ，这种 jar 可以直接通过 java -jar xxx.jar 命令来运行，这种 jar 不可以作为普通的 jar 被其他项目依赖，即使依赖了也无法使用其中的类。

SpringBoot 的 jar 无法被其他项目依赖，主要还是他和普通 jar 的结构不同。普通的 jar 包，解压后直接就是包名，包里就是我们的代码，而 SpringBoot 打包成的可执行 jar 解压后，在 \BOOT-INF\classes 目录下才是我们的代码，因此无法被直接引用。如果非要引用，可以在 pom.xml 文件中增加配置，将 SpringBoot 项目打包成两个 jar ，一个可执行，一个可引用。


### [10、如何在 SpringBoot中禁用 Actuator端点安全性?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#10如何在-springboot中禁用-actuator端点安全性)  


默认情况下，所有敏感的HTTP端点都是安全的，只有具有 `http ACTUATOR`角色的用户才能访问它们。安全性是使用标准的 `httpservletrequest. isuserinrole..isusernrole`方法实施的。可以使用 `management. security. enabled= false`来禁用安全性。只有在执行机构端点在防火墙后访问时，才建议禁用安全性。


### [11、微服务有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#11微服务有什么特点)  

### [12、SpringBoot支持哪些嵌入式容器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#12springboot支持哪些嵌入式容器)  

### [13、bootstrap.yml和application.yml有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#13bootstrapyml和applicationyml有什么区别)  

### [14、springcloud如何实现服务的注册?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#14springcloud如何实现服务的注册)  

### [15、SpringBoot微服务中如何实现 session 共享 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#15springboot微服务中如何实现-session-共享-)  

### [16、自动装配有什么局限？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#16自动装配有什么局限)  

### [17、如何重新加载 SpringBoot 上的更改，而无需重新启动服务器？SpringBoot项目如何热部署？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#17如何重新加载-springboot-上的更改而无需重新启动服务器springboot项目如何热部署)  

### [18、SpringBoot、Spring MVC 和 Spring 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#18springbootspring-mvc-和-spring-有什么区别)  

### [19、怎么设计无状态服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#19怎么设计无状态服务)  

### [20、什么是 JavaConfig？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#20什么是-javaconfig)  

### [21、指出在 spring aop 中 concern 和 cross-cutting concern 的不同之处。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#21指出在-spring-aop-中-concern-和-cross-cutting-concern-的不同之处。)  

### [22、spring-boot-starter-parent有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#22spring-boot-starter-parent有什么用)  

### [23、在Spring MVC应用程序中使用WebMvcTest注释有什么用处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#23在spring-mvc应用程序中使用webmvctest注释有什么用处)  

### [24、spring cloud 和dubbo区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#24spring-cloud-和dubbo区别)  

### [25、微服务中如何实现 session 共享 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#25微服务中如何实现-session-共享-)  

### [26、什么是 Spring Data？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#26什么是-spring-data)  

### [27、既然Nginx可以实现网关？为什么还需要使用Zuul框架](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#27既然nginx可以实现网关为什么还需要使用zuul框架)  

### [28、PACT如何运作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#28pact如何运作)  

### [29、SpringCloud主要项目](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#29springcloud主要项目)  

### [30、SpringBoot 的核心注解是哪个？它主要由哪几个注解组成的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#30springboot-的核心注解是哪个它主要由哪几个注解组成的)  

### [31、开启SpringBoot特性有哪几种方式？（创建SpringBoot项目的两种方式）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring中级面试题大全带答案（2021年Spring面试题及答案整理）.md#31开启springboot特性有哪几种方式创建springboot项目的两种方式)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
