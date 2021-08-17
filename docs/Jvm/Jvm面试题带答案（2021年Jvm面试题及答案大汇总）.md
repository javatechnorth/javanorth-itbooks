# Jvm面试题带答案（2021年Jvm面试题及答案大汇总）

Jvm面试题及答案【最新版】Jvm高级面试题大全(2021版)，发现网上很多Jvm面试题及答案整理都没有答案，所以花了很长时间搜集，本套Jvm面试题大全，Jvm面试题大汇总，有大量经典的Jvm面试题以及答案，包含Jvm语言常见面试题、Jvm工程师高级面试题及一些大厂Jvm开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Jvm面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Jvm面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、新生代与复制算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#1新生代与复制算法)  


目前大部分 JVM 的 GC 对于新生代都采取 Copying 算法，因为新生代中每次垃圾回收都要回收大部分对象，即要复制的操作比较少，但通常并不是按照 1：1 来划分新生代。一般将新生代划分为一块较大的 Eden 空间和两个较小的 Survivor 空间(From Space, To Space)，每次使用Eden 空间和其中的一块 Survivor 空间，当进行回收时，将该两块空间中还存活的对象复制到另一块 Survivor 空间中。


### [2、串行（serial）收集器和吞吐量（throughput）收集器的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#2串行serial收集器和吞吐量throughput收集器的区别是什么)  


吞吐量收集器使用并行版本的新生代垃圾收集器，它用于中等规模和大规模数据的应用程序。 而串行收集器对大多数的小应用（在现代处理器上需要大概 100M 左右的内存）就足够了。


### [3、怎么打出线程栈信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#3怎么打出线程栈信息)  


输入jps，获得进程号。top -Hp pid 获取本进程中所有线程的CPU耗时性能 jstack pid命令查看当前java进程的堆栈状态 或者 jstack -l > /tmp/output.txt 把堆栈信息打到一个txt文件。可以使用fastthread 堆栈定位（fastthread.io）


### [4、JVM怎么判断一个对象是不是要回收？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#4jvm怎么判断一个对象是不是要回收)  


引用计数法（缺点是对于相互引用的对象，无法进行清除） 可达性分析


### [5、JVM 监控与分析工具你用过哪些？介绍一下。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#5jvm-监控与分析工具你用过哪些介绍一下。)  


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


### [6、复制算法（copying）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#6复制算法copying)  


为了解决 Mark-Sweep 算法内存碎片化的缺陷而被提出的算法。按内存容量将内存划分为等大小的两块。每次只使用其中一块，当这一块内存满后将尚存活的对象复制到另一块上去，把已使用的内存清掉

这种算法虽然实现简单，内存效率高，不易产生碎片，但是最大的问题是可用内存被压缩到了原本的一半。且存活对象增多的话， Copying算法的效率会大大降低。


### [7、什么是指令重排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#7什么是指令重排序)  


在实际运行时，代码指令可能并不是严格按照代码语句顺序执行的。大多数现代微处理器都会采用将指令乱序执行（out-of-order execution，简称OoOE或OOE）的方法，在条件允许的情况下，直接运行当前有能力立即执行的后续指令，避开获取下一条指令所需数据时造成的等待。通过乱序执行的技术，处理器可以大大提高执行效率。而这就是指令重排。


### [8、你了解过哪些垃圾收集器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#8你了解过哪些垃圾收集器)  


年轻代 Serial 垃圾收集器（单线程，通常用在客户端应用上。因为客户端应用不会频繁创建很多对象，用户也不会感觉出明显的卡顿。相反，它使用的资源更少，也更轻量级。） ParNew 垃圾收集器（多线程，追求降低用户停顿时间，适合交互式应用。） Parallel Scavenge 垃圾收集器（追求 CPU 吞吐量，能够在较短时间内完成指定任务，适合没有交互的后台计算。）

老年代 Serial Old 垃圾收集器 Parallel Old垃圾收集器 CMS 垃圾收集器（以获取最短 GC 停顿时间为目标的收集器，它在垃圾收集时使得用户线程和 GC 线程能够并发执行，因此在垃圾收集过程中用户也不会感到明显的卡顿。）


### [9、JVM 的内存模型是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#9jvm-的内存模型是什么)  


JVM 试图定义一种统一的内存模型，能将各种底层硬件以及操作系统的内存访问差异进行封装，使 Java 程序在不同硬件以及操作系统上都能达到相同的并发效果。它分为工作内存和主内存，线程无法对主存储器直接进行操作，如果一个线程要和另外一个线程通信，那么只能通过主存进行交换。


### [10、谈谈动态年龄判断](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#10谈谈动态年龄判断)  


**1、** 这里涉及到 -XX:TargetSurvivorRatio 参数，Survivor 区的目标使用率默认 50，即 Survivor 区对象目标使用率为 50%。

**2、** Survivor 区相同年龄所有对象大小的总和 (Survivor 区内存大小 * 这个目标使用率)时，大于或等于该年龄的对象直接进入老年代。

**3、** 当然，这里还需要考虑参数 -XX:MaxTenuringThreshold 晋升年龄最大阈值


### [11、JVM 有哪些运行时内存区域？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#11jvm-有哪些运行时内存区域)  

### [12、工作中常用的 JVM 配置参数有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#12工作中常用的-jvm-配置参数有哪些)  

### [13、Java会存在内存泄漏吗？请简单描述。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#13java会存在内存泄漏吗请简单描述。)  

### [14、GC 是什么？为什么要有 GC？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#14gc-是什么为什么要有-gc)  

### [15、你平时工作中用过的JVM常用基本配置参数有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#15你平时工作中用过的jvm常用基本配置参数有哪些)  

### [16、JRE、JDK、JVM 及 JIT 之间有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#16jrejdkjvm-及-jit-之间有什么不同)  

### [17、JVM的引用类型有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#17jvm的引用类型有哪些)  

### [18、Minor GC与Full GC分别在什么时候发生？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#18minor-gc与full-gc分别在什么时候发生)  

### [19、说说G1垃圾收集器的工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#19说说g1垃圾收集器的工作原理)  

### [20、堆的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#20堆的作用是什么)  

### [21、解释 Java 堆空间及 GC？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#21解释-java-堆空间及-gc)  

### [22、说一下堆和栈的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#22说一下堆和栈的区别)  

### [23、Serial 与 Parallel GC 之间的不同之处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#23serial-与-parallel-gc-之间的不同之处)  

### [24、什么是栈](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#24什么是栈)  

### [25、本地方法栈](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#25本地方法栈)  

### [26、Parallel Old 收集器（多线程标记整理算法）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#26parallel-old-收集器多线程标记整理算法)  

### [27、方法区](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#27方法区)  

### [28、JVM 内存区域](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#28jvm-内存区域)  

### [29、分代回收](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#29分代回收)  

### [30、对象分配规则](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#30对象分配规则)  

### [31、程序计数器有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题带答案（2021年Jvm面试题及答案大汇总）.md#31程序计数器有什么作用)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
