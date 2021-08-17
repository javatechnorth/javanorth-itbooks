# Java面试题及答案大全（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、Sql优化有那些方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#1sql优化有那些方法)  


**1、** 表的设计要规范，即要符合数据库设计三范式。

**2、** 适当建立索引，在频繁作为检索条件，更新较少的字段上建立索引，以提高查询速度。

**3、** 分表查询，有水平分割、垂直分割。

**4、** 读写分离，读(read)、写(create、update、delete)。

**5、** 建立存储过程。


### [2、用 Java 写一个线程安全的单例模式（Singleton）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#2用-java-写一个线程安全的单例模式singleton)  


答案

[http://javarevisited.blogspot.in/2012/12/how-to-create-thread-safe-singleton-in-java-example.html](http://javarevisited.blogspot.in/2012/12/how-to-create-thread-safe-singleton-in-java-example.html)

请参考答案中的示例代码，这里面一步一步教你创建一个线程安全的 Java 单例类。当我们说线程安全时，意思是即使初始化是在多线程环境中，仍然能保证单个实例。Java 中，使用枚举作为单例类是最简单的方式来创建线程安全单例模式的方式。


### [3、在 Java 中，对象什么时候可以被垃圾回收？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#3在-java-中对象什么时候可以被垃圾回收)  


当对象对当前使用这个对象的应用程序变得不可触及的时候，这个对象就可以被回收了。


### [4、线程的 run()和 start()有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#4线程的-run和-start有什么区别)  


**1、** 每个线程都是通过某个特定Thread对象所对应的方法run()来完成其操作的，run()方法称为线程体。通过调用Thread类的start()方法来启动一个线程。

**2、** start() 方法用于启动线程，run() 方法用于执行线程的运行时代码。run() 可以重复调用，而 start() 只能调用一次。

**3、** start()方法来启动一个线程，真正实现了多线程运行。调用start()方法无需等待run方法体代码执行完毕，可以直接继续执行其他的代码； 此时线程是处于就绪状态，并没有运行。 然后通过此Thread类调用方法run()来完成其运行状态， run()方法运行结束， 此线程终止。然后CPU再调度其它线程。

**4、** run()方法是在本线程里的，只是线程里的一个函数，而不是多线程的。 如果直接调用run()，其实就相当于是调用了一个普通函数而已，直接待用run()方法必须等待run()方法执行完毕才能执行下面的代码，所以执行路径还是只有一条，根本就没有线程的特征，所以在多线程执行时要使用start()方法而不是run()方法。


### [5、重排序实际执行的指令步骤](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#5重排序实际执行的指令步骤)  


![87_5.png][87_5.png]

**1、** 编译器优化的重排序。编译器在不改变单线程程序语义的前提下，可以重新安排语句的执行顺序。

**2、** 指令级并行的重排序。现代处理器采用了指令级并行技术（ILP）来将多条指令重叠执行。如果不存在数据依赖性，处理器可以改变语句对应机器指令的执行顺序。

**3、** 内存系统的重排序。由于处理器使用缓存和读/写缓冲区，这使得加载和存储操作看上去可能是在乱序执行。

这些重排序对于单线程没问题，但是多线程都可能会导致多线程程序出现内存可见性问题。


### [6、Java中异常分为哪两种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#6java中异常分为哪两种)  


**1、** 编译时异常

**2、** 运行时异常


### [7、什么是并发容器的实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#7什么是并发容器的实现)  


何为同步容器：可以简单地理解为通过 synchronized 来实现同步的容器，如果有多个线程调用同步容器的方法，它们将会串行执行。比如 Vector，Hashtable，以及 Collections.synchronizedSet，synchronizedList 等方法返回的容器。可以通过查看 Vector，Hashtable 等这些同步容器的实现代码，可以看到这些容器实现线程安全的方式就是将它们的状态封装起来，并在需要同步的方法上加上关键字 synchronized。

并发容器使用了与同步容器完全不同的加锁策略来提供更高的并发性和伸缩性，例如在 ConcurrentHashMap 中采用了一种粒度更细的加锁机制，可以称为分段锁，在这种锁机制下，允许任意数量的读线程并发地访问 map，并且执行读操作的线程和写操作的线程也可以并发的访问 map，同时允许一定数量的写操作线程并发地修改 map，所以它可以在并发环境下实现更高的吞吐量。


### [8、创建线程的四种方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#8创建线程的四种方式)  


**继承 Thread 类；**

```
public class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName() + " run()方法正在执行...");
}
```

**实现 Runnable 接口；**

```
public class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName() + " run()方法执行中...");
}
```

**实现 Callable 接口；**

```
public class MyCallable implements Callable<Integer> {

@Override
public Integer call() {
    System.out.println(Thread.currentThread().getName() + " call()方法执行中...");
    return 1;
}
```

**使用匿名内部类方式**

```
public class CreateRunnable {
    public static void main(String[] args) {
        //创建多线程创建开始
        Thread thread = new Thread(new Runnable() {
                    public void run() {
                    for (int i = 0; i < 10; i++) {
                    System.out.println("i:" + i);
                }
            }
        });
        thread.start();
    }
}
```


### [9、Java 中，直接缓冲区与非直接缓冲器有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#9java-中直接缓冲区与非直接缓冲器有什么区别)  


答案

[http://javarevisited.blogspot.sg/2015/08/difference-between-direct-non-direct-mapped-bytebuffer-nio-java.html](http://javarevisited.blogspot.sg/2015/08/difference-between-direct-non-direct-mapped-bytebuffer-nio-java.html)


### [10、poll() 方法和 remove() 方法的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#10poll-方法和-remove-方法的区别)  


poll() 和 remove() 都是从队列中取出一个元素，但是 poll() 在获取元素失败的时候会返回空，但是 remove() 失败的时候会抛出异常。


### [11、谈谈你知道的垃圾回收算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#11谈谈你知道的垃圾回收算法)  

### [12、什么是OOP?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#12什么是oop)  

### [13、OOP 中的 组合、聚合和关联有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#13oop-中的-组合聚合和关联有什么区别)  

### [14、你平时工作中用过的JVM常用基本配置参数有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#14你平时工作中用过的jvm常用基本配置参数有哪些)  

### [15、请解释什么是Tomcat Coyote ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#15请解释什么是tomcat-coyote-)  

### [16、线程的基本状态以及状态之间的关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#16线程的基本状态以及状态之间的关系)  

### [17、Java语言采用何种编码方案？有何特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#17java语言采用何种编码方案有何特点)  

### [18、描述一下JVM加载class文件的原理机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#18描述一下jvm加载class文件的原理机制)  

### [19、什么是Vector](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#19什么是vector)  

### [20、HashMap 与 HashTable 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#20hashmap-与-hashtable-有什么区别)  

### [21、程序计数器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#21程序计数器是什么)  

### [22、Lock 接口和synchronized 对比同步它有什么优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#22lock-接口和synchronized-对比同步它有什么优势)  

### [23、列出一些你常见的运行时异常？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#23列出一些你常见的运行时异常)  

### [24、一个类文件中能否有多个类？有什么要求？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#24一个类文件中能否有多个类有什么要求)  

### [25、关于 OOP 和设计模式的面试题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#25关于-oop-和设计模式的面试题)  

### [26、JDBC中如何进行事务处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#26jdbc中如何进行事务处理)  

### [27、64 位 JVM 中，int 的长度是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#2764-位-jvm-中int-的长度是多数)  

### [28、Session与cookie的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#28session与cookie的区别)  

### [29、什么是多态机制？Java语言是如何实现多态的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#29什么是多态机制java语言是如何实现多态的)  

### [30、Java线程池中submit() 和 execute()方法有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#30java线程池中submit-和-execute方法有什么区别)  

### [31、Java 中 java.util.Date 与 java.sql.Date 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#31java-中-javautildate-与-javasqldate-有什么区别)  

### [32、Java 中，Maven 和 ANT 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#32java-中maven-和-ant-有什么区别)  

### [33、什么是线程组，为什么在Java中不推荐使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#33什么是线程组为什么在java中不推荐使用)  

### [34、Serial 垃圾收集器（单线程、 复制算法）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#34serial-垃圾收集器单线程-复制算法)  

### [35、讲讲什么情况下会出现内存溢出，内存泄漏？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#35讲讲什么情况下会出现内存溢出内存泄漏)  

### [36、描述 Java 中的重载和重写？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#36描述-java-中的重载和重写)  

### [37、单例防止反射漏洞攻击](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#37单例防止反射漏洞攻击)  

### [38、什么是字节码？采用字节码的最大好处是什么？什么Java是虚拟机？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#38什么是字节码采用字节码的最大好处是什么什么java是虚拟机)  

### [39、Java都有那些开发平台？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#39java都有那些开发平台)  

### [40、你经常使用什么并发容器，为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题及答案大全（2021年Java面试题答案大汇总）.md#40你经常使用什么并发容器为什么)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
