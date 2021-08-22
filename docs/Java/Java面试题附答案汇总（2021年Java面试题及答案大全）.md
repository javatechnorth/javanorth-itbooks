# Java面试题附答案汇总（2021年Java面试题及答案大全）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何测试静态方法？()](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#1如何测试静态方法)  


可以使用 PowerMock 库来测试静态方法。


### [2、Error和Exception有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#2error和exception有什么区别)  




Error表示系统级的错误和程序不必处理的异常，是恢复不是不可能但很困难的情况下的一种严重问题；比如内存溢出，不可能指望程序能处理这样的情况；Exception表示需要捕捉或者需要程序进行处理的异常，是一种设计或实现问题；也就是说，它表示如果程序运行正常，从不会发生的情况。

> 面试题：2005年摩托罗拉的面试中曾经问过这么一个问题“If a process reports a stack overflow run-time error, what’s the most possible cause?”，给了四个选项a、lack of memory; b、write on an invalid memory space; c、recursive function calling; d、array index out of boundary、Java程序在运行时也可能会遭遇StackOverflowError，这是一个无法恢复的错误，只能重新修改代码了，这个面试题的答案是c。如果写了不能迅速收敛的递归，则很有可能引发栈溢出的错误，如下所示：


```
class StackOverflowErrorTest {

    public static void main(String[] args) {
        main(null);
    }
}
```

> 提示：用递归编写程序时一定要牢记两点：1、递归公式；2、收敛条件（什么时候就不再继续递归）。



### [3、你是如何调用 wait（）方法的？使用 if 块还是循环？为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#3你是如何调用-wait方法的使用-if-块还是循环为什么)  


wait() 方法应该在循环调用，因为当线程获取到 CPU 开始执行的时候，其他条件可能还没有满足，所以在处理前，循环检测条件是否满足会更好。下面是一段标准的使用 wait 和 notify 方法的代码：

```java
// The standard idiom for using the wait method
synchronized (obj) {
        while (condition does not hold)
        obj.wait(); // (Releases lock, and reacquires on wakeup)
        ..、// Perform action appropriate to condition
        }
```

参见 [Effective Java]第 69 条，获取更多关于为什么应该在循环中来调用 wait 方法的内容。


### [4、为什么wait()方法和notify()/notifyAll()方法要在同步块中被调用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#4为什么wait方法和notify/notifyall方法要在同步块中被调用)  


这是JDK强制的，wait()方法和notify()/notifyAll()方法在调用前都必须先获得对象的锁


### [5、Java 中，throw 和 throws 有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#5java-中throw-和-throws-有什么区别)  


throw 用于抛出 java.lang.Throwable 类的一个实例化对象，意思是说你可以通过关键字 throw 抛出一个 Error 或者 一个Exception，如：

throw new IllegalArgumentException(“size must be multiple of 2″)

而throws 的作用是作为方法声明和签名的一部分，方法被抛出相应的异常以便调用者能处理。Java 中，任何未处理的受检查异常强制在 throws 子句中声明。


### [6、哪个类包含 clone 方法？是 Cloneable 还是 Object？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#6哪个类包含-clone-方法是-cloneable-还是-object)  


java.lang.Cloneable 是一个标示性接口，不包含任何方法，clone 方法在 object 类中定义。并且需要知道 clone() 方法是一个本地方法，这意味着它是由 c 或 c++ 或 其他本地语言实现的。


### [7、什么情况会造成元空间溢出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#7什么情况会造成元空间溢出)  


元空间（Metaspace）默认是没有上限的，不加限制比较危险。当应用中的Java类过多，比如Spring等一些使用动态代理的框架生成了很多类，如果占用空间超出了`我们的设定值`，就会发生元空间溢出。

所以，默认风险大，但如果你不给足它空间，它也会溢出。


### [8、多线程的劣势：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#8多线程的劣势：)  


**线程也是程序，所以线程需要占用内存，线程越多占用内存也越多；

多线程需要协调和管理，所以需要 CPU 时间跟踪线程；

线程之间对共享资源的访问会相互影响，必须解决竞用共享资源的问题。**


### [9、“a==b”和”a.equals(b)”有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#9“ab和aequalsb有什么区别)  


如果 a 和 b 都是对象，则 a==b 是比较两个对象的引用，只有当 a 和 b 指向的是堆中的同一个对象才会返回 true，而 a.equals(b) 是进行逻辑比较，所以通常需要重写该方法来提供逻辑一致性的比较。例如，String 类重写 equals() 方法，所以可以用于两个不同对象，但是包含的字母相同的比较。


### [10、final、finalize()、finally，作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#10finalfinalizefinally作用)  


**1、** final为用于标识常量的关键字，final标识的关键字存储在常量池中（在这里final常量的具体用法将在下面进行介绍）；

**2、** finalize()方法在Object中进行了定义，用于在对象“消失”时，由JVM进行调用用于对对象进行垃圾回收，类似于C++中的析构函数；用户自定义时，用于释放对象占用的资源（比如进行I/0操作）；

**3、** finally{}用于标识代码块，与try{}进行配合，不论try中的代码执行完或没有执行完（这里指有异常），该代码块之中的程序必定会进行；


### [11、适配器模式和装饰器模式有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#11适配器模式和装饰器模式有什么区别)  

### [12、如何选择单例创建方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#12如何选择单例创建方式)  

### [13、适配器模式是什么？什么时候使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#13适配器模式是什么什么时候使用)  

### [14、什么是AQS](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#14什么是aqs)  

### [15、redux与mobx的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#15redux与mobx的区别)  

### [16、Java中的ReadWriteLock是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#16java中的readwritelock是什么)  

### [17、工厂模式分类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#17工厂模式分类)  

### [18、Java会存在内存泄漏吗？请简单描述。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#18java会存在内存泄漏吗请简单描述。)  

### [19、类加载器双亲委派模型机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#19类加载器双亲委派模型机制)  

### [20、Java对象的布局了解过吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#20java对象的布局了解过吗)  

### [21、Java 中，抽象类与接口之间有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#21java-中抽象类与接口之间有什么不同)  

### [22、Java 中的 TreeMap 是采用什么树实现的？(答案)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#22java-中的-treemap-是采用什么树实现的答案)  

### [23、Java 中 ConcurrentHashMap 的并发度是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#23java-中-concurrenthashmap-的并发度是什么)  

### [24、Array与ArrayList有什么不一样？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#24array与arraylist有什么不一样)  

### [25、什么是 Busy spin？我们为什么要使用它？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#25什么是-busy-spin我们为什么要使用它)  

### [26、如何实现对象克隆？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#26如何实现对象克隆)  

### [27、普通类和抽象类有哪些区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#27普通类和抽象类有哪些区别)  

### [28、你是如何理解fiber的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#28你是如何理解fiber的)  

### [29、你能保证 GC 执行吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#29你能保证-gc-执行吗)  

### [30、分代收集算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#30分代收集算法)  

### [31、什么是线程池（thread pool）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#31什么是线程池thread-pool)  

### [32、虚拟DOM的优劣如何?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#32虚拟dom的优劣如何)  

### [33、什么是接口？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#33什么是接口)  

### [34、说出几点 Java 中使用 Collections 的最佳实践](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#34说出几点-java-中使用-collections-的最佳实践)  

### [35、如何用Java代码列出一个目录下所有的文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#35如何用java代码列出一个目录下所有的文件)  

### [36、如何实现 Array 和 List 之间的转换？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#36如何实现-array-和-list-之间的转换)  

### [37、一个java类中包含那些内容？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#37一个java类中包含那些内容)  

### [38、React如何进行组件/逻辑复用?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#38react如何进行组件/逻辑复用)  

### [39、Statement与preparedStatement区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#39statement与preparedstatement区别)  

### [40、有没有可能两个不相等的对象有有相同的 hashcode？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java面试题附答案汇总（2021年Java面试题及答案大全）.md#40有没有可能两个不相等的对象有有相同的-hashcode)  

### 41、Try.catch.finally是必须要存在的吗？




## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
