# Java高级面试题及答案真题（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是Future？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#1什么是future)  


在并发编程中，我们经常用到非阻塞的模型，在之前的多线程的三种实现中，不管是继承thread类还是实现runnable接口，都无法保证获取到之前的执行结果。通过实现Callback接口，并用Future可以来接收多线程的执行结果。

Future表示一个可能还没有完成的异步任务的结果，针对这个结果可以添加Callback以便在任务执行成功或失败后作出相应的操作。


### [2、设计模式分类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#2设计模式分类)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/047/42/89_1.png#alt=89%5C_1.png)

**1、** 创建型模式，共五种：**工厂方法模式、抽象工厂模式**、**单例模式**、建造者模式、**原型模式。**

**2、** 结构型模式，共七种：适配器模式、装饰器模式、代理模式、外观模式、桥接模式、组合模式、享元模式。

**3、** 行为型模式，共十一种：策略模式、模板方法模式、观察者模式、迭代子模式、责任链模式、命令模式、备忘录模式、状态模式、访问者模式、中介者模式、解释器模式。


### [3、死锁的原因](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#3死锁的原因)  


**1、** 是多个线程涉及到多个锁，这些锁存在着交叉，所以可能会导致了一个锁依赖的闭环。

例如：线程在获得了锁A并且没有释放的情况下去申请锁B，这时，另一个线程已经获得了锁B，在释放锁B之前又要先获得锁A，因此闭环发生，陷入死锁循环。

**2、** 默认的锁申请操作是阻塞的。

所以要避免死锁，就要在一遇到多个对象锁交叉的情况，就要仔细审查这几个对象的类中的所有方法，是否存在着导致锁依赖的环路的可能性。总之是尽量避免在一个同步方法中调用其它对象的延时方法和同步方法。


### [4、43.将下java中的math类有那些常用方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#443将下java中的math类有那些常用方法)  


**1、** Pow()：幂运算

**2、** Sqrt()：平方根

**3、** Round()：四舍五入

**4、** Abs()：求绝对值

**5、** Random()：生成一个0-1的随机数，包括0不包括1


### [5、游标的创建步骤？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#5游标的创建步骤)  


**1、** 定义游标

**2、** 打开游标

**3、** 操作游标数据

**4、** 关闭游标


### [6、在 Java 中 Executor 和 Executors 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#6在-java-中-executor-和-executors-的区别)  


**1、** Executors 工具类的不同方法按照我们的需求创建了不同的线程池，来满足业务的需求。

**2、** Executor 接口对象能执行我们的线程任务。

**3、** ExecutorService 接口继承了 Executor 接口并进行了扩展，提供了更多的方法我们能获得任务执行的状态并且可以获取任务的返回值。

**4、** 使用 ThreadPoolExecutor 可以创建自定义线程池。


### [7、方法区/永久代（线程共享）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#7方法区/永久代线程共享)  


即我们常说的永久代(Permanent Generation), 用于存储被 JVM 加载的类信息、常量、静态变量即、时编译器编译后的代码等数据.HotSpot VM把GC分代收集扩展至方法区, 即使用Java堆的永久代来实现方法区, 这样 HotSpot 的垃圾收集器就可以像管理 Java 堆一样管理这部分内存,而不必为方法区开发专门的内存管理器(永久带的内存回收的主要目标是针对常量池的回收和类型的卸载, 因此收益一般很小) 。

运行时常量池（Runtime Constant Pool）是方法区的一部分。Class 文件中除了有类的版本、字段、方法、接口等描述等信息外，还有一项信息是常量池 （Constant Pool Table），用于存放编译期生成的各种字面量和符号引用，这部分内容将在类加载后存放到方法区的运行时常量池中。Java 虚拟机对 Class 文件的每一部分（自然也包括常量池）的格式都有严格的规定，每一个字节用于存储哪种数据都必须符合规范上的要求，这样才会被虚拟机认可、装载和执行。


### [8、Java的内存模型是什么？（JMM是什么？）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#8java的内存模型是什么jmm是什么)  


JVM试图定义一种统一的内存模型，能将各种底层硬件及操作系统的内存访问差异进行封装，使Java程序在不同硬件及操作系统上都能达到相同的并发效果。它分为工作内存和主内存，线程无法对主存储器**直接**进行操作，一个线程要和另外一个线程通信，只能通过主存进行交换。

JMM可以说是Java并发的基础，它的定义将直接影响多线程实现的机制，如果你想要想深入了解多线程并发中的相关问题现象，对JMM的深入研究是必不可少的。

上面两个问题是经常容易搞混的，但它们的内容却完全不同的。


### [9、说一下 HashSet 的实现原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#9说一下-hashset-的实现原理)  


HashSet 是基于 HashMap 实现的，HashSet的值存放于HashMap的key上，HashMap的value统一为present，因此 HashSet 的实现比较简单，相关 HashSet 的操作，基本上都是直接调用底层 HashMap 的相关方法来完成，HashSet 不允许重复的值。


### [10、什么是线程池？ 为什么要使用它？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#10什么是线程池-为什么要使用它)  


创建线程要花费昂贵的资源和时间，如果任务来了才创建线程那么响应时间会变长，而且一个进程能创建的线程数有限。为了避免这些问题，在程序启动的时候就创建若干线程来响应处理，它们被称为线程池，里面的线程叫工作线程。从JDK1.5开始，Java API提供了Executor框架让你可以创建不同的线程池。


### [11、一个线程运行时发生异常会怎样？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#11一个线程运行时发生异常会怎样)  

### [12、你如何在Java中获取线程堆栈？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#12你如何在java中获取线程堆栈)  

### [13、JVM垃圾回收时候如何确定垃圾？什么是GC Roots？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#13jvm垃圾回收时候如何确定垃圾什么是gc-roots)  

### [14、Java 中，DOM 和 SAX 解析器有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#14java-中dom-和-sax-解析器有什么不同)  

### [15、简述synchronized 和java.util.concurrent.locks.Lock的异同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#15简述synchronized-和javautilconcurrentlockslock的异同)  

### [16、为什么HashTable是线程安全的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#16为什么hashtable是线程安全的)  

### [17、volatile 能使得一个非原子操作变成原子操作吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#17volatile-能使得一个非原子操作变成原子操作吗)  

### [18、List 和 Set 的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#18list-和-set-的区别)  

### [19、Java 中，怎样才能打印出数组中的重复元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#19java-中怎样才能打印出数组中的重复元素)  

### [20、final、finalize()、finally，性质不同](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#20finalfinalizefinally性质不同)  

### [21、ArrayList和Vector有什么不同之处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#21arraylist和vector有什么不同之处)  

### [22、Json是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#22json是什么)  

### [23、在多线程环境下，SimpleDateFormat 是线程安全的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#23在多线程环境下simpledateformat-是线程安全的吗)  

### [24、什么时候使用享元模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#24什么时候使用享元模式)  

### [25、如何在jsp页面上显示一些特定格式的数字或者日期](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#25如何在jsp页面上显示一些特定格式的数字或者日期)  

### [26、引用计数法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#26引用计数法)  

### [27、为什么要使用并发编程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#27为什么要使用并发编程)  

### [28、是否可以从一个静态（static）方法内部发出对非静态（non-static）方法的调用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#28是否可以从一个静态static方法内部发出对非静态non-static方法的调用)  

### [29、Java中用到的线程调度算法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#29java中用到的线程调度算法是什么)  

### [30、什么是重排序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#30什么是重排序)  

### [31、Java Concurrency API中的Lock接口(Lock interface)是什么？对比同步它有什么优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#31java-concurrency-api中的lock接口lock-interface是什么对比同步它有什么优势)  

### [32、死锁与活锁的区别，死锁与饥饿的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#32死锁与活锁的区别死锁与饥饿的区别)  

### [33、形成死锁的四个必要条件是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#33形成死锁的四个必要条件是什么)  

### [34、synchronized关键字的用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#34synchronized关键字的用法)  

### [35、遇到过堆外内存溢出吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#35遇到过堆外内存溢出吗)  

### [36、Hibernate中Session的load和get方法的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#36hibernate中session的load和get方法的区别是什么)  

### [37、Spring开发中的工厂设计模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#37spring开发中的工厂设计模式)  

### [38、我们能自己写一个容器类，然后使用 for-each 循环码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#38我们能自己写一个容器类然后使用-for-each-循环码)  

### [39、如何检查出两个给定的字符串是反序的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#39如何检查出两个给定的字符串是反序的)  

### [40、JVM 运行时内存](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案真题（2021年Java面试题答案大汇总）.md#40jvm-运行时内存)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
