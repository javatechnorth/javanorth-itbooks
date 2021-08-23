# Java中级面试题及答案整理（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、java中有几种方法可以实现一个线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#1java中有几种方法可以实现一个线程)  


继承 Thread 类

实现 Runnable 接口

实现 Callable 接口，需要实现的是 call() 方法


### [2、Java 中的 HashSet，内部是如何工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#2java-中的-hashset内部是如何工作的)  


HashSet 的内部采用 HashMap来实现。由于 Map 需要 key 和 value，所以所有 key 的都有一个默认 value。类似于 HashMap，HashSet 不允许重复的 key，只允许有一个null key，意思就是 HashSet 中只允许存储一个 null 对象。


### [3、redux的工作流程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#3redux的工作流程)  


**首先，我们看下几个核心概念：**

**1、** Store：保存数据的地方，你可以把它看成一个容器，整个应用只能有一个Store。

**2、** State：Store对象包含所有数据，如果想得到某个时点的数据，就要对Store生成快照，这种时点的数据集合，就叫做State。

**3、** Action：State的变化，会导致View的变化。但是，用户接触不到State，只能接触到View。所以，State的变化必须是View导致的。Action就是View发出的通知，表示State应该要发生变化了。

**4、** Action Creator：View要发送多少种消息，就会有多少种Action。如果都手写，会很麻烦，所以我们定义一个函数来生成Action，这个函数就叫Action Creator。

**5、** Reducer：Store收到Action以后，必须给出一个新的State，这样View才会发生变化。这种State的计算过程就叫做Reducer。Reducer是一个函数，它接受Action和当前State作为参数，返回一个新的State。

**6、** dispatch：是View发出Action的唯一方法。

**然后我们过下整个工作流程：**

**1、** 首先，用户（通过View）发出Action，发出方式就用到了dispatch方法。

**2、** 然后，Store自动调用Reducer，并且传入两个参数：当前State和收到的Action，Reducer会返回新的State

**3、** State一旦有变化，Store就会调用监听函数，来更新View。

到这儿为止，一次用户交互流程结束。可以看到，在整个流程中数据都是单向流动的，这种方式保证了流程的清晰。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/4/30/1939/39/97_11.png#alt=97%5C_11.png)

> [redux原理详解](https://github.com/xiaomuzhu/front-end-interview/blob/master/docs/guide/redux.md)



### [4、String类的常用方法有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#4string类的常用方法有那些)  


**1、** charAt：返回指定索引处的字符

**2、** indexOf()：返回指定字符的索引

**3、** replace()：字符串替换

**4、** trim()：去除字符串两端空白

**5、** split()：分割字符串，返回一个分割后的字符串数组

**6、** getBytes()：返回字符串的byte类型数组

**7、** length()：返回字符串长度

**8、** toLowerCase()：将字符串转成小写字母

**9、** toUpperCase()：将字符串转成大写字符

**10、** substring()：截取字符串

**11、** format()：格式化字符串

**12、** equals()：字符串比较


### [5、请你谈谈对OOM的认识](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#5请你谈谈对oom的认识)  


OOM是非常严重的问题，除了`程序计数器`，其他内存区域都有溢出的风险。和我们平常工作最密切的，就是堆溢出。另外，元空间在方法区内容非常多的情况下也会溢出。还有就是栈溢出，这个通常影响比较小。堆外也有溢出的可能，这个就比较难排查一些。


### [6、ParNew 垃圾收集器（Serial+多线程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#6parnew-垃圾收集器serial+多线程)  


ParNew 垃圾收集器其实是 Serial 收集器的多线程版本，也使用复制算法，除了使用多线程进行垃圾收集之外，其余的行为和 Serial 收集器完全一样， ParNew 垃圾收集器在垃圾收集过程中同样也要暂停所有其他的工作线程。

ParNew 收集器默认开启和 CPU 数目相同的线程数，可以通过-XX:ParallelGCThreads 参数来限制垃圾收集器的线程数。【Parallel：平行的】

ParNew 虽然是除了多线程外和Serial 收集器几乎完全一样，但是ParNew垃圾收集器是很多 java虚拟机运行在 Server 模式下新生代的默认垃圾收集器。


### [7、Java 中如何格式化一个日期？如格式化为 ddMMyyyy 的形式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#7java-中如何格式化一个日期如格式化为-ddmmyyyy-的形式)  


[http://javarevisited.blogspot.com/2011/09/convert-date-to-string-simpledateformat.html](http://javarevisited.blogspot.com/2011/09/convert-date-to-string-simpledateformat.html)

Java 中，可以使用 SimpleDateFormat 类或者 joda-time 库来格式日期。DateFormat 类允许你使用多种流行的格式来格式化日期。参见中的示例代码，代码中演示了将日期格式化成不同的格式，如 dd-MM-yyyy 或 ddMMyyyy。


### [8、什么是Java虚拟机](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#8什么是java虚拟机)  


任何一种可以运行Java字节码的软件均可看成是Java的虚拟机（JVM）


### [9、Java 中的同步集合与并发集合有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#9java-中的同步集合与并发集合有什么区别)  


同步集合与并发集合都为多线程和并发提供了合适的线程安全的集合，不过并发集合的可扩展性更高。在 Java1.5 之前程序员们只有同步集合来用且在多线程并发的时候会导致争用，阻碍了系统的扩展性。Java5 介绍了并发集合像ConcurrentHashMap，不仅提供线程安全还用锁分离和内部分区等现代技术提高了可扩展性。


### [10、适配器模式和代理模式之前有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#10适配器模式和代理模式之前有什么不同)  


这个问题与前面的类似，适配器模式和代理模式的区别在于他们的意图不同。由于适配器模式和代理模式都是封装真正执行动作的类，因此结构是一致的，但是适配器模式用于接口之间的转换，而代理模式则是增加一个额外的中间层，以便支持分配、控制或智能访问。


### [11、final不可变对象，它对写并发应用有什么帮助？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#11final不可变对象它对写并发应用有什么帮助)  

### [12、什么是Daemon线程？它有什么意义？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#12什么是daemon线程它有什么意义)  

### [13、Swing 是线程安全的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#13swing-是线程安全的)  

### [14、对象分配内存是否线程安全？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#14对象分配内存是否线程安全)  

### [15、什么是面向对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#15什么是面向对象)  

### [16、redux异步中间件之间的优劣?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#16redux异步中间件之间的优劣)  

### [17、并发编程三要素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#17并发编程三要素)  

### [18、如何合理分配线程池大小?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#18如何合理分配线程池大小)  

### [19、GC垃圾回收算法与垃圾收集器的关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#19gc垃圾回收算法与垃圾收集器的关系)  

### [20、用Java写一个冒泡排序。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#20用java写一个冒泡排序。)  

### [21、四种线程池的创建：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#21四种线程池的创建：)  

### [22、说几个常见的编译时异常类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#22说几个常见的编译时异常类)  

### [23、正则表达式有那些符号？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#23正则表达式有那些符号)  

### [24、普通类与抽象类有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#24普通类与抽象类有什么区别)  

### [25、Html中a标签的target属性有哪些值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#25html中a标签的target属性有哪些值)  

### [26、什么情况下会发生栈溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#26什么情况下会发生栈溢出)  

### [27、对象都是优先分配在年轻代上的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#27对象都是优先分配在年轻代上的吗)  

### [28、JAVA8 与元数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#28java8-与元数据)  

### [29、说一下堆和栈的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#29说一下堆和栈的区别)  

### [30、JVM 中一次完整的 GC 流程（从 ygc 到 fgc）是怎样的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#30jvm-中一次完整的-gc-流程从-ygc-到-fgc是怎样的)  

### [31、为什么我们调用 start() 方法时会执行 run() 方法，为什么我们不能直接调用 run() 方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#31为什么我们调用-start-方法时会执行-run-方法为什么我们不能直接调用-run-方法)  

### [32、什么是Java Timer 类？如何创建一个有特定时间间隔的任务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#32什么是java-timer-类如何创建一个有特定时间间隔的任务)  

### [33、用哪两种方式来实现集合的排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#33用哪两种方式来实现集合的排序)  

### [34、Java 中 sleep 方法和 wait 方法的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#34java-中-sleep-方法和-wait-方法的区别)  

### [35、什么是类加载器，类加载器有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#35什么是类加载器类加载器有哪些)  

### [36、你熟悉哪些垃圾收集算法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#36你熟悉哪些垃圾收集算法)  

### [37、说下有哪些类加载器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#37说下有哪些类加载器)  

### [38、生产环境用的什么JDK？如何配置的垃圾收集器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#38生产环境用的什么jdk如何配置的垃圾收集器)  

### [39、创建socket通讯的步骤？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#39创建socket通讯的步骤)  

### [40、HashMap在JDK1.7和JDK1.8中有哪些不同？HashMap的底层实现](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案整理（2021年Java面试题答案大汇总）.md#40hashmap在jdk17和jdk18中有哪些不同hashmap的底层实现)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
