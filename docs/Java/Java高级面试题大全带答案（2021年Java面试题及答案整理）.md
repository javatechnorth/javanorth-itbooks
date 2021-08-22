# Java高级面试题大全带答案（2021年Java面试题及答案整理）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、volatile 变量和 atomic 变量有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#1volatile-变量和-atomic-变量有什么不同)  


volatile 变量可以确保先行关系，即写操作会发生在后续的读操作之前, 但它并不能保证原子性。例如用 volatile 修饰 count 变量，那么 count++ 操作就不是原子性的。

而 AtomicInteger 类提供的 atomic 方法可以让这种操作具有原子性如getAndIncrement()方法会原子性的进行增量操作把当前值加一，其它数据类型和引用变量也可以进行相似操作。


### [2、堆和栈的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#2堆和栈的区别)  


栈是运行时单位，代表着逻辑，内含基本数据类型和堆中对象引用，所在区域连续，没有碎片；堆是存储单位，代表着数据，可被多个栈共享（包括成员中基本数据类型、引用和引用对象），所在区域不连续，会有碎片。

**功能不同**

栈内存用来存储局部变量和方法调用，而堆内存用来存储Java中的对象。无论是成员变量，局部变量，还是类变量，它们指向的对象都存储在堆内存中。

**共享性不同**

栈内存是线程私有的。

堆内存是所有线程共有的。

**异常错误不同**

如果栈内存或者堆内存不足都会抛出异常。

栈空间不足：java.lang.StackOverFlowError。

堆空间不足：java.lang.OutOfMemoryError。

**空间大小**

栈的空间大小远远小于堆的


### [3、32 位和 64 位的 JVM，int 类型变量的长度是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#332-位和-64-位的-jvmint-类型变量的长度是多数)  


32 位和 64 位的 JVM 中，int 类型变量的长度是相同的，都是 32 位或者 4 个字节。


### [4、如何找到死锁的线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#4如何找到死锁的线程)  


**死锁的线程可以使用 jstack 指令 dump 出 JVM 的线程信息。**

jstack -l <pidthreads.txt

**有时候需要dump出现异常，可以加上 -F 指令，强制导出**

jstack -F -l <pidthreads.txt

如果存在死锁，一般在文件最后会提示找到 deadlock 的数量与线程信息


### [5、float f=3.4;是否正确？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#5float-f=34;是否正确)  


答:不正确。3.4是双精度数，将双精度型（double）赋值给浮点型（float）属于下转型（down-casting，也称为窄化）会造成精度损失，因此需要强制类型转换float f =(float)3.4; 或者写成float f =3.4F;。


### [6、谈谈永久代](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#6谈谈永久代)  


**1、** JDK 8 之前，Hotspot 中方法区的实现是永久代（Perm）

**2、** JDK 7 开始把原本放在永久代的字符串常量池、静态变量等移出到堆，JDK 8 开始去除永久代，使用元空间（Metaspace），永久代剩余内容移至元空间，元空间直接在本地内存分配。


### [7、启动一个线程是调用run()还是start()方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#7启动一个线程是调用run还是start方法)  




启动一个线程是调用start()方法，使线程所代表的虚拟处理机处于可运行状态，这意味着它可以由JVM 调度并执行，这并不意味着线程就会立即运行。run()方法是线程启动后要进行回调（callback）的方法。


### [8、在新生代-复制算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#8在新生代-复制算法)  


每次垃圾收集都能发现大批对象已死, 只有少量存活、因此选用复制算法, 只需要付出少量存活对象的复制成本就可以完成收集


### [9、创建一个对象用什么运算符？对象实体与对象引用有何不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#9创建一个对象用什么运算符对象实体与对象引用有何不同)  


new运算符，new创建对象实例（对象实例在堆内存中），对象引用指向对象实例（对象引用存放在栈内存中）。一个对象引用可以指向0个或1个对象（一根绳子可以不系气球，也可以系一个气球）;一个对象可以有n个引用指向它（可以用n条绳子系住一个气球）


### [10、什么是线程组，为什么在 Java 中不推荐使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#10什么是线程组为什么在-java-中不推荐使用)  


**1、** ThreadGroup 类，可以把线程归属到某一个线程组中，线程组中可以有线程对象，也可以有线程组，组中还可以有线程，这样的组织结构有点类似于树的形式。

**2、** 线程组和线程池是两个不同的概念，他们的作用完全不同，前者是为了方便线程的管理，后者是为了管理线程的生命周期，复用线程，减少创建销毁线程的开销。

**3、** 为什么不推荐使用线程组？因为使用有很多的安全隐患吧，没有具体追究，如果需要使用，推荐使用线程池。


### [11、运行时异常与受检异常有何异同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#11运行时异常与受检异常有何异同)  

### [12、如何理解Hibernate的延迟加载机制？在实际应用中，延迟加载与Session关闭的矛盾是如何处理的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#12如何理解hibernate的延迟加载机制在实际应用中延迟加载与session关闭的矛盾是如何处理的)  

### [13、如何创建守护线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#13如何创建守护线程)  

### [14、你知道哪些JVM性能调优](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#14你知道哪些jvm性能调优)  

### [15、类、方法、成员变量和局部变量的可用修饰符 -](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#15类方法成员变量和局部变量的可用修饰符--)  

### [16、Hibernate中SessionFactory是线程安全的吗？Session是线程安全的吗（两个线程能够共享同一个Session吗）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#16hibernate中sessionfactory是线程安全的吗session是线程安全的吗两个线程能够共享同一个session吗)  

### [17、什么是原子类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#17什么是原子类)  

### [18、程序的结构有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#18程序的结构有那些)  

### [19、Java 中 ++ 操作符是线程安全的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#19java-中-++-操作符是线程安全的吗)  

### [20、抽象的（abstract）方法是否可同时是静态的（static）,是否可同时是本地方法（native），是否可同时被synchronized修饰？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#20抽象的abstract方法是否可同时是静态的static,是否可同时是本地方法native是否可同时被synchronized修饰)  

### [21、为什么 wait(), notify()和 notifyAll()必须在同步方法或者同步块中被调用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#21为什么-wait,-notify和-notifyall必须在同步方法或者同步块中被调用)  

### [22、JIT 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#22jit-是什么)  

### [23、MinorGC，MajorGC、FullGC都什么时候发生？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#23minorgcmajorgcfullgc都什么时候发生)  

### [24、线程池四种创建方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#24线程池四种创建方式)  

### [25、什么是乐观锁和悲观锁](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#25什么是乐观锁和悲观锁)  

### [26、什么是隐式转换，什么是显式转换](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#26什么是隐式转换什么是显式转换)  

### [27、GC是什么？为什么要有GC？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#27gc是什么为什么要有gc)  

### [28、如何查看 JVM 当前使用的是什么垃圾收集器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#28如何查看-jvm-当前使用的是什么垃圾收集器)  

### [29、setState到底是异步还是同步?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#29setstate到底是异步还是同步)  

### [30、Tomcat是怎么打破双亲委派机制的呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#30tomcat是怎么打破双亲委派机制的呢)  

### [31、虚拟机栈(线程私有)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#31虚拟机栈线程私有)  

### [32、WeakHashMap 是怎么工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#32weakhashmap-是怎么工作的)  

### [33、当打开其他程序的网页时，使用的target属性是哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#33当打开其他程序的网页时使用的target属性是哪个)  

### [34、Java 中会存在内存泄漏?简述一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#34java-中会存在内存泄漏简述一下)  

### [35、在 Java 程序中怎么保证多线程的运行安全？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#35在-java-程序中怎么保证多线程的运行安全)  

### [36、动态改变构造](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#36动态改变构造)  

### [37、对象的相等与指向他们的引用相等，两者有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#37对象的相等与指向他们的引用相等两者有什么不同)  

### [38、Java 中怎么创建 ByteBuffer？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#38java-中怎么创建-bytebuffer)  

### [39、Java内存模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#39java内存模型)  

### [40、我们能创建一个包含可变对象的不可变对象吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大全带答案（2021年Java面试题及答案整理）.md#40我们能创建一个包含可变对象的不可变对象吗)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
