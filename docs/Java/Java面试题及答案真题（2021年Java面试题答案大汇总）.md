# Java面试题及答案真题（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、线程与进程的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#1线程与进程的区别)  


进程是系统进行资源分配和调度的一个独立单位，线程是CPU调度和分派的基本单位

进程和线程的关系：

**1、** 一个线程只能属于一个进程，而一个进程可以有多个线程，但至少有一个线程。

**2、** 资源分配给进程，同一进程的所有线程共享该进程的所有资源。

**3、** 线程在执行过程中，需要协作同步。不同进程的线程间要利用消息通信的办法实现同步。

**4、** 线程是指进程内的一个执行单元，也是进程内的可调度实体。

线程与进程的区别：

**1、** 调度：线程作为调度和分配的基本单位，进程作为拥有资源的基本单位。

**2、** 并发性：不仅进程之间可以并发执行，同一个进程的多个线程之间也可以并发执行。

**3、** 拥有资源：进程是拥有资源的一个独立单位，线程不拥有系统资源，但可以访问隶属于进程的资源。

**4、** 系统开销：在创建或撤销进程的时候，由于系统都要为之分配和回收资源，导致系统的明显大于创建或撤销线程时的开销。但进程有独立的地址空间，进程崩溃后，在保护模式下不会对其他的进程产生影响，而线程只是一个进程中的不同的执行路径。线程有自己的堆栈和局部变量，但线程之间没有单独的地址空间，一个线程死掉就等于整个进程死掉，所以多进程的程序要比多线程的程序健壮，但是在进程切换时，耗费的资源较大，效率要差些。


### [2、什么是策略模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#2什么是策略模式)  


定义了一系列的算法 或 逻辑 或 相同意义的操作，并将每一个算法、逻辑、操作封装起来，而且使它们还可以相互替换。（其实策略模式Java中用的非常非常广泛）

我觉得主要是为了 简化 if...else 所带来的复杂和难以维护。


### [3、什么是游标？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#3什么是游标)  


游标是sql查询结果集的一个指针，与select语句相关联。

游标关键字是cursor，主要包含两个部分：游标结果集和游标位置。

**1、** 游标结果集：执行select语句后的查询结果

**2、** 游标位置：一个指向游标结果集内某条记录的指针。

游标主要有两个状态：打开和关闭。

**1、** 只有当游标处于打开状态时，才能够操作结果集中的数据

**2、** 当游标关闭后，查询结果集就不存在了


### [4、单例模式了解吗？给我解释一下双重检验锁方式实现单例模式！”](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#4单例模式了解吗给我解释一下双重检验锁方式实现单例模式)  


**双重校验锁实现对象单例（线程安全）**

**说明：**

双锁机制的出现是为了解决前面同步问题和性能问题，看下面的代码，简单分析下确实是解决了多线程并行进来不会出现重复new对象，而且也实现了懒加载

```
public class Singleton {
       private volatile static Singleton uniqueInstance;

       private Singleton() {
       }

      public static Singleton getUniqueInstance() {
            //先判断对象是否已经实例过，没有实例化过才进入加锁代码
            if (uniqueInstance == null) {
                //类对象加锁
                synchronized (Singleton.class) {
                    if (uniqueInstance == null) {
                        uniqueInstance = new Singleton();
                    }
                }
            }
          return uniqueInstance;
      }
 }
```

另外，需要注意 uniqueInstance 采用 volatile 关键字修饰也是很有必要。

uniqueInstance 采用 volatile 关键字修饰也是很有必要的， uniqueInstance = new Singleton(); 这段代码其实是分为三步执行：

**1、** 为 uniqueInstance 分配内存空间

**2、** 初始化 uniqueInstance

**3、** 将 uniqueInstance 指向分配的内存地址

但是由于 JVM 具有指令重排的特性，执行顺序有可能变成 1->3->2。指令重排在单线程环境下不会出现问题，但是在多线程环境下会导致一个线程获得还没有初始化的实例。例如，线程 T1 执行了 1 和 3，此时 T2 调用 getUniqueInstance() 后发现 uniqueInstance 不为空，因此返回 uniqueInstance，但此时 uniqueInstance 还未被初始化。

使用 volatile 可以禁止 JVM 的指令重排，保证在多线程环境下也能正常运行。


### [5、怎么获取 Java 程序使用的内存？堆使用的百分比？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#5怎么获取-java-程序使用的内存堆使用的百分比)  


可以通过 java.lang.Runtime 类中与内存相关方法来获取剩余的内存，总内存及最大堆内存。通过这些方法你也可以获取到堆使用的百分比及堆内存的剩余空间。Runtime.freeMemory() 方法返回剩余空间的字节数，Runtime.totalMemory()方法总内存的字节数，Runtime.maxMemory() 返回最大内存的字节数。


### [6、在java中守护线程和本地线程区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#6在java中守护线程和本地线程区别)  


java中的线程分为两种：守护线程（Daemon）和用户线程（User）。

任何线程都可以设置为守护线程和用户线程，通过方法Thread.setDaemon(bool on)；true则把该线程设置为守护线程，反之则为用户线程。Thread.setDaemon()必须在Thread.start()之前调用，否则运行时会抛出异常。

**两者的区别**：

唯一的区别是判断虚拟机(JVM)何时离开，Daemon是为其他线程提供服务，如果全部的User Thread已经撤离，Daemon 没有可服务的线程，JVM撤离。也可以理解为守护线程是JVM自动创建的线程（但不一定），用户线程是程序创建的线程；比如JVM的垃圾回收线程是一个守护线程，当所有线程已经撤离，不再产生垃圾，守护线程自然就没事可干了，当垃圾回收线程是Java虚拟机上仅剩的线程时，Java虚拟机会自动离开。

**扩展**：

Thread Dump打印出来的线程信息，含有daemon字样的线程即为守护进程，可能会有：服务守护进程、编译守护进程、windows下的监听Ctrl+break的守护进程、Finalizer守护进程、引用处理守护进程、GC守护进程。


### [7、线程之间是如何通信的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#7线程之间是如何通信的)  


当线程间是可以共享资源时，线程间通信是协调它们的重要的手段。Object类中wait()\notify()\notifyAll()方法可以用于线程间通信关于资源的锁的状态。


### [8、聚集索引与非聚集索引有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#8聚集索引与非聚集索引有什么区别)  


所有的索引都是为了更快地检索数据，索引存放在索引页中，数据存放在数据页中，索引以B（balance）树的形式存储

聚集索引：聚集索引用于决定数据表中的物理存储顺序，一张表最多有一个聚集索引。聚集索引的字段值尽量不能修改，因为修改后，因为修改后数据表的物理顺序需要重写排序。通常主键就是聚集索引

非聚集索引：非聚集索引的关键自是index，不会决定表的物理存储顺序，在一张表内最多可以有249个非聚集索引。


### [9、说一下 ArrayList 的优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#9说一下-arraylist-的优缺点)  


**ArrayList的优点如下：**

**1、** ArrayList 底层以数组实现，是一种随机访问模式。ArrayList 实现了 RandomAccess 接口，因此查找的时候非常快。

**2、** ArrayList 在顺序添加一个元素的时候非常方便。

**ArrayList 的缺点如下：**

**1、** 删除元素的时候，需要做一次元素复制操作。如果要复制的元素很多，那么就会比较耗费性能。

**2、** 插入元素的时候，也需要做一次元素复制操作，缺点同上。

**3、** ArrayList 比较适合顺序添加、随机访问的场景。


### [10、请解释StackOverflowError和OutOfMemeryError的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#10请解释stackoverflowerror和outofmemeryerror的区别)  


通过之前的分析可以发现，实际上每一块内存中都会存在有一部分的可变伸缩区，其基本流程为：如果空间内存不足，在可变范围之内扩大内存空间，当一段时间之后发现内存充足，会缩小内存空间。

**永久代（JDK 1.8后消失了）**

虽然java的版本是JDK1.8，但是java EE 的版本还是jdk1.7，永久代存在于堆内存之中

**元空间**

元空间在Jdk1.8之后才有的，器功能实际上和永久代没区别，唯一的区别在于永久代使用的是JVM的堆内存空间，元空间使用的是物理内存，所以元空间的大小受本地内存影响，一般默认在2M 左右。

**范例：设置一些参数，让元空间出错**

Java -XX:MetaspaceSize=1m


### [11、react-redux是如何工作的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#11react-redux是如何工作的)  

### [12、为什么线程通信的方法wait(), notify()和notifyAll()被定义在Object 类里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#12为什么线程通信的方法wait,-notify和notifyall被定义在object-类里)  

### [13、代理模式应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#13代理模式应用场景)  

### [14、GC 垃圾收集器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#14gc-垃圾收集器)  

### [15、什么是红黑树](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#15什么是红黑树)  

### [16、存储过程与函数的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#16存储过程与函数的区别)  

### [17、如何判断两个类是否相等？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#17如何判断两个类是否相等)  

### [18、你对线程优先级的理解是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#18你对线程优先级的理解是什么)  

### [19、重载和重写的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#19重载和重写的区别)  

### [20、除了使用new创建对象之外，还可以用什么方法创建对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#20除了使用new创建对象之外还可以用什么方法创建对象)  

### [21、如何决定使用 HashMap 还是 TreeMap？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#21如何决定使用-hashmap-还是-treemap)  

### [22、使用Log4j对程序有影响吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#22使用log4j对程序有影响吗)  

### [23、Char类型能不能转成int类型？能不能转化成string类型，能不能转成double类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#23char类型能不能转成int类型能不能转化成string类型能不能转成double类型)  

### [24、Jsp包含那些隐藏对象或者内建对象](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#24jsp包含那些隐藏对象或者内建对象)  

### [25、如何判断一个对象是否存活](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#25如何判断一个对象是否存活)  

### [26、js如何实现页面刷新呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#26js如何实现页面刷新呢)  

### [27、怎么唤醒一个阻塞的线程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#27怎么唤醒一个阻塞的线程)  

### [28、在做文件上传的时候，form表单的enctype的指是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#28在做文件上传的时候form表单的enctype的指是什么)  

### [29、说一下Java对象的创建过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#29说一下java对象的创建过程)  

### [30、什么是线程池？有哪几种创建方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#30什么是线程池有哪几种创建方式)  

### [31、GC的回收流程是怎样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#31gc的回收流程是怎样的)  

### [32、线程之间如何通信及线程之间如何同步](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#32线程之间如何通信及线程之间如何同步)  

### [33、怎样通过 Java 程序来判断 JVM 是 32 位 还是 64位？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#33怎样通过-java-程序来判断-jvm-是-32-位-还是-64位)  

### [34、使用集合框架的好处](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#34使用集合框架的好处)  

### [35、解释如何使用WAR文件部署web应用程序?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#35解释如何使用war文件部署web应用程序)  

### [36、Java 中，Comparator 与 Comparable 有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#36java-中comparator-与-comparable-有什么不同)  

### [37、什么是CAS](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#37什么是cas)  

### [38、JVM 年轻代到年老代的晋升过程的判断条件是什么呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#38jvm-年轻代到年老代的晋升过程的判断条件是什么呢)  

### [39、为什么需要双亲委派模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#39为什么需要双亲委派模式)  

### [40、JAVA 强引用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案真题（2021年Java面试题答案大汇总）.md#40java-强引用)  





