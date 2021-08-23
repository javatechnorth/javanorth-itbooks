# Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）

Jvm面试题及答案【最新版】Jvm高级面试题大全(2021版)，发现网上很多Jvm面试题及答案整理都没有答案，所以花了很长时间搜集，本套Jvm面试题大全，Jvm面试题大汇总，有大量经典的Jvm面试题以及答案，包含Jvm语言常见面试题、Jvm工程师高级面试题及一些大厂Jvm开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Jvm面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Jvm面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Java的内存模型是什么？（JMM是什么？）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#1java的内存模型是什么jmm是什么)  


JVM试图定义一种统一的内存模型，能将各种底层硬件及操作系统的内存访问差异进行封装，使Java程序在不同硬件及操作系统上都能达到相同的并发效果。它分为工作内存和主内存，线程无法对主存储器**直接**进行操作，一个线程要和另外一个线程通信，只能通过主存进行交换。

JMM可以说是Java并发的基础，它的定义将直接影响多线程实现的机制，如果你想要想深入了解多线程并发中的相关问题现象，对JMM的深入研究是必不可少的。

上面两个问题是经常容易搞混的，但它们的内容却完全不同的。


### [2、CMS分为哪几个阶段?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#2cms分为哪几个阶段)  


CMS已经弃用。生活美好，时间有限，不建议再深入研究了。如果碰到问题，直接祭出回收过程即可。

**1、** 初始标记

**2、** 并发标记

**3、** 并发预清理

**4、** 并发可取消的预清理

**5、** 重新标记

**6、** 并发清理

由于《深入理解java虚拟机》一书的流行，面试时省略3、4步一般也是没问题的。


### [3、GC Roots 有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#3gc-roots-有哪些)  


**1、** GC Roots 是一组必须活跃的引用。用通俗的话来说，就是程序接下来通过直接引用或者间接引用，能够访问到的潜在被使用的对象。

**2、** GC Roots 包括：Java 线程中，当前所有正在被调用的方法的引用类型参数、局部变量、临时值等。也就是与我们栈帧相关的各种引用。所有当前被加载的 Java 类。Java 类的引用类型静态变量。运行时常量池里的引用类型常量（String 或 Class 类型）。JVM 内部数据结构的一些引用，比如 sun.jvm.hotspot.memory.Universe 类。用于同步的监控对象，比如调用了对象的 wait() 方法。JNI handles，包括 global handles 和 local handles。

**3、** 这些 GC Roots 大体可以分为三大类，下面这种说法更加好记一些：活动线程相关的各种引用。类的静态变量的引用。JNI 引用。

**4、** 有两个注意点：我们这里说的是活跃的引用，而不是对象，对象是不能作为 GC Roots 的。GC 过程是找出所有活对象，并把其余空间认定为“无用”；而不是找出所有死掉的对象，并回收它们占用的空间。所以，哪怕 JVM 的堆非常的大，基于 tracing 的 GC 方式，回收速度也会非常快。


### [4、如何判断两个类是否相等？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#4如何判断两个类是否相等)  


任意一个类都必须由类加载器和这个类本身共同确立其在虚拟机中的唯一性。

两个类只有由同一类加载器加载才有比较意义，否则即使两个类来源于同一个 Class 文件，被同一个 JVM 加载，只要类加载器不同，这两个类就必定不相等。


### [5、JVM 类加载机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#5jvm-类加载机制)  


JVM 类加载机制分为五个部分：加载，验证，准备，解析，初始化。

**加载**

加载是类加载过程中的一个阶段， 这个阶段会在内存中生成一个代表这个类的 java.lang.Class 对象， 作为方法区这个类的各种数据的入口。注意这里不一定非得要从一个 Class 文件获取，这里既可以从 ZIP 包中读取（比如从 jar 包和 war 包中读取），也可以在运行时计算生成（动态代理），也可以由其它文件生成（比如将 JSP 文件转换成对应的 Class 类）。

**验证**

这一阶段的主要目的是为了确保 Class 文件的字节流中包含的信息是否符合当前虚拟机的要求，并且不会危害虚拟机自身的安全。

**准备**

准备阶段是正式为类变量分配内存并设置类变量的初始值阶段，即在方法区中分配这些变量所使用的内存空间。注意这里所说的初始值概念，比如一个类变量定义为：

实际上变量 v 在准备阶段过后的初始值为 0 而不是 8080， 将 v 赋值为 8080 的 put static 指令是程序被编译后， 存放于类构造器方法之中。

**但是注意如果声明为：**

public static final int v = 8080;

在编译阶段会为 v 生成 ConstantValue 属性，在准备阶段虚拟机会根据 ConstantValue 属性将 v赋值为 8080。

**解析**

解析阶段是指虚拟机将常量池中的符号引用替换为直接引用的过程。符号引用就是 class 文件中的

public static int v = 8080;

实际上变量 v 在准备阶段过后的初始值为 0 而不是 8080， 将 v 赋值为 8080 的 put static 指令是程序被编译后， 存放于类构造器方法之中。但是注意如果声明为：

在编译阶段会为 v 生成 ConstantValue 属性，在准备阶段虚拟机会根据 ConstantValue 属性将 v赋值为 8080。

**解析**

解析阶段是指虚拟机将常量池中的符号引用替换为直接引用的过程。符号引用就是 class 文件中的

public static final int v = 8080;

在编译阶段会为 v 生成 ConstantValue 属性，在准备阶段虚拟机会根据 ConstantValue 属性将 v赋值为 8080。

**解析**

解析阶段是指虚拟机将常量池中的符号引用替换为直接引用的过程。符号引用就是 class 文件中的：

**1、** CONSTANT_Class_info

**2、** CONSTANT_Field_info

**3、** CONSTANT_Method_info

等类型的常量。

**符号引用**

符号引用与虚拟机实现的布局无关， 引用的目标并不一定要已经加载到内存中。各种虚拟机实现的内存布局可以各不相同，但是它们能接受的符号引用必须是一致的，因为符号引用的字面量形式明确定义在 Java 虚拟机规范的 Class 文件格式中。

**直接引用**

直接引用可以是指向目标的指针，相对偏移量或是一个能间接定位到目标的句柄。如果有了直接引用，那引用的目标必定已经在内存中存在。

**初始化**

初始化阶段是类加载最后一个阶段，前面的类加载阶段之后，除了在加载阶段可以自定义类加载器以外，其它操作都由 JVM 主导。到了初始阶段，才开始真正执行类中定义的 Java 程序代码。

**类构造器**

初始化阶段是执行类构造器方法的过程。方法是由编译器自动收集类中的类变量的赋值操作和静态语句块中的语句合并而成的。虚拟机会保证子方法执行之前，父类的方法已经执行完毕， 如果一个类中没有对静态变量赋值也没有静态语句块，那么编译器可以不为这个类生成()方法。

**注意以下几种情况不会执行类初始化：**

**1、** 通过子类引用父类的静态字段，只会触发父类的初始化，而不会触发子类的初始化。

**2、** 定义对象数组，不会触发该类的初始化。

**3、** 常量在编译期间会存入调用类的常量池中，本质上并没有直接引用定义常量的类，不会触发定义常量所在的类。

**4、** 通过类名获取 Class 对象，不会触发类的初始化。

**5、** 通过 Class.forName 加载指定类时，如果指定参数 initialize 为 false 时，也不会触发类初始化，其实这个参数是告诉虚拟机，是否要对类进行初始化。

**6、** 通过 ClassLoader 默认的 loadClass 方法，也不会触发初始化动作。


### [6、怎么看死锁的线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#6怎么看死锁的线程)  


通过jstack命令，可以获得线程的栈信息。死锁信息会在非常明显的位置（一般是最后）进行提示。


### [7、什么是分布式垃圾回收（DGC）？它是如何工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#7什么是分布式垃圾回收dgc它是如何工作的)  


DGC 叫做分布式垃圾回收。RMI 使用 DGC 来做自动垃圾回收。因为 RMI 包含了跨虚拟机的远程对象的引用，垃圾回收是很困难的。DGC 使用引用计数算法来给远程对象提供自动内存管理。


### [8、invokedynamic 指令是干什么的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#8invokedynamic-指令是干什么的)  


Java 7 开始，新引入的字节码指令，可以实现一些动态类型语言的功能。Java 8 的 Lambda 表达式就是通过 invokedynamic 指令实现，使用方法句柄实现。


### [9、Java 的引用有哪些类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#9java-的引用有哪些类型)  


JDK1.2 后对引用进行了扩充，按强度分为四种：

**强引用：** 最常见的引用，例如 `Object obj = new Object()` 就属于强引用。只要对象有强引用指向且 GC Roots 可达，在内存回收时即使濒临内存耗尽也不会被回收。

**软引用：** 弱于强引用，描述非必需对象。在系统将发生内存溢出前，会把软引用关联的对象加入回收范围以获得更多内存空间。用来缓存服务器中间计算结果及不需要实时保存的用户行为等。

**弱引用：** 弱于软引用，描述非必需对象。弱引用关联的对象只能生存到下次 YGC 前，当垃圾收集器开始工作时无论当前内存是否足够都会回收只被弱引用关联的对象。由于 YGC 具有不确定性，因此弱引用何时被回收也不确定。

**虚引用：** 最弱的引用，定义完成后无法通过该引用获取对象。唯一目的就是为了能在对象被回收时收到一个系统通知。虚引用必须与引用队列联合使用，垃圾回收时如果出现虚引用，就会在回收对象前把这个虚引用加入引用队列。


### [10、栈帧里面包含哪些东西？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#10栈帧里面包含哪些东西)  


局部变量表、操作数栈、动态连接、返回地址等


### [11、Java 中会存在内存泄漏?简述一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#11java-中会存在内存泄漏简述一下)  

### [12、谈谈双亲委派模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#12谈谈双亲委派模型)  

### [13、什么情况发生栈溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#13什么情况发生栈溢出)  

### [14、JAVA8 与元数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#14java8-与元数据)  

### [15、假如生产环境CPU占用过高，请谈谈你的分析思路和定位。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#15假如生产环境cpu占用过高请谈谈你的分析思路和定位。)  

### [16、如何查看 JVM 当前使用的是什么垃圾收集器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#16如何查看-jvm-当前使用的是什么垃圾收集器)  

### [17、程序计数器为什么是私有的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#17程序计数器为什么是私有的)  

### [18、JVM 年轻代到年老代的晋升过程的判断条件是什么呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#18jvm-年轻代到年老代的晋升过程的判断条件是什么呢)  

### [19、请解释StackOverflowError和OutOfMemeryError的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#19请解释stackoverflowerror和outofmemeryerror的区别)  

### [20、可达性分析](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#20可达性分析)  

### [21、什么是堆](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#21什么是堆)  

### [22、Java 堆的结构是什么样子的？什么是堆中的永久代（Perm Gen space）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#22java-堆的结构是什么样子的什么是堆中的永久代perm-gen-space)  

### [23、双亲委派模型是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#23双亲委派模型是什么)  

### [24、详细介绍一下JVM内存模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#24详细介绍一下jvm内存模型)  

### [25、什么情况下会发生栈溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#25什么情况下会发生栈溢出)  

### [26、分区收集算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#26分区收集算法)  

### [27、JIT是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#27jit是什么)  

### [28、直接内存是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#28直接内存是什么)  

### [29、你熟悉哪些垃圾收集算法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#29你熟悉哪些垃圾收集算法)  

### [30、JVM 出现 fullGC 很频繁，怎么去线上排查问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#30jvm-出现-fullgc-很频繁怎么去线上排查问题)  

### [31、谈谈你知道的垃圾收集器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题汇总及答案（2021年Jvm面试题及答案大全）.md#31谈谈你知道的垃圾收集器)  





