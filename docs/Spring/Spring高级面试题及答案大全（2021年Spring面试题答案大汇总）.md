# Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）

Spring面试题及答案【最新版】Spring高级面试题大全(2021版)，发现网上很多Spring面试题及答案整理都没有答案，所以花了很长时间搜集，本套Spring面试题大全，Spring面试题大汇总，有大量经典的Spring面试题以及答案，包含Spring语言常见面试题、Spring工程师高级面试题及一些大厂Spring开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Spring面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Spring面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何解决POST请求中文乱码问题，GET的又如何处理呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#1如何解决post请求中文乱码问题get的又如何处理呢)  


**解决post请求乱码问题：**

在web.xml中配置一个CharacterEncodingFilter过滤器，设置成utf-8；

```
<filter>
    <filter-name>CharacterEncodingFilter</filter-name>
    <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
    <init-param>
        <param-name>encoding</param-name>
        <param-value>utf-8</param-value>
    </init-param>
</filter>
<filter-mapping>
    <filter-name>CharacterEncodingFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
```

**get请求中文参数出现乱码解决方法有两个：**

修改tomcat配置文件添加编码与工程编码一致，如下：

```
<ConnectorURIEncoding="utf-8" connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>
```

**另外一种方法对参数进行重新编码：**

String userName = new String(request.getParamter(“userName”).getBytes(“ISO8859-1”),“utf-8”)

ISO8859-1是tomcat默认编码，需要将tomcat编码后的内容按utf-8编码。


### [2、@Component, @Controller, @Repository, [@Service ](/Service ) 有何区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#2@component,-@controller,-@repository,-[@service-]/service--有何区别)  


**1、** @Component： 这将 java 类标记为 bean。 它是任何 Spring 管理组件的通用构造型。 spring 的组件扫描机制现在可以将其拾取并将其拉入应用程序环境中。

**2、** @Controller： 这将一个类标记为 Spring Web MVC 控制器。 标有它的 Bean 会自动导入到 IoC 容器中。

**3、** @Service： 此注解是组件注解的特化。 它不会对 [@Component ](/Component ) 注解提供任何其他行为。 您可以在服务层类中使用 [@Service ](/Service ) 而不是 @Component，因为它以更好的方式指定了意图。

**4、** @Repository： 这个注解是具有类似用途和功能的 [@Component ](/Component ) 注解的特化。 它为 DAO 提供了额外的好处。 它将 DAO 导入 IoC 容器，并使未经检查的异常有资格转换为 Spring DataAccessException。


### [3、[@Qualifier ](/Qualifier ) 注解有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#3[@qualifier-]/qualifier--注解有什么用)  


当您创建多个相同类型的 bean 并希望仅使用属性装配其中一个 bean 时，您可以使用[@Qualifier ](/Qualifier ) 注解和 [@Autowired ](/Autowired ) 通过指定应该装配哪个确切的 bean 来消除歧义。

例如，这里我们分别有两个类，Employee 和 EmpAccount。在 EmpAccount 中，使用[@Qualifier ](/Qualifier ) 指定了必须装配 id 为 emp1 的 bean。

Employee.java

```
public class Employee {
    private String name;
    @Autowired
    public void setName(String name) {
        this.name=name;
    }
    public string getName() {
        return name;
    }
}
```

EmpAccount.java

```
public class EmpAccount {
    private Employee emp;

    @Autowired
    @Qualifier(emp1)
    public void showName() {
        System.out.println(“Employee name : ”+emp.getName);
    }
}
```


### [4、SpringBoot 自动配置原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#4springboot-自动配置原理)  


**1、** SpringBoot启动的时候加载主配置类，开启了自动配置功能 @EnableAutoConfiguration

**2、** @EnableAutoConfiguration 作用:

将类路径下 META-INF/spring.factories 里面配置的所有EnableAutoConfiguration的值加入到了容器中;

每一个这样的 xxxAutoConfiguration类都是容器中的一个组件，都加入到容器中;用他们来做自动配置;

**3、** 每一个自动配置类进行自动配置功能;

根据当前不同的条件判断，决定这个配置类是否生效；

**4、** 一但这个配置类生效;这个配置类就会给容器中添加各种组件;这些组件的属性是从对应的properties类中获取 的，这些类里面的每一个属性又是和配置文件绑定的;

**5、** 所有在配置文件中能配置的属性都是在xxxxProperties类中封装者‘;配置文件能配置什么就可以参照某个功 能对应的这个属性类


### [5、spring bean 容器的生命周期是什么样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#5spring-bean-容器的生命周期是什么样的)  


spring bean 容器的生命周期流程如下：

**1、** Spring 容器根据配置中的 bean 定义中实例化 bean。

**2、** Spring 使用依赖注入填充所有属性，如 bean 中所定义的配置。

**3、** 如果 bean 实现 BeanNameAware 接口，则工厂通过传递 bean 的 ID 来调用 setBeanName()。

**4、** 如果 bean 实现 BeanFactoryAware 接口，工厂通过传递自身的实例来调用 setBeanFactory()。

**5、** 如果存在与 bean 关联的任何 BeanPostProcessors，则调用 preProcessBeforeInitialization() 方法。

**6、** 如果为 bean 指定了 init 方法（ `<bean>` 的 init-method 属性），那么将调用它。

**7、** 最后，如果存在与 bean 关联的任何 BeanPostProcessors，则将调用 postProcessAfterInitialization() 方法。

**8、** 如果 bean 实现 DisposableBean 接口，当 spring 容器关闭时，会调用 destory()。

**9、** 如果为 bean 指定了 destroy 方法（ `<bean>` 的 destroy-method 属性），那么将调用它。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/02/img_3.png#alt=img%5C_3.png)


### [6、SpringBoot 实现热部署有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#6springboot-实现热部署有哪几种方式)  


主要有两种方式：

**1、** Spring Loaded

**2、** Spring-boot-devtools


### [7、Spring由哪些模块组成?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#7spring由哪些模块组成)  


**以下是Spring 框架的基本模块：**

**1、** Core module

**2、** Bean module

**3、** Context module

**4、** Expression Language module

**5、** JDBC module

**6、** ORM module

**7、** OXM module

**8、** Java Messaging Service(JMS) module

**9、** Transaction module

**10、** Web module

**11、** Web-Servlet module

**12、** Web-Struts module

**13、** Web-Portlet module


### [8、Spring IoC 的实现机制。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#8spring-ioc-的实现机制。)  


Spring 中的 IoC 的实现原理就是工厂模式加反射机制。

示例：

```
interface Fruit {
     public abstract void eat();
}
class Apple implements Fruit {
    public void eat(){
        System.out.println("Apple");
    }
}
class Orange implements Fruit {
    public void eat(){
        System.out.println("Orange");
    }
}
class Factory {
    public static Fruit getInstance(String ClassName) {
        Fruit f=null;
        try {
            f=(Fruit)Class.forName(ClassName).newInstance();
        } catch (Exception e) {
            e.printStackTrace();
        }
        return f;
    }
}
class Client {
    public static void main(String[] a) {
        Fruit f=Factory.getInstance("io.github.dunwu.spring.Apple");
        if(f!=null){
            f.eat();
        }
    }
}
```


### [9、使用 Spring 有哪些方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#9使用-spring-有哪些方式)  


**使用 Spring 有以下方式：**

**1、** 作为作为一个成熟的 Spring Web 应用程序。

**2、** 作为第三方 Web 框架，使用 Spring Frameworks 中间层。

**3、** 用于远程使用。

**4、** 作为企业级 Java Bean，它可以包装现有的 POJO（Plain Old Java Objects）。 Bean，它可以包装现有的 POJO（Plain Old Java Objects）。


### [10、什么是 Spring Cloud Bus？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#10什么是-spring-cloud-bus)  


**1、** Spring Cloud Bus就像一个分布式执行器，用于扩展的SpringBoot应用程序的配置文件，但也可以用作应用程序之间的通信通道。

**2、** Spring Cloud Bus 不能单独完成通信，需要配合MQ支持

**3、** Spring Cloud Bus一般是配合Spring Cloud Config做配置中心的

**4、** Springcloud config实时刷新也必须采用SpringCloud Bus消息总线


### [11、dubbo服务注册与发现原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#11dubbo服务注册与发现原理)  

### [12、Ribbon和Feign调用服务的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#12ribbon和feign调用服务的区别)  

### [13、SpringBoot性能如何优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#13springboot性能如何优化)  

### [14、你如何理解 SpringBoot 配置加载顺序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#14你如何理解-springboot-配置加载顺序)  

### [15、什么是基于注解的容器配置?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#15什么是基于注解的容器配置)  

### [16、Web，RESTful API在微服务中的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#16webrestful-api在微服务中的作用是什么)  

### [17、什么是 spring bean？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#17什么是-spring-bean)  

### [18、SpringBoot 中如何实现定时任务 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#18springboot-中如何实现定时任务-)  

### [19、什么是spring?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#19什么是spring)  

### [20、JPA 和 Hibernate 有哪些区别？JPA 可以支持动态 SQL 吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#20jpa-和-hibernate-有哪些区别jpa-可以支持动态-sql-吗)  

### [21、SpringBoot、Spring MVC 和 Spring 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#21springbootspring-mvc-和-spring-有什么区别)  

### [22、Spring Cloud 和dubbo区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#22spring-cloud-和dubbo区别)  

### [23、为什么人们会犹豫使用微服务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#23为什么人们会犹豫使用微服务)  

### [24、自动装配有哪些局限性 ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#24自动装配有哪些局限性-)  

### [25、您对微服务有何了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#25您对微服务有何了解)  

### [26、在Spring AOP 中，关注点和横切关注的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#26在spring-aop-中关注点和横切关注的区别是什么)  

### [27、什么是服务熔断](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#27什么是服务熔断)  

### [28、SpringBoot 有哪几种读取配置的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#28springboot-有哪几种读取配置的方式)  

### [29、如何重新加载SpringBoot上的更改，而无需重新启动服务器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#29如何重新加载springboot上的更改而无需重新启动服务器)  

### [30、什么是Hystrix?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#30什么是hystrix)  

### [31、什么是自动配置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Spring/Spring高级面试题及答案大全（2021年Spring面试题答案大汇总）.md#31什么是自动配置)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
