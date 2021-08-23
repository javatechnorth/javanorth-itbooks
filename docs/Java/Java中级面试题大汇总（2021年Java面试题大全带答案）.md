# Java中级面试题大汇总（2021年Java面试题大全带答案）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是方法内联？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#1什么是方法内联)  


为了减少方法调用的开销，可以把一些短小的方法，比如`getter/setter`，纳入到目标方法的调用范围之内，就少了一次方法调用，速度就能得到提升，这就是方法内联的概念。


### [2、你对线程优先级的理解是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#2你对线程优先级的理解是什么)  


**1、** 每一个线程都是有优先级的，一般来说，高优先级的线程在运行时会具有优先权，但这依赖于线程调度的实现，这个实现是和操作系统相关的(OS dependent)。我们可以定义线程的优先级，但是这并不能保证高优先级的线程会在低优先级的线程前执行。线程优先级是一个 int 变量(从 1-10)，1 代表最低优先级，10 代表最高优先级。

**2、** Java 的线程优先级调度会委托给操作系统去处理，所以与具体的操作系统优先级有关，如非特别需要，一般无需设置线程优先级。

**3、** 当然，如果你真的想设置优先级可以通过setPriority()方法设置，但是设置了不一定会该变，这个是不准确的


### [3、Java是否需要开发人员回收内存垃圾吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#3java是否需要开发人员回收内存垃圾吗)  


大多情况下是不需要的。Java提供了一个系统级的线程来跟踪内存分配，不再使用的内存区将会自动回收


### [4、说说Java 垃圾回收机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#4说说java-垃圾回收机制)  


在 Java 中，程序员是不需要显示的去释放一个对象的内存的，而是由虚拟机自行执行。在 JVM 中，有一个垃圾回收线程，它是低优先级的，在正常情况下是不会执行的，只有在虚拟机空闲或者当前堆内存不足时，才会触发执行，扫面那些没有被任何引用的对象，并将它们添加到要回收的集合中，进行回收。


### [5、62、volatile 变量和 atomic 变量有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#562volatile-变量和-atomic-变量有什么不同)  


Volatile变量可以确保先行关系，即写操作会发生在后续的读操作之前, 但它并不能保证原子性。例如用volatile修饰count变量那么 count++ 操作就不是原子性的。

而AtomicInteger类提供的atomic方法可以让这种操作具有原子性如getAndIncrement()方法会原子性的进行增量操作把当前值加一，其它数据类型和引用变量也可以进行相似操作。


### [6、JVM 内存区域](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#6jvm-内存区域)  


JVM 内存区域主要分为线程私有区域【程序计数器、虚拟机栈、本地方法区】、线程共享区域【JAVA 堆、方法区】、直接内存。

线程私有数据区域生命周期与线程相同, 依赖用户线程的启动/结束 而 创建/销毁(在 Hotspot VM 内, 每个线程都与操作系统的本地线程直接映射, 因此这部分内存区域的存/否跟随本地线程的生/死对应)。

线程共享区域随虚拟机的启动/关闭而创建/销毁。

直接内存并不是 JVM 运行时数据区的一部分, 但也会被频繁的使用: 在 JDK 1.4 引入的 NIO 提供了基于Channel与 Buffer的IO方式, 它可以使用Native函数库直接分配堆外内存, 然后使用DirectByteBuffer 对象作为这块内存的引用进行操作(详见: Java I/O 扩展), 这样就避免了在 Java堆和 Native 堆中来回复制数据, 因此在一些场景中可以显著提高性能。


### [7、JVM 有哪些运行时内存区域？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#7jvm-有哪些运行时内存区域)  


**Java 8**

**1、** The pc Register，程序计数器

**2、** Java Virtual Machine Stacks，Java 虚拟机栈

**3、** Heap，堆

**4、** Method Area，方法区

**5、** Run-Time Constant Pool，运行时常量池

**6、** Native Method Stacks，本地方法栈


### [8、Spring中Bean的作用域有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#8spring中bean的作用域有哪些)  


**1、** Singleton：Bean以单例的方式存在

**2、** Prototype：表示每次从容器中调用Bean时，都会返回一个新的实例，prototype通常翻译为原型

**3、** Request：每次HTTP请求都会创建一个新的Bean

**4、** Session：同一个HttpSession共享同一个Bean，不同的HttpSession使用不同的Bean

**5、** globalSession：同一个全局Session共享一个Bean


### [9、String str=”aaa”,与String str=new String(“aaa”)一样吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#9string-str=aaa,与string-str=new-string“aaa一样吗)  


**1、** 不一样的。因为内存分配的方式不一样。

**2、** 第一种，创建的”aaa”是常量，jvm都将其分配在常量池中。

**3、** 第二种创建的是一个对象，jvm将其值分配在堆内存中。


### [10、什么是建造者模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#10什么是建造者模式)  


**1、** 建造者模式：是将一个复杂的对象的构建与它的表示分离，使得同样的构建过程可以创建不同的方式进行创建。

**2、** 工厂类模式是提供的是创建单个类的产品

**3、** 而建造者模式则是将各种产品集中起来进行管理，用来具有不同的属性的产品

**建造者模式通常包括下面几个角色：**

**1、** uilder：给出一个抽象接口，以规范产品对象的各个组成成分的建造。这个接口规定要实现复杂对象的哪些部分的创建，并不涉及具体的对象部件的创建。

**2、** ConcreteBuilder：实现Builder接口，针对不同的商业逻辑，具体化复杂对象的各部分的创建。 在建造过程完成后，提供产品的实例。

**3、** Director：调用具体建造者来创建复杂对象的各个部分，在指导者中不涉及具体产品的信息，只负责保证对象各部分完整创建或按某种顺序创建。

**4、** Product：要创建的复杂对象。


### [11、Javascript中常用的事件有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#11javascript中常用的事件有哪些)  

### [12、如何设置请求的编码以及响应内容的类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#12如何设置请求的编码以及响应内容的类型)  

### [13、在一个静态方法内调用一个非静态成员为什么是非法的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#13在一个静态方法内调用一个非静态成员为什么是非法的)  

### [14、HashMap 和 ConcurrentHashMap 的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#14hashmap-和-concurrenthashmap-的区别)  

### [15、为什么wait, notify 和 notifyAll这些方法不在thread类里面？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#15为什么wait,-notify-和-notifyall这些方法不在thread类里面)  

### [16、什么是设计模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#16什么是设计模式)  

### [17、Collection和Collections的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#17collection和collections的区别)  

### [18、什么是JDK?什么是JRE？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#18什么是jdk什么是jre)  

### [19、Java中的同步集合与并发集合有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#19java中的同步集合与并发集合有什么区别)  

### [20、Java 中应该使用什么数据类型来代表价格？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#20java-中应该使用什么数据类型来代表价格)  

### [21、Java的数据结构有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#21java的数据结构有那些)  

### [22、volatile 修饰符的有过什么实践？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#22volatile-修饰符的有过什么实践)  

### [23、方法区的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#23方法区的作用是什么)  

### [24、你对 Time Slice的理解?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#24你对-time-slice的理解)  

### [25、Java 线程数过多会造成什么异常？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#25java-线程数过多会造成什么异常)  

### [26、怎么判断并发队列是阻塞队列还是非阻塞队列](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#26怎么判断并发队列是阻塞队列还是非阻塞队列)  

### [27、如何使用exception对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#27如何使用exception对象)  

### [28、如何边遍历边移除 Collection 中的元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#28如何边遍历边移除-collection-中的元素)  

### [29、请解释一下MAC代表什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#29请解释一下mac代表什么)  

### [30、Session加载实体对象的过程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#30session加载实体对象的过程。)  

### [31、如何实现数组和 List 之间的转换？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#31如何实现数组和-list-之间的转换)  

### [32、重载（Overload）和重写（Override）的区别。重载的方法能否根据返回类型进行区分？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#32重载overload和重写override的区别。重载的方法能否根据返回类型进行区分)  

### [33、如何开启和查看 GC 日志？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#33如何开启和查看-gc-日志)  

### [34、Java中垃圾回收有什么目的？什么时候进行垃圾回收？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#34java中垃圾回收有什么目的什么时候进行垃圾回收)  

### [35、JAVA软引用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#35java软引用)  

### [36、抽象的关键字是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#36抽象的关键字是什么)  

### [37、建造者模式的使用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#37建造者模式的使用场景)  

### [38、分代回收](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#38分代回收)  

### [39、代理的分类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#39代理的分类)  

### [40、什么是并发容器的实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题大汇总（2021年Java面试题大全带答案）.md#40什么是并发容器的实现)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
