# SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）

SpringCloud面试题及答案【最新版】SpringCloud高级面试题大全(2021版)，发现网上很多SpringCloud面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringCloud面试题大全，SpringCloud面试题大汇总，有大量经典的SpringCloud面试题以及答案，包含SpringCloud语言常见面试题、SpringCloud工程师高级面试题及一些大厂SpringCloud开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringCloud面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringCloud面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是客户证书？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#1什么是客户证书)  


客户端系统用于向远程服务器发出经过身份验证的请求的一种数字证书称为客户端证书。客户端证书在许多相互认证设计中起着非常重要的作用，为请求者的身份提供了强有力的保证。


### [2、REST 和RPC对比](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#2rest-和rpc对比)  


**1、** RPC主要的缺陷是服务提供方和调用方式之间的依赖太强，需要对每一个微服务进行接口的定义，并通过持续继承发布，严格版本控制才不会出现冲突。

**2、** REST是轻量级的接口，服务的提供和调用不存在代码之间的耦合，只需要一个约定进行规范。


### [3、分布式配置中心的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#3分布式配置中心的作用)  


动态变更项目配置信息而不必重新部署项目。


### [4、链路跟踪Sleuth](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#4链路跟踪sleuth)  


当我们项目中引入Spring Cloud Sleuth后，每次链路请求都会添加一串追踪信息，格式是[server-name, main-traceId,sub-spanId,boolean]：

**1、** server-name：服务结点名称。

**2、** main-traceId：一条链路唯一的ID，为TraceID。

**3、** sub-spanId：链路中每一环的ID，为SpanID。

**4、** boolean：是否将信息输出到Zipkin等服务收集和展示。

Sleuth的实现是基于HTTP的，为了在数据的收集过程中不能影响到正常业务，Sleuth会在每个请求的Header上添加跟踪需求的重要信息。这样在数据收集时，只需要将Header上的相关信息发送给对应的图像工具即可，图像工具根据上传的数据，按照Span对应的逻辑进行分析、展示。



### [5、服务注册和发现是什么意思？Spring Cloud如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#5服务注册和发现是什么意思spring-cloud如何实现)  


当我们开始一个项目时，我们通常在属性文件中进行所有的配置。随着越来越多的服务开发和部署，添加和修改这些属性变得更加复杂。有些服务可能会下降，而某些位置可能会发生变化。手动更改属性可能会产生问题。 Eureka服务注册和发现可以在这种情况下提供帮助。由于所有服务都在Eureka服务器上注册并通过调用Eureka服务器完成查找，因此无需处理服务地点的任何更改和处理。


### [6、21、在Spring MVC应用程序中使用WebMvcTest注释有什么用处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#621在spring-mvc应用程序中使用webmvctest注释有什么用处)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_13.png#alt=img%5C_13.png)

在测试目标只关注Spring MVC组件的情况下，WebMvcTest注释用于单元测试Spring MVC应用程序。在上面显示的快照中，我们只想启动ToTestController。执行此单元测试时，不会启动所有其他控制器和映射。


### [7、什么是双因素身份验证？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#7什么是双因素身份验证)  


双因素身份验证为帐户登录过程启用第二级身份验证。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_14.png#alt=img%5C_14.png)

图11： 双因素认证的表示 – 微服务访谈问题

因此，假设用户必须只输入用户名和密码，那么这被认为是单因素身份验证。


### [8、什么是不同类型的微服务测试？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#8什么是不同类型的微服务测试)  


在使用微服务时，由于有多个微服务协同工作，测试变得非常复杂。因此，测试分为不同的级别。

在底层，我们有面向技术的测试，如单元测试和性能测试。这些是完全自动化的。

在中间层面，我们进行了诸如压力测试和可用性测试之类的探索性测试。

在顶层， 我们的 验收测试数量很少。这些验收测试有助于利益相关者理解和验证软件功能。


### [9、什么是Eureka](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#9什么是eureka)  


Eureka作为SpringCloud的服务注册功能服务器，他是服务注册中心，系统中的其他服务使用Eureka的客户端将其连接到Eureka Service中，并且保持心跳，这样工作人员可以通过Eureka Service来监控各个微服务是否运行正常。


### [10、常用网关框架有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#10常用网关框架有那些)  


Nginx、Zuul、Gateway


### [11、什么是REST / RESTful以及它的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#11什么是rest-/-restful以及它的用途是什么)  

### [12、什么是耦合？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#12什么是耦合)  

### [13、什么是Netflix Feign？它的优点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#13什么是netflix-feign它的优点是什么)  

### [14、eureka的缺点：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#14eureka的缺点：)  

### [15、网关与过滤器有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#15网关与过滤器有什么区别)  

### [16、什么是 Hystrix？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#16什么是-hystrix)  

### [17、微服务的缺点：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#17微服务的缺点：)  

### [18、什么是微服务中的反应性扩展？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#18什么是微服务中的反应性扩展)  

### [19、Ribbon和Feign调用服务的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#19ribbon和feign调用服务的区别)  

### [20、spring cloud 和dubbo区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#20spring-cloud-和dubbo区别)  

### [21、如何设计一套API接口](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#21如何设计一套api接口)  

### [22、什么是持续监测？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#22什么是持续监测)  

### [23、Spring Cloud OpenFeign](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#23spring-cloud-openfeign)  

### [24、什么是Hystrix断路器？我们需要它吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#24什么是hystrix断路器我们需要它吗)  

### [25、SpringCloud限流：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#25springcloud限流：)  

### [26、什么是客户证书？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#26什么是客户证书)  

### [27、为什么要选择微服务架构？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#27为什么要选择微服务架构)  

### [28、Spring Cloud Sleuth](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#28spring-cloud-sleuth)  

### [29、Spring Cloud Gateway](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#29spring-cloud-gateway)  

### [30、Spring Cloud 是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud高级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#30spring-cloud-是什么)  





