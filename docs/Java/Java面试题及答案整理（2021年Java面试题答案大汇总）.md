# Java面试题及答案整理（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、你说你做过JVM参数调优和参数配置，请问如何查看JVM系统默认值](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#1你说你做过jvm参数调优和参数配置请问如何查看jvm系统默认值)  


使用-XX:+PrintFlagsFinal参数可以看到参数的默认值。这个默认值还和垃圾回收器有关，比如UseAdaptiveSizePolicy。


### [2、Java 中怎样将 bytes 转换为 long 类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#2java-中怎样将-bytes-转换为-long-类型)  


这个问题你来回答 :-)


### [3、如何避免线程死锁](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#3如何避免线程死锁)  


**1、** 避免一个线程同时获得多个锁

**2、** 避免一个线程在锁内同时占用多个资源，尽量保证每个锁只占用一个资源

**3、** 尝试使用定时锁，使用lock.tryLock(timeout)来替代使用内部锁机制


### [4、生产环境 CPU 占用过高，你如何解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#4生产环境-cpu-占用过高你如何解决)  


**1、** top + H 指令找出占用 CPU 最高的进程的 pid

**2、** top -H -p

在该进程中找到，哪些线程占用的 CPU 最高的线程，记录下 tid

**3、** jstack -l

threads.txt，导出进程的线程栈信息到文本，导出出现异常的话，加上 -F 参数

**4、** 将 tid 转换为十六进制，在 threads.txt 中搜索，查到对应的线程代码执行栈，在代码中查找占 CPU 比较高的原因。其中 tid 转十六进制，可以借助 Linux 的 printf "%x" tid 指令

我用上述方法查到过，jvm 多条线程疯狂 full gc 导致的CPU 100% 的问题和 JDK1.6 HashMap 并发 put 导致线程 CPU 100% 的问题


### [5、同步方法和同步块，哪个是更好的选择？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#5同步方法和同步块哪个是更好的选择)  


同步块是更好的选择，因为它不会锁住整个对象（当然你也可以让它锁住整个对象）。同步方法会锁住整个对象，哪怕这个类中有多个不相关联的同步块，这通常会导致他们停止执行并需要等待获得这个对象上的锁。

同步块更要符合开放调用的原则，只在需要锁住的代码块锁住相应的对象，这样从侧面来说也可以避免死锁。


### [6、自动装箱与拆箱](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#6自动装箱与拆箱)  


**装箱**：将基本类型用它们对应的引用类型包装起来；

**拆箱**：将包装类型转换为基本数据类型；

Java使用自动装箱和拆箱机制，节省了常用数值的内存开销和创建对象的开销，提高了效率，由编译器来完成，编译器会在编译期根据语法决定是否进行装箱和拆箱动作。


### [7、详细介绍一下JVM内存模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#7详细介绍一下jvm内存模型)  


根据 JVM 规范，JVM 内存共分为虚拟机栈、堆、方法区、程序计数器、本地方法栈五个部分。

具体可能会聊聊jdk1.7以前的PermGen（永久代），替换成Metaspace（元空间）

**1、** 原本永久代存储的数据：符号引用(Symbols)转移到了native heap；字面量(interned strings)转移到了java heap；类的静态变量(class statics)转移到了java heap

**2、** Metaspace（元空间）存储的是类的元数据信息（metadata）

**3、** 元空间的本质和永久代类似，都是对JVM规范中方法区的实现。不过元空间与永久代之间最大的区别在于：元空间并不在虚拟机中，而是使用本地内存。

**4、** 替换的好处：一、字符串存在永久代中，容易出现性能问题和内存溢出。二、永久代会为 GC 带来不必要的复杂度，并且回收效率偏低。


### [8、监听器有哪些作用和用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#8监听器有哪些作用和用法)  


ava Web开发中的监听器（listener）就是application、session、request三个对象创建、销毁或者往其中添加修改删除属性时自动执行代码的功能组件，如下所示：

**1、** ServletContextListener：对Servlet上下文的创建和销毁进行监听。

**2、** ServletContextAttributeListener：监听Servlet上下文属性的添加、删除和替换。

**3、** HttpSessionListener：对Session的创建和销毁进行监听。


### [9、说一下堆内存中对象的分配的基本策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#9说一下堆内存中对象的分配的基本策略)  


eden区、s0区、s1区都属于新生代，tentired 区属于老年代。大部分情况，对象都会首先在 Eden 区域分配，在一次新生代垃圾回收后，如果对象还存活，则会进入 s0 或者 s1，并且对象的年龄还会加 1(Eden区->Survivor 区后对象的初始年龄变为1)，当它的年龄增加到一定程度（默认为15岁），就会被晋升到老年代中。对象晋升到老年代的年龄阈值，可以通过参数 -XX:MaxTenuringThreshold 来设置。另外，大对象和长期存活的对象会直接进入老年代。


### [10、HashSet与HashMap的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#10hashset与hashmap的区别)  

| HashMap | HashSet |
| --- | --- |
| 实现了Map接口 | 实现Set接口 |
| 存储键值对 | 仅存储对象 |
| 调用put（）向map中添加元素 | 调用add（）方法向Set中添加元素 |
| HashMap使用键（Key）计算Hashcode | HashSet使用成员对象来计算hashcode值，对于两个对象来说hashcode可能相同，所以equals()方法用来判断对象的相等性，如果两个对象不同的话，那么返回false |
| HashMap相对于HashSet较快，因为它是使用唯一的键获取对象 | HashSet较HashMap来说比较慢 |



### [11、什么时候会造成堆外内存溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#11什么时候会造成堆外内存溢出)  

### [12、XML文档定义有几种形式？它们之间有何本质区别？解析XML文档有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#12xml文档定义有几种形式它们之间有何本质区别解析xml文档有哪几种方式)  

### [13、说出 5 个 JDK 1.8 引入的新特性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#13说出-5-个-jdk-18-引入的新特性)  

### [14、阻塞队列和非阻塞队列区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#14阻塞队列和非阻塞队列区别)  

### [15、对象的内存布局了解吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#15对象的内存布局了解吗)  

### [16、面向对象和面向过程的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#16面向对象和面向过程的区别)  

### [17、stackoverflow错误，permgen space错误](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#17stackoverflow错误permgen-space错误)  

### [18、解释内存中的栈(stack)、堆(heap)和方法区(method area)的用法。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#18解释内存中的栈stack堆heap和方法区method-area的用法。)  

### [19、什么情况下会违反迪米特法则？为什么会有这个问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#19什么情况下会违反迪米特法则为什么会有这个问题)  

### [20、解释servlet如何完成生命周期?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#20解释servlet如何完成生命周期)  

### [21、指出下面程序的运行结果](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#21指出下面程序的运行结果)  

### [22、CyclicBarrier和CountDownLatch的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#22cyclicbarrier和countdownlatch的区别)  

### [23、如何修改tomcat的端口号？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#23如何修改tomcat的端口号)  

### [24、synchronized可重入的原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#24synchronized可重入的原理)  

### [25、int 和 Integer 哪个会占用更多的内存？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#25int-和-integer-哪个会占用更多的内存)  

### [26、Java语言如何进行异常处理，关键字：throws、throw、try、catch、finally分别如何使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#26java语言如何进行异常处理关键字：throwsthrowtrycatchfinally分别如何使用)  

### [27、String str="i"与 String str=new String("i")一样吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#27string-str="i"与-string-str=new-string"i"一样吗)  

### [28、调优命令有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#28调优命令有哪些)  

### [29、有什么堆外内存的排查思路？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#29有什么堆外内存的排查思路)  

### [30、为什么 ArrayList 的 elementData 加上 transient 修饰？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#30为什么-arraylist-的-elementdata-加上-transient-修饰)  

### [31、Java应用程序与小程序之间有那些差别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#31java应用程序与小程序之间有那些差别)  

### [32、虚拟DOM实现原理?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#32虚拟dom实现原理)  

### [33、用Java实现阻塞队列](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#33用java实现阻塞队列)  

### [34、Java反射创建对象效率高还是通过new创建对象的效率高？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#34java反射创建对象效率高还是通过new创建对象的效率高)  

### [35、==与equlas有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#35与equlas有什么区别)  

### [36、Java 中，Serializable 与 Externalizable 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#36java-中serializable-与-externalizable-的区别)  

### [37、构造器注入和 setter 依赖注入，那种方式更好？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#37构造器注入和-setter-依赖注入那种方式更好)  

### [38、谈谈 JVM 中的常量池](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#38谈谈-jvm-中的常量池)  

### [39、策略模式的优点和缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#39策略模式的优点和缺点)  

### [40、String str=”aa”,String s=”bb”,String aa=aa+s;一种创建了几个对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案整理（2021年Java面试题答案大汇总）.md#40string-str=aa,string-s=bb,string-aa=aa+s;一种创建了几个对象)  





