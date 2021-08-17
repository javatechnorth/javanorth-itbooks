# Java高级面试题及答案汇总（2021年Java面试题答案大全）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、Jsp由哪些内容组成？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#1jsp由哪些内容组成)  


**1、** 指令：<%@ %>

**2、** 脚本：<% %>

**3、** 表达式：<%=%>

**4、** 声明：<%! %>

**5、** 注释：<% -- %>

**6、** 动作：<jsp：动作名称 属性=””>

**7、** 静态内容：html内容


### [2、运行时数据区是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#2运行时数据区是什么)  


虚拟机在执行 Java 程序的过程中会把它所管理的内存划分为若干不同的数据区，这些区域有各自的用途、创建和销毁时间。

线程私有：程序计数器、Java 虚拟机栈、本地方法栈。

线程共享：Java 堆、方法区。


### [3、Java中用到的线程调度算法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#3java中用到的线程调度算法是什么)  


采用时间片轮转的方式。可以设置线程的优先级，会映射到下层的系统上面的优先级上，如非特别需要，尽量不要用，防止线程饥饿。


### [4、equals 和 == 的区别？#](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#4equals-和--的区别#)  


通俗点讲：是看看左右是不是一个东西。equals是看看左右是不是长得一样。如何记住嘛。如果单纯是想记住，：等于。equals：相同。两个长得一样的人，只能说长的相同(equals)，但是不等于他们俩是一个人。你只要记住equals，==就不用记了。

**术语来讲的区别：**

**1、** ==是判断两个变量或实例是不是指向同一个内存空间 equals是判断两个变量或实例所指向的内存空间的值是不是相同

**2、** ==是指对内存地址进行比较 equals()是对字符串的内容进行比较3.==指引用是否相同 equals()指的是值是否相同



### [5、怎么检查一个字符串只包含数字？解决方案](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#5怎么检查一个字符串只包含数字解决方案)  


[http://java67.blogspot.com/2014/01/java-regular-expression-to-check-numbers-in-String.html](http://java67.blogspot.com/2014/01/java-regular-expression-to-check-numbers-in-String.html)


### [6、新生代与复制算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#6新生代与复制算法)  


目前大部分 JVM 的 GC 对于新生代都采取 Copying 算法，因为新生代中每次垃圾回收都要回收大部分对象，即要复制的操作比较少，但通常并不是按照 1：1 来划分新生代。一般将新生代划分为一块较大的 Eden 空间和两个较小的 Survivor 空间(From Space, To Space)，每次使用Eden 空间和其中的一块 Survivor 空间，当进行回收时，将该两块空间中还存活的对象复制到另一块 Survivor 空间中。


### [7、如何进行单元测试](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#7如何进行单元测试)  


使用junit


### [8、在老年代-标记整理算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#8在老年代-标记整理算法)  


因为对象存活率高、没有额外空间对它进行分配担保, 就必须采用“标记—清理”或“标记—整理” 算法来进行回收, 不必进行内存复制, 且直接腾出空闲内存。


### [9、模块化编程与热插拔](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#9模块化编程与热插拔)  


OSGi 旨在为实现 Java 程序的模块化编程提供基础条件，基于 OSGi 的程序很可能可以实现模块级的热插拔功能，当程序升级更新时，可以只停用、重新安装然后启动程序的其中一部分，这对企业级程序开发来说是非常具有诱惑力的特性。

OSGi 描绘了一个很美好的模块化开发目标，而且定义了实现这个目标的所需要服务与架构，同时也有成熟的框架进行实现支持。但并非所有的应用都适合采用 OSGi 作为基础架构，它在提供强大功能同时，也引入了额外的复杂度，因为它不遵守了类加载的双亲委托模型。


### [10、线程的 sleep()方法和 yield()方法有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#10线程的-sleep方法和-yield方法有什么区别)  


**1、** sleep()方法给其他线程运行机会时不考虑线程的优先级，因此会给低优先级的线程以运行的机会；yield()方法只会给相同优先级或更高优先级的线程以运行的机会；

**2、** 线程执行 sleep()方法后转入阻塞（blocked）状态，而执行 yield()方法后转入就绪（ready）状态；

**3、** sleep()方法声明抛出 InterruptedException，而 yield()方法没有声明任何异常；

**4、** sleep()方法比 yield()方法（跟操作系统 CPU 调度相关）具有更好的可移植性，通常不建议使用yield()方法来控制并发线程的执行。


### [11、类加载是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#11类加载是什么)  

### [12、Collections.synchronized  是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#12collectionssynchronized- 是什么)  

### [13、sleep() 和 wait() 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#13sleep-和-wait-有什么区别)  

### [14、Java 中的编译期常量是什么？使用它又什么风险？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#14java-中的编译期常量是什么使用它又什么风险)  

### [15、FutureTask是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#15futuretask是什么)  

### [16、Java中Semaphore是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#16java中semaphore是什么)  

### [17、构造方法能不能显式调用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#17构造方法能不能显式调用)  

### [18、怎样将GB2312编码的字符串转换为ISO-8859-1编码的字符串？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#18怎样将gb2312编码的字符串转换为iso-8859-1编码的字符串)  

### [19、Java 中 WeakReference 与 SoftReference的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#19java-中-weakreference-与-softreference的区别)  

### [20、Java 程序是怎样运行的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#20java-程序是怎样运行的)  

### [21、Final在java中的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#21final在java中的作用)  

### [22、说说CMS垃圾收集器的工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#22说说cms垃圾收集器的工作原理)  

### [23、Java语言有哪些特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#23java语言有哪些特点)  

### [24、什么情况发生栈溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#24什么情况发生栈溢出)  

### [25、Java 中，如何计算两个日期之间的差距？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#25java-中如何计算两个日期之间的差距)  

### [26、Java 中 interrupted 和 isInterrupted 方法的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#26java-中-interrupted-和-isinterrupted-方法的区别)  

### [27、常用并发列队的介绍：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#27常用并发列队的介绍：)  

### [28、请说出与线程同步以及线程调度相关的方法。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#28请说出与线程同步以及线程调度相关的方法。)  

### [29、为什么你应该在循环中检查等待条件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#29为什么你应该在循环中检查等待条件)  

### [30、如何停止一个正在运行的线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#30如何停止一个正在运行的线程)  

### [31、线程的sleep()方法和yield()方法有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#31线程的sleep方法和yield方法有什么区别)  

### [32、用最有效率的方法计算2乘以8？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#32用最有效率的方法计算2乘以8)  

### [33、获得一个类的类对象有哪些方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#33获得一个类的类对象有哪些方式)  

### [34、JIT是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#34jit是什么)  

### [35、不可变对象对多线程有什么帮助](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#35不可变对象对多线程有什么帮助)  

### [36、如何通过反射获取和设置对象私有字段的值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#36如何通过反射获取和设置对象私有字段的值)  

### [37、CopyOnWriteArrayList 的使用场景?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#37copyonwritearraylist-的使用场景)  

### [38、ArrayList 和 HashMap 的默认大小是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#38arraylist-和-hashmap-的默认大小是多数)  

### [39、实例化数组后，能不能改变数组长度呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#39实例化数组后能不能改变数组长度呢)  

### [40、32 位 JVM 和 64 位 JVM 的最大堆内存分别是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案汇总（2021年Java面试题答案大全）.md#4032-位-jvm-和-64-位-jvm-的最大堆内存分别是多数)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
