# SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）

SpringCloud面试题及答案【最新版】SpringCloud高级面试题大全(2021版)，发现网上很多SpringCloud面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringCloud面试题大全，SpringCloud面试题大汇总，有大量经典的SpringCloud面试题以及答案，包含SpringCloud语言常见面试题、SpringCloud工程师高级面试题及一些大厂SpringCloud开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringCloud面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringCloud面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是微服务](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#1什么是微服务)  


**1、** 微服务是⼀种架构⻛格，也是⼀种服务；

**2、** 微服务的颗粒⽐较⼩，⼀个⼤型复杂软件应⽤由多个微服务组成，⽐如Netflix⽬前由500多的微服务组成；

**3、** 它采⽤UNIX设计的哲学，每种服务只做⼀件事，是⼀种松耦合的能够被独⽴开发和部署的⽆状态化服务（独⽴扩展、升级和可替换）。


### [2、微服务限流 http限流：我们使⽤nginx的limitzone来完成：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#2微服务限流-http限流：我们使⽤nginx的limitzone来完成：)  


```
//这个表示使⽤ip进⾏限流 zone名称为req_one 分配了10m 空间使⽤漏桶算法 每秒钟允许1个请求
limit_req_zone $binary_remote_addr zone=req_one:10m rate=1r/s; //这边burst表示可以瞬间超过20个请求 由于没有noDelay参数因此需要排队 如果超过这20个那么直接返回503
limit_req zone=req_three burst=20;
```


### [3、Spring Cloud Netflix(重点，这些组件用的最多)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#3spring-cloud-netflix重点这些组件用的最多)  


Netflix OSS 开源组件集成，包括Eureka、Hystrix、Ribbon、Feign、Zuul等核心组件。

**1、** Eureka：服务治理组件，包括服务端的注册中心和客户端的服务发现机制；

**2、** Ribbon：负载均衡的服务调用组件，具有多种负载均衡调用策略；

**3、** Hystrix：服务容错组件，实现了断路器模式，为依赖服务的出错和延迟提供了容错能力；

**4、** Feign：基于Ribbon和Hystrix的声明式服务调用组件；

**5、** Zuul：API网关组件，对请求提供路由及过滤功能。

`我觉得SpringCloud的福音是Netflix，他把人家的组件都搬来进行封装了，使开发者能快速简单安全的使用`


### [4、什么是端到端微服务测试？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#4什么是端到端微服务测试)  


端到端测试验证了工作流中的每个流程都正常运行。这可确保系统作为一个整体协同工作并满足所有要求。

通俗地说，你可以说端到端测试是一种测试，在特定时期后测试所有东西。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_17.png#alt=img%5C_17.png)

图14：测试层次 – 微服务面试问题


### [5、什么是Netflix Feign？它的优点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#5什么是netflix-feign它的优点是什么)  


Feign是受到Retrofit，JAXRS-2.0和WebSocket启发的java客户端联编程序。Feign的第一个目标是将约束分母的复杂性统一到http apis，而不考虑其稳定性。在employee-consumer的例子中，我们使用了employee-producer使用REST模板公开的REST服务。

但是我们必须编写大量代码才能执行以下步骤

**1、** 使用功能区进行负载平衡。

**2、** 获取服务实例，然后获取基本URL。

**3、** 利用REST模板来使用服务。 前面的代码如下

```
@Controller
public class ConsumerControllerClient {

@Autowired
private LoadBalancerClient loadBalancer;

public void getEmployee() throws RestClientException, IOException {

    ServiceInstance serviceInstance=loadBalancer.choose("employee-producer");

    System.out.println(serviceInstance.getUri());

    String baseUrl=serviceInstance.getUri().toString();

    baseUrl=baseUrl+"/employee";

    RestTemplate restTemplate = new RestTemplate();
    ResponseEntity<String> response=null;
    try{
    response=restTemplate.exchange(baseUrl,
            HttpMethod.GET, getHeaders(),String.class);
    }catch (Exception ex)
    {
        System.out.println(ex);
    }
    System.out.println(response.getBody());
```

之前的代码，有像NullPointer这样的例外的机会，并不是最优的。我们将看到如何使用Netflix Feign使呼叫变得更加轻松和清洁。如果Netflix Ribbon依赖关系也在类路径中，那么Feign默认也会负责负载平衡。


### [6、什么是OAuth？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#6什么是oauth)  


OAuth 代表开放授权协议。这允许通过在HTTP服务上启用客户端应用程序（例如第三方提供商Facebook，GitHub等）来访问资源所有者的资源。因此，您可以在不使用其凭据的情况下与另一个站点共享存储在一个站点上的资源。


### [7、Ribbon是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#7ribbon是什么)  


**1、** Ribbon是Netflix发布的开源项目，主要功能是提供客户端的软件负载均衡算法

**2、** Ribbon客户端组件提供一系列完善的配置项，如连接超时，重试等。简单的说，就是在配置文件中列出后面所有的机器，Ribbon会自动的帮助你基于某种规则（如简单轮询，随即连接等）去连接这些机器。我们也很容易使用Ribbon实现自定义的负载均衡算法。（有点类似Nginx）


### [8、Spring Cloud抛弃了Dubbo 的RPC通信，采用的是基于HTTP的REST方式。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#8spring-cloud抛弃了dubbo-的rpc通信采用的是基于http的rest方式。)  


严格来说，这两种方式各有优劣。虽然在一定程度上来说，后者牺牲了服务调用的性能，但也避免了上面提到的原生RPC带来的问题。而且REST相比RPC更为灵活，服务提供方和调用方的依赖只依靠一纸契约，不存在代码级别的强依赖，这在强调快速演化的微服务环境下，显得更为合适。



### [9、什么是Idempotence以及它在哪里使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#9什么是idempotence以及它在哪里使用)  


幂等性是能够以这样的方式做两次事情的特性，即最终结果将保持不变，即好像它只做了一次。

用法：在远程服务或数据源中使用 Idempotence，这样当它多次接收指令时，它只处理指令一次。


### [10、SpringBoot支持哪些嵌入式容器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#10springboot支持哪些嵌入式容器)  


无论何时创建Java应用程序，都可以通过两种方法进行部署： 使用外部的应用程序容器。 将容器嵌入jar文件中。 SpringBoot包含Jetty，Tomcat和Undertow服务器，所有服务器都是嵌入式的。 Jetty - 用于大量项目，Eclipse Jetty可以嵌入到框架，应用程序服务器，工具和集群中。 Tomcat - Apache Tomcat是一个开源JavaServer Pages实现，可以很好地与嵌入式系统配合使用。 Undertow - 一个灵活而突出的Web服务器，它使用小型单一处理程序来开发Web服务器。


### [11、什么是Spring Cloud Bus？我们需要它吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#11什么是spring-cloud-bus我们需要它吗)  

### [12、双因素身份验证的凭据类型有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#12双因素身份验证的凭据类型有哪些)  

### [13、如何在SpringBoot应用程序中实现Spring安全性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#13如何在springboot应用程序中实现spring安全性)  

### [14、在使用微服务架构时，您面临哪些挑战？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#14在使用微服务架构时您面临哪些挑战)  

### [15、Spring Cloud Netflix](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#15spring-cloud-netflix)  

### [16、什么是Spring引导的执行器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#16什么是spring引导的执行器)  

### [17、既然Nginx可以实现网关？为什么还需要使用Zuul框架](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#17既然nginx可以实现网关为什么还需要使用zuul框架)  

### [18、spring cloud 断路器的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#18spring-cloud-断路器的作用是什么)  

### [19、在Spring MVC应用程序中使用WebMvcTest注释有什么用处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#19在spring-mvc应用程序中使用webmvctest注释有什么用处)  

### [20、Eureka怎么实现高可用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#20eureka怎么实现高可用)  

### [21、什么是Hystrix？它如何实现容错？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#21什么是hystrix它如何实现容错)  

### [22、您将如何在微服务上执行安全测试？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#22您将如何在微服务上执行安全测试)  

### [23、Zookeeper如何 保证CP](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#23zookeeper如何-保证cp)  

### [24、springcloud核⼼组件及其作⽤，以及springcloud⼯作原理：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#24springcloud核⼼组件及其作⽤以及springcloud⼯作原理：)  

### [25、什么是Oauth？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#25什么是oauth)  

### [26、SpringCloud Config 可以实现实时刷新吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#26springcloud-config-可以实现实时刷新吗)  

### [27、Eureka和ZooKeeper都可以提供服务注册与发现的功能,请说说两个的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#27eureka和zookeeper都可以提供服务注册与发现的功能,请说说两个的区别)  

### [28、PACT在微服务架构中的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#28pact在微服务架构中的用途是什么)  

### [29、Spring Cloud Security](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#29spring-cloud-security)  

### [30、在微服务中，如何保护服务?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题附答案汇总（2021年SpringCloud面试题及答案大全）.md#30在微服务中如何保护服务)  





