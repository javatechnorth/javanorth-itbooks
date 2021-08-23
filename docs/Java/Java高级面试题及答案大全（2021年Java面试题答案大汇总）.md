# Java高级面试题及答案大全（2021年Java面试题答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、重定向和请求转发的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#1重定向和请求转发的区别)  


请求转发只能将请求转发给同一个Web应用中的其他资源，而重定向不仅可以定向到当前应用程序中的其他资源，也可以重定向到其他站点上的资源。

重定向结束后，浏览器地址栏显示URL会发生改变，由初始的URL地址变成重定向的目标URL。而请求转发过程结束后，浏览器地址栏保持初始的URL地址不变。

请求转发的发起者和接受者之间共享相同的HttpServletRequest实例和HttpServletResponse实例，而重定向的发起者和接受者使用各自的HttpServletRequest实例和HttpServletResponse实例。

转发是一次请求，重定向是二次请求。转发是在服务器进行的，重定向在客服端进行的。


### [2、为什么 Java 中的 String 是不可变的（Immutable）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#2为什么-java-中的-string-是不可变的immutable)  


Java 中的 String 不可变是因为 Java 的设计者认为字符串使用非常频繁，将字符串设置为不可变可以允许多个客户端之间共享相同的字符串。

**29、** 我们能在 Switch 中使用 String 吗？

从 Java 7 开始，我们可以在 switch case 中使用字符串，但这仅仅是一个语法糖。内部实现在 switch 中使用字符串的 hash code。

**30、** Java 中的构造器链是什么？

当你从一个构造器中调用另一个构造器，就是Java 中的构造器链。这种情况只在重载了类的构造器的时候才会出现。


### [3、什么是模板方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#3什么是模板方法)  


模板方法模式：定义一个操作中的算法骨架（父类），而将一些步骤延迟到子类中。 模板方法使得子类可以不改变一个算法的结构来重定义该算法的


### [4、JRE、JDK、JVM 及 JIT 之间有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#4jrejdkjvm-及-jit-之间有什么不同)  


JRE 代表 Java 运行时（Java run-time），是运行 Java 引用所必须的。JDK 代表 Java 开发工具（Java development kit），是 Java 程序的开发工具，如 Java 编译器，它也包含 JRE。JVM 代表 Java 虚拟机（Java virtual machine），它的责任是运行 Java 应用。JIT 代表即时编译（Just In Time compilation），当代码执行的次数超过一定的阈值时，会将 Java 字节码转换为本地代码，如，主要的热点代码会被准换为本地代码，这样有利大幅度提高 Java 应用的性能。


### [5、什么是外观模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#5什么是外观模式)  


**外观模式：**

也叫门面模式，隐藏系统的复杂性，并向客户端提供了一个客户端可以访问系统的接口。

它向现有的系统添加一个接口，用这一个接口来隐藏实际的系统的复杂性。

使用外观模式，他外部看起来就是一个接口，其实他的内部有很多复杂的接口已经被实现

- 代码演示

用户注册完之后，需要调用阿里短信接口、邮件接口、微信推送接口。

**1、** 创建阿里短信接口

```
package com.lijie;

//阿里短信消息
public interface AliSmsService {
    void sendSms();
}
```

```
package com.lijie;

public class AliSmsServiceImpl implements AliSmsService {

    public void sendSms() {
        System.out.println("阿里短信消息");
    }

}
```

**2、** 创建邮件接口

```
package com.lijie;

//发送邮件消息
public interface EamilSmsService {
    void sendSms();
}
```

```
package com.lijie;

public class EamilSmsServiceImpl implements   EamilSmsService{
    public void sendSms() {
        System.out.println("发送邮件消息");
    }
}
```

**3、** 创建微信推送接口

```
package com.lijie;

//微信消息推送
public interface WeiXinSmsService {
   void sendSms();
}
```

```
package com.lijie;

public class WeiXinSmsServiceImpl implements  WeiXinSmsService {
    public void sendSms() {
        System.out.println("发送微信消息推送");
    }
}
```

**4、** 创建门面（门面看起来很简单使用，复杂的东西以及被门面给封装好了）

```
package com.lijie;

public class Computer {
    AliSmsService aliSmsService;
    EamilSmsService eamilSmsService;
    WeiXinSmsService weiXinSmsService;

    public Computer() {
        aliSmsService = new AliSmsServiceImpl();
        eamilSmsService = new EamilSmsServiceImpl();
        weiXinSmsService = new WeiXinSmsServiceImpl();
    }

    //只需要调用它
    public void sendMsg() {
        aliSmsService.sendSms();
        eamilSmsService.sendSms();
        weiXinSmsService.sendSms();
    }
}
```

**5、** 启动测试

```
package com.lijie;

public class Client {

    public static void main(String[] args) {
        //普通模式需要这样
        AliSmsService aliSmsService = new AliSmsServiceImpl();
        EamilSmsService eamilSmsService = new EamilSmsServiceImpl();
        WeiXinSmsService weiXinSmsService = new WeiXinSmsServiceImpl();
        aliSmsService.sendSms();
        eamilSmsService.sendSms();
        weiXinSmsService.sendSms();

        //利用外观模式简化方法
        new Computer().sendMsg();
    }
}
```


### [6、如果父类只有有参构造方法，那么子类必须要重写父类的构造方法吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#6如果父类只有有参构造方法那么子类必须要重写父类的构造方法吗)  


必须重写


### [7、重排序遵守的规则](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#7重排序遵守的规则)  


**as-if-serial：**

**1、** 不管怎么排序，结果不能改变

**2、** 不存在数据依赖的可以被编译器和处理器重排序

**3、** 一个操作依赖两个操作，这两个操作如果不存在依赖可以重排序

**4、** 单线程根据此规则不会有问题，但是重排序后多线程会有问题


### [8、url是什么？由哪些部分组成？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#8url是什么由哪些部分组成)  


统一资源定位符

http://localhost:8080/myWeb/index.html：协议+主机地址+端口+项目名称+资源名称


### [9、什么是线程同步和线程互斥，有哪几种实现方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#9什么是线程同步和线程互斥有哪几种实现方式)  


**1、** 当一个线程对共享的数据进行操作时，应使之成为一个”原子操作“，即在没有完成相关操作之前，不允许其他线程打断它，否则，就会破坏数据的完整性，必然会得到错误的处理结果，这就是线程的同步。

**2、** 在多线程应用中，考虑不同线程之间的数据同步和防止死锁。当两个或多个线程之间同时等待对方释放资源的时候就会形成线程之间的死锁。为了防止死锁的发生，需要通过同步来实现线程安全。

**3、** 线程互斥是指对于共享的进程系统资源，在各单个线程访问时的排它性。当有若干个线程都要使用某一共享资源时，任何时刻最多只允许一个线程去使用，其它要使用该资源的线程必须等待，直到占用资源者释放该资源。线程互斥可以看成是一种特殊的线程同步。

**4、** 线程间的同步方法大体可分为两类：用户模式和内核模式。顾名思义，内核模式就是指利用系统内核对象的单一性来进行同步，使用时需要切换内核态与用户态，而用户模式就是不需要切换到内核态，只在用户态完成操作。

**5、** 用户模式下的方法有：

原子操作（例如一个单一的全局变量），临界区。内核模式下的方法有：事件，信号量，互斥量。

**实现线程同步的方法**

**1、** 同步代码方法：sychronized 关键字修饰的方法

**2、** 同步代码块：sychronized 关键字修饰的代码块

**3、** 使用特殊变量域volatile实现线程同步：volatile关键字为域变量的访问提供了一种免锁机制

**4、** 使用重入锁实现线程同步：reentrantlock类是可冲入、互斥、实现了lock接口的锁他与sychronized方法具有相同的基本行为和语义


### [10、什么是线程死锁](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#10什么是线程死锁)  


**1、** 死锁是指两个或两个以上的进程（线程）在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞的现象，若无外力作用，它们都将无法推进下去。此时称系统处于死锁状态或系统产生了死锁，这些永远在互相等待的进程（线程）称为死锁进程（线程）。

**2、** 多个线程同时被阻塞，它们中的一个或者全部都在等待某个资源被释放。由于线程被无限期地阻塞，因此程序不可能正常终止。

**3、** 如下图所示，线程 A 持有资源 2，线程 B 持有资源 1，他们同时都想申请对方的资源，所以这两个线程就会互相等待而进入死锁状态。

![87_1.png][87_1.png]


### [11、你做过 JVM 调优，说说如何查看 JVM 参数默认值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#11你做过-jvm-调优说说如何查看-jvm-参数默认值)  

### [12、CopyOnWriteArrayList 的设计思想?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#12copyonwritearraylist-的设计思想)  

### [13、常用JVM基本配置参数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#13常用jvm基本配置参数)  

### [14、写一段代码在遍历 ArrayList 时移除一个元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#14写一段代码在遍历-arraylist-时移除一个元素)  

### [15、说说 JVM 如何执行 class 中的字节码。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#15说说-jvm-如何执行-class-中的字节码。)  

### [16、Parallel Scavenge 收集器（多线程复制算法、高效）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#16parallel-scavenge-收集器多线程复制算法高效)  

### [17、JVM的引用类型有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#17jvm的引用类型有哪些)  

### [18、构造方法能不能重载？能不能重写？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#18构造方法能不能重载能不能重写)  

### [19、char 型变量中能不能存贮一个中文汉字，为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#19char-型变量中能不能存贮一个中文汉字为什么)  

### [20、简单描述一下（分代）垃圾回收的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#20简单描述一下分代垃圾回收的过程)  

### [21、单例模式的线程安全性](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#21单例模式的线程安全性)  

### [22、单例优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#22单例优缺点)  

### [23、怎么在JDBC内调用一个存储过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#23怎么在jdbc内调用一个存储过程)  

### [24、在异常捕捉时，如果发生异常，那么try.catch.finally块外的return语句会执行吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#24在异常捕捉时如果发生异常那么trycatchfinally块外的return语句会执行吗)  

### [25、如果使用Object作为HashMap的Key，应该怎么办呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#25如果使用object作为hashmap的key应该怎么办呢)  

### [26、工厂模式好处](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#26工厂模式好处)  

### [27、Iterator 和 ListIterator 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#27iterator-和-listiterator-有什么区别)  

### [28、程序计数器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#28程序计数器)  

### [29、多线程的好处](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#29多线程的好处)  

### [30、什么是多线程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#30什么是多线程)  

### [31、invokedynamic指令是干什么的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#31invokedynamic指令是干什么的)  

### [32、Java 中会存在内存泄漏吗，请简单描述。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#32java-中会存在内存泄漏吗请简单描述。)  

### [33、请解释Tomcat中使用的连接器是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#33请解释tomcat中使用的连接器是什么)  

### [34、你在项目中哪些地方用到了XML？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#34你在项目中哪些地方用到了xml)  

### [35、在java中wait和sleep方法的不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#35在java中wait和sleep方法的不同)  

### [36、Java中有几种数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#36java中有几种数据类型)  

### [37、谈谈对 OOM 的认识](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#37谈谈对-oom-的认识)  

### [38、什么是Hash算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#38什么是hash算法)  

### [39、Iterator 怎么使用？有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#39iterator-怎么使用有什么特点)  

### [40、什么是线程组，为什么在Java中不推荐使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题及答案大全（2021年Java面试题答案大汇总）.md#40什么是线程组为什么在java中不推荐使用)  





