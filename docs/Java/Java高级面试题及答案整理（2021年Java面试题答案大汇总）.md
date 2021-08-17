# Java高级面试题及答案整理（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、如何让正在运行的线程暂停一段时间？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#1如何让正在运行的线程暂停一段时间)  


我们可以使用Thread类的Sleep()方法让线程暂停一段时间。需要注意的是，这并不会让线程终止，一旦从休眠中唤醒线程，线程的状态将会被改变为Runnable，并且根据线程调度，它将得到执行。


### [2、原型模式的应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#2原型模式的应用场景)  


**1、** 类初始化需要消化非常多的资源，这个资源包括数据、硬件资源等。这时我们就可以通过原型拷贝避免这些消耗。

**2、** 通过new产生的一个对象需要非常繁琐的数据准备或者权限，这时可以使用原型模式。

**3、** 一个对象需要提供给其他对象访问，而且各个调用者可能都需要修改其值时，可以考虑使用原型模式拷贝多个对象供调用者使用，即保护性拷贝。

我们Spring框架中的多例就是使用原型


### [3、Java中各种数据默认值](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#3java中各种数据默认值)  


**1、** Byte,short,int,long默认是都是0

**2、** Boolean默认值是false

**3、** Char类型的默认值是’’

**4、** Float与double类型的默认是0.0

**5、** 对象类型的默认值是null


### [4、生产上如何配置垃圾收集器的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#4生产上如何配置垃圾收集器的)  


首先是内存大小问题，基本上每一个内存区域我都会设置一个上限，来避免溢出问题，比如元空间。通常，堆空间我会设置成操作系统的`2/3`（这是想给其他进程和操作系统预留一些时间），超过8GB的堆优先选用G1。

接下来，我会对JVM进行初步优化。比如根据老年代的对象提升速度，来调整年轻代和老年代之间的比例。

再接下来，就是专项优化，主要判断的依据就是系统容量、访问延迟、吞吐量等。我们的服务是高并发的，所以对STW的时间非常敏感。

我会通过记录详细的GC日志，来找到这个瓶颈点，借用`gceasy`（重点）这样的日志分析工具，很容易定位到问题。之所以选择采用工具，是因为gc日志看起来实在是太麻烦了，gceasy号称是AI学习分析问题，可视化做的较好。


### [5、为什么wait和notify方法要在同步块中调用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#5为什么wait和notify方法要在同步块中调用)  


Java API强制要求这样做，如果你不这么做，你的代码会抛出IllegalMonitorStateException异常。还有一个原因是为了避免wait和notify之间产生竞态条件。


### [6、类与对象的关系?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#6类与对象的关系)  


类是对象的抽象，对象是类的具体，类是对象的模板，对象是类的实例


### [7、说说类加载的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#7说说类加载的过程)  


加载 验证 准备（为一些类变量分配内存，并将其初始化为默认值） 解析（将符号引用替换为直接引用。类和接口、类方法、接口方法、字段等解析） 初始化


### [8、JSP中的静态包含和动态包含有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#8jsp中的静态包含和动态包含有什么区别)  


静态包含是通过JSP的include指令包含页面，动态包含是通过JSP标准动作  包含页面。

静态包含是编译时包含，如果包含的页面不存在则会产生编译错误，而且两个页面的"contentType"属性应保持一致，因为两个页面会合二为一，只产生一个class文件，因此被包含页面发生的变动再包含它的页面更新前不会得到更新。

动态包含是运行时包含，可以向被包含的页面传递参数，包含页面和被包含页面是独立的，会编译出两个class文件，如果被包含的页面不存在，不会产生编译错误，也不影响页面其他部分的执行。


### [9、抽象类可以使用final修饰吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#9抽象类可以使用final修饰吗)  


不可以。定义抽象类就是让其他继承的，而final修饰类表示该类不能被继承，与抽象类的理念违背了


### [10、介绍一下类文件结构吧！](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#10介绍一下类文件结构吧)  


魔数: 确定这个文件是否为一个能被虚拟机接收的 Class 文件。Class 文件版本 ：Class 文件的版本号，保证编译正常执行。常量池 ：常量池主要存放两大常量：字面量和符号引用。访问标志 ：标志用于识别一些类或者接口层次的访问信息，包括：这个 Class 是类还是接口，是否为 public 或者 abstract 类型，如果是类的话是否声明为 final 等等。当前类索引,父类索引 ：类索引用于确定这个类的全限定名，父类索引用于确定这个类的父类的全限定名，由于 Java 语言的单继承，所以父类索引只有一个，除了 java.lang.Object 之外，所有的 java 类都有父类，因此除了 java.lang.Object 外，所有 Java 类的父类索引都不为 0。接口索引集合 ：接口索引集合用来描述这个类实现了那些接口，这些被实现的接口将按implents(如果这个类本身是接口的话则是extends) 后的接口顺序从左到右排列在接口索引集合中。字段表集合 ：描述接口或类中声明的变量。字段包括类级变量以及实例变量，但不包括在方法内部声明的局部变量。方法表集合 ：类中的方法。属性表集合 ：在 Class 文件，字段表，方法表中都可以携带自己的属性表集合。


### [11、工作中常用的 JVM 配置参数有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#11工作中常用的-jvm-配置参数有哪些)  

### [12、final、finalize 和 finally 的不同之处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#12finalfinalize-和-finally-的不同之处)  

### [13、React最新的生命周期是怎样的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#13react最新的生命周期是怎样的)  

### [14、说出 JDK 1.7 中的三个新特性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#14说出-jdk-17-中的三个新特性)  

### [15、什么是不可变对象，它对写并发应用有什么帮助？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#15什么是不可变对象它对写并发应用有什么帮助)  

### [16、Semaphore有什么作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#16semaphore有什么作用)  

### [17、redux中如何进行异步操作?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#17redux中如何进行异步操作)  

### [18、JVM 选项 -XX:+UseCompressedOops 有什么作用？为什么要使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#18jvm-选项--xx:+usecompressedoops-有什么作用为什么要使用)  

### [19、同步方法和同步块，哪个是更好的选择？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#19同步方法和同步块哪个是更好的选择)  

### [20、什么是重写？什么是重载？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#20什么是重写什么是重载)  

### [21、内部类可以引用它的包含类（外部类）的成员吗？有没有什么限制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#21内部类可以引用它的包含类外部类的成员吗有没有什么限制)  

### [22、线程的调度策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#22线程的调度策略)  

### [23、乐观锁和悲观锁的理解及如何实现，有哪些实现方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#23乐观锁和悲观锁的理解及如何实现有哪些实现方式)  

### [24、Java线程数过多会造成什么异常？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#24java线程数过多会造成什么异常)  

### [25、栈帧都有哪些数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#25栈帧都有哪些数据)  

### [26、React组件通信如何实现?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#26react组件通信如何实现)  

### [27、什么时候使用组合模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#27什么时候使用组合模式)  

### [28、Java 中的 LinkedList 是单向链表还是双向链表？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#28java-中的-linkedlist-是单向链表还是双向链表)  

### [29、什么是JDK？什么是JRE?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#29什么是jdk什么是jre)  

### [30、什么是单例](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#30什么是单例)  

### [31、什么是内存屏障？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#31什么是内存屏障)  

### [32、数组有没有length()方法？String有没有length()方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#32数组有没有length方法string有没有length方法)  

### [33、栈溢出的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#33栈溢出的原因)  

### [34、打印昨天的当前时刻。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#34打印昨天的当前时刻。)  

### [35、运行时常量池的作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#35运行时常量池的作用是什么)  

### [36、as-if-serial规则和happens-before规则的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#36as-if-serial规则和happens-before规则的区别)  

### [37、存在两个类，B 继承 A，C 继承 B，我们能将 B 转换为 C 么？如 C = (C) B；](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#37存在两个类b-继承-ac-继承-b我们能将-b-转换为-c-么如-c-=-c-b；)  

### [38、在调用子类构造方法之前会先调用父类没有参数的构造方法，其目的是？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#38在调用子类构造方法之前会先调用父类没有参数的构造方法其目的是)  

### [39、原型模式的使用方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#39原型模式的使用方式)  

### [40、48、List、Set、Map 和 Queue 之间的区别(答案)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案整理（2021年Java面试题答案大汇总）.md#4048listsetmap-和-queue-之间的区别答案)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
