# Java高级面试题大汇总（2021年Java面试题大全带答案）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、38、数据类型之间的转换：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#138数据类型之间的转换：)  


1. 如何将字符串转换为基本数据类型？
2. 如何将基本数据类型转换为字符串？



1. 调用基本数据类型对应的包装类中的方法parseXXX(String)或valueOf(String)即可返回相应基本类型；
2. 一种方法是将基本数据类型与空字符串（”“）连接（+）即可获得其所对应的字符串；另一种方法是调用String 类中的valueOf()方法返回相应字符串


### [2、为什么选择使用框架而不是原生?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#2为什么选择使用框架而不是原生)  


框架的好处:

**1、** 组件化: 其中以 React 的组件化最为彻底,甚至可以到函数级别的原子组件,高度的组件化可以是我们的工程易于维护、易于组合拓展。

**2、** 天然分层: JQuery 时代的代码大部分情况下是面条代码,耦合严重,现代框架不管是 MVC、MVP还是MVVM 模式都能帮助我们进行分层，代码解耦更易于读写。

**3、** 生态: 现在主流前端框架都自带生态,不管是数据流管理架构还是 UI 库都有成熟的解决方案。

**4、** 开发效率: 现代前端框架都默认自动更新DOM,而非我们手动操作,解放了开发者的手动DOM成本,提高开发效率,从根本上解决了UI 与状态同步问题.


### [3、线程池都有哪些状态？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#3线程池都有哪些状态)  


**1、** RUNNING：这是最正常的状态，接受新的任务，处理等待队列中的任务。

**2、** SHUTDOWN：不接受新的任务提交，但是会继续处理等待队列中的任务。

**3、** STOP：不接受新的任务提交，不再处理等待队列中的任务，中断正在执行任务的线程。

**4、** TIDYING：所有的任务都销毁了，workCount 为 0，线程池的状态在转换为 TIDYING 状态时，会执行钩子方法 terminated()。

**5、** TERMINATED：terminated()方法结束后，线程池的状态就会变成这个。


### [4、Java 8 为什么要将永久代(PermGen)替换为元空间(MetaSpace)呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#4java-8-为什么要将永久代permgen替换为元空间metaspace呢)  


整个永久代有一个 JVM 本身设置固定大小上线，无法进行调整，而元空间使用的是直接内存，受本机可用内存的限制，并且永远不会出现java.lang.OutOfMemoryError。你可以使用 -XX：MaxMetaspaceSize 标志设置最大元空间大小，默认值为 unlimited，这意味着它只受系统内存的限制。-XX：MetaspaceSize 调整标志定义元空间的初始大小如果未指定此标志，则 Metaspace 将根据运行时的应用程序需求动态地重新调整大小。


### [5、在Java中，如何跳出当前的多重嵌套循环？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#5在java中如何跳出当前的多重嵌套循环)  




在最外层循环前加一个标记如A，然后用break A;可以跳出多重循环。（Java中支持带标签的break和continue语句，作用有点类似于C和C++中的goto语句，但是就像要避免使用goto一样，应该避免使用带标签的break和continue，因为它不会让你的程序变得更优雅，很多时候甚至有相反的作用，所以这种语法其实不知道更好）


### [6、如何解析json对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#6如何解析json对象)  


使用json-lib、gson、jackson可以解析json对象。需要将json对象转换成一个java对象，使用java对象访问属性。


### [7、comparable 和 comparator的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#7comparable-和-comparator的区别)  


**1、** comparable接口实际上是出自java.lang包，它有一个 compareTo(Object obj)方法用来排序

**2、** omparator接口实际上是出自 java.util 包，它有一个compare(Object obj1, Object obj2)方法用来排序

**3、** 一般我们需要对一个集合使用自定义排序时，我们就要重写compareTo方法或compare方法，当我们需要对某一个集合实现两种排序方式，比如一个song对象中的歌名和歌手名分别采用一种排序方法的话，我们可以重写compareTo方法和使用自制的Comparator方法或者以两个Comparator来实现歌名排序和歌星名排序，第二种代表我们只能使用两个参数版的Collections.sort().


### [8、SynchronizedMap 和 ConcurrentHashMap 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#8synchronizedmap-和-concurrenthashmap-有什么区别)  


**1、** SynchronizedMap 一次锁住整张表来保证线程安全，所以每次只能有一个线程来访为 map。

**2、** ConcurrentHashMap 使用分段锁来保证在多线程下的性能。

**3、** ConcurrentHashMap 中则是一次锁住一个桶。ConcurrentHashMap 默认将hash 表分为 16 个桶，诸如 get，put，remove 等常用操作只锁当前需要用到的桶。

**4、** 这样，原来只能一个线程进入，现在却能同时有 16 个写线程执行，并发性能的提升是显而易见的。

**5、** 另外 ConcurrentHashMap 使用了一种不同的迭代方式。在这种迭代方式中，当iterator 被创建后集合再发生改变就不再是抛出ConcurrentModificationException，取而代之的是在改变时 new 新的数据从而不影响原有的数据，iterator 完成后再将头指针替换为新的数据 ，这样 iterator线程可以使用原来老的数据，而写线程也可以并发的完成改变。


### [9、怎么检测一个线程是否拥有锁？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#9怎么检测一个线程是否拥有锁)  


在java.lang.Thread中有一个方法叫holdsLock()，它返回true如果当且仅当当前线程拥有某个具体对象的锁。


### [10、Java 中怎么获取一份线程 dump 文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#10java-中怎么获取一份线程-dump-文件)  


在 Linux 下，你可以通过命令 kill -3 PID （Java 进程的进程 ID）来获取 Java 应用的 dump 文件。在 Windows 下，你可以按下 Ctrl + Break 来获取。这样 JVM 就会将线程的 dump 文件打印到标准输出或错误文件中，它可能打印在控制台或者日志文件中，具体位置依赖应用的配置。如果你使用Tomcat。


### [11、什么是线程调度器(Thread Scheduler)和时间分片(Time Slicing )？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#11什么是线程调度器thread-scheduler和时间分片time-slicing-)  

### [12、TreeMap 和 TreeSet 在排序时如何比较元素？Collections 工具类中的 sort()方法如何比较元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#12treemap-和-treeset-在排序时如何比较元素collections-工具类中的-sort方法如何比较元素)  

### [13、Java网络编程有几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#13java网络编程有几种)  

### [14、什么是观察者模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#14什么是观察者模式)  

### [15、对象是怎么从年轻代进入老年代的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#15对象是怎么从年轻代进入老年代的)  

### [16、接口和抽象类有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#16接口和抽象类有什么区别)  

### [17、你知道哪些垃圾收集器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#17你知道哪些垃圾收集器)  

### [18、什么情况下会发生栈内存溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#18什么情况下会发生栈内存溢出)  

### [19、为什么线程通信的方法 wait(), notify()和 notifyAll()被定义在 Object 类里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#19为什么线程通信的方法-wait,-notify和-notifyall被定义在-object-类里)  

### [20、三种代理的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#20三种代理的区别)  

### [21、原子类的常用类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#21原子类的常用类)  

### [22、方法区溢出的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#22方法区溢出的原因)  

### [23、你将如何使用thread dump？你将如何分析Thread dump？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#23你将如何使用thread-dump你将如何分析thread-dump)  

### [24、用代码演示三种代理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#24用代码演示三种代理)  

### 25、栈
### [26、Java 中，怎么打印出一个字符串的所有排列？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#26java-中怎么打印出一个字符串的所有排列)  

### [27、简述Hibernate常见优化策略。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#27简述hibernate常见优化策略。)  

### [28、异常的处理机制有几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#28异常的处理机制有几种)  

### [29、JDK 和 JRE 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#29jdk-和-jre-有什么区别)  

### [30、什么是分布式垃圾回收（DGC）？它是如何工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#30什么是分布式垃圾回收dgc它是如何工作的)  

### [31、java中会存在内存泄漏吗，请简单描述。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#31java中会存在内存泄漏吗请简单描述。)  

### [32、阐述Spring框架中Bean的生命周期？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#32阐述spring框架中bean的生命周期)  

### [33、如何判断一个常量是废弃常量 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#33如何判断一个常量是废弃常量-)  

### [34、遇到过元空间溢出吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#34遇到过元空间溢出吗)  

### [35、创建一个子类对象的时候，那么父类的构造方法会执行吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#35创建一个子类对象的时候那么父类的构造方法会执行吗)  

### [36、Statement和PreparedStatement有什么区别？哪个性能更好？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#36statement和preparedstatement有什么区别哪个性能更好)  

### [37、synchronized 和 volatile 的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#37synchronized-和-volatile-的区别是什么)  

### [38、JVM中一次完整的GC流程是怎样的，对象如何晋升到老年代？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#38jvm中一次完整的gc流程是怎样的对象如何晋升到老年代)  

### [39、Java 中，受检查异常 和 不受检查异常的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#39java-中受检查异常-和-不受检查异常的区别)  

### [40、什么是链表](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题大汇总（2021年Java面试题大全带答案）.md#40什么是链表)  





