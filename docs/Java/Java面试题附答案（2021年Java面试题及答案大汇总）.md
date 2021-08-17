# Java面试题附答案（2021年Java面试题及答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、线程B怎么知道线程A修改了变量](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#1线程b怎么知道线程a修改了变量)  


**1、** volatile修饰变量

**2、** synchronized修饰修改变量的方法

**3、** wait/notify

**4、** while轮询


### [2、双亲委派](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#2双亲委派)  


当一个类收到了类加载请求，他首先不会尝试自己去加载这个类，而是把这个请求委派给父类去完成，每一个层次类加载器都是如此，因此所有的加载请求都应该传送到启动类加载其中，只有当父类加载器反馈自己无法完成这个请求的时候（在它的加载路径下没有找到所需加载的Class）， 子类加载器才会尝试自己去加载。

采用双亲委派的一个好处是比如加载位于 rt.jar 包中的类 java.lang.Object，不管是哪个加载器加载这个类，最终都是委托给顶层的启动类加载器进行加载，这样就保证了使用不同的类加载器最终得到的都是同样一个 Object 对象


### [3、ConcurrentHashMap 和 Hashtable 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#3concurrenthashmap-和-hashtable-的区别)  


ConcurrentHashMap 和 Hashtable 的区别主要体现在实现线程安全的方式上不同。

**底层数据结构**：

JDK1.7的 ConcurrentHashMap 底层采用 **分段的数组+链表** 实现，JDK1.8 采用的数据结构跟HashMap1.8的结构一样，数组+链表/红黑二叉树。Hashtable 和 JDK1.8 之前的 HashMap 的底层数据结构类似都是采用 **数组+链表**的形式，数组是 HashMap 的主体，链表则是主要为了解决哈希冲突而存在的；

**实现线程安全的方式**：

**1、** 在JDK1.7的时候，ConcurrentHashMap（分段锁对整个桶数组进行了分割分段(Segment)，每一把锁只锁容器其中一部分数据，多线程访问容器里不同数据段的数据，就不会存在锁竞争，提高并发访问率。（默认分配16个Segment，比Hashtable效率提高16倍。） **到了 JDK1.8 的时候已经摒弃了Segment的概念，而是直接用 Node 数组+链表+红黑树的数据结构来实现，并发控制使用 synchronized 和 CAS 来操作。（JDK1.6以后 对 synchronized锁做了很多优化）** 整个看起来就像是优化过且线程安全的 HashMap，虽然在JDK1.8中还能看到 Segment 的数据结构，但是已经简化了属性，只是为了兼容旧版本；

**2、** **Hashtable(同一把锁)** :使用 synchronized 来保证线程安全，效率非常低下。当一个线程访问同步方法时，其他线程也访问同步方法，可能会进入阻塞或轮询状态，如使用 put 添加元素，另一个线程不能使用 put 添加元素，也不能使用 get，竞争会越来越激烈效率越低。

**两者的对比图**：

**1、** HashTable

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/056/58/114_10.png#alt=114%5C_10.png)

**2、**  JDK1.7的ConcurrentHashMap

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/056/58/114_11.png#alt=114%5C_11.png)

**3、** JDK1.8的ConcurrentHashMap（TreeBin: 红黑二叉树节点 Node: 链表节点）

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/056/58/114_12.png#alt=114%5C_12.png)

ConcurrentHashMap 结合了 HashMap 和 HashTable 二者的优势。HashMap 没有考虑同步，HashTable 考虑了同步的问题使用了synchronized 关键字，所以 HashTable 在每次同步执行时都要锁住整个结构。 ConcurrentHashMap 锁的方式是稍微细粒度的。


### [4、本地方法栈](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#4本地方法栈)  


与栈类似,也是用来保存执行方法的信息.执行Java方法是使用栈,执行Native方法时使用本地方法栈.


### [5、Java 中 WeakReference 与 SoftReference 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#5java-中-weakreference-与-softreference-的区别)  


虽然 WeakReference 与 SoftReference 都有利于提高 GC 和 内存的效率，但是 WeakReference ，一旦失去最后一个强引用，就会被 GC回收，而软引用虽然不能阻止被回收，但是可以延迟到 JVM 内存不足的时候。


### [6、如何通过反射创建对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#6如何通过反射创建对象)  




**1、** 方法1：通过类对象调用newInstance()方法，例如：String.class.newInstance()

**2、** 方法2：通过类对象的getConstructor()或getDeclaredConstructor()方法获得构造器（Constructor）对象并调用其newInstance()方法创建对象，例如：String.class.getConstructor(String.class).newInstance(“Hello”);


### [7、TCP 协议与 UDP 协议有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#7tcp-协议与-udp-协议有什么区别)  


答案

[http://javarevisited.blogspot.com/2014/07/9-difference-between-tcp-and-udp-protocol.html](http://javarevisited.blogspot.com/2014/07/9-difference-between-tcp-and-udp-protocol.html)


### [8、并行和并发有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#8并行和并发有什么区别)  


**1、** 并发：多个任务在同一个 CPU 核上，按细分的时间片轮流(交替)执行，从逻辑上来看那些任务是同时执行。

**2、** 并行：单位时间内，多个处理器或多核处理器同时处理多个任务，是真正意义上的“同时进行”。

**3、** 串行：有n个任务，由一个线程按顺序执行。由于任务、方法都在一个线程执行所以不存在线程不安全情况，也就不存在临界区的问题。

**做一个形象的比喻：**

**1、** 并发 = 俩个人用一台电脑。

**2、** 并行 = 俩个人分配了俩台电脑。

**3、** 串行 = 俩个人排队使用一台电脑。


### [9、判断两个对象是否相同，能使用equlas比较吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#9判断两个对象是否相同能使用equlas比较吗)  


不能。Equlas大多用来做字符串比较，要判断基本数据类型或者对象类型，需要使用==


### [10、Java集合的快速失败机制 “fail-fast”？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#10java集合的快速失败机制-“fail-fast)  


是java集合的一种错误检测机制，当多个线程对集合进行结构上的改变的操作时，有可能会产生 fail-fast 机制。

**例如：**假设存在两个线程（线程**1、** 线程2），线程1通过Iterator在遍历集合A中的元素，在某个时候线程2修改了集合A的结构（是结构上面的修改，而不是简单的修改集合元素的内容），那么这个时候程序就会抛出 ConcurrentModificationException 异常，从而产生fail-fast机制。

**原因：**迭代器在遍历时直接访问集合中的内容，并且在遍历过程中使用一个 modCount 变量。集合在被遍历期间如果内容发生变化，就会改变modCount的值。每当迭代器使用hashNext()/next()遍历下一个元素之前，都会检测modCount变量是否为expectedmodCount值，是的话就返回遍历；否则抛出异常，终止遍历。

**解决办法：**

**1、** 在遍历过程中，所有涉及到改变modCount值得地方全部加上synchronized。

**2、** 使用CopyOnWriteArrayList来替换ArrayList


### [11、Serial 与 Parallel GC 之间的不同之处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#11serial-与-parallel-gc-之间的不同之处)  

### [12、程序计数器有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#12程序计数器有什么作用)  

### [13、设计模式的六大原则](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#13设计模式的六大原则)  

### [14、Object类常用方法有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#14object类常用方法有那些)  

### [15、常用io类有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#15常用io类有那些)  

### [16、什么是拆装箱？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#16什么是拆装箱)  

### [17、为什么wait(), notify()和notifyAll ()必须在同步方法或者同步块中被调用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#17为什么wait,-notify和notifyall-必须在同步方法或者同步块中被调用)  

### [18、实现可见性的方法有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#18实现可见性的方法有哪些)  

### [19、你都用过G1垃圾回收器的哪几个重要参数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#19你都用过g1垃圾回收器的哪几个重要参数)  

### [20、如何停止一个正在运行的线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#20如何停止一个正在运行的线程)  

### [21、程序计数器为什么是私有的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#21程序计数器为什么是私有的)  

### [22、Java中是如何支持正则表达式操作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#22java中是如何支持正则表达式操作的)  

### [23、谈谈动态年龄判断](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#23谈谈动态年龄判断)  

### [24、什么是方法的返回值？返回值在类的方法里的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#24什么是方法的返回值返回值在类的方法里的作用是什么)  

### [25、内存溢出和内存泄漏的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#25内存溢出和内存泄漏的区别)  

### [26、Java 中 LinkedHashMap 和 PriorityQueue 的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#26java-中-linkedhashmap-和-priorityqueue-的区别是什么)  

### [27、Log4j日志有几个级别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#27log4j日志有几个级别)  

### [28、Java中用到的线程调度算法是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#28java中用到的线程调度算法是什么)  

### [29、java中equals方法的用法以及==的用法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#29java中equals方法的用法以及的用法)  

### [30、老年代与标记复制算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#30老年代与标记复制算法)  

### [31、如果一个类中有抽象方法，那么这个一定是抽象类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#31如果一个类中有抽象方法那么这个一定是抽象类)  

### [32、谈一谈Hibernate的一级缓存、二级缓存和查询缓存。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#32谈一谈hibernate的一级缓存二级缓存和查询缓存。)  

### [33、构造器Constructor是否可被override](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#33构造器constructor是否可被override)  

### [34、你所知道网络协议有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#34你所知道网络协议有那些)  

### [35、我能在不进行强制转换的情况下将一个 double 值赋值给 long 类型的变量吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#35我能在不进行强制转换的情况下将一个-double-值赋值给-long-类型的变量吗)  

### [36、GC 是什么? 为什么要有 GC](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#36gc-是什么-为什么要有-gc)  

### [37、如何自定义一个异常](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#37如何自定义一个异常)  

### [38、面向对象的特征有哪些方面？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#38面向对象的特征有哪些方面)  

### [39、线程的状态流转图](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#39线程的状态流转图)  

### [40、ArrayList 和 Vector 的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案（2021年Java面试题及答案大汇总）.md#40arraylist-和-vector-的区别是什么)  

### 41、invokedynamic 指令是干什么的？




## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
