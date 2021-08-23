# SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）

SpringCloud面试题及答案【最新版】SpringCloud高级面试题大全(2021版)，发现网上很多SpringCloud面试题及答案整理都没有答案，所以花了很长时间搜集，本套SpringCloud面试题大全，SpringCloud面试题大汇总，有大量经典的SpringCloud面试题以及答案，包含SpringCloud语言常见面试题、SpringCloud工程师高级面试题及一些大厂SpringCloud开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套SpringCloud面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个SpringCloud面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Spring Cloud解决了哪些问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#1spring-cloud解决了哪些问题)  


在使用SpringBoot开发分布式微服务时，我们面临的问题很少由Spring Cloud解决。

与分布式系统相关的复杂性 – 包括网络问题，延迟开销，带宽问题，安全问题。

处理服务发现的能力 – 服务发现允许集群中的进程和服务找到彼此并进行通信。

解决冗余问题 – 冗余问题经常发生在分布式系统中。

负载平衡 – 改进跨多个计算资源（例如计算机集群，网络链接，中央处理单元）的工作负载分布。

减少性能问题 – 减少因各种操作开销导致的性能问题。


### [2、Zuul网关如何搭建集群](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#2zuul网关如何搭建集群)  


使用Nginx的upstream设置Zuul服务集群，通过location拦截请求并转发到upstream，默认使用轮询机制对Zuul集群发送请求。


### [3、我们可以用微服务创建状态机吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#3我们可以用微服务创建状态机吗)  


我们知道拥有自己的数据库的每个微服务都是一个可独立部署的程序单元，这反过来又让我们可以创建一个状态机。因此，我们可以为特定的微服务指定不同的状态和事件。

例如，我们可以定义Order微服务。订单可以具有不同的状态。Order状态的转换可以是Order微服务中的独立事件。


### [4、什么是Feign？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#4什么是feign)  


**1、** Feign 是一个声明web服务客户端，这使得编写web服务客户端更容易

**2、** 他将我们需要调用的服务方法定义成抽象方法保存在本地就可以了，不需要自己构建Http请求了，直接调用接口就行了，不过要注意，调用方法要和本地抽象方法的签名完全一致。


### [5、如何设置服务发现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#5如何设置服务发现)  


有多种方法可以设置服务发现。我将选择我认为效率最高的那个，Netflix的Eureka。这是一个简单的程序，不会对应用程序造成太大影响。此外，它支持多种类型的Web应用程序。 Eureka配置包括两个步骤 - 客户端配置和服务器配置。

使用属性文件可以轻松完成客户端配置。在clas spath中，Eureka搜索一个eureka-client.properties文件。它还搜索由特定于环境的属性文件中的环境引起的覆盖。

对于服务器配置，您必须首先配置客户端。完成后，服务器启动一个客户端，该客户端用于查找其他服务器。。默认情况下，Eureka服务器使用客户端配置来查找对等服务器。


### [6、您对微服务有何了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#6您对微服务有何了解)  


微服务，又称微服务架构，是一种架构风格，它将应用程序构建为以业务领域为模型的小型自治服务集合 。

通俗地说，你必须看到蜜蜂如何通过对齐六角形蜡细胞来构建它们的蜂窝状物。他们最初从使用各种材料的小部分开始，并继续从中构建一个大型蜂箱。这些细胞形成图案，产生坚固的结构，将蜂窝的特定部分固定在一起。这里，每个细胞独立于另一个细胞，但它也与其他细胞相关。这意味着对一个细胞的损害不会损害其他细胞，因此，蜜蜂可以在不影响完整蜂箱的情况下重建这些细胞。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_1.png#alt=img%5C_1.png)

图1：微服务的蜂窝表示 – 微服务访谈问题

请参考上图。这里，每个六边形形状代表单独的服务组件。与蜜蜂的工作类似，每个敏捷团队都使用可用的框架和所选的技术堆栈构建单独的服务组件。就像在蜂箱中一样，每个服务组件形成一个强大的微服务架构，以提供更好的可扩展性。此外，敏捷团队可以单独处理每个服务组件的问题，而对整个应用程序没有影响或影响最小。


### [7、什么是耦合和凝聚力？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#7什么是耦合和凝聚力)  


组件之间依赖关系强度的度量被认为是**耦合**。一个好的设计总是被认为具有**高内聚力和低耦合性**。 面试官经常会问起凝聚力。它也是另一个测量单位。更像是一个模块内部的元素保持结合的程度。 必须记住，设计微服务的一个重要关键是低耦合和高内聚的组合。当低耦合时，服务对其他服务的依赖很少。这样可以保持服务的完整性。在高内聚性中，将所有相关逻辑保存在服务中成为可能。否则，服务将尝试彼此通信，从而影响整体性能。


### [8、什么是Spring Cloud？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#8什么是spring-cloud)  


spring cloud 是一系列框架的有序集合。它利用 spring boot 的开发便利性巧妙地简化了分布式系统基础设施的开发，如服务发现注册、配置中心、消息总线、负载均衡、断路器、数据监控等，都可以用 spring boot 的开发风格做到一键启动和部署。


### [9、dubbo服务注册与发现原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#9dubbo服务注册与发现原理)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_5.png#alt=45%5C_5.png)

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/01/44/45_6.png#alt=45%5C_6.png)

调⽤关系说明：

**1、** 服务容器负责启动,加载,运⾏服务提供者。

**2、** 服务提供者在启动时,向注册中⼼注册⾃⼰提供的服务。

**3、** 服务消费者在启动时,向注册中⼼订阅⾃⼰所需的服务。

**4、** 注册中⼼返回服务提供者地址列表给消费者,如果有变更,注册中⼼将基于⻓连接推送变更数据给消费者。

**5、** 服务消费者,从提供者地址列表中,基于软负载均衡算法,选⼀台提供者进⾏调⽤,如果调⽤失败,再选另⼀台调⽤。

**6、** 服务消费者和提供者,在内存中累计调⽤次数和调⽤时间,定时每分钟发送⼀次统计数据到监控中⼼。


### [10、微服务有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#10微服务有什么特点)  


您可以列出微服务的特征，如下所示：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/01/img_9.png#alt=img%5C_9.png)

图7：微服务的特征 – 微服务访谈问题


### [11、Spring Cloud Task](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#11spring-cloud-task)  

### [12、微服务架构的优缺点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#12微服务架构的优缺点是什么)  

### [13、什么是 Spring Cloud Bus？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#13什么是-spring-cloud-bus)  

### [14、什么是幂等性?它是如何使用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#14什么是幂等性它是如何使用的)  

### [15、SpringCloud有几种调用接口方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#15springcloud有几种调用接口方式)  

### [16、SpringBoot和SpringCloud的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#16springboot和springcloud的区别)  

### [17、SpringCloud由什么组成](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#17springcloud由什么组成)  

### [18、什么是金丝雀释放？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#18什么是金丝雀释放)  

### [19、微服务之间是如何独立通讯的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#19微服务之间是如何独立通讯的)  

### [20、熔断的原理，以及如何恢复？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#20熔断的原理以及如何恢复)  

### [21、您对微服务架构中的语义监控有何了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#21您对微服务架构中的语义监控有何了解)  

### [22、什么是无所不在的语言？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#22什么是无所不在的语言)  

### [23、什么是断路器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#23什么是断路器)  

### [24、访问RESTful微服务的方法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#24访问restful微服务的方法是什么)  

### [25、什么是Spring Cloud？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#25什么是spring-cloud)  

### [26、您对Distributed Transaction有何了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#26您对distributed-transaction有何了解)  

### [27、什么是 Hystrix 断路器？我们需要它吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#27什么是-hystrix-断路器我们需要它吗)  

### [28、eureka缓存机制：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#28eureka缓存机制：)  

### [29、Eureka和ZooKeeper都可以提供服务注册与发现的功能,请说说两个的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#29eureka和zookeeper都可以提供服务注册与发现的功能,请说说两个的区别)  

### [30、我们如何进行跨功能测试？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/SpringCloud/SpringCloud中级面试题汇总及答案（2021年SpringCloud面试题及答案大全）.md#30我们如何进行跨功能测试)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
