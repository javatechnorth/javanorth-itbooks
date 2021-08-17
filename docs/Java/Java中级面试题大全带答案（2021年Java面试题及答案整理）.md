# Java中级面试题大全带答案（2021年Java面试题及答案整理）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、怎么获取 Java 程序使用的内存？堆使用的百分比？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#1怎么获取-java-程序使用的内存堆使用的百分比)  


可以通过 java.lang.Runtime 类中与内存相关方法来获取剩余的内存，总内存及最大堆内存。通过这些方法你也可以获取到堆使用的百分比及堆内存的剩余空间。Runtime.freeMemory() 方法返回剩余空间的字节数，Runtime.totalMemory() 方法总内存的字节数，Runtime.maxMemory() 返回最大内存的字节数。


### [2、强引用、软引用、弱引用、虚引用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#2强引用软引用弱引用虚引用是什么)  


**普通的对象引用关系就是强引用**

软引用用于维护一些可有可无的对象。只有在内存不足时，系统则会回收软引用对象，如果回收了软引用对象之后仍然没有足够的内存，才会抛出内存溢出异常。

弱引用对象相比较软引用，要更加无用`一些`，它拥有更短的生命周期。当JVM进行垃圾回收时，无论内存是否充足，都会回收被弱引用关联的对象。

虚引用是一种形同虚设的引用，在现实场景中用的不是很多，它主要用来跟踪对象被垃圾回收的活动。


### [3、G1 收集器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#3g1-收集器)  


Garbage first 垃圾收集器是目前垃圾收集器理论发展的最前沿成果，相比与 CMS 收集器， G1 收集器两个最突出的改进是：

**1、** 基于标记-整理算法，不产生内存碎片。

**2、** 可以非常精确控制停顿时间，在不牺牲吞吐量前提下，实现低停顿垃圾回收。G1 收集器避免全区域垃圾收集，它把堆内存划分为大小固定的几个独立区域，并且跟踪这些区域的垃圾收集进度，同时在后台维护一个优先级列表，每次根据所允许的收集时间， 优先回收垃圾最多的区域。区域划分和优先级区域回收机制，确保 G1 收集器可以在有限时间获得最高的垃圾收集效率


### [4、运行时常量池溢出的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#4运行时常量池溢出的原因)  


String 的 `intern` 方法是一个本地方法，作用是如果字符串常量池中已包含一个等于此 String 对象的字符串，则返回池中这个字符串的 String 对象的引用，否则将此 String 对象包含的字符串添加到常量池并返回此 String 对象的引用。

在 JDK6 及之前常量池分配在永久代，因此可以通过 `-XX:PermSize` 和 `-XX:MaxPermSize` 限制永久代大小，间接限制常量池。在 while 死循环中调用 `intern` 方法导致运行时常量池溢出。在 JDK7 后不会出现该问题，因为存放在永久代的字符串常量池已经被移至堆中。


### [5、Java最顶级的父类是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#5java最顶级的父类是哪个)  


Object


### [6、JVM 监控与分析工具你用过哪些？介绍一下。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#6jvm-监控与分析工具你用过哪些介绍一下。)  


**1、** jps，显示系统所有虚拟机进程信息的命令行工具

**2、** jstat，监视分析虚拟机运行状态的命令行工具

**3、** jinfo，查看和调整虚拟机参数的命令行工具

**4、** jmap，生成虚拟机堆内存转储快照的命令行工具

**5、** jhat，显示和分析虚拟机的转储快照文件的命令行工具

**6、** jstack，生成虚拟机的线程快照的命令行工具

**7、** jcmd，虚拟机诊断工具，JDK 7 提供

**8、** jhsdb，基于服务性代理实现的进程外可视化调试工具，JDK 9 提供

**9、** JConsole，基于JMX的可视化监视和管理工具

**10、** jvisualvm，图形化虚拟机使用情况的分析工具

**11、** Java Mission Control，监控和管理 Java 应用程序的工具

**1、** MAT，Memory Analyzer Tool，虚拟机内存分析工具

**2、** vjtools，唯品会的包含核心类库与问题分析工具

**3、** arthas，阿里开源的 Java 诊断工具

**4、** greys，JVM进程执行过程中的异常诊断工具

**5、** GCHisto，GC 分析工具

**6、** GCViewer，GC 日志文件分析工具

**7、** GCeasy，在线版 GC 日志文件分析工具

**8、** JProfiler，检查、监控、追踪 Java 性能的工具

**9、** BTrace，基于动态字节码修改技术(Hotswap)实现的Java程序追踪与分析工具

**下面可以重点体验下：**

JDK 自带的命令行工具方便快捷，不是特别复杂的问题可以快速定位；

阿里的 arthas 命令行也不错；

可视化工具 MAT、JProfiler 比较强大。


### [7、JVM新生代中为什么要分为Eden和Survivor？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#7jvm新生代中为什么要分为eden和survivor)  


如果没有Survivor，Eden区每进行一次Minor GC，存活的对象就会被送到老年代。老年代很快被填满，触发Major GC.老年代的内存空间远大于新生代，进行一次Full GC消耗的时间比Minor GC长得多,所以需要分为Eden和Survivor。Survivor的存在意义，就是减少被送到老年代的对象，进而减少Full GC的发生，Survivor的预筛选保证，只有经历16次Minor GC还能在新生代中存活的对象，才会被送到老年代。设置两个Survivor区最大的好处就是解决了碎片化，刚刚新建的对象在Eden中，经历一次Minor GC，Eden中的存活对象就会被移动到第一块survivor space S0，Eden被清空；等Eden区再满了，就再触发一次Minor GC，Eden和S0中的存活对象又会被复制送入第二块survivor space S1（这个过程非常重要，因为这种复制算法保证了S1中来自S0和Eden两部分的存活对象占用连续的内存空间，避免了碎片化的发生）


### [8、Parallel Old 收集器（多线程标记整理算法）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#8parallel-old-收集器多线程标记整理算法)  


Parallel Old 收集器是Parallel Scavenge的年老代版本，使用多线程的标记-整理算法，在 JDK1.6才开始提供。

在 JDK1.6 之前，新生代使用 ParallelScavenge 收集器只能搭配年老代的 Serial Old 收集器，只能保证新生代的吞吐量优先，无法保证整体的吞吐量， Parallel Old 正是为了在年老代同样提供吞吐量优先的垃圾收集器， 如果系统对吞吐量要求比较高，可以优先考虑新生代Parallel Scavenge和年老代 Parallel Old 收集器的搭配策略。


### [9、Java线程具有五中基本状态](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#9java线程具有五中基本状态)  


**1、** 新建状态（New）：当线程对象对创建后，即进入了新建状态，如：Thread t = new MyThread()；

**2、** 就绪状态（Runnable）：当调用线程对象的start()方法（t.start();），线程即进入就绪状态。处于就绪状态的线程，只是说明此线程已经做好了准备，随时等待CPU调度执行，并不是说执行了t.start()此线程立即就会执行；

**3、** 运行状态（Running）：当CPU开始调度处于就绪状态的线程时，此时线程才得以真正执行，即进入到运行状态。注：就 绪状态是进入到运行状态的唯一入口，也就是说，线程要想进入运行状态执行，首先必须处于就绪状态中；

**4、** 阻塞状态（Blocked）：处于运行状态中的线程由于某种原因，暂时放弃对CPU的使用权，停止执行，此时进入阻塞状态，直到其进入到就绪状态，才 有机会再次被CPU调用以进入到运行状态。

**根据阻塞产生的原因不同，阻塞状态又可以分为三种：**

**1、** 等待阻塞：运行状态中的线程执行wait()方法，使本线程进入到等待阻塞状态；

**2、** 同步阻塞：线程在获取synchronized同步锁失败(因为锁被其它线程所占用)，它会进入同步阻塞状态；

**3、** 其他阻塞：通过调用线程的sleep()或join()或发出了I/O请求时，线程会进入到阻塞状态。当sleep()状态超时、join()等待线程终止或者超时、或者I/O处理完毕时，线程重新转入就绪状态。

**5、** 死亡状态（Dead）：线程执行完了或者因异常退出了run()方法，该线程结束生命周期。


### [10、双亲委派模型是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#10双亲委派模型是什么)  


类加载器具有等级制度但非继承关系，以组合的方式复用父加载器的功能。双亲委派模型要求除了顶层的启动类加载器外，其余类加载器都应该有自己的父加载器。

一个类加载器收到了类加载请求，它不会自己去尝试加载，而将该请求委派给父加载器，每层的类加载器都是如此，因此所有加载请求最终都应该传送到启动类加载器，只有当父加载器反馈无法完成请求时，子加载器才会尝试。

类跟随它的加载器一起具备了有优先级的层次关系，确保某个类在各个类加载器环境中都是同一个，保证程序的稳定性。


### [11、HashMap为什么不直接使用hashCode()处理后的哈希值直接作为table的下标？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#11hashmap为什么不直接使用hashcode处理后的哈希值直接作为table的下标)  

### [12、在不使用 StringBuffer 的前提下，怎么反转一个字符串？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#12在不使用-stringbuffer-的前提下怎么反转一个字符串)  

### [13、数组实例化有几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#13数组实例化有几种方式)  

### [14、方法区](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#14方法区)  

### [15、Js如何实现动态效果？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#15js如何实现动态效果)  

### [16、Spring中如何使用注解来配置Bean？有哪些相关的注解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#16spring中如何使用注解来配置bean有哪些相关的注解)  

### [17、Static关键字有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#17static关键字有什么作用)  

### [18、对象的访问定位有哪几种方式?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#18对象的访问定位有哪几种方式)  

### [19、生产环境服务器变慢，如何诊断处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#19生产环境服务器变慢如何诊断处理)  

### [20、ConcurrentHashMap 底层具体实现知道吗？实现原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#20concurrenthashmap-底层具体实现知道吗实现原理是什么)  

### [21、什么是自旋](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#21什么是自旋)  

### [22、线程池有什么优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#22线程池有什么优点)  

### [23、Java中集合框架的有几个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#23java中集合框架的有几个)  

### [24、JRE、JDK、JVM 及 JIT 之间有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#24jrejdkjvm-及-jit-之间有什么不同)  

### [25、阐述JDBC操作数据库的步骤。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#25阐述jdbc操作数据库的步骤。)  

### [26、标记清除算法（ Mark-Sweep）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#26标记清除算法-mark-sweep)  

### [27、形参与实参](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#27形参与实参)  

### [28、Session的save()、update()、merge()、lock()、saveOrUpdate()和persist()方法分别是做什么的？有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#28session的saveupdatemergelocksaveorupdate和persist方法分别是做什么的有什么区别)  

### [29、Set接口有什么特点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#29set接口有什么特点)  

### [30、如何将字符串反转？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#30如何将字符串反转)  

### [31、有哪些打破了双亲委托机制的案例？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#31有哪些打破了双亲委托机制的案例)  

### [32、Java中的包装类都是那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#32java中的包装类都是那些)  

### [33、JVM的永久代中会发生垃圾回收么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#33jvm的永久代中会发生垃圾回收么)  

### [34、什么是线程池？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#34什么是线程池)  

### [35、什么是数据结构？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#35什么是数据结构)  

### [36、Java常用包有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#36java常用包有那些)  

### [37、多线程场景下如何使用 ArrayList？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#37多线程场景下如何使用-arraylist)  

### [38、抽象类（abstract class）和接口（interface）有什么异同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#38抽象类abstract-class和接口interface有什么异同)  

### [39、64 位 JVM 中，int 的长度是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#3964-位-jvm-中int-的长度是多数)  

### [40、GC Roots 有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大全带答案（2021年Java面试题及答案整理）.md#40gc-roots-有哪些)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
