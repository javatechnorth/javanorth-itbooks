# Jvm面试题附答案（2021年Jvm面试题及答案大汇总）

Jvm面试题及答案【最新版】Jvm高级面试题大全(2021版)，发现网上很多Jvm面试题及答案整理都没有答案，所以花了很长时间搜集，本套Jvm面试题大全，Jvm面试题大汇总，有大量经典的Jvm面试题以及答案，包含Jvm语言常见面试题、Jvm工程师高级面试题及一些大厂Jvm开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Jvm面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Jvm面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、标记清除算法（ Mark-Sweep）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#1标记清除算法-mark-sweep)  


最基础的垃圾回收算法，分为两个阶段，标注和清除。标记阶段标记出所有需要回收的对象，清除阶段回收被标记的对象所占用的空间。

从图中我们就可以发现，该算法最大的问题是内存碎片化严重，后续可能发生大对象不能找到可利用空间的问题。


### [2、Serial Old 收集器（单线程标记整理算法 ）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#2serial-old-收集器单线程标记整理算法-)  


Serial Old 是 Serial 垃圾收集器年老代版本，它同样是个单线程的收集器，使用标记-整理算法，这个收集器也主要是运行在 Client 默认的

**java 虚拟机默认的年老代垃圾收集器。在 Server 模式下，主要有两个用途：**

**1、** 在 JDK1.5 之前版本中与新生代的 Parallel Scavenge 收集器搭配使用。

**2、** 作为年老代中使用 CMS 收集器的后备垃圾收集方案。新生代 Serial 与年老代 Serial Old 搭配垃圾收集

新生代 Parallel Scavenge 收集器与 ParNew 收集器工作原理类似，都是多线程的收集器，都使用的是复制算法，在垃圾收集过程中都需要暂停所有的工作线程。新生代 ParallelScavenge/ParNew 与年老代 Serial Old 搭配垃圾收集过程图：


### [3、你都有哪些手段用来排查内存溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#3你都有哪些手段用来排查内存溢出)  


（这个话题很大，可以从实践环节中随便摘一个进行总结，下面举例一个最普通的）

你可以来一个中规中矩的回

内存溢出包含很多种情况，我在平常工作中遇到最多的就是`堆溢出`。有一次线上遇到故障，重新启动后，使用jstat命令，发现Old区在一直增长。我使用jmap命令，导出了一份线上堆栈，然后使用`MAT`进行分析。通过对`GC Roots`的分析，我发现了一个非常大的HashMap对象，这个原本是有位同学`做缓存`用的，但是一个无界缓存，造成了堆内存占用一直上升。后来，将这个缓存改成 guava的Cache，并设置了弱引用，故障就消失了。

这个回答不是十分出彩，但着实是常见问题，让人挑不出毛病。


### [4、类加载为什么要使用双亲委派模式，有没有什么场景是打破了这个模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#4类加载为什么要使用双亲委派模式有没有什么场景是打破了这个模式)  


**双亲委托模型的重要用途是为了解决类载入过程中的安全性问题。**

**1、** 假设有一个开发者自己编写了一个名为`java.lang.Object`的类，想借此欺骗JVM。现在他要使用自定义`ClassLoader`来加载自己编写的`java.lang.Object`类。

**2、** 然而幸运的是，双亲委托模型不会让他成功。因为JVM会优先在`Bootstrap ClassLoader`的路径下找到`java.lang.Object`类，并载入它

Java的类加载是否一定遵循双亲委托模型？

**1、** 在实际开发中，我们可以通过自定义ClassLoader，并重写父类的loadClass方法，来打破这一机制。

**2、** SPI就是打破了双亲委托机制的(SPI：服务提供发现)。


### [5、描述一下 JVM 加载 class 文件的原理机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#5描述一下-jvm-加载-class-文件的原理机制)  


**1、** JVM 中类的装载是由类加载器（ClassLoader）和它的子类来实现的，Java 中各类加载器是一个重要的 Java 运行时系统组件，它负责在运行时查找和装入类文件中的类。

**2、** 由于 Java 的跨平台性，经过编译的 Java 源程序并不是一个可执行程序，而是一个或多个类文件。当 Java 程序需要使用某个类时，JVM 会确保这个类已经被加载、连接（验证、准备和解析）和初始化。类的加载是指把类的.class 文件中的数据读入到内存中，通常是创建一个字节数组读入.class 文件，然后产生与所加载类对应的 Class 对象。

**3、** 加载完成后，Class 对象还不完整，所以此时的类还不可用。当类被加载后就进入连接阶段，这一阶段包括验证、准备（为静态变量分配内存并设置默认的初始值）和解析（将符号引用替换为直接引用）三个步骤。最后 JVM 对类进行初始化，包括：1)如果类存在直接的父类并且这个类还没有被初始化，那么就先初始化父类；2)如果类中存在初始化语句，就依次执行这些初始化语句。

**4、** 类的加载是由类加载器完成的，类加载器包括：根加载器（BootStrap）、扩展加载器（Extension）、系统加载器（System）和用户自定义类加载器（java.lang.ClassLoader 的子类）。

**5、** 从 Java 2（JDK 1.2）开始，类加载过程采取了父亲委托机制（PDM）。PDM 更好的保证了 Java 平台的安全性，在该机制中，JVM 自带的Bootstrap 是根加载器，其他的加载器都有且仅有一个父类加载器。类的加载首先请求父类加载器加载，父类加载器无能为力时才由其子类加载器自行加载。JVM 不会向 Java 程序提供对 Bootstrap 的引用。下面是关于几个类

**加载器的说明：**

**1、** Bootstrap：一般用本地代码实现，负责加载 JVM 基础核心类库（rt.jar）；

**2、** Extension：从 java.ext.dirs 系统属性所指定的目录中加载类库，它的父加载器是 Bootstrap；

**3、** System：又叫应用类加载器，其父类是 Extension。它是应用最广泛的类加载器。它从环境变量 classpath 或者系统属性

java.class.path 所指定的目录中记载类，是用户自定义加载器的默认父加载器。


### [6、能够找到 Reference Chain 的对象，就一定会存活么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#6能够找到-reference-chain-的对象就一定会存活么)  


这不一定，还要看reference类型。弱引用会在GC时会被回收，软引用会在内存不足的时候被回收。但没有Reference Chain的对象就一定会被回收。


### [7、类加载器双亲委派模型机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#7类加载器双亲委派模型机制)  


**基本定义：**

双亲委派模型的工作流程是：如果一个类加载器收到了类加载的请求，它首先不会自己去加载这个类，而是把请求委托给父加载器去完成，依次向上，因此，所有的类加载请求最终都应该被传递到顶层的启动类加载器中，只有当父加载器没有找到所需的类时，子加载器才会尝试去加载该类。

**双亲委派机制:**

**1、** 当 AppClassLoader 加载一个 class 时，它首先不会自己去尝试加载这个类，而是把类加载请求委派给父类加载器 ExtClassLoader 去完成。

**2、** 当 ExtClassLoader 加载一个 class 时，它首先也不会自己去尝试加载这个类，而是把类加载请求委派给 BootStrapClassLoader 去完成。

**3、** 如果 BootStrapClassLoader 加载失败，会使用 ExtClassLoader 来尝试加载；

**4、** 若 ExtClassLoader 也加载失败，则会使用 AppClassLoader 来加载，如果 AppClassLoader 也加载失败，则会报出异常 ClassNotFoundException。

**如下图所示：**

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/05/34/39_4.png#alt=39%5C_4.png)

**双亲委派作用：**

**1、** 通过带有优先级的层级关可以避免类的重复加载；

**2、** 保证 Java 程序安全稳定运行，Java 核心 API 定义类型不会被随意替换。


### [8、字符串常量存放在哪个区域？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#8字符串常量存放在哪个区域)  


**1、** 字符串常量池，已经移动到堆上（jdk8之前是perm区），也就是执行intern方法后存的地方。

**2、** 类文件常量池，constant_pool，是每个类每个接口所拥有的，这部分数据在方法区，也就是元数据区。而运行时常量池是在类加载后的一个内存区域，它们都在元空间。


### [9、你知道哪些内存分配与回收策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#9你知道哪些内存分配与回收策略)  


**对象优先在 Eden 区分配**

大多数情况下对象在新生代 Eden 区分配，当 Eden 没有足够空间时将发起一次 Minor GC。

**大对象直接进入老年代**

大对象指需要大量连续内存空间的对象，典型是很长的字符串或数量庞大的数组。大对象容易导致内存还有不少空间就提前触发垃圾收集以获得足够的连续空间。

HotSpot 提供了 `-XX:PretenureSizeThreshold` 参数，大于该值的对象直接在老年代分配，避免在 Eden 和 Survivor 间来回复制。

**长期存活对象进入老年代**

虚拟机给每个对象定义了一个对象年龄计数器，存储在对象头。如果经历过第一次 Minor GC 仍然存活且能被 Survivor 容纳，该对象就会被移动到 Survivor 中并将年龄设置为 1。对象在 Survivor 中每熬过一次 Minor GC 年龄就加 1 ，当增加到一定程度（默认15）就会被晋升到老年代。对象晋升老年代的阈值可通过 `-XX:MaxTenuringThreshold` 设置。

**动态对象年龄判定**

为了适应不同内存状况，虚拟机不要求对象年龄达到阈值才能晋升老年代，如果在 Survivor 中相同年龄所有对象大小的总和大于 Survivor 的一半，年龄不小于该年龄的对象就可以直接进入老年代。

**空间分配担保**

MinorGC 前虚拟机必须检查老年代最大可用连续空间是否大于新生代对象总空间，如果满足则说明这次 Minor GC 确定安全。

如果不满足，虚拟机会查看 `-XX:HandlePromotionFailure` 参数是否允许担保失败，如果允许会继续检查老年代最大可用连续空间是否大于历次晋升老年代对象的平均大小，如果满足将冒险尝试一次 Minor GC，否则改成一次 FullGC。

冒险是因为新生代使用复制算法，为了内存利用率只使用一个 Survivor，大量对象在 Minor GC 后仍然存活时，需要老年代进行分配担保，接收 Survivor 无法容纳的对象。


### [10、Java 8 为什么要将永久代(PermGen)替换为元空间(MetaSpace)呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#10java-8-为什么要将永久代permgen替换为元空间metaspace呢)  


整个永久代有一个 JVM 本身设置固定大小上线，无法进行调整，而元空间使用的是直接内存，受本机可用内存的限制，并且永远不会出现java.lang.OutOfMemoryError。你可以使用 -XX：MaxMetaspaceSize 标志设置最大元空间大小，默认值为 unlimited，这意味着它只受系统内存的限制。-XX：MetaspaceSize 调整标志定义元空间的初始大小如果未指定此标志，则 Metaspace 将根据运行时的应用程序需求动态地重新调整大小。


### [11、谈谈永久代](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#11谈谈永久代)  

### [12、简述Java的对象结构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#12简述java的对象结构)  

### [13、SWAP会影响性能么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#13swap会影响性能么)  

### [14、列举一些你知道的打破双亲委派机制的例子。为什么要打破？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#14列举一些你知道的打破双亲委派机制的例子。为什么要打破)  

### [15、内存溢出和内存泄漏的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#15内存溢出和内存泄漏的区别)  

### [16、对于JDK自带的监控和性能分析工具用过哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#16对于jdk自带的监控和性能分析工具用过哪些)  

### [17、Serial 垃圾收集器（单线程、 复制算法）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#17serial-垃圾收集器单线程-复制算法)  

### [18、GC垃圾回收算法与垃圾收集器的关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#18gc垃圾回收算法与垃圾收集器的关系)  

### [19、方法区/永久代（线程共享）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#19方法区/永久代线程共享)  

### [20、safepoint 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#20safepoint-是什么)  

### [21、什么是双亲委派机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#21什么是双亲委派机制)  

### [22、垃圾回收的优点和原理。说说2种回收机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#22垃圾回收的优点和原理。说说2种回收机制)  

### [23、程序计数器(线程私有)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#23程序计数器线程私有)  

### [24、为什么需要双亲委派模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#24为什么需要双亲委派模式)  

### [25、介绍一下类文件结构吧！](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#25介绍一下类文件结构吧)  

### [26、哪些是 GC Roots？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#26哪些是-gc-roots)  

### [27、MinorGC、MajorGC、FullGC 什么时候发生？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#27minorgcmajorgcfullgc-什么时候发生)  

### [28、方法区溢出的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#28方法区溢出的原因)  

### [29、如何判断对象可以被回收](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#29如何判断对象可以被回收)  

### [30、Java 中堆和栈有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#30java-中堆和栈有什么区别)  

### [31、本地方法栈的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题附答案（2021年Jvm面试题及答案大汇总）.md#31本地方法栈的作用)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
