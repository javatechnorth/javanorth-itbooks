# SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）

SpringCloud面试题及答案【最新版】SpringCloud高级面试题大全(2021版)，发现网上很多SpringCloud面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringCloud面试题大全，SpringCloud面试题大汇总，有大量经典的SpringCloud面试题以及答案，包含SpringCloud语言常见面试题、SpringCloud工程师高级面试题及一些大厂SpringCloud开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringCloud面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringCloud面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是凝聚力？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#1什么是凝聚力)  


模块内部元素所属的程度被认为是凝聚力。


### [2、为什么需要域驱动设计（DDD）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#2为什么需要域驱动设计ddd)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_11.png#alt=img%5C_11.png)

图9：我们需要DDD的因素 – 微服务面试问题


### [3、eureka和zookeeper都可以提供服务注册与发现的功能，请说说两个的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#3eureka和zookeeper都可以提供服务注册与发现的功能请说说两个的区别)  


**1、** zookeeper 是CP原则，强一致性和分区容错性。

**2、** eureka 是AP 原则 可用性和分区容错性。

**3、** zookeeper当主节点故障时，zk会在剩余节点重新选择主节点，耗时过长，虽然最终能够恢复，但是选取主节点期间会导致服务不可用，这是不能容忍的。

**4、** eureka各个节点是平等的，一个节点挂掉，其他节点仍会正常保证服务。


### [4、服务降级底层是如何实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#4服务降级底层是如何实现的)  


Hystrix实现服务降级的功能是通过重写HystrixCommand中的getFallback()方法，当Hystrix的run方法或construct执行发生错误时转而执行getFallback()方法。


### [5、什么是持续集成（CI）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#5什么是持续集成ci)  


持续集成（CI）是每次团队成员提交版本控制更改时自动构建和测试代码的过程。这鼓励开发人员通过在每个小任务完成后将更改合并到共享版本控制存储库来共享代码和单元测试。


### [6、第⼀层缓存：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#6第⼀层缓存：)  


readOnlyCacheMap，本质上是ConcurrentHashMap：这是⼀个JVM的CurrentHashMap只读缓存，这个主要是为了供客户端获取注册信息时使⽤，其缓存更新，依赖于定时器的更新，通过和readWriteCacheMap 的值做对⽐，如果数据不⼀致，则以readWriteCacheMap 的数据为准。readOnlyCacheMap 缓存更新的定时器时间间隔，默认为30秒

#
### [7、微服务测试的主要障碍是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#7微服务测试的主要障碍是什么)  


说到缺点，这里是另一个微服务面试问题，将围绕测试微服务时面临的挑战。

**1、** 在开始编写集成测试的测试用例之前，测试人员应该全面了解对所有入站和出站过程。

**2、** 当独立的团队正在开发不同的功能时，协作可能会被证明是一项非常困难的任务。很难找到空闲时间窗口来执行完整的回归测试。

**3、** 随着微服务数量的增加，系统的复杂性也随之增加。

**4、** 在从单片架构过渡期间，测试人员必须确保组件之间的内部通信没有中断。


### [8、接⼝限流⽅法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#8接⼝限流⽅法)  


**限制 总并发数（⽐如 数据库连接池、线程池）**

**1、** 限制 瞬时并发数（如 nginx 的 limit_conn 模块，⽤来限制 瞬时并发连接数）

**2、** 限制 时间窗⼝内的平均速率（如 Guava 的 RateLimiter、nginx 的 limit_req模块，限制每秒的平均速率）

**3、** 限制 远程接⼝ 调⽤速率

**4、** 限制 MQ 的消费速率

**5、** 可以根据⽹络连接数、⽹络流量、CPU或内存负载等来限流



### [9、什么是feigin？它的优点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#9什么是feigin它的优点是什么)  


**1、** feign采用的是基于接口的注解

**2、** feign整合了ribbon，具有负载均衡的能力

**3、** 整合了Hystrix，具有熔断的能力

**使用:**

**1、** 添加pom依赖。

**2、** 启动类添加[@EnableFeignClients ](/EnableFeignClients )

**3、** 定义一个接口@FeignClient(name=“xxx”)指定调用哪个服务


### [10、设计微服务的最佳实践是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#10设计微服务的最佳实践是什么)  


以下是设计微服务的最佳实践：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_4.png#alt=img%5C_4.png)

图4：设计微服务的最佳实践 – 微服务访谈问题


### [11、服务雪崩效应产生的原因](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#11服务雪崩效应产生的原因)  

### [12、单片，SOA和微服务架构有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#12单片soa和微服务架构有什么区别)  

### [13、Zuul与Nginx有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#13zuul与nginx有什么区别)  

### [14、如何配置SpringBoot应用程序日志记录？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#14如何配置springboot应用程序日志记录)  

### [15、康威定律是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#15康威定律是什么)  

### [16、SOA和微服务架构之间的主要区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#16soa和微服务架构之间的主要区别是什么)  

### [17、什么是Semantic监控？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#17什么是semantic监控)  

### [18、服务注册和发现是什么意思？Spring Cloud如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#18服务注册和发现是什么意思spring-cloud如何实现)  

### [19、架构师在微服务架构中的角色是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#19架构师在微服务架构中的角色是什么)  

### [20、Spring Cloud Consul](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#20spring-cloud-consul)  

### [21、微服务架构有哪些优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#21微服务架构有哪些优势)  

### [22、Spring Cloud Sleuth](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#22spring-cloud-sleuth)  

### [23、PACT如何运作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#23pact如何运作)  

### [24、Spring Cloud Bus](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#24spring-cloud-bus)  

### [25、什么是SpringBoot？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#25什么是springboot)  

### [26、网关的作用是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#26网关的作用是什么)  

### [27、什么是服务降级](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#27什么是服务降级)  

### [28、Spring Cloud Task](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#28spring-cloud-task)  

### [29、Eureka如何 保证AP](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#29eureka如何-保证ap)  

### [30、负载均衡的意义是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#30负载均衡的意义是什么)  

### [31、SpringCloud的优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud面试题带答案（2021年SpringCloud面试题及答案大汇总）.md#31springcloud的优缺点)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
