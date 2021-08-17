# Java中级面试题汇总及答案（2021年Java面试题及答案大全）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、为什么HashMap中String、Integer这样的包装类适合作为K？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#1为什么hashmap中stringinteger这样的包装类适合作为k)  


String、Integer等包装类的特性能够保证Hash值的不可更改性和计算准确性，能够有效的减少Hash碰撞的几率

**1、** 都是final类型，即不可变性，保证key的不可更改性，不会存在获取hash值不同的情况

**2、** 内部已重写了`equals()`、`hashCode()`等方法，遵守了HashMap内部的规范（不清楚可以去上面看看putValue的过程），不容易出现Hash值计算错误的情况；


### [2、常见的计算机网络协议有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#2常见的计算机网络协议有那些)  


**1、** TCP/IP协议

**2、** IPX/SPX协议

**3、** NetBEUI协议


### [3、一个线程运行时发生异常会怎样？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#3一个线程运行时发生异常会怎样)  


如果异常没有被捕获该线程将会停止执行。Thread.UncaughtExceptionHandler是用于处理未捕获异常造成线程突然中断情况的一个内嵌接口。当一个未捕获异常将造成线程中断的时候JVM会使用Thread.getUncaughtExceptionHandler()来查询线程的UncaughtExceptionHandler并将线程和异常作为参数传递给handler的uncaughtException()方法进行处理。


### [4、遍历一个 List 有哪些不同的方式？每种方法的实现原理是什么？Java 中 List 遍历的最佳实践是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#4遍历一个-list-有哪些不同的方式每种方法的实现原理是什么java-中-list-遍历的最佳实践是什么)  


**遍历方式有以下几种：**

**1、** for 循环遍历，基于计数器。在集合外部维护一个计数器，然后依次读取每一个位置的元素，当读取到最后一个元素后停止。

**2、** 迭代器遍历，Iterator。Iterator 是面向对象的一个设计模式，目的是屏蔽不同数据集合的特点，统一遍历集合的接口。Java 在 Collections 中支持了 Iterator 模式。

**3、** foreach 循环遍历。foreach 内部也是采用了 Iterator 的方式实现，使用时不需要显式声明 Iterator 或计数器。优点是代码简洁，不易出错；缺点是只能做简单的遍历，不能在遍历过程中操作数据集合，例如删除、替换。

**最佳实践：**

Java Collections 框架中提供了一个 RandomAccess 接口，用来标记 List 实现是否支持 Random Access。

**1、** 如果一个数据集合实现了该接口，就意味着它支持 Random Access，按位置读取元素的平均时间复杂度为 O(1)，如ArrayList。

**2、** 如果没有实现该接口，表示不支持 Random Access，如LinkedList。

**3、** 推荐的做法就是，支持 Random Access 的列表可用 for 循环遍历，否则建议用 Iterator 或 foreach 遍历。


### [5、StringBuffer，Stringbuilder有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#5stringbufferstringbuilder有什么区别)  


StringBuffer与StringBuilder都继承了AbstractStringBulder类，而AbtractStringBuilder又实现了CharSequence接口，两个类都是用来进行字符串操作的。

在做字符串拼接修改删除替换时，效率比string更高。

StringBuffer是线程安全的，Stringbuilder是非线程安全的。所以Stringbuilder比stringbuffer效率更高，StringBuffer的方法大多都加了synchronized关键字


### [6、什么是线程池？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#6什么是线程池)  


Java中的线程池是运用场景最多的并发框架，几乎所有需要异步或并发执行任务的程序都可以使用线程池。在开发过程中，合理地使用线程池能够带来许多好处。

**1、** 降低资源消耗。通过重复利用已创建的线程降低线程创建和销毁造成的消耗。

**2、** 提高响应速度。当任务到达时，任务可以不需要等到线程创建就能立即执行。

**3、** 提高线程的可管理性。线程是稀缺资源，如果无限制地创建，不仅会消耗系统资源，还会降低系统的稳定性，使用线程池可以进行统一分配、调优和监控。但是，要做到合理利用


### [7、JDBC操作的步骤](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#7jdbc操作的步骤)  


**1、** 加载数据库驱动类

**2、** 打开数据库连接

**3、** 执行sql语句

**4、** 处理返回结果

**5、** 关闭资源


### [8、说一下 JVM 调优的工具？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#8说一下-jvm-调优的工具)  


常用调优工具分为两类,jdk自带监控工具：jconsole和jvisualvm，第三方有：MAT(Memory AnalyzerTool)、GChisto。

jconsole，Java Monitoring and Management Console是从java5开始，在JDK中自带的java监控和管理控制台，用于对JVM中内存， 线程和类等的监控。jvisualvm，jdk自带全能工具，可以分析内存快照、线程快照；监控内存变化、GC变化等。MAT，Memory Analyzer Tool，一个基于Eclipse的内存分析工具，是一个快速、功能丰富的Javaheap分析工具，它可以帮助我们查找内存泄漏和减少内存消耗。GChisto，一款专业分析gc日志的工具。


### [9、JVM 提供的常用工具](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#9jvm-提供的常用工具)  


**jps：**

用来显示本地的 Java 进程，可以查看本地运行着几个 Java 程序，并显示他们的进程号。 命令格式：jps

**jinfo：**

运行环境参数：Java System 属性和 JVM 命令行参数，Java class path 等信息。 命令格式：jinfo 进程 pid

**jstat：**

监视虚拟机各种运行状态信息的命令行工具。 命令格式：jstat -gc 123 250 20

**jstack：**

可以观察到 JVM 中当前所有线程的运行情况和线程当前状态。 命令格式：jstack 进程 pid

**jmap：**

观察运行中的 JVM 物理内存的占用情况（如：产生哪些对象，及其数量）。 命令格式：jmap [option] pid


### [10、SynchronizedMap和ConcurrentHashMap有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#10synchronizedmap和concurrenthashmap有什么区别)  


SynchronizedMap一次锁住整张表来保证线程安全，所以每次只能有一个线程来访为map。

**1、** ConcurrentHashMap使用分段锁来保证在多线程下的性能。ConcurrentHashMap中则是一次锁住一个桶。ConcurrentHashMap默认将hash表分为16个桶，诸如get,put,remove等常用操作只锁当前需要用到的桶。这样，原来只能一个线程进入，现在却能同时有16个写线程执行，并发性能的提升是显而易见的。

**2、** 另外ConcurrentHashMap使用了一种不同的迭代方式。在这种迭代方式中，当iterator被创建后集合再发生改变就不再是抛出ConcurrentModificationException，取而代之的是在改变时new新的数据从而不影响原有的数据 ，iterator完成后再将头指针替换为新的数据 ，这样iterator线程可以使用原来老的数据，而写线程也可以并发的完成改变。


### [11、MinorGC、MajorGC、FullGC 什么时候发生？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#11minorgcmajorgcfullgc-什么时候发生)  

### [12、如何使session失效](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#12如何使session失效)  

### [13、Query接口的list方法和iterate方法有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#13query接口的list方法和iterate方法有什么区别)  

### [14、多线程同步和互斥有几种实现方法，都是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#14多线程同步和互斥有几种实现方法都是什么)  

### [15、Servlet中如何获取用户提交的查询参数或表单数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#15servlet中如何获取用户提交的查询参数或表单数据)  

### [16、依赖注入和工程模式之间有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#16依赖注入和工程模式之间有什么不同)  

### [17、Java 中怎么打印数组？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#17java-中怎么打印数组)  

### [18、是否了解连接池，使用连接池有什么好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#18是否了解连接池使用连接池有什么好处)  

### [19、sleep方法和wait方法有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#19sleep方法和wait方法有什么区别)  

### [20、Java 中，如何将字符串 YYYYMMDD 转换为日期？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#20java-中如何将字符串-yyyyd-转换为日期)  

### [21、能否使用任何类作为 Map 的 key？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#21能否使用任何类作为-map-的-key)  

### [22、JVM有哪些内存区域？(JVM的内存布局是什么？)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#22jvm有哪些内存区域jvm的内存布局是什么)  

### [23、线程与进程的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#23线程与进程的区别)  

### [24、上传文件是如何做的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#24上传文件是如何做的)  

### [25、当一个线程进入一个对象的 synchronized 方法 A 之后，其它线程是否可进入此对象的 synchronized 方法 B？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#25当一个线程进入一个对象的-synchronized-方法-a-之后其它线程是否可进入此对象的-synchronized-方法-b)  

### [26、volatile 能使得一个非原子操作变成原子操作吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#26volatile-能使得一个非原子操作变成原子操作吗)  

### [27、乐观锁和悲观锁的理解及如何实现，有哪些实现方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#27乐观锁和悲观锁的理解及如何实现有哪些实现方式)  

### [28、List、Map、Set三个接口存取元素时，各有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#28listmapset三个接口存取元素时各有什么特点)  

### [29、JAVA为什么需要接口？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#29java为什么需要接口)  

### [30、java 中的 Math.round(-1.5) 等于多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#30java-中的-mathround-15-等于多少)  

### 31、堆
### [32、什么是双亲委派机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#32什么是双亲委派机制)  

### [33、什么是 FutureTask](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#33什么是-futuretask)  

### [34、创建对象的过程是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#34创建对象的过程是什么)  

### [35、在Java中CycliBarriar和CountdownLatch有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#35在java中cyclibarriar和countdownlatch有什么区别)  

### [36、并发编程有什么缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#36并发编程有什么缺点)  

### [37、synchronized 和 ReentrantLock 区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#37synchronized-和-reentrantlock-区别是什么)  

### [38、JVM 的内存模型是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#38jvm-的内存模型是什么)  

### [39、Java中如何实现多线程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#39java中如何实现多线程)  

### [40、Java 中的内存映射缓存区是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题汇总及答案（2021年Java面试题及答案大全）.md#40java-中的内存映射缓存区是什么)  

### 41、Minor GC与Full GC分别在什么时候发生？




## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
