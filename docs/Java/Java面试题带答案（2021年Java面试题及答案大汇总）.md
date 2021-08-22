# Java面试题带答案（2021年Java面试题及答案大汇总）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、safepoint是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#1safepoint是什么)  


STW并不会只发生在内存回收的时候。现在程序员这么卷，碰到几次safepoint的问题几率也是比较大的。

当发生GC时，用户线程必须全部停下来，才可以进行垃圾回收，这个状态我们可以认为JVM是安全的（safe），整个堆的状态是稳定的。

如果在GC前，有线程迟迟进入不了safepoint，那么整个JVM都在等待这个阻塞的线程，造成了整体GC的时间变长。


### [2、垃圾回收器的基本原理是什么？垃圾回收器可以马上回收内存吗？有什么办法主动通知虚拟机进行垃圾回收？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#2垃圾回收器的基本原理是什么垃圾回收器可以马上回收内存吗有什么办法主动通知虚拟机进行垃圾回收)  


对于 GC 来说，当程序员创建对象时，GC 就开始监控这个对象的地址、大小以及使用情况。通常，GC 采用有向图的方式记录和管理堆（heap）中的所有对象。通过这种方式确定哪些对象是”可达的”，哪些对象是”不可达的”。当 GC 确定一些对象为“不可达”时，GC 就有责任回收这些内存空间。可以。程序员可以手动执行 System.gc()，通知 GC 运行，但是 Java 语言规范并不保证 GC 一定会执行。


### [3、运行时栈帧包含哪些结构？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#3运行时栈帧包含哪些结构)  


**1、** 局部变量表

**2、** 操作数栈

**3、** 动态连接

**4、** 返回地址

**5、** 附加信息


### [4、TreeMap和TreeSet在排序时如何比较元素？Collections工具类中的sort()方法如何比较元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#4treemap和treeset在排序时如何比较元素collections工具类中的sort方法如何比较元素)  




TreeSet要求存放的对象所属的类必须实现Comparable接口，该接口提供了比较元素的compareTo()方法，当插入元素时会回调该方法比较元素的大小。TreeMap要求存放的键值对映射的键必须实现Comparable接口从而根据键对元素进行排序。Collections工具类的sort方法有两种重载的形式，第一种要求传入的待排序容器中存放的对象比较实现Comparable接口以实现元素的比较；第二种不强制性的要求容器中的元素必须可比较，但是要求传入第二个参数，参数是Comparator接口的子类型（需要重写compare方法实现元素的比较），相当于一个临时定义的排序规则，其实就是通过接口注入比较元素大小的算法，也是对回调模式的应用（Java中对函数式编程的支持）。

例子1：

```

public class Student implements Comparable<Student> {
    private String name;        // 姓名
    private int age;            // 年龄

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Student [name=" + name + ", age=" + age + "]";
    }

    @Override
    public int compareTo(Student o) {
        return this.age - o.age; // 比较年龄(年龄的升序)
    }

}
```

```
import java.util.Set;
import java.util.TreeSet;

class Test01 {

    public static void main(String[] args) {
        Set<Student> set = new TreeSet<>();     // Java 7的钻石语法(构造器后面的尖括号中不需要写类型)
        set.add(new Student("Hao LUO", 33));
        set.add(new Student("XJ WANG", 32));
        set.add(new Student("Bruce LEE", 60));
        set.add(new Student("Bob YANG", 22));

        for(Student stu : set) {
            System.out.println(stu);
        }
//      输出结果: 
//      Student [name=Bob YANG, age=22]
//      Student [name=XJ WANG, age=32]
//      Student [name=Hao LUO, age=33]
//      Student [name=Bruce LEE, age=60]
    }
}
```

例子2：

```
public class Student {
    private String name;    // 姓名
    private int age;        // 年龄

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    /
     * 获取学生姓名
     */
    public String getName() {
        return name;
    }

    /
     * 获取学生年龄
     */
    public int getAge() {
        return age;
    }

    @Override
    public String toString() {
        return "Student [name=" + name + ", age=" + age + "]";
    }

}
```

```
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

class Test02 {

    public static void main(String[] args) {
        List<Student> list = new ArrayList<>();     // Java 7的钻石语法(构造器后面的尖括号中不需要写类型)
        list.add(new Student("Hao LUO", 33));
        list.add(new Student("XJ WANG", 32));
        list.add(new Student("Bruce LEE", 60));
        list.add(new Student("Bob YANG", 22));

        // 通过sort方法的第二个参数传入一个Comparator接口对象
        // 相当于是传入一个比较对象大小的算法到sort方法中
        // 由于Java中没有函数指针、仿函数、委托这样的概念
        // 因此要将一个算法传入一个方法中唯一的选择就是通过接口回调
        Collections.sort(list, new Comparator<Student> () {

            @Override
            public int compare(Student o1, Student o2) {
                return o1.getName().compareTo(o2.getName());    // 比较学生姓名
            }
        });

        for(Student stu : list) {
            System.out.println(stu);
        }
//      输出结果: 
//      Student [name=Bob YANG, age=22]
//      Student [name=Bruce LEE, age=60]
//      Student [name=Hao LUO, age=33]
//      Student [name=XJ WANG, age=32]
    }
}
```


### [5、访问修饰符public,private,protected,以及不写（默认）时的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#5访问修饰符public,private,protected,以及不写默认时的区别)  




| 修饰符 | 当前类 | 同 包 | 子 类 | 其他包 |
| :---: | :---: | :---: | :---: | :---: |
| public | √ | √ | √ | √ |
| protected | √ | √ | √ | × |
| default | √ | √ | × | × |
| private | √ | × | × | × |


类的成员不写访问修饰时默认为default。默认对于同一个包中的其他类相当于公开（public），对于不是同一个包中的其他类相当于私有（private）。受保护（protected）对子类相当于公开，对不是同一包中的没有父子关系的类相当于私有。Java中，外部类的修饰符只能是public或默认，类的成员（包括内部类）的修饰符可以是以上四种。


### [6、如何在两个线程间共享数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#6如何在两个线程间共享数据)  


**在两个线程间共享变量即可实现共享**

一般来说，共享变量要求变量本身是线程安全的，然后在线程内使用的时候，如果有对共享变量的复合操作，那么也得保证复合操作的线程安全性


### [7、类ExampleA继承Exception，类ExampleB继承ExampleA。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#7类examplea继承exception类exampleb继承examplea。)  


有如下代码片断：

```
try {
    throw new ExampleB("b")
} catch（ExampleA e）{
    System.out.println("ExampleA");
} catch（Exception e）{
    System.out.println("Exception");
}
```

请问执行此段代码的输出是什么？



输出：ExampleA。（根据里氏代换原则[能使用父类型的地方一定能使用子类型]，抓取ExampleA类型异常的catch块能够抓住try块中抛出的ExampleB类型的异常）

> 面试题 - 说出下面代码的运行结果。（此题的出处是《Java编程思想》一书）


```
class Annoyance extends Exception {}
class Sneeze extends Annoyance {}

class Human {

    public static void main(String[] args) 
        throws Exception {
        try {
            try {
                throw new Sneeze();
            } 
            catch ( Annoyance a ) {
                System.out.println("Caught Annoyance");
                throw a;
            }
        } 
        catch ( Sneeze s ) {
            System.out.println("Caught Sneeze");
            return ;
        }
        finally {
            System.out.println("Hello World!");
        }
    }
}
```


### [8、构造方法有哪些特性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#8构造方法有哪些特性)  


**1、** 名字与类名相同；

**2、** 没有返回值，但不能用void声明构造函数；

**3、** 生成类的对象时自动执行，无需调用。


### [9、如何在两个线程间共享数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#9如何在两个线程间共享数据)  


在两个线程间共享变量即可实现共享。

一般来说，共享变量要求变量本身是线程安全的，然后在线程内使用的时候，如果有对共享变量的复合操作，那么也得保证复合操作的线程安全性。


### [10、调优工具](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#10调优工具)  


常用调优工具分为两类,jdk自带监控工具：jconsole和jvisualvm，第三方有：MAT(Memory AnalyzerTool)、GChisto。

**1、** jconsole，Java Monitoring and Management Console是从java5开始，在JDK中自带的java监控和管理控制台，用于对JVM中内存，线程和类等的监控

**2、** jvisualvm，jdk自带全能工具，可以分析内存快照、线程快照；监控内存变化、GC变化等。

**3、** MAT，Memory Analyzer Tool，一个基于Eclipse的内存分析工具，是一个快速、功能丰富的Javaheap分析工具，它可以帮助我们查找内存泄漏和减少内存消耗

**4、** GChisto，一款专业分析gc日志的工具


### [11、说出至少 5 点在 Java 中使用线程的最佳实践。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#11说出至少-5-点在-java-中使用线程的最佳实践。)  

### [12、什么是DAO模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#12什么是dao模式)  

### [13、short s1 = 1; s1 = s1 + 1;有错吗?short s1 = 1; s1 += 1;有错吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#13short-s1-=-1;-s1-=-s1-+-1;有错吗short-s1-=-1;-s1-+=-1;有错吗)  

### [14、什么是JVM？java虚拟机包括什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#14什么是jvmjava虚拟机包括什么)  

### [15、什么是阻塞队列？阻塞队列的实现原理是什么？如何使用阻塞队列来实现生产者-消费者模型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#15什么是阻塞队列阻塞队列的实现原理是什么如何使用阻塞队列来实现生产者-消费者模型)  

### [16、简述一下面向对象的”六原则一法则”。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#16简述一下面向对象的六原则一法则。)  

### [17、什么是逃逸分析？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#17什么是逃逸分析)  

### [18、Array 和 ArrayList 有何区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#18array-和-arraylist-有何区别)  

### [19、为什么 Thread 类的 sleep()和 yield ()方法是静态的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#19为什么-thread-类的-sleep和-yield-方法是静态的)  

### [20、Minor Gc和Full GC 有什么不同呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#20minor-gc和full-gc-有什么不同呢)  

### [21、集合和数组的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#21集合和数组的区别)  

### [22、你知道哪些GC类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#22你知道哪些gc类型)  

### [23、synchronized和ReentrantLock的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#23synchronized和reentrantlock的区别)  

### [24、a = a + b 与 a += b 的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#24a-=-a-+-b-与-a-+=-b-的区别)  

### [25、List、Set、Map是否继承自Collection接口？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#25listsetmap是否继承自collection接口)  

### [26、对象的访问方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#26对象的访问方式有哪些)  

### [27、JVM 的内存模型以及分区情况和作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#27jvm-的内存模型以及分区情况和作用)  

### [28、什么是多线程中的上下文切换？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#28什么是多线程中的上下文切换)  

### [29、Java 中垃圾收集的方法有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#29java-中垃圾收集的方法有哪些)  

### [30、什么时候使用模板方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#30什么时候使用模板方法)  

### [31、String和StringBuilder、StringBuffer的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#31string和stringbuilderstringbuffer的区别)  

### [32、如果你提交任务时，线程池队列已满，这时会发生什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#32如果你提交任务时线程池队列已满这时会发生什么)  

### [33、线程类的构造方法、静态块是被哪个线程调用的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#33线程类的构造方法静态块是被哪个线程调用的)  

### [34、什么是原子操作？在Java Concurrency API中有哪些原子类(atomic classes)？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#34什么是原子操作在java-concurrency-api中有哪些原子类atomic-classes)  

### [35、接口是否可继承（extends）接口？抽象类是否可实现（implements）接口？抽象类是否可继承具体类（concrete class）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#35接口是否可继承extends接口抽象类是否可实现implements接口抽象类是否可继承具体类concrete-class)  

### [36、什么是工厂模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#36什么是工厂模式)  

### [37、CMS都有哪些问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#37cms都有哪些问题)  

### [38、是否可以继承String类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#38是否可以继承string类)  

### [39、什么是ThreadLocal变量？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#39什么是threadlocal变量)  

### [40、常用的并发工具类有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题带答案（2021年Java面试题及答案大汇总）.md#40常用的并发工具类有哪些)  

### 41、可以描述一下 class 文件的结构吗？




## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
