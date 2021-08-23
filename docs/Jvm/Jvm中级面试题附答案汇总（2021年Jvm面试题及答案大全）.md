# Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）

Jvm面试题及答案【最新版】Jvm高级面试题大全(2021版)，发现网上很多Jvm面试题及答案整理都没有答案，所以花了很长时间搜集，本套Jvm面试题大全，Jvm面试题大汇总，有大量经典的Jvm面试题以及答案，包含Jvm语言常见面试题、Jvm工程师高级面试题及一些大厂Jvm开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Jvm面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Jvm面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、遇到过元空间溢出吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#1遇到过元空间溢出吗)  


元空间在本地内存上，默认是没有上限的，不加限制出了问题会影响整个服务器的，所以也是比较危险的。-XX:MaxMetaspaceSize 可以指定最大值。

一般使用动态代理的框架会生成很多 Java 类，如果占用空间超出了我们的设定最大值，会发生元空间溢出。


### [2、JVM中一次完整的GC流程是怎样的，对象如何晋升到老年代？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#2jvm中一次完整的gc流程是怎样的对象如何晋升到老年代)  


当 Eden 区的空间满了， Java虚拟机会触发一次 Minor GC，以收集新生代的垃圾，存活下来的对象，则会转移到 Survivor区。大对象（需要大量连续内存空间的Java对象，如那种很长的字符串）直接进入老年态；如果对象在Eden出生，并经过第一次Minor GC后仍然存活，并且被Survivor容纳的话，年龄设为1，每熬过一次Minor GC，年龄+1，若年龄超过一定限制（15），则被晋升到老年态。即长期存活的对象进入老年态。老年代满了而无法容纳更多的对象，Minor GC 之后通常就会进行Full GC，Full GC 清理整个内存堆 – 包括年轻代和年老代。Major GC 发生在老年代的GC，清理老年区，经常会伴随至少一次Minor GC，比Minor GC慢10倍以上。


### [3、什么情况会造成元空间溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#3什么情况会造成元空间溢出)  


元空间（Metaspace）默认是没有上限的，不加限制比较危险。当应用中的Java类过多，比如Spring等一些使用动态代理的框架生成了很多类，如果占用空间超出了`我们的设定值`，就会发生元空间溢出。

所以，默认风险大，但如果你不给足它空间，它也会溢出。


### [4、垃圾收集算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#4垃圾收集算法)  


GC最基础的算法有三种：标记 -清除算法、复制算法、标记-压缩算法，我们常用的垃圾回收器一般都采用分代收集算法。

**标记 -清除算法**

“标记-清除”（Mark-Sweep）算法，如它的名字一样，算法分为“标记”和“清除”两个阶段：首先标记出所有需要回收的对象，在标记完成后统一回收掉所有被标记的对象。

**复制算法**

“复制”（Copying）的收集算法，它将可用内存按容量划分为大小相等的两块，每次只使用其中的一块。当这一块的内存用完了，就将还存活着的对象复制到另外一块上面，然后再把已使用过的内存空间一次清理掉。

**标记-压缩算法**

标记过程仍然与“标记-清除”算法一样，但后续步骤不是直接对可回收对象进行清理，而是让所有存活的对象都向一端移动，然后直接清理掉端边界以外的内存

**分代收集算法**

“分代收集”（Generational Collection）算法，把Java堆分为新生代和老年代，这样就可以根据各个年代的特点采用最适当的收集算法


### [5、Java对象的布局了解过吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#5java对象的布局了解过吗)  


对象头区域此处存储的信息包括两部分：1、对象自身的运行时数据( MarkWord )，占8字节 存储 hashCode、GC 分代年龄、锁类型标记、偏向锁线程 ID 、 CAS 锁指向线程 LockRecord 的指针等， synconized 锁的机制与这个部分( markwork )密切相关，用 markword 中最低的三位代表锁的状态，其中一位是偏向锁位，另外两位是普通锁位。2、对象类型指针( Class Pointer )，占4字节 对象指向它的类元数据的指针、 JVM 就是通过它来确定是哪个 Class 的实例。

实例数据区域 此处存储的是对象真正有效的信息，比如对象中所有字段的内容

对齐填充区域 JVM 的实现 HostSpot 规定对象的起始地址必须是 8 字节的整数倍，换句话来说，现在 64 位的 OS 往外读取数据的时候一次性读取 64bit 整数倍的数据，也就是 8 个字节，所以 HotSpot 为了高效读取对象，就做了"对齐"，如果一个对象实际占的内存大小不是 8byte 的整数倍时，就"补位"到 8byte 的整数倍。所以对齐填充区域的大小不是固定的。


### [6、HashMap中的key，可以是普通对象么？需要什么注意的地方？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#6hashmap中的key可以是普通对象么需要什么注意的地方)  


Map的key和value都可以是任何类型。但要注意的是，一定要重写它的equals和hashCode方法，否则容易发生内存泄漏。


### [7、GC 是什么? 为什么要有 GC](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#7gc-是什么-为什么要有-gc)  


GC 是垃圾收集的意思（GabageCollection），内存处理是编程人员容易出现问题的地方，忘记或者错误的内存回收会导致程序或系统的不稳定甚至崩溃，Java 提供的 GC 功能可以自动监测对象是否超过作用域从而达到自动回收内存的目的，Java 语言没有提供释放已分配内存的显示操作方法。


### [8、有哪些类加载器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#8有哪些类加载器)  


自 JDK1.2 起 Java 一直保持三层类加载器：

**启动类加载器**

在 JVM 启动时创建，负责加载最核心的类，例如 Object、System 等。无法被程序直接引用，如果需要把加载委派给启动类加载器，直接使用 null 代替即可，因为启动类加载器通常由操作系统实现，并不存在于 JVM 体系。

**平台类加载器**

从 JDK9 开始从扩展类加载器更换为平台类加载器，负载加载一些扩展的系统类，比如 XML、加密、压缩相关的功能类等。

**应用类加载器**

也称系统类加载器，负责加载用户类路径上的类库，可以直接在代码中使用。如果没有自定义类加载器，一般情况下应用类加载器就是默认的类加载器。自定义类加载器通过继承 ClassLoader 并重写 `findClass` 方法实现。


### [9、stackoverflow错误，permgen space错误](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#9stackoverflow错误permgen-space错误)  


stackoverflow错误主要出现：

在虚拟机栈中(线程请求的栈深度大于虚拟机栈锁允许的最大深度)

permgen space错误(针对jdk之前1.7版本)：

**1、** 大量加载class文件

**2、** 常量池内存溢出


### [10、类初始化的情况有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#10类初始化的情况有哪些)  


1.
遇到 `new`、`getstatic`、`putstatic` 或 `invokestatic` 字节码指令时，还未初始化。典型场景包括 new 实例化对象、读取或设置静态字段、调用静态方法。

2.
对类反射调用时，还未初始化。

3.
初始化类时，父类还未初始化。

4.
虚拟机启动时，会先初始化包含 main 方法的主类。

5.
使用 JDK7 的动态语言支持时，如果 MethodHandle 实例的解析结果为指定类型的方法句柄且句柄对应的类还未初始化。

6.
口定义了默认方法，如果接口的实现类初始化，接口要在其之前初始化。

7.
其余所有引用类型的方式都不会触发初始化，称为被动引用。被动引用实例：① 子类使用父类的静态字段时，只有父类被初始化。② 通过数组定义使用类。③ 常量在编译期会存入调用类的常量池，不会初始化定义常量的类。

8.
接口和类加载过程的区别：初始化类时如果父类没有初始化需要初始化父类，但接口初始化时不要求父接口初始化，只有在真正使用父接口时（如引用接口中定义的常量）才会初始化。



### [11、方法区的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#11方法区的作用是什么)  

### [12、Java 中垃圾收集的方法有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#12java-中垃圾收集的方法有哪些)  

### [13、类加载器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#13类加载器)  

### [14、32 位和 64 位的 JVM，int 类型变量的长度是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#1432-位和-64-位的-jvmint-类型变量的长度是多数)  

### [15、如何找到死锁的线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#15如何找到死锁的线程)  

### [16、什么是类加载器，类加载器有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#16什么是类加载器类加载器有哪些)  

### [17、你有哪些手段来排查 OOM 的问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#17你有哪些手段来排查-oom-的问题)  

### [18、类加载是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#18类加载是什么)  

### [19、类的实例化顺序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#19类的实例化顺序)  

### [20、什么是逃逸分析？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#20什么是逃逸分析)  

### [21、Minor Gc和Full GC 有什么不同呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#21minor-gc和full-gc-有什么不同呢)  

### [22、有什么堆外内存的排查思路？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#22有什么堆外内存的排查思路)  

### 23、栈

### [24、生产环境 CPU 占用过高，你如何解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#24生产环境-cpu-占用过高你如何解决)  

### [25、简单描述一下（分代）垃圾回收的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#25简单描述一下分代垃圾回收的过程)  

### [26、什么是 Class 文件？ Class 文件主要的信息结构有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#26什么是-class-文件-class-文件主要的信息结构有哪些)  

### [27、怎样通过 Java 程序来判断 JVM 是 32 位 还是 64位？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#27怎样通过-java-程序来判断-jvm-是-32-位-还是-64位)  

### [28、如何开启和查看 GC 日志？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#28如何开启和查看-gc-日志)  

### [29、ZGC收集器中的染色指针有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#29zgc收集器中的染色指针有什么用)  

### [30、堆（Heap-线程共享） -运行时数据区](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm中级面试题附答案汇总（2021年Jvm面试题及答案大全）.md#30堆heap-线程共享--运行时数据区)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
