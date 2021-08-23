# Jvm面试题大全带答案（2021年Jvm面试题及答案整理）

Jvm面试题及答案【最新版】Jvm高级面试题大全(2021版)，发现网上很多Jvm面试题及答案整理都没有答案，所以花了很长时间搜集，本套Jvm面试题大全，Jvm面试题大汇总，有大量经典的Jvm面试题以及答案，包含Jvm语言常见面试题、Jvm工程师高级面试题及一些大厂Jvm开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Jvm面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Jvm面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、JVM 数据运行区，哪些会造成 OOM 的情况？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#1jvm-数据运行区哪些会造成-oom-的情况)  


除了数据运行区，其他区域均有可能造成 OOM 的情况。

**堆溢出：**java.lang.OutOfMemoryError: Java heap space

**栈溢出：**java.lang.StackOverflowError

**永久代溢出：**java.lang.OutOfMemoryError: PermGen space


### [2、谈谈你知道的垃圾回收算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#2谈谈你知道的垃圾回收算法)  


**判断对象是否可回收的算法有两种：**

**1、** Reference Counting GC，引用计数算法

**2、** Tracing GC，可达性分析算法

**3、** JVM 各厂商基本都是用的 Tracing GC 实现

**4、** 大部分垃圾收集器遵从了分代收集(Generational Collection)理论。

**5、** 针对新生代与老年代回收垃圾内存的特点，提出了 3 种不同的算法：

**1、** 标记-清除算法(Mark-Sweep)

标记需回收对象，统一回收；或标记存活对象，回收未标记对象。

缺点：

大量对象需要标记与清除时，效率不高

标记、清除产生的大量不连续内存碎片，导致无法分配大对象

**2、** 标记-复制算法(Mark-Copy)

可用内存等分两块，使用其中一块 A，用完将存活的对象复制到另外一块 B，一次性清空 A，然后改分配新对象到 B，如此循环。

缺点：

不适合大量对象不可回收的情况，换句话说就是仅适合大量对象可回收，少量对象需复制的区域

只能使用内存容量的一半，浪费较多内存空间

**3、** 标记-整理算法(Mark-Compact)

标记存活的对象，统一移到内存区域的一边，清空占用内存边界以外的内存。

缺点：

移动大量存活对象并更新引用，需暂停程序运行


### [3、Java 内存分配与回收策率以及 Minor GC 和 Major GC](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#3java-内存分配与回收策率以及-minor-gc-和-major-gc)  


**1、** 对象优先在堆的 Eden 区分配

**2、** 大对象直接进入老年代

**3、** 长期存活的对象将直接进入老年代

当 Eden 区没有足够的空间进行分配时，虚拟机会执行一次 Minor GC。Minor GC 通常发生在新生代的 Eden 区，在这个区的对象生存期短，往往发生 Gc 的频率较高，回收速度比较快；Full GC/Major GC 发生在老年代，一般情况下，触发老年代 GC 的时候不会触发 Minor GC，但是通过配置，可以在 Full GC 之前进行一次 Minor GC 这样可以加快老年代的回收速度。


### [4、JVM有哪些内存区域？(JVM的内存布局是什么？)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#4jvm有哪些内存区域jvm的内存布局是什么)  


JVM包含`堆`、`元空间`、`Java虚拟机栈`、`本地方法栈`、`程序计数器`等内存区域。其中，堆是占用内存最大的一块。我们平常的`-Xmx`、`-Xms`等参数，就是针对于堆进行设计的。

**1、** 堆：JVM堆中的数据，是共享的，是占用内存最大的一块区域

**2、** 虚拟机栈：Java虚拟机栈，是基于线程的，用来服务字节码指令的运行

**3、** 程序计数器：当前线程所执行的字节码的行号指示器

**4、** 元空间：方法区就在这里，非堆本地内存：其他的内存占用空间


### [5、被引用的对象就一定能存活吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#5被引用的对象就一定能存活吗)  


不一定，看 Reference 类型，弱引用在 GC 时会被回收，软引用在内存不足的时候，即 OOM 前会被回收，但如果没有在 Reference Chain 中的对象就一定会被回收。


### [6、JVM调优命令有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#6jvm调优命令有哪些)  


jps，JVM Process Status Tool,显示指定系统内所有的HotSpot虚拟机进程。jstat，JVM statistics Monitoring是用于监视虚拟机运行时状态信息的命令，它可以显示出虚拟机进程中的类装载、内存、垃圾收集、JIT编译等运行数据。jmap，JVM Memory Map命令用于生成heap dump文件 jhat，JVM Heap Analysis Tool命令是与jmap搭配使用，用来分析jmap生成的dump，jhat内置了一个微型的HTTP/HTML服务器，生成dump的分析结果后，可以在浏览器中查看 jstack，用于生成java虚拟机当前时刻的线程快照。jinfo，JVM Conﬁguration info 这个命令作用是实时查看和调整虚拟机运行参数。


### [7、说说类加载的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#7说说类加载的过程)  


**1、** 加载（Loading），通过一个类的全限定名来获取定义此类的二进制字节流；将这个字节流所代表的静态存储结构转化为方法区的运行时数据结构；在内存中生成一个代表这个类的java.lang.Class对象，作为方法区这个类的各种数据的访问入口。

**2、** 验证（Verification），确保Class文件的字节流中包含的信息符合《Java虚拟机规范》的全部约束要求，保证这些信息被当作代码运行后不会危害虚拟机自身的安全。

**3、** 准备（Preparation），正式为类中定义的变量（即静态变量，被static修饰的变量）分配内存并设置类变量初始值。

**4、** 解析（Resolution），是 JVM 将常量池内的符号引用替换为直接引用的过程。

**5、** 初始化（Initialization），执行类构造器 <clinit方法的过程，执行所有类变量的赋值动作和静态语句块（static{}块）。

其中验证、准备、解析统称为称为连接（Linking）


### [8、Java 程序是怎样运行的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#8java-程序是怎样运行的)  


1.
首先通过 Javac 编译器将 `.java` 转为 JVM 可加载的 `.class` 字节码文件。

2.
Javac 是由 Java 编写的程序，编译过程可以分为：① 词法解析，通过空格分割出单词、操作符、控制符等信息，形成 token 信息流，传递给语法解析器。② 语法解析，把 token 信息流按照 Java 语法规则组装成语法树。③ 语义分析，检查关键字使用是否合理、类型是否匹配、作用域是否正确等。④ 字节码生成，将前面各个步骤的信息转换为字节码。

3.
字节码必须通过类加载过程加载到 JVM 后才可以执行，执行有三种模式，解释执行、JIT 编译执行、JIT 编译与解释器混合执行（主流 JVM 默认执行的方式）。混合模式的优势在于解释器在启动时先解释执行，省去编译时间。

4.
之后通过即时编译器 JIT 把字节码文件编译成本地机器码。

5.
Java 程序最初都是通过解释器进行解释执行的，当虚拟机发现某个方法或代码块的运行特别频繁，就会认定其为"热点代码"，热点代码的检测主要有基于采样和基于计数器两种方式，为了提高热点代码的执行效率，虚拟机会把它们编译成本地机器码，尽可能对代码优化，在运行时完成这个任务的后端编译器被称为即时编译器。

6.
还可以通过静态的提前编译器 AOT 直接把程序编译成与目标机器指令集相关的二进制代码。



### [9、谈谈对 OOM 的认识](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#9谈谈对-oom-的认识)  


除了程序计数器，其他内存区域都有 OOM 的风险。

**1、** 栈一般经常会发生 StackOverflowError，比如 32 位的 windows 系统单进程限制 2G 内存，无限创建线程就会发生栈的 OOM

**2、** Java 8 常量池移到堆中，溢出会出 java.lang.OutOfMemoryError: Java heap space，设置最大元空间大小参数无效

**3、** 堆内存溢出，报错同上，这种比较好理解，GC 之后无法在堆中申请内存创建对象就会报错

**4、** 方法区 OOM，经常会遇到的是动态生成大量的类、jsp 等

**5、** 直接内存 OOM，涉及到 -XX:MaxDirectMemorySize 参数和 Unsafe 对象对内存的申请


### [10、Java 虚拟机栈的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#10java-虚拟机栈的作用)  


**Java 虚拟机栈**来描述 Java 方法的内存模型。每当有新线程创建时就会分配一个栈空间，线程结束后栈空间被回收，栈与线程拥有相同的生命周期。栈中元素用于支持虚拟机进行方法调用，每个方法在执行时都会创建一个栈帧存储方法的局部变量表、操作栈、动态链接和方法出口等信息。每个方法从调用到执行完成，就是栈帧从入栈到出栈的过程。

有两类异常：① 线程请求的栈深度大于虚拟机允许的深度抛出 StackOverflowError。② 如果 JVM 栈容量可以动态扩展，栈扩展无法申请足够内存抛出 OutOfMemoryError（HotSpot 不可动态扩展，不存在此问题）。


### [11、标记整理算法(Mark-Compact)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#11标记整理算法mark-compact)  

### [12、谈谈JVM中，对类加载器的认识](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#12谈谈jvm中对类加载器的认识)  

### [13、栈帧都有哪些数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#13栈帧都有哪些数据)  

### [14、64 位 JVM 中，int 的长度是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#1464-位-jvm-中int-的长度是多数)  

### [15、程序计数器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#15程序计数器是什么)  

### [16、Tomcat是怎么打破双亲委派机制的呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#16tomcat是怎么打破双亲委派机制的呢)  

### [17、运行时栈帧包含哪些结构？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#17运行时栈帧包含哪些结构)  

### [18、GC日志的real、user、sys是什么意思？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#18gc日志的realusersys是什么意思)  

### [19、什么是程序计数器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#19什么是程序计数器)  

### [20、说说ZGC垃圾收集器的工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#20说说zgc垃圾收集器的工作原理)  

### [21、可以描述一下 class 文件的结构吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#21可以描述一下-class-文件的结构吗)  

### [22、你知道哪些JVM性能调优](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#22你知道哪些jvm性能调优)  

### [23、JVM内存模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#23jvm内存模型)  

### [24、在 Java 中，对象什么时候可以被垃圾回收？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#24在-java-中对象什么时候可以被垃圾回收)  

### [25、ParNew 垃圾收集器（Serial+多线程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#25parnew-垃圾收集器serial+多线程)  

### [26、各种回收器，各自优缺点，重点CMS、G1](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#26各种回收器各自优缺点重点cmsg1)  

### [27、对象的访问方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#27对象的访问方式有哪些)  

### [28、描述一下JVM加载class文件的原理机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#28描述一下jvm加载class文件的原理机制)  

### [29、什么是方法区](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#29什么是方法区)  

### [30、永久代](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题大全带答案（2021年Jvm面试题及答案整理）.md#30永久代)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
