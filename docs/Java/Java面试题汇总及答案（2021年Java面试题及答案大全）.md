# Java面试题汇总及答案（2021年Java面试题及答案大全）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Spring中自动装配的方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#1spring中自动装配的方式有哪些)  


**1、** no：不进行自动装配，手动设置Bean的依赖关系。

**2、** byName：根据Bean的名字进行自动装配。

**3、** byType：根据Bean的类型进行自动装配。

**4、** constructor：类似于byType，不过是应用于构造器的参数，如果正好有一个Bean与构造器的参数类型相同则可以自动装配，否则会导致错误。

**5、** autodetect：如果有默认的构造器，则通过constructor的方式进行自动装配，否则使用byType的方式进行自动装配。


### [2、栈帧里面包含哪些东西？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#2栈帧里面包含哪些东西)  


局部变量表、操作数栈、动态连接、返回地址等


### [3、你是如何调用 wait() 方法的？使用 if 块还是循环？为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#3你是如何调用-wait-方法的使用-if-块还是循环为什么)  


处于等待状态的线程可能会收到错误警报和伪唤醒，如果不在循环中检查等待条件，程序就会在没有满足结束条件的情况下退出。

wait() 方法应该在循环调用，因为当线程获取到 CPU 开始执行的时候，其他条件可能还没有满足，所以在处理前，循环检测条件是否满足会更好。下面是一段标准的使用 wait 和 notify 方法的代码：

```
synchronized (monitor) {
    //  判断条件谓词是否得到满足
    while(!locked) {
    //  等待唤醒
    monitor.wait();
    }
    //  处理其他的业务逻辑
}
```


### [4、ArrayList与LinkedList有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#4arraylist与linkedlist有什么区别)  


**1、** ArrayList与LinkedList都实现了List接口。

**2、** ArrayList是线性表，底层是使用数组实现的，它在尾端插入和访问数据时效率较高，

**3、** Linked是双向链表，他在中间插入或者头部插入时效率较高，在访问数据时效率较低


### [5、Super与this表示什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#5super与this表示什么)  


**1、** Super表示当前类的父类对象

**2、** This表示当前类的对象


### [6、简述Java的对象结构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#6简述java的对象结构)  


Java对象由三个部分组成：对象头、实例数据、对齐填充。

对象头由两部分组成，第一部分存储对象自身的运行时数据：哈希码、GC分代年龄、锁标识状态、线程持有的锁、偏向线程ID（一般占32/64 bit）。第二部分是指针类型，指向对象的类元数据类型（即对象代表哪个类）。如果是数组对象，则对象头中还有一部分用来记录数组长度。

实例数据用来存储对象真正的有效信息（包括父类继承下来的和自己定义的）

对齐填充：JVM要求对象起始地址必须是8字节的整数倍（8字节对齐 )


### [7、Java 虚拟机栈的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#7java-虚拟机栈的作用)  


**Java 虚拟机栈**来描述 Java 方法的内存模型。每当有新线程创建时就会分配一个栈空间，线程结束后栈空间被回收，栈与线程拥有相同的生命周期。栈中元素用于支持虚拟机进行方法调用，每个方法在执行时都会创建一个栈帧存储方法的局部变量表、操作栈、动态链接和方法出口等信息。每个方法从调用到执行完成，就是栈帧从入栈到出栈的过程。

有两类异常：① 线程请求的栈深度大于虚拟机允许的深度抛出 StackOverflowError。② 如果 JVM 栈容量可以动态扩展，栈扩展无法申请足够内存抛出 OutOfMemoryError（HotSpot 不可动态扩展，不存在此问题）。


### [8、实际开发中应用场景哪里用到了模板方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#8实际开发中应用场景哪里用到了模板方法)  


其实很多框架中都有用到了模板方法模式

**例如：**

数据库访问的封装、Junit单元测试、servlet中关于doGet/doPost方法的调用等等


### [9、import java和javax有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#9import-java和javax有什么区别)  


[tech.souyunku.com/EasonJim/p/…](http://tech.souyunku.com/EasonJim/p/6993139.html)


### [10、构造器（constructor）是否可被重写（override）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#10构造器constructor是否可被重写override)  




构造器不能被继承，因此不能被重写，但可以被重载。


### [11、在Java中定义一个不做事且没有参数的构造方法的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#11在java中定义一个不做事且没有参数的构造方法的作用)  

### [12、int和Integer有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#12int和integer有什么区别)  

### [13、类加载的过程是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#13类加载的过程是什么)  

### [14、String 属于基础的数据类型吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#14string-属于基础的数据类型吗)  

### [15、a.hashCode() 有什么用？与 a.equals(b) 有什么关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#15ahashcode-有什么用与-aequalsb-有什么关系)  

### [16、两个对象的 hashCode()相同，则 equals()也一定为 true，对吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#16两个对象的-hashcode相同则-equals也一定为-true对吗)  

### [17、说说ZGC垃圾收集器的工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#17说说zgc垃圾收集器的工作原理)  

### [18、分代收集算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#18分代收集算法)  

### [19、什么是多线程的上下文切换](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#19什么是多线程的上下文切换)  

### [20、在没有使用临时变量的情况如何交换两个整数变量的值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#20在没有使用临时变量的情况如何交换两个整数变量的值)  

### [21、JAVA弱引用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#21java弱引用)  

### [22、为什么要学习工厂设计模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#22为什么要学习工厂设计模式)  

### [23、什么是多线程中的上下文切换？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#23什么是多线程中的上下文切换)  

### [24、描述一下 JVM 加载 class 文件的原理机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#24描述一下-jvm-加载-class-文件的原理机制)  

### [25、说一下 Atomic的原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#25说一下-atomic的原理)  

### [26、&和&&的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#26&和&&的区别)  

### [27、类的实例化顺序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#27类的实例化顺序)  

### [28、什么是多线程环境下的伪共享（false sharing）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#28什么是多线程环境下的伪共享false-sharing)  

### [29、模式的职责](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#29模式的职责)  

### [30、那些地方用到了单例模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#30那些地方用到了单例模式)  

### [31、线程 B 怎么知道线程 A 修改了变量](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#31线程-b-怎么知道线程-a-修改了变量)  

### [32、抽象类和接口的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#32抽象类和接口的区别)  

### [33、什么时候用断言（assert）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#33什么时候用断言assert)  

### [34、safepoint 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#34safepoint-是什么)  

### [35、什么是IoC和DI？DI是如何实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#35什么是ioc和didi是如何实现的)  

### [36、你所知道的web服务器有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#36你所知道的web服务器有哪些)  

### [37、如何自定义线程线程池?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#37如何自定义线程线程池)  

### [38、List接口有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#38list接口有什么特点)  

### [39、Java 中用到的线程调度算法是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#39java-中用到的线程调度算法是什么)  

### [40、我们可以在 hashcode() 中使用随机数字吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题汇总及答案（2021年Java面试题及答案大全）.md#40我们可以在-hashcode-中使用随机数字吗)  

### 41、对象在哪块内存分配？




