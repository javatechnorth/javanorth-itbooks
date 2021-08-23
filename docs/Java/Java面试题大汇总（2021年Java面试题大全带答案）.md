# Java面试题大汇总（2021年Java面试题大全带答案）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、请阐述Catalina的配置文件有哪些?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#1请阐述catalina的配置文件有哪些)  


Catalina包含的配置文件有：

**1、** ·policy

**2、** ·properties

**3、** ·properties

**4、** ·xml

**5、** ·xml

**6、** ·Tomcat-users.xml


### [2、Java中有几种类型的流？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#2java中有几种类型的流)  




字节流和字符流。字节流继承于InputStream、OutputStream，字符流继承于Reader、Writer。在java.io 包中还有许多其他的流，主要是为了提高性能和使用方便。关于Java的I/O需要注意的有两点：一是两种对称性（输入和输出的对称性，字节和字符的对称性）；二是两种设计模式（适配器模式和装潢模式）。另外Java中的流不同于C#的是它只有一个维度一个方向。

> 面试题 - 编程实现文件拷贝。（这个题目在笔试的时候经常出现，下面的代码给出了两种实现方案）


```
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.nio.ByteBuffer;
import java.nio.channels.FileChannel;

public final class MyUtil {

    private MyUtil() {
        throw new AssertionError();
    }

    public static void fileCopy(String source, String target) throws IOException {
        try (InputStream in = new FileInputStream(source)) {
            try (OutputStream out = new FileOutputStream(target)) {
                byte[] buffer = new byte[4096];
                int bytesToRead;
                while((bytesToRead = in.read(buffer)) != -1) {
                    out.write(buffer, 0, bytesToRead);
                }
            }
        }
    }

    public static void fileCopyNIO(String source, String target) throws IOException {
        try (FileInputStream in = new FileInputStream(source)) {
            try (FileOutputStream out = new FileOutputStream(target)) {
                FileChannel inChannel = in.getChannel();
                FileChannel outChannel = out.getChannel();
                ByteBuffer buffer = ByteBuffer.allocate(4096);
                while(inChannel.read(buffer) != -1) {
                    buffer.flip();
                    outChannel.write(buffer);
                    buffer.clear();
                }
            }
        }
    }
}
```

> 注意：上面用到Java 7的TWR，使用TWR后可以不用在finally中释放外部资源 ，从而让代码更加优雅。



### [3、当一个线程进入一个对象的synchronized方法A之后，其它线程是否可进入此对象的synchronized方法B？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#3当一个线程进入一个对象的synchronized方法a之后其它线程是否可进入此对象的synchronized方法b)  




不能。其它线程只能访问该对象的非同步方法，同步方法则不能进入。因为非静态方法上的synchronized修饰符要求执行方法时要获得对象的锁，如果已经进入A方法说明对象锁已经被取走，那么试图进入B方法的线程就只能在等锁池（注意不是等待池哦）中等待对象的锁。


### [4、什么是不可变对象（immutable object）？Java 中怎么创建一个不可变对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#4什么是不可变对象immutable-objectjava-中怎么创建一个不可变对象)  


不可变对象指对象一旦被创建，状态就不能再改变。任何修改都会创建一个新的对象，如 String、Integer及其它包装类。详情参见答案，一步一步指导你在 Java 中创建一个不可变的类。


### [5、怎么利用 JUnit 来测试一个方法的异常？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#5怎么利用-junit-来测试一个方法的异常)  


[http://javarevisited.blogspot.sg/2013/04/JUnit-tutorial-example-test-exception-thrown-by-java-method.html](http://javarevisited.blogspot.sg/2013/04/JUnit-tutorial-example-test-exception-thrown-by-java-method.html)


### [6、两个相同的对象会有不同的的 hash code 吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#6两个相同的对象会有不同的的-hash-code-吗)  


不能，根据 hash code 的规定，这是不可能的。


### [7、如果你提交任务时，线程池队列已满，这时会发生什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#7如果你提交任务时线程池队列已满这时会发生什么)  


**有俩种可能：**

**1、** 如果使用的是无界队列 LinkedBlockingQueue，也就是无界队列的话，没关系，继续添加任务到阻塞队列中等待执行，因为 LinkedBlockingQueue 可以近乎认为是一个无穷大的队列，可以无限存放任务

**2、** 如果使用的是有界队列比如 ArrayBlockingQueue，任务首先会被添加到ArrayBlockingQueue 中，ArrayBlockingQueue 满了，会根据maximumPoolSize 的值增加线程数量，如果增加了线程数量还是处理不过来，ArrayBlockingQueue 继续满，那么则会使用拒绝策略RejectedExecutionHandler 处理满了的任务，默认是 AbortPolicy


### [8、GC日志的real、user、sys是什么意思？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#8gc日志的realusersys是什么意思)  


`real` 实际花费的时间，指的是从开始到结束所花费的时间。比如进程在等待I/O完成，这个阻塞时间也会被计算在内。`user` 指的是进程在用户态（User Mode）所花费的时间，只统计本进程所使用的时间，是指多核。`sys` 指的是进程在核心态（Kernel Mode）花费的CPU时间量，指的是内核中的系统调用所花费的时间，只统计本进程所使用的时间。

这个是用来看日志用的，如果你不看日志，那不了解也无妨。不过，这三个参数的意义，在你能看到的地方，基本上都是一致的，比如操作系统。


### [9、解释 Java 堆空间及 GC？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#9解释-java-堆空间及-gc)  


当通过 Java 命令启动 Java 进程的时候，会为它分配内存。内存的一部分用于创建堆空间，当程序中创建对象的时候，就从对空间中分配内存。GC 是 JVM 内部的一个进程，回收无效对象的内存用于将来的分配。


### [10、类的实例化顺序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#10类的实例化顺序)  


**比如父类静态数据，构造函数，字段，子类静态数据，构造函数，字段，他们的执行顺序**

先静态、先父后子。

先静态：父静态 > 子静态

优先级：父类 > 子类 静态代码块 > 非静态代码块 > 构造函数

**一个类的实例化过程：**

**1、** 父类中的static代码块，当前类的static

**2、** 顺序执行父类的普通代码块

**3、** 父类的构造函数

**4、** 子类普通代码块

**5、** 子类（当前类）的构造函数，按顺序执行。

**6、** 子类方法的执行，


### [11、线程的状态](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#11线程的状态)  

### [12、Java 中，嵌套公共静态类与顶级类有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#12java-中嵌套公共静态类与顶级类有什么不同)  

### [13、Java死锁以及如何避免？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#13java死锁以及如何避免)  

### [14、同步方法和同步块，哪个是更好的选择?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#14同步方法和同步块哪个是更好的选择)  

### [15、字符串常量存放在哪个区域？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#15字符串常量存放在哪个区域)  

### [16、84.Map有什么特点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#1684map有什么特点)  

### [17、HTTP的状态码](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#17http的状态码)  

### [18、说出几条 Java 中方法重载的最佳实践？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#18说出几条-java-中方法重载的最佳实践)  

### [19、Java 如何实现多线程之间的通讯和协作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#19java-如何实现多线程之间的通讯和协作)  

### [20、Java Concurrency API中的Lock接口(Lock interface)是什么？对比同步它有什么优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#20java-concurrency-api中的lock接口lock-interface是什么对比同步它有什么优势)  

### [21、用Java写一个折半查找。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#21用java写一个折半查找。)  

### [22、创建线程的有哪些方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#22创建线程的有哪些方式)  

### [23、== 和 equals 的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#23-和-equals-的区别是什么)  

### [24、页面前进或者后退](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#24页面前进或者后退)  

### [25、双亲委派机制可以被违背吗？请举例说明。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#25双亲委派机制可以被违背吗请举例说明。)  

### [26、简述一下你了解的设计模式。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#26简述一下你了解的设计模式。)  

### [27、JVM 选项 -XX:+UseCompressedOops 有什么作用？为什么要使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#27jvm-选项--xx:+usecompressedoops-有什么作用为什么要使用)  

### [28、什么是方法内联？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#28什么是方法内联)  

### [29、什么是 CAS](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#29什么是-cas)  

### [30、Js如何跳转到到一个指定页面](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#30js如何跳转到到一个指定页面)  

### [31、什么是线程局部变量？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#31什么是线程局部变量)  

### [32、Java 中怎么获取一份线程 dump 文件？你如何在 Java 中获取线程堆栈？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#32java-中怎么获取一份线程-dump-文件你如何在-java-中获取线程堆栈)  

### [33、Java 的引用有哪些类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#33java-的引用有哪些类型)  

### [34、什么是FutureTask?使用ExecutorService启动任务。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#34什么是futuretask使用executorservice启动任务。)  

### [35、Spring MVC的工作原理是怎样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#35spring-mvc的工作原理是怎样的)  

### [36、阐述ArrayList、Vector、LinkedList的存储性能和特性。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#36阐述arraylistvectorlinkedlist的存储性能和特性。)  

### [37、可达性分析](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#37可达性分析)  

### [38、请解释将Tomcat作为一个Windows 服务运行会带来哪些好处?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#38请解释将tomcat作为一个windows-服务运行会带来哪些好处)  

### [39、HashMap是怎么解决哈希冲突的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#39hashmap是怎么解决哈希冲突的)  

### [40、finalize()方法什么时候被调用？析构函数(finalization)的目的是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题大汇总（2021年Java面试题大全带答案）.md#40finalize方法什么时候被调用析构函数finalization的目的是什么)  





