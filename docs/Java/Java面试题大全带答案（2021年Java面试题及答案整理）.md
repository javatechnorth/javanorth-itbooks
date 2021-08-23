# Java面试题大全带答案（2021年Java面试题及答案整理）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、线程的状态](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#1线程的状态)  


![87_2.png][87_2.png]

**1、** 新建(new)：新创建了一个线程对象。

**2、** 就绪（可运行状态）(runnable)：线程对象创建后，当调用线程对象的 start()方法，该线程处于就绪状态，等待被线程调度选中，获取cpu的使用权。

**3、** 运行(running)：可运行状态(runnable)的线程获得了cpu时间片（timeslice），执行程序代码。注：就绪状态是进入到运行状态的唯一入口，也就是说，线程要想进入运行状态执行，首先必须处于就绪状态中；

**4、** 阻塞(block)：处于运行状态中的线程由于某种原因，暂时放弃对 CPU的使用权，停止执行，此时进入阻塞状态，直到其进入到就绪状态，才 有机会再次被 CPU 调用以进入到运行状态。

**阻塞的情况分三种：**

**1、** 等待阻塞：

运行状态中的线程执行 wait()方法，JVM会把该线程放入等待队列(waitting queue)中，使本线程进入到等待阻塞状态；

**2、** 同步阻塞：

线程在获取 synchronized 同步锁失败(因为锁被其它线程所占用)，，则JVM会把该线程放入锁池(lock pool)中，线程会进入同步阻塞状态；

**3、** 其他阻塞:

通过调用线程的 sleep()或 join()或发出了 I/O 请求时，线程会进入到阻塞状态。当 sleep()状态超时、join()等待线程终止或者超时、或者 I/O 处理完毕时，线程重新转入就绪状态。

**4、** 死亡(dead)(结束)：

线程run()、main()方法执行结束，或者因异常退出了run()方法，则该线程结束生命周期。死亡的线程不可再次复生。


### [2、Spring支持的事务管理类型有哪些？你在项目中使用哪种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#2spring支持的事务管理类型有哪些你在项目中使用哪种方式)  


Spring支持编程式事务管理和声明式事务管理。声明式事务管理要优于编程式事务管理，尽管在灵活性方面它弱于编程式事务管理，因为编程式事务允许通过代码控制业务。


### [3、在进行数据库编程时，连接池有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#3在进行数据库编程时连接池有什么作用)  




由于创建连接和释放连接都有很大的开销（尤其是数据库服务器不在本地时，每次建立连接都需要进行TCP的三次握手，释放连接需要进行TCP四次握手，造成的开销是不可忽视的），为了提升系统访问数据库的性能，可以事先创建若干连接置于连接池中，需要时直接从连接池获取，使用结束时归还连接池而不必关闭连接，从而避免频繁创建和释放连接所造成的开销，这是典型的用空间换取时间的策略（浪费了空间存储连接，但节省了创建和释放连接的时间）。池化技术在Java开发中是很常见的，在使用线程时创建线程池的道理与此相同。基于Java的开源数据库连接池主要有：[C3P0](http://sourceforge.net/projects/c3p0/)、[Proxool](http://proxool.sourceforge.net)、[DBCP](http://commons.apache.org/proper/commons-dbcp/)、[BoneCP](https://github.com/wwadge/bonecp)、[Druid](https://github.com/alibaba/druid)等。

> 补充：在计算机系统中时间和空间是不可调和的矛盾，理解这一点对设计满足性能要求的算法是至关重要的。大型网站性能优化的一个关键就是使用缓存，而缓存跟上面讲的连接池道理非常类似，也是使用空间换时间的策略。可以将热点数据置于缓存中，当用户查询这些数据时可以直接从缓存中得到，这无论如何也快过去数据库中查询。当然，缓存的置换策略等也会对系统性能产生重要影响，对于这个问题的讨论已经超出了这里要阐述的范围。



### [4、内部类与静态内部类的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#4内部类与静态内部类的区别)  


静态内部类相对与外部类是独立存在的，在静态内部类中无法直接访问外部类中变量、方法。如果要访问的话，必须要new一个外部类的对象，使用new出来的对象来访问。但是可以直接访问静态的变量、调用静态的方法；

普通内部类作为外部类一个成员而存在，在普通内部类中可以直接访问外部类属性，调用外部类的方法。

如果外部类要访问内部类的属性或者调用内部类的方法，必须要创建一个内部类的对象，使用该对象访问属性或者调用方法。

如果其他的类要访问普通内部类的属性或者调用普通内部类的方法，必须要在外部类中创建一个普通内部类的对象作为一个属性，外同类可以通过该属性调用普通内部类的方法或者访问普通内部类的属性

如果其他的类要访问静态内部类的属性或者调用静态内部类的方法，直接创建一个静态内部类对象即可。


### [5、JVM 如何确定垃圾对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#5jvm-如何确定垃圾对象)  


**1、** JVM 采用的是可达性分析算法，通过 GC Roots 来判定对象是否存活，从 GC Roots 向下追溯、搜索，会产生 Reference Chain。当一个对象不能和任何一个 GC Root 产生关系时，就判定为垃圾。

**2、** 软引用和弱引用，也会影响对象的回收。内存不足时会回收软引用对象；GC 时会回收弱引用对象。


### [6、在 Java 程序中怎么保证多线程的运行安全？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#6在-java-程序中怎么保证多线程的运行安全)  


出现线程安全问题的原因一般都是三个原因：

**1、** 线程切换带来的原子性问题 解决办法：使用多线程之间同步synchronized或使用锁(lock)。

**2、** 缓存导致的可见性问题 解决办法：synchronized、volatile、LOCK，可以解决可见性问题

**3、** 编译优化带来的有序性问题 解决办法：Happens-Before 规则可以解决有序性问题


### [7、堆（Heap-线程共享） -运行时数据区](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#7堆heap-线程共享--运行时数据区)  


是被线程共享的一块内存区域， 创建的对象和数组都保存在 Java 堆内存中，也是垃圾收集器进行垃圾收集的最重要的内存区域。由于现代VM 采用分代收集算法, 因此 Java 堆从 GC 的角度还可以细分为: 新生代(Eden 区、 From Survivor 区和 To Survivor 区)和老年代。


### [8、try{}里有一个return语句，那么紧跟在这个try后的finally{}里的代码会不会被执行，什么时候被执行，在return前还是后?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#8try{}里有一个return语句那么紧跟在这个try后的finally{}里的代码会不会被执行什么时候被执行在return前还是后)  




会执行，在方法返回调用者前执行。

> 注意：在finally中改变返回值的做法是不好的，因为如果存在finally代码块，try中的return语句不会立马返回调用者，而是记录下返回值待finally代码块执行完毕之后再向调用者返回其值，然后如果在finally中修改了返回值，就会返回修改后的值。显然，在finally中返回或者修改返回值会对程序造成很大的困扰，C#中直接用编译错误的方式来阻止程序员干这种龌龊的事情，Java中也可以通过提升编译器的语法检查级别来产生警告或错误，Eclipse中可以在如图所示的地方进行设置，强烈建议将此项设置为编译错误。


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/03/img_1.png#alt=img%5C_1.png)


### [9、什么是线程调度器(Thread Scheduler)和时间分片(Time Slicing)？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#9什么是线程调度器thread-scheduler和时间分片time-slicing)  


线程调度器是一个操作系统服务，它负责为Runnable状态的线程分配CPU时间。一旦我们创建一个线程并启动它，它的执行便依赖于线程调度器的实现。时间分片是指将可用的CPU时间分配给可用的Runnable线程的过程。分配CPU时间可以基于线程优先级或者线程等待的时间。线程调度并不受到Java虚拟机控制，所以由应用程序来控制它是更好的选择（也就是说不要让你的程序依赖于线程的优先级）。


### [10、如何在 Windows 和 Linux 上查找哪个线程cpu利用率最高？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#10如何在-windows-和-linux-上查找哪个线程cpu利用率最高)  


windows上面用任务管理器看，linux下可以用 top 这个工具看。

**1、** 找出cpu耗用厉害的进程pid， 终端执行top命令，然后按下shift+p (shift+m是找出消耗内存最高)查找出cpu利用最厉害的pid号

**2、** 根据上面第一步拿到的pid号，top -H -p pid 。然后按下shift+p，查找出cpu利用率最厉害的线程号，比如top -H -p 1328

**3、** 将获取到的线程号转换成16进制，去百度转换一下就行

**4、** 使用jstack工具将进程信息打印输出，jstack pid号 > /tmp/t.dat，比如jstack 31365 > /tmp/t.dat

**5、** 编辑/tmp/t.dat文件，查找线程号对应的信息

或者直接使用JDK自带的工具查看“jconsole” 、“visualVm”，这都是JDK自带的，可以直接在JDK的bin目录下找到直接使用


### [11、线程池作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#11线程池作用)  

### [12、串行（serial）收集器和吞吐量（throughput）收集器的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#12串行serial收集器和吞吐量throughput收集器的区别是什么)  

### [13、HashMap的put方法的具体流程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#13hashmap的put方法的具体流程)  

### [14、一个类的构造方法的作用是什么？若一个类没有声明构造方法，改程序能正确执行吗？为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#14一个类的构造方法的作用是什么若一个类没有声明构造方法改程序能正确执行吗为什么)  

### [15、notify()和notifyAll()有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#15notify和notifyall有什么区别)  

### [16、怎么看死锁的线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#16怎么看死锁的线程)  

### [17、ArrayList 和 LinkedList 的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#17arraylist-和-linkedlist-的区别是什么)  

### [18、Java里有哪些引用类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#18java里有哪些引用类型)  

### [19、你能写出一个正则表达式来判断一个字符串是否是一个数字吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#19你能写出一个正则表达式来判断一个字符串是否是一个数字吗)  

### [20、什么是TreeMap](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#20什么是treemap)  

### [21、守护线程和用户线程有什么区别呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#21守护线程和用户线程有什么区别呢)  

### [22、String 类的常用方法都有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#22string-类的常用方法都有那些)  

### [23、谈谈双亲委派模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#23谈谈双亲委派模型)  

### [24、Java 中能创建 volatile 数组吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#24java-中能创建-volatile-数组吗)  

### [25、java中有没有指针？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#25java中有没有指针)  

### [26、CMS 收集器（多线程标记清除算法）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#26cms-收集器多线程标记清除算法)  

### [27、Java 中的final关键字有哪些用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#27java-中的final关键字有哪些用法)  

### [28、本地方法区(线程私有)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#28本地方法区线程私有)  

### [29、什么是B/S架构？什么是C/S架构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#29什么是b/s架构什么是c/s架构)  

### [30、Collection 和 Collections 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#30collection-和-collections-有什么区别)  

### [31、ThreadPoolExecutor饱和策略有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#31threadpoolexecutor饱和策略有哪些)  

### [32、谈谈你知道的垃圾收集器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#32谈谈你知道的垃圾收集器)  

### [33、如何判断对象可以被回收](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#33如何判断对象可以被回收)  

### [34、类加载有几个过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#34类加载有几个过程)  

### [35、switch 是否能作用在byte 上，是否能作用在long 上，是否能作用在String上？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#35switch-是否能作用在byte-上是否能作用在long-上是否能作用在string上)  

### [36、怎么打出线程栈信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#36怎么打出线程栈信息)  

### [37、HashSet如何检查重复？HashSet是如何保证数据不可重复的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#37hashset如何检查重复hashset是如何保证数据不可重复的)  

### [38、CAS的问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#38cas的问题)  

### [39、Java 内存分配与回收策率以及 Minor GC 和 Major GC](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#39java-内存分配与回收策率以及-minor-gc-和-major-gc)  

### [40、程序计数器(线程私有)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大全带答案（2021年Java面试题及答案整理）.md#40程序计数器线程私有)  





