# Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）

Jvm面试题及答案【最新版】Jvm高级面试题大全(2021版)，发现网上很多Jvm面试题及答案整理都没有答案，所以花了很长时间搜集，本套Jvm面试题大全，Jvm面试题大汇总，有大量经典的Jvm面试题以及答案，包含Jvm语言常见面试题、Jvm工程师高级面试题及一些大厂Jvm开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Jvm面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Jvm面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、双亲委派机制可以被违背吗？请举例说明。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#1双亲委派机制可以被违背吗请举例说明。)  


可以被违背。打破双亲委派的例子：Tomcat

对于一些需要加载的非基础类，会由一个叫作WebAppClassLoader的类加载器优先加载。等它加载不到的时候，再交给上层的ClassLoader进行加载。这个加载器用来隔绝不同应用的 .class 文件，比如你的两个应用，可能会依赖同一个第三方的不同版本，它们是相互没有影响的。


### [2、类的实例化顺序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#2类的实例化顺序)  


**1、** 父类静态成员和静态初始化块 ，按在代码中出现的顺序依次执行

**2、** 子类静态成员和静态初始化块 ，按在代码中出现的顺序依次执行

**3、** 父类实例成员和实例初始化块 ，按在代码中出现的顺序依次执行

**4、** 父类构造方法

**5、** 子类实例成员和实例初始化块 ，按在代码中出现的顺序依次执行

**6、** 子类构造方法

**检验一下是不是真懂了：**

```
public class Base {
    private String name = "博客：Soinice";

    public Base() {
        tellName();
        printName();
    }

    public void tellName() {
        System.out.println("Base tell name: " + name);
    }

    public void printName() {
        System.out.println("Base print name: " + name);
    }
}
```

```
public class Dervied extends Base {
    private String name = "Java3y";

    public Dervied() {
        tellName();
        printName();
    }

    @Override
    public void tellName() {
        System.out.println("Dervied tell name: " + name);
    }

    @Override
    public void printName() {
        System.out.println("Dervied print name: " + name);
    }

    public static void main(String[] args) {
        new Dervied();
    }
}
```

**输出数据：**

```
Dervied tell name: null
Dervied print name: null
Dervied tell name: Java3y
Dervied print name: Java3y

Process finished with exit code 0
```

第一次做错的同学点个赞，加个关注不过分吧(hahaha。


### [3、栈溢出的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#3栈溢出的原因)  


由于 HotSpot 不区分虚拟机和本地方法栈，设置本地方法栈大小的参数没有意义，栈容量只能由 `-Xss` 参数来设定，存在两种异常：

**StackOverflowError：** 如果线程请求的栈深度大于虚拟机所允许的深度，将抛出 StackOverflowError，例如一个递归方法不断调用自己。该异常有明确错误堆栈可供分析，容易定位到问题所在。

**OutOfMemoryError：** 如果 JVM 栈可以动态扩展，当扩展无法申请到足够内存时会抛出 OutOfMemoryError。HotSpot 不支持虚拟机栈扩展，所以除非在创建线程申请内存时就因无法获得足够内存而出现 OOM，否则在线程运行时是不会因为扩展而导致溢出的。


### [4、如何判断一个常量是废弃常量 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#4如何判断一个常量是废弃常量-)  


运行时常量池主要回收的是废弃的常量。假如在常量池中存在字符串 "abc"，如果当前没有任何 String 对象引用该字符串常量的话，就说明常量 "abc" 就是废弃常量，如果这时发生内存回收的话而且有必要的话，"abc" 就会被系统清理出常量池。

### [5、你知道哪些垃圾收集器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#5你知道哪些垃圾收集器)  


**序列号**

最基础的收集器，使用复制算法、单线程工作，只用一个处理器或一条线程完成垃圾收集，进行垃圾收集时必须暂停其他所有工作线程。

Serial 是虚拟机在客户端模式的默认新生代收集器，简单高效，对于内存受限的环境它是所有收集器中额外内存消耗最小的，对于处理器核心较少的环境，Serial 由于没有线程交互开销，可获得最高的单线程收集效率。

**新品**

Serial 的多线程版本，除了使用多线程进行垃圾收集外其余行为完全一致。

ParNew 是虚拟机在服务端模式的默认新生代收集器，一个重要原因是除了 Serial 外只有它能与 CMS 配合。自从 JDK 9 开始，ParNew 加 CMS 不再是官方推荐的解决方案，官方希望它被 G1 取代。

**并行清理**

新生代收集器，基于复制算法，是可并行的多线程收集器，与 ParNew 类似。

特点是它的关注点与其他收集器不同，Parallel Scavenge 的目标是达到一个可控制的吞吐量，吞吐量就是处理器用于运行用户代码的时间与处理器消耗总时间的比值。

**串行旧**

Serial 的老年代版本，单线程工作，使用标记-整理算法。

Serial Old 是虚拟机在客户端模式的默认老年代收集器，用于服务端有两种用途：① JDK5 及之前与 Parallel Scavenge 搭配。② 作为CMS 失败预案。

**平行老**

Parallel Scavenge 的老年代版本，支持多线程，基于标记-整理算法。JDK6 提供，注重吞吐量可考虑 Parallel Scavenge 加 Parallel Old。

**不育系**

以获取最短回收停顿时间为目标，基于标记-清除算法，过程相对复杂，分为四个步骤：初始标记、并发标记、重新标记、并发清除。

初始标记和重新标记需要 STW（Stop The World，系统停顿），初始标记仅是标记 GC Roots 能直接关联的对象，速度很快。并发标记从 GC Roots 的直接关联对象开始遍历整个对象图，耗时较长但不需要停顿用户线程。重新标记则是为了修正并发标记期间因用户程序运作而导致标记产生变动的那部分记录。并发清除清理标记阶段判断的已死亡对象，不需要移动存活对象，该阶段也可与用户线程并发。

缺点：① 对处理器资源敏感，并发阶段虽然不会导致用户线程暂停，但会降低吞吐量。② 无法处理浮动垃圾，有可能出现并发失败而导致 Full GC。③ 基于标记-清除算法，产生空间碎片。

**G1**

开创了收集器面向局部收集的设计思路和基于 Region 的内存布局，主要面向服务端，最初设计目标是替换 CMS。

G1 之前的收集器，垃圾收集目标要么是整个新生代，要么是整个老年代或整个堆。而 G1 可面向堆任何部分来组成回收集进行回收，衡量标准不再是分代，而是哪块内存中存放的垃圾数量最多，回收受益最大。

跟踪各 Region 里垃圾的价值，价值即回收所获空间大小以及回收所需时间的经验值，在后台维护一个优先级列表，每次根据用户设定允许的收集停顿时间优先处理回收价值最大的 Region。这种方式保证了 G1 在有限时间内获取尽可能高的收集效率。

**G1 运作过程：**

1.
初始标记：标记 GC Roots 能直接关联到的对象，让下一阶段用户线程并发运行时能正确地在可用 Region 中分配新对象。需要 STW 但耗时很短，在 Minor GC 时同步完成。

2.
并发标记：从 GC Roots 开始对堆中对象进行可达性分析，递归扫描整个堆的对象图。耗时长但可与用户线程并发，扫描完成后要重新处理 SATB 记录的在并发时有变动的对象。

3.
最终标记：对用户线程做短暂暂停，处理并发阶段结束后仍遗留下来的少量 SATB 记录。

4.
筛选回收：对各 Region 的回收价值排序，根据用户期望停顿时间制定回收计划。必须暂停用户线程，由多条收集线程并行完成。


可由用户指定期望停顿时间是 G1 的一个强大功能，但该值不能设得太低，一般设置为100~300 ms。


### [6、本地方法区(线程私有)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#6本地方法区线程私有)  


本地方法区和 Java Stack 作用类似, 区别是虚拟机栈为执行 Java 方法服务, 而本地方法栈则为Native 方法服务, 如果一个 VM 实现使用 C-linkage 模型来支持 Native 调用, 那么该栈将会是一个C 栈，但 HotSpot VM 直接就把本地方法栈和虚拟机栈合二为一 。


### [7、说说 JVM 如何执行 class 中的字节码。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#7说说-jvm-如何执行-class-中的字节码。)  


**1、** JVM 先加载包含字节码的 class 文件，存放在方法区，实际运行时，虚拟机会执行方法区内的代码。Java 虚拟机在内存中划分出栈和堆来存储运行时的数据。

**2、** 运行过程中，每当调用进入 Java 方法，都会在 Java 方法栈中生成一个栈帧，用来支持虚拟机进行方法的调用与执行，包含了局部变量表、操作数栈、动态链接、方法返回地址等信息。

**3、** 当退出当前执行的方法时，不管正常返回还是异常返回，Java 虚拟机均会弹出当前线程的当前栈帧，并将之舍弃。

**4、** 方法的调用，需要通过解析完成符号引用到直接引用；通过分派完成动态找到被调用的方法。

**5、** 从硬件角度来看，Java 字节码无法直接执行。因此，Java 虚拟机需要将字节码翻译成机器码。翻译过程由两种形式：第一种是解释执行，即将遇到的字节一边码翻译成机器码一边执行；第二种是即时编译(Just-In-Time compilation,JIT)，即将一个方法中包含的所有字节码编译成机器码后再执行。在 HotSpot 里两者都有，解释执行在启动时节约编译时间执行速度较快；随着时间的推移，编译器逐渐会返回作用，把越来越多的代码编译成本地代码后，可以获取更高的执行效率。


### [8、分代收集算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#8分代收集算法)  


当前主流 VM 垃圾收集都采用”分代收集” (Generational Collection)算法, 这种算法会根据对象存活周期的不同将内存划分为几块, 如 JVM 中的新生代、老年代、永久代， 这样就可以根据各年代特点分别采用最适当的 GC 算法


### 9、老年代

**1、** 主要存放应用程序中生命周期长的内存对象。

**2、** 老年代的对象比较稳定，所以 MajorGC 不会频繁执行。在进行 MajorGC 前一般都先进行了一次MinorGC，使得有新生代的对象晋身入老年代，导致空间不够用时才触发。当无法找到足够大的连续空间分配给新创建的较大对象时也会提前触发一次 MajorGC 进行垃圾回收腾出空间。

**3、** MajorGC 采用标记清除算法：首先扫描一次所有老年代，标记出存活的对象，然后回收没有标记的对象。ajorGC 的耗时比较长，因为要扫描再回收。MajorGC 会产生内存碎片，为了减少内存损耗，我们一般需要进行合并或者标记出来方便下次直接分配。当老年代也满了装不下的时候，就会抛出 OOM（Out of Memory）异常。


### [10、怎么查看服务器默认的垃圾回收器是哪一个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#10怎么查看服务器默认的垃圾回收器是哪一个)  


这通常会使用另外一个参数：`-XX:+PrintCommandLineFlags`可以打印所有的参数，包括使用的垃圾回收器。


### [11、OSGI（ 动态模型系统）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#11osgi-动态模型系统)  

### [12、对象是怎么从年轻代进入老年代的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#12对象是怎么从年轻代进入老年代的)  

### [13、对象分配内存的方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#13对象分配内存的方式有哪些)  

### [14、对象在哪块内存分配？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#14对象在哪块内存分配)  

### [15、类加载的过程是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#15类加载的过程是什么)  

### [16、谈谈 JVM 中的常量池](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#16谈谈-jvm-中的常量池)  

### [17、ZGC 了解吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#17zgc-了解吗)  

### [18、生产上如何配置垃圾收集器的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#18生产上如何配置垃圾收集器的)  

### [19、对象都是优先分配在年轻代上的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#19对象都是优先分配在年轻代上的吗)  

### [20、模块化编程与热插拔](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#20模块化编程与热插拔)  

### [21、JVM 运行时内存](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#21jvm-运行时内存)  

### [22、运行时数据区是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#22运行时数据区是什么)  

### [23、JVM垃圾回收时候如何确定垃圾？什么是GC Roots？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#23jvm垃圾回收时候如何确定垃圾什么是gc-roots)  

### [24、JAVA虚引用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#24java虚引用)  

### [25、对象的访问定位有哪几种方式?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#25对象的访问定位有哪几种方式)  

### [26、线上常用的 JVM 参数有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#26线上常用的-jvm-参数有哪些)  

### [27、对象分配内存是否线程安全？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#27对象分配内存是否线程安全)  

### [28、JVM新生代中为什么要分为Eden和Survivor？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#28jvm新生代中为什么要分为eden和survivor)  

### [29、说说Java 垃圾回收机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#29说说java-垃圾回收机制)  

### [30、JAVA 强引用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm高级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#30java-强引用)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
