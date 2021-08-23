# Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）

Jvm面试题及答案【最新版】Jvm高级面试题大全(2021版)，发现网上很多Jvm面试题及答案整理都没有答案，所以花了很长时间搜集，本套Jvm面试题大全，Jvm面试题大汇总，有大量经典的Jvm面试题以及答案，包含Jvm语言常见面试题、Jvm工程师高级面试题及一些大厂Jvm开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Jvm面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Jvm面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、你能保证 GC 执行吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#1你能保证-gc-执行吗)  


不能，虽然你可以调用 System.gc() 或者 Runtime.gc()，但是没有办法保证 GC的执行。


### [2、动态改变构造](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#2动态改变构造)  


OSGi 服务平台提供在多种网络设备上无需重启的动态改变构造的功能。为了最小化耦合度和促使这些耦合度可管理， OSGi 技术提供一种面向服务的架构，它能使这些组件动态地发现对方。


### [3、JRE、JDK、JVM 及 JIT 之间有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#3jrejdkjvm-及-jit-之间有什么不同)  


JRE 代表 Java 运行时（Java run-time），是运行 Java 引用所必须的。JDK 代表 Java 开发工具（Java development kit），是 Java 程序打开发工具，如 Java编译器，它也包含 JRE。JVM 代表 Java 虚拟机（Java virtual machine），它的责任是运行 Java 应用。JIT 代表即时编译（Just In Time compilation），当代码执行的次数超过一定的阈值时，会将 Java 字节码转换为本地代码，如，主要的热点代码会被准换为本地代码，这样有利大幅度提高 Java 应用的性能。


### [4、说说类加载的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#4说说类加载的过程)  


加载 验证 准备（为一些类变量分配内存，并将其初始化为默认值） 解析（将符号引用替换为直接引用。类和接口、类方法、接口方法、字段等解析） 初始化


### [5、CMS 收集器（多线程标记清除算法）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#5cms-收集器多线程标记清除算法)  


Concurrent mark sweep(CMS)收集器是一种年老代垃圾收集器，其最主要目标是获取最短垃圾回收停顿时间， 和其他年老代使用标记-整理算法不同，它使用多线程的标记-清除算法。最短的垃圾收集停顿时间可以为交互比较高的程序提高用户体验。CMS 工作机制相比其他的垃圾收集器来说更复杂。整个过程分为以下 4 个阶段：

**初始标记**

只是标记一下 GC Roots 能直接关联的对象，速度很快，仍然需要暂停所有的工作线程。

**并发标记**

进行 GC Roots 跟踪的过程，和用户线程一起工作，不需要暂停工作线程。

**重新标记**

为了修正在并发标记期间，因用户程序继续运行而导致标记产生变动的那一部分对象的标记记录，仍然需要暂停所有的工作线程。

**并发清除**

清除 GC Roots 不可达对象，和用户线程一起工作，不需要暂停工作线程。由于耗时最长的并发标记和并发清除过程中，垃圾收集线程可以和用户现在一起并发工作， 所以总体上来看CMS 收集器的内存回收和用户线程是一起并发地执行。


### [6、讲讲什么情况下会出现内存溢出，内存泄漏？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#6讲讲什么情况下会出现内存溢出内存泄漏)  


内存泄漏的原因很简单：

**1、** 对象是可达的(一直被引用)

**2、** 但是对象不会被使用

常见的内存泄漏例子：

```
    public static void main(String[] args) {
        Set<Object> set = new HashSet<>();

        for (int i = 0; i < 10; i++) {
            Object object = new Object();
            set.add(object);

            // 设置为空，该对象不再使用
            object = null;
        }

        // 但是set集合中还维护object的引用，gc不会回收object对象
        System.out.println(set);
        System.out.println(set.size());
    }
}
```

输出结果

```
[java.lang.Object@74a14482, 
java.lang.Object@677327b6, 
java.lang.Object@6d6f6e28, 
java.lang.Object@4554617c, 
java.lang.Object@45ee12a7, 
java.lang.Object@1b6d3586, 
java.lang.Object@7f31245a,
java.lang.Object@135fbaa4,
java.lang.Object@1540e19d, 
java.lang.Object@14ae5a5]
10

Process finished with exit code 0
```

解决这个内存泄漏问题也很简单，将set设置为null，那就可以避免上述内存泄漏问题了。其他内存泄漏得一步一步分析了。

**内存溢出的原因：**

**1、** 内存泄露导致堆栈内存不断增大，从而引发内存溢出。

**2、** 大量的jar，class文件加载，装载类的空间不够，溢出

**3、** 操作大量的对象导致堆内存空间已经用满了，溢出

**4、** nio直接操作内存，内存过大导致溢出

**解决：**

**1、** 查看程序是否存在内存泄漏的问题

**2、** 设置参数加大空间

**3、** 代码中是否存在死循环或循环产生过多重复的对象实体、

**4、** 查看是否使用了nio直接操作内存。


### [7、说下有哪些类加载器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#7说下有哪些类加载器)  


Bootstrap ClassLoader（启动类加载器） Extention ClassLoader（扩展类加载器） App ClassLoader（应用类加载器）


### [8、说一下垃圾分代收集的过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#8说一下垃圾分代收集的过程)  


分为新生代和老年代，新生代默认占总空间的 1/3，老年代默认占 2/3。

新生代使用复制算法，有 3 个分区：Eden、To Survivor、From Survivor，它们的默认占比是 8:1:1。

当新生代中的 Eden 区内存不足时，就会触发 Minor GC，过程如下：

**1、** 在 Eden 区执行了第一次 GC 之后，存活的对象会被移动到其中一个 Survivor 分区；

**2、** Eden 区再次 GC，这时会采用复制算法，将 Eden 和 from 区一起清理，存活的对象会被复制到 to 区；

**3、** 移动一次，对象年龄加 1，对象年龄大于一定阀值会直接移动到老年代

**4、** Survivor 区相同年龄所有对象大小的总和 (Survivor 区内存大小 * 这个目标使用率)时，大于或等于该年龄的对象直接进入老年代。其中这个使用率通过 -XX:TargetSurvivorRatio 指定，默认为 50%

**5、** Survivor 区内存不足会发生担保分配

**6、** 超过指定大小的对象可以直接进入老年代

Major GC，指的是老年代的垃圾清理，但并未找到明确说明何时在进行Major GC

FullGC，整个堆的垃圾收集，触发条件：

**1、** 每次晋升到老年代的对象平均大小>老年代剩余空间

**2、** MinorGC后存活的对象超过了老年代剩余空间

**3、** 元空间不足

**4、** System.gc() 可能会引起

**5、** CMS GC异常，promotion failed:MinorGC时，survivor空间放不下，对象只能放入老年代，而老年代也放不下造成；concurrent mode failure:GC时，同时有对象要放入老年代，而老年代空间不足造成

**6、** 堆内存分配很大的对象


### [9、描述一下什么情况下，对象会从年轻代进入老年代](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#9描述一下什么情况下对象会从年轻代进入老年代)  


**1、** 对象的年龄超过一定阀值，-XX:MaxTenuringThreshold 可以指定该阀值

**2、** 动态对象年龄判定，有的垃圾回收算法，比如 G1，并不要求 age 必须达到 15 才能晋升到老年代，它会使用一些动态的计算方法

**3、** 大小超出某个阀值的对象将直接在老年代上分配，值默认为 0，意思是全部首选 Eden 区进行分配，-XX:PretenureSizeThreshold 可以指定该阀值，部分收集器不支持

**4、** 分配担保，当 Survivor 空间不够的时候，则需要依赖其他内存（指老年代）进行分配担保，这个时候，对象也会直接在老年代上分配


### [10、类加载有几个过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#10类加载有几个过程)  


加载、验证、准备、解析、初始化。


### [11、safepoint是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#11safepoint是什么)  

### [12、什么是方法内联？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#12什么是方法内联)  

### [13、有哪些打破了双亲委托机制的案例？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#13有哪些打破了双亲委托机制的案例)  

### [14、java中会存在内存泄漏吗，请简单描述。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#14java中会存在内存泄漏吗请简单描述。)  

### [15、有哪些 GC 算法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#15有哪些-gc-算法)  

### [16、如何判断一个类是无用的类?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#16如何判断一个类是无用的类)  

### [17、怎么获取 Java 程序使用的内存？堆使用的百分比？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#17怎么获取-java-程序使用的内存堆使用的百分比)  

### [18、JVM 中一次完整的 GC 流程（从 ygc 到 fgc）是怎样的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#18jvm-中一次完整的-gc-流程从-ygc-到-fgc是怎样的)  

### [19、32 位 JVM 和 64 位 JVM 的最大堆内存分别是多数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#1932-位-jvm-和-64-位-jvm-的最大堆内存分别是多数)  

### [20、Java 内存分配](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#20java-内存分配)  

### [21、GC 垃圾收集器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#21gc-垃圾收集器)  

### [22、双亲委派](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#22双亲委派)  

### [23、如何写一段简单的死锁代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#23如何写一段简单的死锁代码)  

### [24、什么时候会造成堆外内存溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#24什么时候会造成堆外内存溢出)  

### [25、调优工具](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#25调优工具)  

### [26、什么是本地方法栈](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#26什么是本地方法栈)  

### [27、JIT 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#27jit-是什么)  

### [28、你做过 JVM 调优，说说如何查看 JVM 参数默认值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#28你做过-jvm-调优说说如何查看-jvm-参数默认值)  

### [29、JVM 的内存模型以及分区情况和作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#29jvm-的内存模型以及分区情况和作用)  

### [30、什么是happen-before原则？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#30什么是happen-before原则)  

### [31、如何判断对象是否是垃圾？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Jvm/Jvm面试题汇总及答案（2021年Jvm面试题及答案大全）.md#31如何判断对象是否是垃圾)  





