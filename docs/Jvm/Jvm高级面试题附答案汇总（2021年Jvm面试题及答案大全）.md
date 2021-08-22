# Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）

Jvm面试题及答案【最新版】Jvm高级面试题大全(2021版)，发现网上很多Jvm面试题及答案整理都没有答案，所以花了很长时间搜集，本套Jvm面试题大全，Jvm面试题大汇总，有大量经典的Jvm面试题以及答案，包含Jvm语言常见面试题、Jvm工程师高级面试题及一些大厂Jvm开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Jvm面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Jvm面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、程序计数器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#1程序计数器)  


保存着当前线程执行的字节码位置,每个线程工作时都有独立的计数器,只为执行Java方法服务,执行Native方法时,程序计数器为空.


### [2、常用JVM基本配置参数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#2常用jvm基本配置参数)  


**1、** -Xmx：最大分配内存，默认为物理内存的1/4

**2、** -Xms：初始分配内存，默认为物理内存的1/64

**3、** -Xss：等价于-XX:ThreadStackSize，单个线程栈空间大小，默认一般为512k-1024k，通过jinfo查看为0时，表示使用默认值

**4、** -Xmn：设置年轻代大小

**5、** -XX:MetaspeaceSize：设置元空间大小（默认21M左右，可以配置大一些），元空间的本质可永久代类似，都是对JVM规范中方法区的实现，不过元空间与永久代的最大区别在于：元空间不在虚拟机中，而是使用本地内存，因此，默认情况下，元空间大小仅受本地内存大小限制

**6、** 典型设置案例：-Xms128m -Xmx4096m -Xss1024k -XX:MetaspaceSize=512m -XX:+PrintCommandLineFlags -XX:+PrintGCDetails -XX:+UseSerialGC

**7、** -XX:+PrintGCDetails：打印垃圾回收细节，打印GC： 打印Full GC：

**8、** -XX:SurvivorRatio：调整Eden中survivor区比例，默认-XX:SurvivorRatio=8（8:1:1），调整为-XX:SurvivorRatio=4（4:1:1）,一般使用默认值

**9、** -XX:NewRatio：调整新生代与老年代的比例，默认为2（新生代1，老年代2，年轻代占整个堆的1/3）,调整为-XX:NewRatio=4表示（新生代1，老年代4，年轻代占堆的1/5）,一般使用默认值

**10、** -XX:MaxTenuringThreshold：设置垃圾的最大年龄（经历多少次垃圾回收进入老年代），默认15（15次垃圾回收后依旧存活的对象进入老年代），JDK1.8设置必须0<-XX:MaxTenuringThreshold<15


### [3、创建对象的过程是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#3创建对象的过程是什么)  


**字节码角度**

**NEW**

如果找不到 Class 对象则进行类加载。加载成功后在堆中分配内存，从 Object 到本类路径上的所有属性都要分配。分配完毕后进行零值设置。最后将指向实例对象的引用变量压入虚拟机栈顶。

**DUP：**

在栈顶复制引用变量，这时栈顶有两个指向堆内实例的引用变量。两个引用变量的目的不同，栈底的引用用于赋值或保存局部变量表，栈顶的引用作为句柄调用相关方法。

**INVOKESPECIAL**

通过栈顶的引用变量调用 init 方法。

**执行角度**

1.
当 JVM 遇到字节码 new 指令时，首先将检查该指令的参数能否在常量池中定位到一个类的符号引用，并检查引用代表的类是否已被加载、解析和初始化，如果没有就先执行类加载。

2.
在类加载检查通过后虚拟机将为新生对象分配内存。

3.
内存分配完成后虚拟机将成员变量设为零值，保证对象的实例字段可以不赋初值就使用。

4.
设置对象头，包括哈希码、GC 信息、锁信息、对象所属类的类元信息等。

5.
执行 init 方法，初始化成员变量，执行实例化代码块，调用类的构造方法，并把堆内对象的首地址赋值给引用变量。



### [4、说说你知道的几种主要的JVM参数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#4说说你知道的几种主要的jvm参数)  


**1、** 堆栈配置相关 -Xmx3550m：最大堆大小为3550m。-Xms3550m：设置初始堆大小为3550m。-Xmn2g：设置年轻代大小为2g。-Xss128k：每个线程的堆栈大小为128k。-XX:MaxPermSize：设置持久代大小为16m -XX:NewRatio=4: 设置年轻代（包括Eden和两个Survivor区）与年老代的比值（除去持久代）。-XX:SurvivorRatio=4：设置年轻代中Eden区与Survivor区的大小比值。设置为4，则两个Survivor区与一个Eden区的比值为2:4，一个Survivor区占整个年轻代的1/6 -XX:MaxTenuringThreshold=0：设置垃圾最大年龄。如果设置为0的话，则年轻代对象不经过Survivor区，直接进入年老代。

**2、** 垃圾收集器相关 -XX:+UseParallelGC：选择垃圾收集器为并行收集器。-XX:ParallelGCThreads=20：配置并行收集器的线程数 -XX:+UseConcMarkSweepGC：设置年老代为并发收集。-XX:CMSFullGCsBeforeCompaction：由于并发收集器不对内存空间进行压缩、整理，所以运行一段时间以后会产生“碎片”，使得运行效率降低。此值设置运行多少次GC以后对内存空间进行压缩、整理。-XX:+UseCMSCompactAtFullCollection：打开对年老代的压缩。可能会影响性能，但是可以消除碎片

**3、** 辅助信息相关 -XX:+PrintGC 输出形式: [GC 118250K->113543K(130112K), 0.0094143 secs] [Full GC 121376K->10414K(130112K), 0.0650971 secs]

**4、** -XX:+PrintGCDetails 输出形式: [GC [DefNew: 8614K->781K(9088K), 0.0123035 secs] 118250K->113543K(130112K), 0.0124633 secs] [GC [DefNew: 8614K->8614K(9088K), 0.0000665 secs][Tenured: 112761K->10414K(121024K), 0.0433488 secs] 121376K->10414K(130112K), 0.0436268 secs


### [5、说说CMS垃圾收集器的工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#5说说cms垃圾收集器的工作原理)  


Concurrent mark sweep(CMS)收集器是一种年老代垃圾收集器，其最主要目标是获取最短垃圾回收停顿时间， 和其他年老代使用标记-整理算法不同，它使用多线程的标记-清除算法。最短的垃圾收集停顿时间可以为交互比较高的程序提高用户体验。CMS 工作机制相比其他的垃圾收集器来说更复杂

**整个过程分为以下 4 个阶段：**

**1、** 初始标记 只是标记一下 GC Roots 能直接关联的对象，速度很快，仍然需要暂停所有的工作线程。

**2、** 并发标记 进行 GC Roots 跟踪的过程，和用户线程一起工作，不需要暂停工作线程。

**3、** 重新标记 为了修正在并发标记期间，因用户程序继续运行而导致标记产生变动的那一部分对象的标记记录，仍然需要暂停所有的工作线程。

**4、** 并发清除 清除 GC Roots 不可达对象，和用户线程一起工作，不需要暂停工作线程。由于耗时最长的并发标记和并发清除过程中，垃圾收集线程可以和用户线程一起并发工作， 所以总体上来看CMS 收集器的内存回收和用户线程是一起并发地执行。


### [6、在老年代-标记整理算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#6在老年代-标记整理算法)  


因为对象存活率高、没有额外空间对它进行分配担保, 就必须采用“标记—清理”或“标记—整理” 算法来进行回收, 不必进行内存复制, 且直接腾出空闲内存。


### [7、垃圾回收器的基本原理是什么？垃圾回收器可以马上回收内存吗？有什么办法主动通知虚拟机进行垃圾回收？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#7垃圾回收器的基本原理是什么垃圾回收器可以马上回收内存吗有什么办法主动通知虚拟机进行垃圾回收)  


对于 GC 来说，当程序员创建对象时，GC 就开始监控这个对象的地址、大小以及使用情况。通常，GC 采用有向图的方式记录和管理堆（heap）中的所有对象。通过这种方式确定哪些对象是”可达的”，哪些对象是”不可达的”。当 GC 确定一些对象为“不可达”时，GC 就有责任回收这些内存空间。可以。程序员可以手动执行 System.gc()，通知 GC 运行，但是 Java 语言规范并不保证 GC 一定会执行。


### [8、什么是Java虚拟机？为什么Java被称作是“平台无关的编程语言”？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#8什么是java虚拟机为什么java被称作是“平台无关的编程语言)  


Java虚拟机是一个可以执行Java字节码的虚拟机进程。Java源文件被编译成能被Java虚拟机执行的字节码文件。Java被设计成允许应用程序可以运行在任意的平台，而不需要程序员为每一个平台单独重写或者是重新编译。Java虚拟机让这个变为可能，因为它知道底层硬件平台的指令长度和其他特性。


### [9、你都用过G1垃圾回收器的哪几个重要参数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#9你都用过g1垃圾回收器的哪几个重要参数)  


最重要的是`MaxGCPauseMillis`，可以通过它设定G1的目标停顿时间，它会尽量的去达成这个目标。G1HeapRegionSize可以设置小堆区的大小，一般是2的次幂。

`InitiatingHeapOccupancyPercent`，启动并发GC时的堆内存占用百分比。G1用它来触发并发GC周期，基于整个堆的使用率，而不只是某一代内存的使用比例，默认是45%。

再多？不是专家，就没必要要求别人也是。


### [10、什么是方法内联？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#10什么是方法内联)  


为了减少方法调用的开销，可以把一些短小的方法，纳入到目标方法的调用范围之内，这样就少了一次方法调用，提升速度


### [11、什么是内存屏障？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#11什么是内存屏障)  

### 12、堆
### [13、JVM 如何确定垃圾对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#13jvm-如何确定垃圾对象)  

### [14、说一下堆内存中对象的分配的基本策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#14说一下堆内存中对象的分配的基本策略)  

### [15、Java 中 WeakReference 与 SoftReference 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#15java-中-weakreference-与-softreference-的区别)  

### [16、JVM 提供的常用工具](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#16jvm-提供的常用工具)  

### [17、说说线程栈](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#17说说线程栈)  

### [18、说一下 JVM 调优的工具？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#18说一下-jvm-调优的工具)  

### [19、运行时常量池溢出的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#19运行时常量池溢出的原因)  

### [20、你知道哪些GC类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#20你知道哪些gc类型)  

### [21、invokedynamic指令是干什么的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#21invokedynamic指令是干什么的)  

### [22、堆溢出的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#22堆溢出的原因)  

### [23、JVM垃圾回收机制，何时触发MinorGC等操作](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#23jvm垃圾回收机制何时触发minorgc等操作)  

### [24、G1 收集器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#24g1-收集器)  

### [25、如何判断一个对象是否存活](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#25如何判断一个对象是否存活)  

### [26、强引用、软引用、弱引用、虚引用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#26强引用软引用弱引用虚引用是什么)  

### [27、JAVA软引用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#27java软引用)  

### [28、堆和栈的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#28堆和栈的区别)  

### [29、GC的回收流程是怎样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#29gc的回收流程是怎样的)  

### [30、什么时候会触发FullGC](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#30什么时候会触发fullgc)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
