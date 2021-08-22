# Java高级面试题附答案汇总（2021年Java面试题及答案大全）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、多线程同步有哪几种方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#1多线程同步有哪几种方法)  


Synchronized关键字，Lock锁实现，分布式锁等。


### [2、Java中如何实现序列化，有什么意义？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#2java中如何实现序列化有什么意义)  




序列化就是一种用来处理对象流的机制，所谓对象流也就是将对象的内容进行流化。可以对流化后的对象进行读写操作，也可将流化后的对象传输于网络之间。序列化是为了解决对象流读写操作时可能引发的问题（如果不进行序列化可能会存在数据乱序的问题）。

要实现序列化，需要让一个类实现Serializable接口，该接口是一个标识性接口，标注该类对象是可被序列化的，然后使用一个输出流来构造一个对象输出流并通过writeObject(Object)方法就可以将实现对象写出（即保存其状态）；如果需要反序列化则可以用一个输入流建立对象输入流，然后通过readObject方法从流中读取对象。序列化除了能够实现对象的持久化之外，还能够用于对象的深度克隆（可以参考第29题）。


### [3、32 位和 64 位的 JVM，int 类型变量的长度是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#332-位和-64-位的-jvmint-类型变量的长度是多数)  


32 位和 64 位的 JVM 中，int 类型变量的长度是相同的，都是 32 位或者 4个字节。


### [4、synchronized、volatile、CAS 比较](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#4synchronizedvolatilecas-比较)  


**1、** synchronized 是悲观锁，属于抢占式，会引起其他线程阻塞。

**2、** volatile 提供多线程共享变量可见性和禁止指令重排序优化。

**3、** CAS 是基于冲突检测的乐观锁（非阻塞）


### [5、有哪些 GC 算法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#5有哪些-gc-算法)  


**标记-清除算法**

分为标记和清除阶段，首先从每个 GC Roots 出发依次标记有引用关系的对象，最后清除没有标记的对象。

执行效率不稳定，如果堆包含大量对象且大部分需要回收，必须进行大量标记清除，导致效率随对象数量增长而降低。

存在内存空间碎片化问题，会产生大量不连续的内存碎片，导致以后需要分配大对象时容易触发 Full GC。

**标记-复制算法**

为了解决内存碎片问题，将可用内存按容量划分为大小相等的两块，每次只使用其中一块。当使用的这块空间用完了，就将存活对象复制到另一块，再把已使用过的内存空间一次清理掉。主要用于进行新生代。

实现简单、运行高效，解决了内存碎片问题。代价是可用内存缩小为原来的一半，浪费空间。

HotSpot 把新生代划分为一块较大的 Eden 和两块较小的 Survivor，每次分配内存只使用 Eden 和其中一块 Survivor。垃圾收集时将 Eden 和 Survivor 中仍然存活的对象一次性复制到另一块 Survivor 上，然后直接清理掉 Eden 和已用过的那块 Survivor。HotSpot 默认Eden 和 Survivor 的大小比例是 8:1，即每次新生代中可用空间为整个新生代的 90%。

**标记-整理算法**

标记-复制算法在对象存活率高时要进行较多复制操作，效率低。如果不想浪费空间，就需要有额外空间分配担保，应对被使用内存中所有对象都存活的极端情况，所以老年代一般不使用此算法。

老年代使用标记-整理算法，标记过程与标记-清除算法一样，但不直接清理可回收对象，而是让所有存活对象都向内存空间一端移动，然后清理掉边界以外的内存。

标记-清除与标记-整理的差异在于前者是一种非移动式算法而后者是移动式的。如果移动存活对象，尤其是在老年代这种每次回收都有大量对象存活的区域，是一种极为负重的操作，而且移动必须全程暂停用户线程。如果不移动对象就会导致空间碎片问题，只能依赖更复杂的内存分配器和访问器解决。


### [6、什么是集合](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#6什么是集合)  


**1、** 集合就是一个放数据的容器，准确的说是放数据对象引用的容器

**2、** 集合类存放的都是对象的引用，而不是对象的本身

**3、** 集合类型主要有3种：set(集）、list(列表）和map(映射)。


### [7、对于JDK自带的监控和性能分析工具用过哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#7对于jdk自带的监控和性能分析工具用过哪些)  


`jps`：用来显示Java进程；`jstat`：用来查看GC；`jmap`：用来dump堆；`jstack`：用来dump栈；`jhsdb`：用来查看执行中的内存信息；

都是非常常用的工具，要熟练掌握。因为线上环境通常都有很多限制，用不了图形化工具。当出现这些情况，上面的命令就是救命的。


### [8、如何将字符串反转？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#8如何将字符串反转)  


Stringbuilder或者stringbuffer的reverse方法


### [9、String 是最基本的数据类型吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#9string-是最基本的数据类型吗)  




不是。Java中的基本数据类型只有8个：byte、short、int、long、float、double、char、boolean；除了基本类型（primitive type），剩下的都是引用类型（reference type），Java 5以后引入的枚举类型也算是一种比较特殊的引用类型。


### [10、什么是代理模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#10什么是代理模式)  


通过代理控制对象的访问，可以在这个对象调用方法之前、调用方法之后去处理/添加新的功能。(也就是AO的P微实现)

代理在原有代码乃至原业务流程都不修改的情况下，直接在业务流程中切入新代码，增加新功能，这也和Spring的（面向切面编程）很相似


### [11、你知道哪些故障处理工具？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#11你知道哪些故障处理工具)  

### [12、如何阻止表单提交](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#12如何阻止表单提交)  

### [13、i与i的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#13i与i的区别)  

### [14、接口是什么？为什么要使用接口而不是直接使用具体类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#14接口是什么为什么要使用接口而不是直接使用具体类)  

### [15、你所了解的数据源技术有那些？使用数据源有什么好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#15你所了解的数据源技术有那些使用数据源有什么好处)  

### [16、并发关键字 synchronized ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#16并发关键字-synchronized-)  

### [17、Sql中delete与truncate的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#17sql中delete与truncate的区别)  

### [18、什么是Java程序的主类？应用程序和小程序的主类有何不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#18什么是java程序的主类应用程序和小程序的主类有何不同)  

### [19、java如何实现多线程之间的通讯和协作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#19java如何实现多线程之间的通讯和协作)  

### [20、什么时候使用访问者模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#20什么时候使用访问者模式)  

### [21、什么是UML？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#21什么是uml)  

### [22、如果对象的引用被置为null，垃圾收集器是否会立即释放对象占用的内存？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#22如果对象的引用被置为null垃圾收集器是否会立即释放对象占用的内存)  

### [23、Error与Exception区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#23error与exception区别)  

### [24、Get请求与post有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#24get请求与post有什么区别)  

### [25、jspservlet中通信作用域有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#25jspservlet中通信作用域有那些)  

### [26、类加载器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#26类加载器)  

### [27、BIO、NIO、AIO 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#27bionioaio-有什么区别)  

### [28、各种回收算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#28各种回收算法)  

### [29、接口和抽象类的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#29接口和抽象类的区别是什么)  

### [30、那针对浮点型数据运算出现的误差的问题，你怎么解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#30那针对浮点型数据运算出现的误差的问题你怎么解决)  

### [31、synchronized、volatile、CAS比较](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#31synchronizedvolatilecas比较)  

### [32、为什么代码会重排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#32为什么代码会重排序)  

### [33、ZGC 了解吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#33zgc-了解吗)  

### [34、线程池的优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#34线程池的优点)  

### [35、什么是Web Service（Web服务）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#35什么是web-serviceweb服务)  

### [36、四种构建线程池的区别及特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#36四种构建线程池的区别及特点)  

### [37、对象分配内存的方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#37对象分配内存的方式有哪些)  

### [38、什么是 Callable 和 Future?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#38什么是-callable-和-future)  

### [39、集合框架底层数据结构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#39集合框架底层数据结构)  

### [40、JDBC能否处理Blob和Clob？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题附答案汇总（2021年Java面试题及答案大全）.md#40jdbc能否处理blob和clob)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
