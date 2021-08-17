# Java面试题及答案汇总（2021年Java面试题答案大全）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、线程和进程区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#1线程和进程区别)  


什么是线程和进程?

**进程**

一个在内存中运行的应用程序。 每个正在系统上运行的程序都是一个进程

**线程**

进程中的一个执行任务（控制单元）， 它负责在程序里独立执行。

一个进程至少有一个线程，一个进程可以运行多个线程，多个线程可共享数据

**进程与线程的区别**

**1、** 根本区别：进程是操作系统资源分配的基本单位，而线程是处理器任务调度和执行的基本单位

**2、** 资源开销：每个进程都有独立的代码和数据空间（程序上下文），程序之间的切换会有较大的开销；线程可以看做轻量级的进程，同一类线程共享代码和数据空间，每个线程都有自己独立的运行栈和程序计数器（PC），线程之间切换的开销小。

**3、** 包含关系：如果一个进程内有多个线程，则执行过程不是一条线的，而是多条线（线程）共同完成的；线程是进程的一部分，所以线程也被称为轻权进程或者轻量级进程。

**4、** 内存分配：同一进程的线程共享本进程的地址空间和资源，而进程与进程之间的地址空间和资源是相互独立的

**5、** 影响关系：一个进程崩溃后，在保护模式下不会对其他进程产生影响，但是一个线程崩溃有可能导致整个进程都死掉。所以多进程要比多线程健壮。

**6、** 执行过程：每个独立的进程有程序运行的入口、顺序执行序列和程序出口。但是线程不能独立执行，必须依存在应用程序中，由应用程序提供多个线程执行控制，两者均可并发执行


### [2、列举一些你知道的打破双亲委派机制的例子。为什么要打破？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#2列举一些你知道的打破双亲委派机制的例子。为什么要打破)  


**1、** JNDI 通过引入线程上下文类加载器，可以在 Thread.setContextClassLoader 方法设置，默认是应用程序类加载器，来加载 SPI 的代码。有了线程上下文类加载器，就可以完成父类加载器请求子类加载器完成类加载的行为。打破的原因，是为了 JNDI 服务的类加载器是启动器类加载，为了完成高级类加载器请求子类加载器（即上文中的线程上下文加载器）加载类。

**2、** Tomcat，应用的类加载器优先自行加载应用目录下的 class，并不是先委派给父加载器，加载不了才委派给父加载器。打破的目的是为了完成应用间的类隔离。

**3、** OSGi，实现模块化热部署，为每个模块都自定义了类加载器，需要更换模块时，模块与类加载器一起更换。其类加载的过程中，有平级的类加载器加载行为。打破的原因是为了实现模块热替换。

**4、** JDK 9，Extension ClassLoader 被 Platform ClassLoader 取代，当平台及应用程序类加载器收到类加载请求，在委派给父加载器加载前，要先判断该类是否能够归属到某一个系统模块中，如果可以找到这样的归属关系，就要优先委派给负责那个模块的加载器完成加载。打破的原因，是为了添加模块化的特性。


### [3、CopyOnWriteArrayList可以用于什么应用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#3copyonwritearraylist可以用于什么应用场景)  


CopyOnWriteArrayList(免锁容器)的好处之一是当多个迭代器同时遍历和修改这个列表时，不会抛出ConcurrentModificationException。在CopyOnWriteArrayList中，写入将导致创建整个底层数组的副本，而源数组将保留在原地，使得复制的数组在被修改时，读取操作可以安全地执行。

**1、** 由于写操作的时候，需要拷贝数组，会消耗内存，如果原数组的内容比较多的情况下，可能导致young gc或者full gc；

**2、** 不能用于实时读的场景，像拷贝数组、新增元素都需要时间，所以调用一个set操作后，读取到数据可能还是旧的,虽然CopyOnWriteArrayList 能做到最终一致性,但是还是没法满足实时性要求；

**CopyOnWriteArrayList透露的思想**

**1、** 读写分离，读和写分开

**2、** 最终一致性

**3、** 使用另外开辟空间的思路，来解决并发冲突


### [4、我们能将 int 强制转换为 byte 类型的变量吗？如果该值大于 byte 类型的范围，将会出现什么现象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#4我们能将-int-强制转换为-byte-类型的变量吗如果该值大于-byte-类型的范围将会出现什么现象)  


是的，我们可以做强制转换，但是 Java 中 int 是 32 位的，而 byte 是 8 位的，所以，如果强制转化是，int 类型的高 24 位将会被丢弃，byte 类型的范围是从 -128 到 128。


### [5、成员变量与局部变量的区别有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#5成员变量与局部变量的区别有那些)  


**1、** 从语法形式上，看成员变量是属于类的，而局部变量是在方法中定义的变量或是方法的参数；成员变量可以被public,private,static等修饰符所修饰，而局部变量不能被访问控制修饰符及static所修饰；成员变量和局部变量都能被final所修饰；

**2、** 从变量在内存中的存储方式来看，成员变量是对象的一部分，而对象存在于堆内存，局部变量存在于栈内存

**3、** 从变量在内存中的生存时间上看，成员变量是对象的一部分，它随着对象的创建而存在，而局部变量随着方法的调用而自动消失。

**4、** 成员变量如果没有被赋初值，则会自动以类型的默认值而赋值（一种情况例外被final修饰但没有被static修饰的成员变量必须显示地赋值）；而局部变量则不会自动赋值。


### [6、哪些是 GC Roots？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#6哪些是-gc-roots)  


**1、** 在虚拟机栈（栈帧中的本地变量表）中引用的对象，譬如各个线程被调用的方法堆栈中使用到的参数、局部变量、临时变量等。

**2、** 在方法区中类静态属性引用的对象，譬如Java类的引用类型静态变量。

**3、** 在方法区中常量引用的对象，譬如字符串常量池（String Table）里的引用。

**4、** 在本地方法栈中JNI（即通常所说的Native方法）引用的对象。

**5、** Java虚拟机内部的引用，如基本数据类型对应的Class对象，一些常驻的异常对象（比如 NullPointExcepiton、OutOfMemoryError）等，还有系统类加载器。

**6、** 所有被同步锁（synchronized关键字）持有的对象。

**7、** 反映 Java 虚拟机内部情况的 JMXBean、JVMTI中注册的回调、本地代码缓存等。


### [7、你能解释一下里氏替换原则吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#7你能解释一下里氏替换原则吗)  


[https://blog.csdn.net/pu_xubo565599455/article/details/51488323](https://blog.csdn.net/pu_xubo565599455/article/details/51488323)


### [8、类加载为什么要使用双亲委派模式，有没有什么场景是打破了这个模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#8类加载为什么要使用双亲委派模式有没有什么场景是打破了这个模式)  


**双亲委托模型的重要用途是为了解决类载入过程中的安全性问题。**

**1、** 假设有一个开发者自己编写了一个名为`java.lang.Object`的类，想借此欺骗JVM。现在他要使用自定义`ClassLoader`来加载自己编写的`java.lang.Object`类。

**2、** 然而幸运的是，双亲委托模型不会让他成功。因为JVM会优先在`Bootstrap ClassLoader`的路径下找到`java.lang.Object`类，并载入它

Java的类加载是否一定遵循双亲委托模型？

**1、** 在实际开发中，我们可以通过自定义ClassLoader，并重写父类的loadClass方法，来打破这一机制。

**2、** SPI就是打破了双亲委托机制的(SPI：服务提供发现)。


### [9、为什么Thread类的sleep()和yield ()方法是静态的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#9为什么thread类的sleep和yield-方法是静态的)  


Thread类的sleep()和yield()方法将在当前正在执行的线程上运行。所以在其他处于等待状态的线程上调用这些方法是没有意义的。这就是为什么这些方法是静态的。它们可以在当前正在执行的线程中工作，并避免程序员错误的认为可以在其他非运行线程调用这些方法。


### [10、在监视器(Monitor)内部，是如何做线程同步的？程序应该做哪种级别的同步？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#10在监视器monitor内部是如何做线程同步的程序应该做哪种级别的同步)  


在 java 虚拟机中，监视器和锁在Java虚拟机中是一块使用的。监视器监视一块同步代码块，确保一次只有一个线程执行同步代码块。每一个监视器都和一个对象引用相关联。线程在获取锁之前不允许执行同步代码。

一旦方法或者代码块被 synchronized 修饰，那么这个部分就放入了监视器的监视区域，确保一次只能有一个线程执行该部分的代码，线程在获取锁之前不允许执行该部分的代码

另外 java 还提供了显式监视器( Lock )和隐式监视器( synchronized )两种锁方案


### [11、Java 中你怎样唤醒一个阻塞的线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#11java-中你怎样唤醒一个阻塞的线程)  

### [12、并发队列的常用方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#12并发队列的常用方法)  

### [13、线程池中 submit() 和 execute() 方法有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#13线程池中-submit-和-execute-方法有什么区别)  

### [14、计算机网络有几层？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#14计算机网络有几层)  

### [15、并发编程三个必要因素是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#15并发编程三个必要因素是什么)  

### [16、ArrayList 与 LinkedList 的不区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#16arraylist-与-linkedlist-的不区别)  

### [17、描述一下什么情况下，对象会从年轻代进入老年代](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#17描述一下什么情况下对象会从年轻代进入老年代)  

### [18、volatile有什么用？能否用一句话说明下volatile的应用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#18volatile有什么用能否用一句话说明下volatile的应用场景)  

### [19、解释什么是Tomcat Valve?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#19解释什么是tomcat-valve)  

### [20、本地方法栈的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#20本地方法栈的作用)  

### [21、3*0.1 == 0.3 将会返回什么？true 还是 false？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#213*01--03-将会返回什么true-还是-false)  

### [22、你知道哪些内存分配与回收策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#22你知道哪些内存分配与回收策略)  

### [23、请说明NAT协议的目的是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#23请说明nat协议的目的是什么)  

### [24、什么是上下文切换?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#24什么是上下文切换)  

### [25、Files的常用方法都有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#25files的常用方法都有哪些)  

### [26、观察者模式应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#26观察者模式应用场景)  

### [27、各种回收器，各自优缺点，重点CMS、G1](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#27各种回收器各自优缺点重点cmsg1)  

### [28、标记整理算法(Mark-Compact)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#28标记整理算法mark-compact)  

### [29、抽象类能使用 final 修饰吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#29抽象类能使用-final-修饰吗)  

### [30、如何确保线程安全？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#30如何确保线程安全)  

### [31、静态嵌套类(Static Nested Class)和内部类（Inner Class）的不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#31静态嵌套类static-nested-class和内部类inner-class的不同)  

### [32、什么是线程异步？什么是线程同步？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#32什么是线程异步什么是线程同步)  

### [33、synchronized的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#33synchronized的作用)  

### [34、哪些集合类是线程安全的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#34哪些集合类是线程安全的)  

### [35、JVM 数据运行区，哪些会造成 OOM 的情况？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#35jvm-数据运行区哪些会造成-oom-的情况)  

### [36、Java 中，编写多线程程序的时候你会遵循哪些最佳实践？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#36java-中编写多线程程序的时候你会遵循哪些最佳实践)  

### [37、什么是可重入锁（ReentrantLock）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#37什么是可重入锁reentrantlock)  

### [38、AQS支持两种同步方式：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#38aqs支持两种同步方式：)  

### [39、你了解过哪些垃圾收集器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#39你了解过哪些垃圾收集器)  

### [40、HashMap的扩容操作是怎么实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案汇总（2021年Java面试题答案大全）.md#40hashmap的扩容操作是怎么实现的)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
