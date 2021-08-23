# Java中级面试题及答案大全（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、为什么使用Executor框架？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#1为什么使用executor框架)  


**1、** 每次执行任务创建线程 new Thread()比较消耗性能，创建一个线程是比较耗时、耗资源的。

**2、** 调用 new Thread()创建的线程缺乏管理，被称为野线程，而且可以无限制的创建，线程之间的相互竞争会导致过多占用系统资源而导致系统瘫痪，还有线程之间的频繁交替也会消耗很多系统资源。

**3、** 接使用new Thread() 启动的线程不利于扩展，比如定时执行、定期执行、定时定期执行、线程中断等都不便实现。


### [2、你能保证 GC 执行吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#2你能保证-gc-执行吗)  


不能，虽然你可以调用 System.gc() 或者 Runtime.gc()，但是没有办法保证 GC的执行。


### [3、UML中有哪些常用的图？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#3uml中有哪些常用的图)  




UML定义了多种图形化的符号来描述软件系统部分或全部的静态结构和动态结构，包括：用例图（use case diagram）、类图（class diagram）、时序图（sequence diagram）、协作图（collaboration diagram）、状态图（statechart diagram）、活动图（activity diagram）、构件图（component diagram）、部署图（deployment diagram）等。在这些图形化符号中，有三种图最为重要，分别是：用例图（用来捕获需求，描述系统的功能，通过该图可以迅速的了解系统的功能模块及其关系）、类图（描述类以及类与类之间的关系，通过该图可以快速了解系统）、时序图（描述执行特定任务时对象之间的交互关系以及执行顺序，通过该图可以了解对象能接收的消息也就是说对象能够向外界提供的服务）。

用例图：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/03/img_6.png#alt=img%5C_6.png)

类图：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/03/img_7.png#alt=img%5C_7.png)

时序图：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2019/08/0816/03/img_8.png#alt=img%5C_8.png)


### [4、volatile关键字的原理是什么？干什么用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#4volatile关键字的原理是什么干什么用的)  


使用了volatile关键字的变量，每当变量的值有变动的时候，都会将更改立即同步到主内存中；而如果某个线程想要使用这个变量，就先要从主存中刷新到工作内存，这样就确保了变量的可见性。

一般使用一个volatile修饰的bool变量，来控制线程的运行状态。

```
volatile boolean stop = false;
 
 void stop(){
  this.stop = true;
 }
 void start(){
  new Thread(()->{
   while (!stop){
    //sth
   }
  }).start();
 }
```


### [5、synchronized 和 Lock 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#5synchronized-和-lock-有什么区别)  


**1、** 首先synchronized是Java内置关键字，在JVM层面，Lock是个Java类；

**2、** synchronized 可以给类、方法、代码块加锁；而 lock 只能给代码块加锁。

**3、** synchronized 不需要手动获取锁和释放锁，使用简单，发生异常会自动释放锁，不会造成死锁；而 lock 需要自己加锁和释放锁，如果使用不当没有 unLock()去释放锁就会造成死锁。

**4、** 通过 Lock 可以知道有没有成功获取锁，而 synchronized 却无法办到。


### [6、抽象类必须要有抽象方法吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#6抽象类必须要有抽象方法吗)  


不是必须。抽象类可以没有抽象方法。


### [7、强引用、软引用、弱引用、虚引用是什么，有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#7强引用软引用弱引用虚引用是什么有什么区别)  


**1、** 强引用，就是普通的对象引用关系，如 String s = new String("ConstXiong")

**2、** 软引用，用于维护一些可有可无的对象。只有在内存不足时，系统则会回收软引用对象，如果回收了软引用对象之后仍然没有足够的内存，才会抛出内存溢出异常。SoftReference 实现

**3、** 弱引用，相比软引用来说，要更加无用一些，它拥有更短的生命周期，当 JVM 进行垃圾回收时，无论内存是否充足，都会回收被弱引用关联的对象。WeakReference 实现

**4、** 虚引用是一种形同虚设的引用，在现实场景中用的不是很多，它主要用来跟踪对象被垃圾回收的活动。PhantomReference 实现


### [8、Servlet的生命周期？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#8servlet的生命周期)  


**1、** 加载：判断servlet实例是否存在，如果不存在，就加载serlvet

**2、** 实例化：

**3、** 初始化

4、服务

5、销毁


### [9、Hibernate的对象有几种状态](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#9hibernate的对象有几种状态)  


**1、** 瞬时态（transient）

**2、** 持久态（persistent）

**3、** 游离态（detached）


### [10、说一下HashMap的实现原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#10说一下hashmap的实现原理)  


**1、** HashMap概述： HashMap是基于哈希表的Map接口的非同步实现。此实现提供所有可选的映射操作，并允许使用null值和null键。此类不保证映射的顺序，特别是它不保证该顺序恒久不变。

**2、** HashMap的数据结构： 在Java编程语言中，最基本的结构就是两种，一个是数组，另外一个是模拟指针（引用），所有的数据结构都可以用这两个基本结构来构造的，HashMap也不例外。HashMap实际上是一个“链表散列”的数据结构，即数组和链表的结合体。

**HashMap 基于 Hash 算法实现的**

**1、** 当我们往HashMap中put元素时，利用key的hashCode重新hash计算出当前对象的元素在数组中的下标

**2、** 存储时，如果出现hash值相同的key，此时有两种情况。

(1)如果key相同，则覆盖原始值；

(2)如果key不同（出现冲突），则将当前的key-value放入链表中

**3、** 获取时，直接找到hash值对应的下标，在进一步判断key是否相同，从而找到对应值。

**4、** 理解了以上过程就不难明白HashMap是如何解决hash冲突的问题，核心就是使用了数组的存储方式，然后将冲突的key的对象放入链表中，一旦发现冲突就在链表中做进一步的对比。

需要注意Jdk 1.8中对HashMap的实现做了优化，当链表中的节点数据超过八个之后，该链表会转为红黑树来提高查询效率，从原来的O(n)到O(logn)


### [11、什么是方法重载？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#11什么是方法重载)  

### [12、Java中interrupted 和 isInterrupted方法的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#12java中interrupted-和-isinterrupted方法的区别)  

### [13、OSGI（ 动态模型系统）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#13osgi-动态模型系统)  

### [14、Executors类是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#14executors类是什么)  

### [15、React有哪些优化性能是手段?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#15react有哪些优化性能是手段)  

### [16、Java的io流分为哪两种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#16java的io流分为哪两种)  

### [17、现实生活中的模板方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#17现实生活中的模板方法)  

### [18、ZGC收集器中的染色指针有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#18zgc收集器中的染色指针有什么用)  

### [19、Linux环境下如何查找哪个线程使用CPU最长](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#19linux环境下如何查找哪个线程使用cpu最长)  

### [20、当一个对象被当作参数传递到一个方法后，此方法可改变这个对象的属性，并可返回变化后的结果，那么这里到底是值传递还是引用传递？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#20当一个对象被当作参数传递到一个方法后此方法可改变这个对象的属性并可返回变化后的结果那么这里到底是值传递还是引用传递)  

### [21、什么是Executors框架？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#21什么是executors框架)  

### [22、如何创建一个json对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#22如何创建一个json对象)  

### [23、用Java写一个单例类。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#23用java写一个单例类。)  

### [24、单例模式使用注意事项：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#24单例模式使用注意事项：)  

### [25、阐述final、finally、finalize的区别。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#25阐述finalfinallyfinalize的区别。)  

### [26、什么是“依赖注入”和“控制反转”？为什么有人使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#26什么是“依赖注入和“控制反转为什么有人使用)  

### [27、什么是竞争条件？你怎样发现和解决竞争？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#27什么是竞争条件你怎样发现和解决竞争)  

### [28、React的请求应该放在哪个生命周期中?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#28react的请求应该放在哪个生命周期中)  

### [29、你知道有哪些开源框架？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#29你知道有哪些开源框架)  

### [30、Servlet生命周期内调用的方法过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#30servlet生命周期内调用的方法过程)  

### [31、Java中Synchronized关键字的使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#31java中synchronized关键字的使用)  

### [32、如果对象的引用被置为null，垃圾收集器是否会立即释放对象占用的内存？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#32如果对象的引用被置为null垃圾收集器是否会立即释放对象占用的内存)  

### [33、CopyOnWriteArrayList 的缺点?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#33copyonwritearraylist-的缺点)  

### [34、怎么确保一个集合不能被修改？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#34怎么确保一个集合不能被修改)  

### [35、如何部署一个web项目？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#35如何部署一个web项目)  

### [36、在使用jdbc的时候，如何防止出现sql注入的问题。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#36在使用jdbc的时候如何防止出现sql注入的问题。)  

### [37、常用的并发工具类有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#37常用的并发工具类有哪些)  

### [38、类初始化的情况有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#38类初始化的情况有哪些)  

### [39、串行(serial)收集器和吞吐量(throughput)收集器的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#39串行serial收集器和吞吐量throughput收集器的区别是什么)  

### [40、为什么要学习设计模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案大全（2021年Java面试题答案大汇总）.md#40为什么要学习设计模式)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
