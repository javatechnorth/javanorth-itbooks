# Java高级面试题汇总及答案（2021年Java面试题及答案大全）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、JVM 出现 fullGC 很频繁，怎么去线上排查问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#1jvm-出现-fullgc-很频繁怎么去线上排查问题)  


**这题就依据full GC的触发条件来做：**

**1、** 如果有perm gen的话(jdk1.8就没了)，要给perm gen分配空间，但没有足够的空间时，会触发full gc。

**2、** 所以看看是不是perm gen区的值设置得太小了。

**3、** `System.gc()`方法的调用

**4、** 这个一般没人去调用吧~~~

**5、** 当统计得到的Minor GC晋升到旧生代的平均大小大于老年代的剩余空间，则会触发full gc(这就可以从多个角度上看了)

**6、** 是不是频繁创建了大对象(也有可能eden区设置过小)(大对象直接分配在老年代中，导致老年代空间不足--->从而频繁gc)

**7、** 是不是老年代的空间设置过小了(Minor GC几个对象就大于老年代的剩余空间了)


### [2、集合的特点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#2集合的特点)  


**集合的特点主要有如下两点：**

**1、** 集合用于存储对象的容器，对象是用来封装数据，对象多了也需要存储集中式管理。

**2、** 和数组对比对象的大小不确定。因为集合是可变长度的。数组需要提前定义大小


### [3、Java 中如何将字符串转换为整数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#3java-中如何将字符串转换为整数)  


String s="123";

int i;

第一种方法：i=Integer.parseInt(s);

第二种方法：i=Integer.valueOf(s).intValue();


### [4、什么是阻塞式方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#4什么是阻塞式方法)  


阻塞式方法是指程序会一直等待该方法完成期间不做其他事情，ServerSocket的accept()方法就是一直等待客户端连接。这里的阻塞是指调用结果返回之前，当前线程会被挂起，直到得到结果之后才会返回。此外，还有异步和非阻塞式方法在任务完成前就返回。


### [5、抽象类必须要有抽象方法吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#5抽象类必须要有抽象方法吗)  


示例代码：

```
abstract class Cat {
    public static void sayHi() {
    System.out.println("hi~");
    }
}
```

上面代码，抽象类并没有抽象方法但完全可以正常运行。


### [6、重载与重写](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#6重载与重写)  


**1、** Overload为重载，Override为重写方法的重写和重载是Java多态性的不同表现。重写是父类与子类之间多态性的一种表现，重载是一个类中多态性的一种表现。

**2、** 如果在子类中定义某方法与其父类有相同的名称和参数，我们说该方法被重写 (Override)。子类的对象使用这个方法时，将调用子类中的定义，对它而言，父类中的定义如同被"屏蔽"了。

**3、** 如果在一个类中定义了多个同名的方法，它们或有不同的参数个数或有不同的参数类型，则称为方法的重载(Overload)。

```
重载的方法是可以改变返回值的类型。
```


### [7、如何实现字符串的反转及替换？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#7如何实现字符串的反转及替换)  




方法很多，可以自己写实现也可以使用String或StringBuffer/StringBuilder中的方法。有一道很常见的面试题是用递归实现字符串反转，代码如下所示：

```
    public static String reverse(String originStr) {
        if(originStr == null || originStr.length() <= 1) 
            return originStr;
        return reverse(originStr.substring(1)) + originStr.charAt(0);
    }
```


### [8、32 位 JVM 和 64 位 JVM 的最大堆内存分别是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#832-位-jvm-和-64-位-jvm-的最大堆内存分别是多数)  


理论上说上 32 位的 JVM 堆内存可以到达 2^32，即 4GB，但实际上会比这个小很多。不同操作系统之间不同，如 Windows 系统大约 1.5GB，Solaris 大约3GB。64 位 JVM 允许指定最大的堆内存，理论上可以达到 2^64，这是一个非常大的数字，实际上你可以指定堆内存大小到 100GB。甚至有的 JVM，如 Azul，堆内存到 1000G 都是可能的。


### [9、List，Set，Map三者的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#9listsetmap三者的区别)  


![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/056/58/114_1.png#alt=114%5C_1.png)

Java 容器分为 Collection 和 Map 两大类，Collection集合的子接口有Set、List、Queue三种子接口。我们比较常用的是Set、List，Map接口不是collection的子接口。

**Collection集合主要有List和Set两大接口**

**1、** List：一个有序（元素存入集合的顺序和取出的顺序一致）容器，元素可以重复，可以插入多个null元素，元素都有索引。常用的实现类有 ArrayList、LinkedList 和 Vector。

**2、** Set：一个无序（存入和取出顺序有可能不一致）容器，不可以存储重复元素，只允许存入一个null元素，必须保证元素唯一性。Set 接口常用实现类是 HashSet、LinkedHashSet 以及 TreeSet。

**3、** Map是一个键值对集合，存储键、值和之间的映射。 Key无序，唯一；value 不要求有序，允许重复。Map没有继承于Collection接口，从Map集合中检索元素时，只要给出键对象，就会返回对应的值对象。

**4、** Map 的常用实现类：HashMap、TreeMap、HashTable、LinkedHashMap、ConcurrentHashMap


### [10、举例说明同步和异步。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#10举例说明同步和异步。)  




如果系统中存在临界资源（资源数量少于竞争资源的线程数量的资源），例如正在写的数据以后可能被另一个线程读到，或者正在读的数据可能已经被另一个线程写过了，那么这些数据就必须进行同步存取（数据库操作中的排他锁就是最好的例子）。当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效率。事实上，所谓的同步就是指阻塞式操作，而异步就是非阻塞式操作。


### [11、多线程的价值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#11多线程的价值)  

### [12、什么是阻塞式方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#12什么是阻塞式方法)  

### [13、面向对象的语言有那些特征？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#13面向对象的语言有那些特征)  

### [14、为什么我们调用start()方法时会执行run()方法，为什么我们不能直接调用run()方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#14为什么我们调用start方法时会执行run方法为什么我们不能直接调用run方法)  

### [15、复制算法（copying）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#15复制算法copying)  

### [16、迭代器 Iterator 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#16迭代器-iterator-是什么)  

### [17、线程的调度策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#17线程的调度策略)  

### [18、你如何确保main()方法所在的线程是Java 程序最后结束的线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#18你如何确保main方法所在的线程是java-程序最后结束的线程)  

### [19、什么是模板方法模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#19什么是模板方法模式)  

### [20、例如： if(a+1.0=4.0)，这样做好吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#20例如：-ifa+10=40这样做好吗)  

### [21、Java的双亲委托机制是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#21java的双亲委托机制是什么)  

### [22、构造方法能不能重写？能不能重载？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#22构造方法能不能重写能不能重载)  

### [23、Thow与thorws区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#23thow与thorws区别)  

### [24、用Java的套接字编程实现一个多线程的回显（echo）服务器。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#24用java的套接字编程实现一个多线程的回显echo服务器。)  

### [25、个线程和 2 个线程的同步代码，哪个更容易写？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#25个线程和-2-个线程的同步代码哪个更容易写)  

### [26、ThreadLocal是什么？有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#26threadlocal是什么有什么用)  

### [27、什么是ThreadPoolExecutor？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#27什么是threadpoolexecutor)  

### [28、简述正则表达式及其用途。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#28简述正则表达式及其用途。)  

### [29、什么是Callable和Future?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#29什么是callable和future)  

### [30、在Java中Executor和Executors的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#30在java中executor和executors的区别)  

### [31、java 面向对象编程三大特性------封装、继承、多态](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#31java-面向对象编程三大特性------封装继承多态)  

### [32、Int与integer的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#32int与integer的区别)  

### [33、列出 5 个应该遵循的 JDBC 最佳实践](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#33列出-5-个应该遵循的-jdbc-最佳实践)  

### [34、Thread 类中的 yield 方法有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#34thread-类中的-yield-方法有什么作用)  

### [35、谈谈JVM中，对类加载器的认识](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#35谈谈jvm中对类加载器的认识)  

### [36、为什么使用Executor框架比使用应用创建和管理线程好？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#36为什么使用executor框架比使用应用创建和管理线程好)  

### [37、什么叫线程安全？servlet是线程安全吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#37什么叫线程安全servlet是线程安全吗)  

### [38、notify() 和 notifyAll() 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#38notify-和-notifyall-有什么区别)  

### [39、字符型常量和字符串常量的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#39字符型常量和字符串常量的区别)  

### [40、被引用的对象就一定能存活吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java高级面试题汇总及答案（2021年Java面试题及答案大全）.md#40被引用的对象就一定能存活吗)  

### 41、插入数据时 ArrayList、LinkedList、Vector谁速度较快？




## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
