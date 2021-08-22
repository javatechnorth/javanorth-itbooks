# Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）

Jvm面试题及答案【最新版】Jvm高级面试题大全(2021版)，发现网上很多Jvm面试题及答案整理都没有答案，所以花了很长时间搜集，本套Jvm面试题大全，Jvm面试题大汇总，有大量经典的Jvm面试题以及答案，包含Jvm语言常见面试题、Jvm工程师高级面试题及一些大厂Jvm开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Jvm面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Jvm面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、生产环境服务器变慢，如何诊断处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#1生产环境服务器变慢如何诊断处理)  


**1、** 使用 top 指令，服务器中 CPU 和 内存的使用情况，-H 可以按 CPU 使用率降序，-M 内存使用率降序。排除其他进程占用过高的硬件资源，对 Java 服务造成影响。

**2、** 如果发现 CPU 使用过高，可以使用 top 指令查出 JVM 中占用 CPU 过高的线程，通过 jstack 找到对应的线程代码调用，排查出问题代码。

**3、** 如果发现内存使用率比较高，可以 dump 出 JVM 堆内存，然后借助 MAT 进行分析，查出大对象或者占用最多的对象来自哪里，为什么会长时间占用这么多；如果 dump 出的堆内存文件正常，此时可以考虑堆外内存被大量使用导致出现问题，需要借助操作系统指令 pmap 查出进程的内存分配情况、gdb dump 出具体内存信息、perf 查看本地函数调用等。

**4、** 如果 CPU 和 内存使用率都很正常，那就需要进一步开启 GC 日志，分析用户线程暂停的时间、各部分内存区域 GC 次数和时间等指标，可以借助 jstat 或可视化工具 GCeasy 等，如果问题出在 GC 上面的话，考虑是否是内存不够、根据垃圾对象的特点进行参数调优、使用更适合的垃圾收集器；分析 jstack 出来的各个线程状态。如果问题实在比较隐蔽，考虑是否可以开启 jmx，使用 visualmv 等可视化工具远程监控与分析。


### [2、引用计数法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#2引用计数法)  


在 Java 中，引用和对象是有关联的。如果要操作对象则必须用引用进行。因此，很显然一个简单的办法是通过引用计数来判断一个对象是否可以回收。简单说，即一个对象如果没有任何与之关联的引用， 即他们的引用计数都不为 0， 则说明对象不太可能再被用到，那么这个对象就是可回收对象。


### [3、MinorGC，MajorGC、FullGC都什么时候发生？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#3minorgcmajorgcfullgc都什么时候发生)  


MinorGC在年轻代空间不足的时候发生，MajorGC指的是老年代的GC，出现MajorGC一般经常伴有MinorGC。

FullGC有三种情况。

**1、** 当老年代无法再分配内存的时候

**2、** 元空间不足的时候

**3、** 显示调用System.gc的时候。另外，像CMS一类的垃圾回收器，在MinorGC出现promotion failure的时候也会发生FullGC


### [4、调优命令有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#4调优命令有哪些)  


Sun JDK监控和故障处理命令有jps jstat jmap jhat jstack jinfo

**1、** jps，JVM Process Status Tool,显示指定系统内所有的HotSpot虚拟机进程。

**2、** jstat，JVM statistics Monitoring是用于监视虚拟机运行时状态信息的命令，它可以显示出虚拟机进程中的类装载、内存、垃圾收集、JIT编译等运行数据。

**3、** jmap，JVM Memory Map命令用于生成heap dump文件

**4、** jhat，JVM Heap Analysis Tool命令是与jmap搭配使用，用来分析jmap生成的dump，jhat内置了一个微型的HTTP/HTML服务器，生成dump的分析结果后，可以在浏览器中查看

**5、** jstack，用于生成java虚拟机当前时刻的线程快照。

**6、** jinfo，JVM Configuration info 这个命令作用是实时查看和调整虚拟机运行参数


### [5、JVM 选项 -XX:+UseCompressedOops 有什么作用？为什么要使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#5jvm-选项--xx:+usecompressedoops-有什么作用为什么要使用)  


当你将你的应用从 32 位的 JVM 迁移到 64 位的 JVM 时，由于对象的指针从32 位增加到了 64 位，因此堆内存会突然增加，差不多要翻倍。这也会对 CPU缓存（容量比内存小很多）的数据产生不利的影响。因为，迁移到 64 位的 JVM主要动机在于可以指定最大堆大小，通过压缩OOP 可以节省一定的内存。通过-XX:+UseCompressedOops 选项，JVM 会使用 32 位的 OOP，而不是 64 位的 OOP。


### [6、Parallel Scavenge 收集器（多线程复制算法、高效）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#6parallel-scavenge-收集器多线程复制算法高效)  


Parallel Scavenge 收集器也是一个新生代垃圾收集器，同样使用复制算法，也是一个多线程的垃圾收集器， 它重点关注的是程序达到一个可控制的吞吐量（Thoughput， CPU 用于运行用户代码的时间/CPU 总消耗时间，即吞吐量=运行用户代码时间/(运行用户代码时间+垃圾收集时间)），高吞吐量可以最高效率地利用 CPU 时间，尽快地完成程序的运算任务，主要适用于在后台运算而不需要太多交互的任务。自适应调节策略也是 ParallelScavenge 收集器与 ParNew 收集器的一个重要区别。


### [7、老年代与标记复制算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#7老年代与标记复制算法)  


**而老年代因为每次只回收少量对象，因而采用 Mark-Compact 算法。**

**1、** JAVA 虚拟机提到过的处于方法区的永生代(Permanet Generation)， 它用来存储 class 类，常量，方法描述等。对永生代的回收主要包括废弃常量和无用的类。

**2、** 对象的内存分配主要在新生代的 Eden Space 和 Survivor Space 的 From Space(Survivor 目前存放对象的那一块)，少数情况会直接分配到老生代。

**3、** 当新生代的 Eden Space 和 From Space 空间不足时就会发生一次 GC，进行 GC 后， EdenSpace 和 From Space 区的存活对象会被挪到 To Space，然后将 Eden Space 和 FromSpace 进行清理。

**4、** 如果 To Space 无法足够存储某个对象，则将这个对象存储到老生代。

**5、** 在进行 GC 后，使用的便是 Eden Space 和 To Space 了，如此反复循环。

**6、** 当对象在 Survivor 去躲过一次 GC 后，其年龄就会+1。默认情况下年龄到达 15 的对象会被移到老生代中。


### [8、遇到过堆外内存溢出吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#8遇到过堆外内存溢出吗)  


**1、** Unsafe 类申请内存、JNI 对内存进行操作、Netty 调用操作系统的 malloc 函数的直接内存，这些内存是不受 JVM 控制的，不加限制的使用，很容易发生溢出。这种情况有个显著特点，dump 的堆文件信息正常甚至很小。

**2、** -XX:MaxDirectMemorySize 可以指定最大直接内存，但限制不住所有堆外内存的使用。


### [9、虚拟机栈(线程私有)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#9虚拟机栈线程私有)  


是描述java方法执行的内存模型，每个方法在执行的同时都会创建一个栈帧（Stack Frame）用于存储局部变量表、操作数栈、动态链接、方法出口等信息。每一个方法从调用直至执行完成的过程，就对应着一个栈帧在虚拟机栈中入栈到出栈的过程。

栈帧（ Frame）是用来存储数据和部分过程结果的数据结构，同时也被用来处理动态链接(Dynamic Linking)、 方法返回值和异常分派（Dispatch Exception）。栈帧随着方法调用而创建，随着方法结束而销毁——无论方法是正常完成还是异常完成（抛出了在方法内未被捕获的异常）都算作方法结束。


### [10、Java的双亲委托机制是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#10java的双亲委托机制是什么)  


它的意思是，除了顶层的启动类加载器以外，其余的类加载器，在加载之前，都会委派给它的父加载器进行加载。这样一层层向上传递，直到祖先们都无法胜任，它才会真正的加载。

Java默认是这种行为。当然Java中也有很多打破双亲行为的骚操作，比如SPI（JDBC驱动加载），OSGI等。


### [11、CMS都有哪些问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#11cms都有哪些问题)  

### [12、Java里有哪些引用类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#12java里有哪些引用类型)  

### [13、你知道哪些故障处理工具？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#13你知道哪些故障处理工具)  

### [14、运行时常量池的作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#14运行时常量池的作用是什么)  

### [15、JVM的永久代中会发生垃圾回收么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#15jvm的永久代中会发生垃圾回收么)  

### [16、对象的内存布局了解吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#16对象的内存布局了解吗)  

### [17、各种回收算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#17各种回收算法)  

### [18、你说你做过JVM参数调优和参数配置，请问如何查看JVM系统默认值](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#18你说你做过jvm参数调优和参数配置请问如何查看jvm系统默认值)  

### [19、JAVA弱引用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#19java弱引用)  

### [20、Java对象创建过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#20java对象创建过程)  

### [21、在新生代-复制算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#21在新生代-复制算法)  

### [22、生产环境用的什么JDK？如何配置的垃圾收集器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#22生产环境用的什么jdk如何配置的垃圾收集器)  

### [23、分代收集算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#23分代收集算法)  

### [24、32、volatile关键字的原理是什么？干什么用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#2432volatile关键字的原理是什么干什么用的)  

### [25、说一下Java对象的创建过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#25说一下java对象的创建过程)  

### [26、什么情况下会发生栈内存溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#26什么情况下会发生栈内存溢出)  

### [27、强引用、软引用、弱引用、虚引用是什么，有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#27强引用软引用弱引用虚引用是什么有什么区别)  

### [28、请你谈谈对OOM的认识](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#28请你谈谈对oom的认识)  

### [29、怎么打破双亲委派模型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#29怎么打破双亲委派模型)  

### [30、介绍一下 JVM 中垃圾收集器有哪些？ 他们特点分别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案汇总（2021年Jvm面试题及答案大全）.md#30介绍一下-jvm-中垃圾收集器有哪些-他们特点分别是什么)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
