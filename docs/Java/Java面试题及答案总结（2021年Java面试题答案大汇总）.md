# Java面试题及答案总结（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、Java有没有goto？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#1java有没有goto)  




goto 是Java中的保留字，在目前版本的Java中没有使用。（根据James Gosling（Java之父）编写的《The Java Programming Language》一书的附录中给出了一个Java关键字列表，其中有goto和const，但是这两个是目前无法使用的关键字，因此有些地方将其称之为保留字，其实保留字这个词应该有更广泛的意义，因为熟悉C语言的程序员都知道，在系统类库中使用过的有特殊意义的单词或单词的组合都被视为保留字）


### [2、JVM怎么判断一个对象是不是要回收？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#2jvm怎么判断一个对象是不是要回收)  


引用计数法（缺点是对于相互引用的对象，无法进行清除） 可达性分析


### [3、String s = new String(“xyz”);创建了几个字符串对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#3string-s-=-new-string“xyz;创建了几个字符串对象)  




两个对象，一个是静态区的”xyz”，一个是用new创建在堆上的对象。


### [4、什么是过滤器？怎么创建一个过滤器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#4什么是过滤器怎么创建一个过滤器)  


过滤器：在请求发送之后，处理之前对请求的一次拦截，可以更改请求状态或者参数值等。

创建过滤器：实现filter接口，重写doFilter方法，最后在web.xml中配置过滤器


### [5、介绍一下 JVM 中垃圾收集器有哪些？ 他们特点分别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#5介绍一下-jvm-中垃圾收集器有哪些-他们特点分别是什么)  


**新生代垃圾收集器**

**Serial 收集器**

特点： Serial 收集器只能使用一条线程进行垃圾收集工作，并且在进行垃圾收集的时候，所有的工作线程都需要停止工作，等待垃圾收集线程完成以后，其他线程才可以继续工作。

**使用算法：复制算法**

**ParNew 收集器**

特点： ParNew 垃圾收集器是Serial收集器的多线程版本。为了利用 CPU 多核多线程的优势，ParNew 收集器可以运行多个收集线程来进行垃圾收集工作。这样可以提高垃圾收集过程的效率。

**使用算法：复制算法**

**Parallel Scavenge 收集器**

特点： Parallel Scavenge 收集器是一款多线程的垃圾收集器，但是它又和 ParNew 有很大的不同点。

Parallel Scavenge 收集器和其他收集器的关注点不同。其他收集器，比如 ParNew 和 CMS 这些收集器，它们主要关注的是如何缩短垃圾收集的时间。而 Parallel Scavenge 收集器关注的是如何控制系统运行的吞吐量。这里说的吞吐量，指的是 CPU 用于运行应用程序的时间和 CPU 总时间的占比，吞吐量 = 代码运行时间 / （代码运行时间 + 垃圾收集时间）。如果虚拟机运行的总的 CPU 时间是 100 分钟，而用于执行垃圾收集的时间为 1 分钟，那么吞吐量就是 99%。

**使用算法：复制算法**

**老年代垃圾收集器**

**Serial Old 收集器**

特点： Serial Old 收集器是 Serial 收集器的老年代版本。这款收集器主要用于客户端应用程序中作为老年代的垃圾收集器，也可以作为服务端应用程序的垃圾收集器。

**使用算法：标记-整理**

**Parallel Old 收集器**

特点： Parallel Old 收集器是 Parallel Scavenge 收集器的老年代版本这个收集器是在 JDK1.6 版本中出现的，所以在 JDK1.6 之前，新生代的 Parallel Scavenge 只能和 Serial Old 这款单线程的老年代收集器配合使用。Parallel Old 垃圾收集器和 Parallel Scavenge 收集器一样，也是一款关注吞吐量的垃圾收集器，和 Parallel Scavenge 收集器一起配合，可以实现对 Java 堆内存的吞吐量优先的垃圾收集策略。

**使用算法：标记-整理**

**CMS 收集器**

特点： CMS 收集器是目前老年代收集器中比较优秀的垃圾收集器。CMS 是 Concurrent Mark Sweep，从名字可以看出，这是一款使用"标记-清除"算法的并发收集器。

CMS 垃圾收集器是一款以获取最短停顿时间为目标的收集器。如下图所示：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/05/34/39_3.png#alt=39%5C_3.png)

**从图中可以看出，CMS 收集器的工作过程可以分为 4 个阶段：**

**1、** 初始标记（CMS initial mark）阶段

**2、** 并发标记（CMS concurrent mark）阶段

**3、** 重新标记（CMS remark）阶段

**4、** 并发清除(（CMS concurrent sweep）阶段

使用算法：复制+标记清除

**其他**

**G1 垃圾收集器**

特点： 主要步骤：`初始标记，并发标记，重新标记，复制清除。`

**使用算法：复制 + 标记整理**


### [6、线程池的执行原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#6线程池的执行原理)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/045/42/87_9.png#alt=87%5C_9.png)

提交一个任务到线程池中，线程池的处理流程如下：

**1、**  判断线程池里的核心线程是否都在执行任务，如果不是（核心线程空闲或者还有核心线程没有被创建）则创建一个新的工作线程来执行任务。如果核心线程都在执行任务，则进入下个流程。

**2、**  线程池判断工作队列是否已满，如果工作队列没有满，则将新提交的任务存储在这个工作队列里。如果工作队列满了，则进入下个流程。

**3、**  判断线程池里的线程是否都处于工作状态，如果没有，则创建一个新的工作线程来执行任务。如果已经满了，则交给饱和策略来处理这个任务。


### [7、假设数组内有5个元素，如果对数组进行反序，该如何做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#7假设数组内有5个元素如果对数组进行反序该如何做)  


创建一个新数组，从后到前循环遍历每个元素，将取出的元素依次顺序放入新数组中


### [8、java 中 IO 流分为几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#8java-中-io-流分为几种)  


按功能来分：输入流（input）、输出流（output）。

按类型来分：字节流和字符流。

字节流和字符流的区别是：字节流按 8 位传输以字节为单位输入输出数据，字符流按 16 位传输以字符为单位输入输出数据。


### [9、你都有哪些手段用来排查内存溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#9你都有哪些手段用来排查内存溢出)  


（这个话题很大，可以从实践环节中随便摘一个进行总结，下面举例一个最普通的）

你可以来一个中规中矩的回

内存溢出包含很多种情况，我在平常工作中遇到最多的就是`堆溢出`。有一次线上遇到故障，重新启动后，使用jstat命令，发现Old区在一直增长。我使用jmap命令，导出了一份线上堆栈，然后使用`MAT`进行分析。通过对`GC Roots`的分析，我发现了一个非常大的HashMap对象，这个原本是有位同学`做缓存`用的，但是一个无界缓存，造成了堆内存占用一直上升。后来，将这个缓存改成 guava的Cache，并设置了弱引用，故障就消失了。

这个回答不是十分出彩，但着实是常见问题，让人挑不出毛病。


### [10、GC 是什么？为什么要有 GC？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#10gc-是什么为什么要有-gc)  


GC 是垃 圾收 集的 意思 ，内存 处理 是编 程人 员容 易出 现问 题的 地方 ，忘记 或者 错误的内 存回 收会 导致 程序 或系 统的 不稳 定甚 至崩 溃， Java 提供 的 GC 功能 可以 自动监测 对象 是否 超过 作用 域从 而达 到自 动回 收内 存的 目的 ，Java 语言 没有 提供 释放已分配内存的 显示 操作 方法 。Java 程序 员不 用担 心内 存管 理， 因为 垃圾 收集 器会自动 进行 管理 。要 请求 垃圾 收集 ，可 以调 用下 面的 方法 之一 ：System.gc() 或Runtime.getRuntime().gc() ，但 JVM 可以 屏蔽 掉线 示的 垃圾 回收 调用 。

垃圾回收可以有效的防止内存泄露，有效的使用可以使用的内存。垃圾回收器通常是作为一个单独的低优先级的线程运行，不可预知的情况下对内存堆中已经死亡的或者长时间没有使用的对象进行清除和回收，程序员不能实时的调用垃圾回收器对某个对象或所有对象进行垃圾回收。在 Java 诞生初期，垃圾回收是 Java最大的亮点之一，因为服务器端的编程需要有效的防止内存泄露问题，然而时过境迁，如今 Java 的垃圾回收机制已经成为被诟病的东。移动智能终端用户通常觉得 iOS 的系统比 Android 系统有更好的用户体验，其中一个深层次的原因就在于 Android 系统中垃圾回收的不可预知性。


### [11、如何判断一个类是无用的类?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#11如何判断一个类是无用的类)  

### [12、堆的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#12堆的作用是什么)  

### [13、MyBatis中使用#和$书写占位符有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#13mybatis中使用#和$书写占位符有什么区别)  

### [14、使用sql写出一个分页程序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#14使用sql写出一个分页程序)  

### [15、说一下 synchronized 底层实现原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#15说一下-synchronized-底层实现原理)  

### [16、什么是指令重排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#16什么是指令重排序)  

### [17、什么是ORM？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#17什么是orm)  

### [18、直接内存是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#18直接内存是什么)  

### [19、java 中操作字符串都有哪些类？它们之间有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#19java-中操作字符串都有哪些类它们之间有什么区别)  

### [20、ConcurrentHashMap的并发度是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#20concurrenthashmap的并发度是什么)  

### [21、集合的特点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#21集合的特点)  

### [22、ReadWriteLock是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#22readwritelock是什么)  

### [23、线程类的构造方法、静态块是被哪个线程调用的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#23线程类的构造方法静态块是被哪个线程调用的)  

### [24、说出 5 条 IO 的最佳实践(答案)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#24说出-5-条-io-的最佳实践答案)  

### [25、&和&&的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#25&和&&的区别)  

### [26、垃圾回收的优点和原理。说说2种回收机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#26垃圾回收的优点和原理。说说2种回收机制)  

### [27、老年代](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#27老年代)  

### [28、请解释Tomcat的默认端口是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#28请解释tomcat的默认端口是什么)  

### [29、编写多线程程序有几种实现方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#29编写多线程程序有几种实现方式)  

### [30、假如生产环境CPU占用过高，请谈谈你的分析思路和定位。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#30假如生产环境cpu占用过高请谈谈你的分析思路和定位。)  

### [31、Tcp协议的特点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#31tcp协议的特点)  

### [32、什么时候会触发FullGC](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#32什么时候会触发fullgc)  

### [33、解释一下什么叫AOP（面向切面编程）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#33解释一下什么叫aop面向切面编程)  

### [34、Collection接口下有那些集合框架？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#34collection接口下有那些集合框架)  

### [35、JVM调优命令有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#35jvm调优命令有哪些)  

### [36、怎么将 byte 转换为 String？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#36怎么将-byte-转换为-string)  

### [37、什么是 Class 文件？ Class 文件主要的信息结构有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#37什么是-class-文件-class-文件主要的信息结构有哪些)  

### [38、什么是原型模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#38什么是原型模式)  

### [39、Java中操作字符串使用哪个类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#39java中操作字符串使用哪个类)  

### [40、抽象工厂模式和原型模式之间的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案总结（2021年Java面试题答案大汇总）.md#40抽象工厂模式和原型模式之间的区别)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
