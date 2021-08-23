# Java高级面试题及答案总结（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、CMS分为哪几个阶段?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#1cms分为哪几个阶段)  


CMS已经弃用。生活美好，时间有限，不建议再深入研究了。如果碰到问题，直接祭出回收过程即可。

**1、** 初始标记

**2、** 并发标记

**3、** 并发预清理

**4、** 并发可取消的预清理

**5、** 重新标记

**6、** 并发清理

由于《深入理解java虚拟机》一书的流行，面试时省略3、4步一般也是没问题的。


### [2、Thread类的sleep()方法和对象的wait()方法都可以让线程暂停执行，它们有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#2thread类的sleep方法和对象的wait方法都可以让线程暂停执行它们有什么区别)  




sleep()方法（休眠）是线程类（Thread）的静态方法，调用此方法会让当前线程暂停执行指定的时间，将执行机会（CPU）让给其他线程，但是对象的锁依然保持，因此休眠时间结束后会自动恢复（线程回到就绪状态，请参考第66题中的线程状态转换图）。wait()是Object类的方法，调用对象的wait()方法导致当前线程放弃对象的锁（线程暂停执行），进入对象的等待池（wait pool），只有调用对象的notify()方法（或notifyAll()方法）时才能唤醒等待池中的线程进入等锁池（lock pool），如果线程重新获得对象的锁就可以进入就绪状态。

> 补充：可能不少人对什么是进程，什么是线程还比较模糊，对于为什么需要多线程编程也不是特别理解。简单的说：进程是具有一定独立功能的程序关于某个数据集合上的一次运行活动，是操作系统进行资源分配和调度的一个独立单位；线程是进程的一个实体，是CPU调度和分派的基本单位，是比进程更小的能独立运行的基本单位。线程的划分尺度小于进程，这使得多线程程序的并发性高；进程在执行时通常拥有独立的内存单元，而线程之间可以共享内存。使用多线程的编程通常能够带来更好的性能和用户体验，但是多线程的程序对于其他程序是不友好的，因为它可能占用了更多的CPU资源。当然，也不是线程越多，程序的性能就越好，因为线程之间的调度和切换也会浪费CPU时间。时下很时髦的[Node.js](https://nodejs.org)就采用了单线程异步I/O的工作模式。



### [3、请解释如何配置Tomcat来使用IIS和NTLM ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#3请解释如何配置tomcat来使用iis和ntlm-)  


必须遵循isapi_redirector.dll的标准指令

配置IIS使用“集成windows验证”

确保在服务器.xml中您已经禁用了tomcat身份验证

### [4、Java中的继承是单继承还是多继承](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#4java中的继承是单继承还是多继承)  


Java中既有单继承，又有多继承。对于java类来说只能有一个父类，对于接口来说可以同时继承多个接口


### [5、事务的使用场景在什么地方？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#5事务的使用场景在什么地方)  


但一个业务逻辑包括多个数据库操作的时候，而且需要保证每个数据表操作都执行的成功进行下一个操作，这个时候可以使用事务


### [6、说一下垃圾分代收集的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#6说一下垃圾分代收集的过程)  


分为新生代和老年代，新生代默认占总空间的 1/3，老年代默认占 2/3。

新生代使用复制算法，有 3 个分区：Eden、To Survivor、From Survivor，它们的默认占比是 8:1:1。

当新生代中的 Eden 区内存不足时，就会触发 Minor GC，过程如下：

**1、** 在 Eden 区执行了第一次 GC 之后，存活的对象会被移动到其中一个 Survivor 分区；

**2、** Eden 区再次 GC，这时会采用复制算法，将 Eden 和 from 区一起清理，存活的对象会被复制到 to 区；

**3、** 移动一次，对象年龄加 1，对象年龄大于一定阀值会直接移动到老年代

**4、** Survivor 区相同年龄所有对象大小的总和 (Survivor 区内存大小 * 这个目标使用率)时，大于或等于该年龄的对象直接进入老年代。其中这个使用率通过 -XX:TargetSurvivorRatio 指定，默认为 50%

**5、** Survivor 区内存不足会发生担保分配

**6、** 超过指定大小的对象可以直接进入老年代

Major GC，指的是老年代的垃圾清理，但并未找到明确说明何时在进行Major GC

FullGC，整个堆的垃圾收集，触发条件：

**1、** 每次晋升到老年代的对象平均大小>老年代剩余空间

**2、** MinorGC后存活的对象超过了老年代剩余空间

**3、** 元空间不足

**4、** System.gc() 可能会引起

**5、** CMS GC异常，promotion failed:MinorGC时，survivor空间放不下，对象只能放入老年代，而老年代也放不下造成；concurrent mode failure:GC时，同时有对象要放入老年代，而老年代空间不足造成

**6、** 堆内存分配很大的对象


### [7、可以直接调用Thread类的run ()方法么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#7可以直接调用thread类的run-方法么)  


当然可以。但是如果我们调用了Thread的run()方法，它的行为就会和普通的方法一样，会在当前线程中执行。为了在新的线程中执行我们的代码，必须使用Thread.start()方法。


### [8、Math.round(11.5) 等于多少？Math.round(-11.5)等于多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#8mathround115-等于多少mathround-115等于多少)  




Math.round(11.5)的返回值是12，Math.round(-11.5)的返回值是-11。四舍五入的原理是在参数上加0.5然后进行下取整。


### [9、字节流与字符流的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#9字节流与字符流的区别)  


**1、** 以字节为单位输入输出数据，字节流按照8位传输

**2、** 以字符为单位输入输出数据，字符流按照16位传输


### [10、Java 堆的结构是什么样子的？什么是堆中的永久代（Perm Gen space）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#10java-堆的结构是什么样子的什么是堆中的永久代perm-gen-space)  


JVM 的堆是运行时数据区，所有类的实例和数组都是在堆上分配内存。它在 JVM 启动的时候被创建。对象所占的堆内存是由自动内存管理系统也就是垃圾收集器回收。

堆内存是由存活和死亡的对象组成的。存活的对象是应用可以访问的，不会被垃圾回收。死亡的对象是应用不可访问尚且还没有被垃圾收集器回收掉的对象。一直到垃圾收集器把这些 对象回收掉之前，他们会一直占据堆内存空间。


### [11、说明Tomcat配置了多少个Valve?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#11说明tomcat配置了多少个valve)  

### [12、说说类加载的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#12说说类加载的过程)  

### [13、Hashtable 与 HashMap 有什么不同之处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#13hashtable-与-hashmap-有什么不同之处)  

### [14、接口与抽象类有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#14接口与抽象类有什么区别)  

### [15、如何写一段简单的死锁代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#15如何写一段简单的死锁代码)  

### [16、多线程的常用方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#16多线程的常用方法)  

### [17、并发队列和并发集合的区别：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#17并发队列和并发集合的区别：)  

### [18、静态方法和实例方法有何不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#18静态方法和实例方法有何不同)  

### [19、什么是Java虚拟机？为什么Java被称作是“平台无关的编程语言”？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#19什么是java虚拟机为什么java被称作是“平台无关的编程语言)  

### [20、Anonymous Inner Class(匿名内部类)是否可以继承其它类？是否可以实现接口？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#20anonymous-inner-class匿名内部类是否可以继承其它类是否可以实现接口)  

### [21、分区收集算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#21分区收集算法)  

### [22、Java 中，怎么获取一个文件中单词出现的最高频率？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#22java-中怎么获取一个文件中单词出现的最高频率)  

### [23、Java中你怎样唤醒一个阻塞的线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#23java中你怎样唤醒一个阻塞的线程)  

### [24、嵌套静态类与顶级类有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#24嵌套静态类与顶级类有什么区别)  

### [25、说说自己是怎么使用 synchronized 关键字，在项目中用到了吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#25说说自己是怎么使用-synchronized-关键字在项目中用到了吗)  

### [26、比较一下Java和JavaSciprt。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#26比较一下java和javasciprt。)  

### [27、Serial 与 Parallel GC之间的不同之处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#27serial-与-parallel-gc之间的不同之处)  

### [28、什么是happen-before原则？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#28什么是happen-before原则)  

### [29、什么是线程调度器(Thread Scheduler)和时间分片(Time Slicing )？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#29什么是线程调度器thread-scheduler和时间分片time-slicing-)  

### [30、Java 中堆和栈有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#30java-中堆和栈有什么区别)  

### [31、怎么查看服务器默认的垃圾回收器是哪一个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#31怎么查看服务器默认的垃圾回收器是哪一个)  

### [32、策略模式应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#32策略模式应用场景)  

### [33、Java 中能创建 volatile 数组吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#33java-中能创建-volatile-数组吗)  

### [34、怎样通过 Java 程序来判断 JVM 是 32 位 还是 64 位？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#34怎样通过-java-程序来判断-jvm-是-32-位-还是-64-位)  

### [35、阐述静态变量和实例变量的区别。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#35阐述静态变量和实例变量的区别。)  

### [36、用过ConcurrentHashMap，讲一下他和HashTable的不同之处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#36用过concurrenthashmap讲一下他和hashtable的不同之处)  

### [37、常用的集合类有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#37常用的集合类有哪些)  

### [38、Java 中，怎么在格式化的日期中显示时区？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#38java-中怎么在格式化的日期中显示时区)  

### [39、[@Before ](/Before ) 和 [@BeforeClass ](/BeforeClass ) 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#39[@before-]/before--和-[@beforeclass-]/beforeclass--有什么区别)  

### [40、Serial Old 收集器（单线程标记整理算法 ）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案总结（2021年Java面试题答案大汇总）.md#40serial-old-收集器单线程标记整理算法-)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
