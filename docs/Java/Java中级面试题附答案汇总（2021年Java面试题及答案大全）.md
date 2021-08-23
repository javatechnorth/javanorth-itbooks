# Java中级面试题附答案汇总（2021年Java面试题及答案大全）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、有哪些类加载器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#1有哪些类加载器)  


自 JDK1.2 起 Java 一直保持三层类加载器：

**启动类加载器**

在 JVM 启动时创建，负责加载最核心的类，例如 Object、System 等。无法被程序直接引用，如果需要把加载委派给启动类加载器，直接使用 null 代替即可，因为启动类加载器通常由操作系统实现，并不存在于 JVM 体系。

**平台类加载器**

从 JDK9 开始从扩展类加载器更换为平台类加载器，负载加载一些扩展的系统类，比如 XML、加密、压缩相关的功能类等。

**应用类加载器**

也称系统类加载器，负责加载用户类路径上的类库，可以直接在代码中使用。如果没有自定义类加载器，一般情况下应用类加载器就是默认的类加载器。自定义类加载器通过继承 ClassLoader 并重写 `findClass` 方法实现。


### [2、mixin、hoc、render props、react-hooks的优劣如何？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#2mixinhocrender-propsreact-hooks的优劣如何)  


**Mixin的缺陷：**

**1、** 组件与 Mixin 之间存在隐式依赖（Mixin 经常依赖组件的特定方法，但在定义组件时并不知道这种依赖关系）

**2、** 多个 Mixin 之间可能产生冲突（比如定义了相同的state字段）

**3、** Mixin 倾向于增加更多状态，这降低了应用的可预测性（The more state in your application, the harder it is to reason about it.），导致复杂度剧增

**隐式依赖导致依赖关系不透明，维护成本和理解成本迅速攀升：**

**1、** 难以快速理解组件行为，需要全盘了解所有依赖 Mixin 的扩展行为，及其之间的相互影响

**2、** 组价自身的方法和state字段不敢轻易删改，因为难以确定有没有 Mixin 依赖它

**3、** Mixin 也难以维护，因为 Mixin 逻辑最后会被打平合并到一起，很难搞清楚一个 Mixin 的输入输出

**HOC相比Mixin的优势:**

**1、** HOC通过外层组件通过 Props 影响内层组件的状态，而不是直接改变其 State不存在冲突和互相干扰,这就降低了耦合度

**2、** 不同于 Mixin 的打平+合并，HOC 具有天然的层级结构（组件树结构），这又降低了复杂度

**HOC的缺陷:**

**1、** 扩展性限制: HOC 无法从外部访问子组件的 State因此无法通过shouldComponentUpdate滤掉不必要的更新,React 在支持 ES6 Class 之后提供了React.PureComponent来解决这个问题

**2、** Ref 传递问题: Ref 被隔断,后来的React.forwardRef 来解决这个问题

**3、** Wrapper Hell: HOC可能出现多层包裹组件的情况,多层抽象同样增加了复杂度和理解成本

**4、** 命名冲突: 如果高阶组件多次嵌套,没有使用命名空间的话会产生冲突,然后覆盖老属性

**5、** 不可见性: HOC相当于在原有组件外层再包装一个组件,你压根不知道外层的包装是啥,对于你是黑盒

**Render Props优点:**

上述HOC的缺点Render Props都可以解决

**Render Props缺陷:**

**1、** 使用繁琐: HOC使用只需要借助装饰器语法通常一行代码就可以进行复用,Render Props无法做到如此简单

**2、** 嵌套过深: Render Props虽然摆脱了组件多层嵌套的问题,但是转化为了函数回调的嵌套

**React Hooks优点:**

**1、** 简洁: React Hooks解决了HOC和Render Props的嵌套问题,更加简洁

**2、** 解耦: React Hooks可以更方便地把 UI 和状态分离,做到更彻底的解耦

**3、** 组合: Hooks 中可以引用另外的 Hooks形成新的Hooks,组合变化万千

**4、** 函数友好: React Hooks为函数组件而生,从而解决了类组件的几大问题:

**1、** this 指向容易错误

**2、** 分割在不同声明周期中的逻辑使得代码难以理解和维护

**3、** 代码复用成本高（高阶组件容易使代码量剧增）

**React Hooks缺陷:**

**1、** 额外的学习成本（Functional Component 与 Class Component 之间的困惑）

**2、** 写法上有限制（不能出现在条件、循环中），并且写法限制增加了重构成本

**3、** 破坏了PureComponent、React.memo浅比较的性能优化效果（为了取最新的props和state，每次render()都要重新创建事件处函数）

**4、** 在闭包场景可能会引用到旧的state、props值

**5、** 内部实现上不直观（依赖一份可变的全局状态，不再那么“纯”）

**6、** React.memo并不能完全替代shouldComponentUpdate（因为拿不到 state change，只针对 props change）

> 关于react-hooks的评价来源于官方[react-hooks RFC](https://github.com/reactjs/rfcs/blob/master/text/0068-react-hooks.md#drawbacks)



### [3、什么是Executors？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#3什么是executors)  


**Executors框架实现的就是线程池的功能**

Executors工厂类中提供的newCachedThreadPool、newFixedThreadPool 、newScheduledThreadPool 、newSingleThreadExecutor 等方法其实也只是ThreadPoolExecutor的构造函数参数不同而已。通过传入不同的参数，就可以构造出适用于不同应用场景下的线程池，

Executor工厂类如何创建线程池图：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/045/42/87_7.png#alt=87%5C_7.png)


### [4、如何判断对象是否是垃圾？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#4如何判断对象是否是垃圾)  


**引用计数：**在对象中添加一个引用计数器，如果被引用计数器加 1，引用失效时计数器减 1，如果计数器为 0 则被标记为垃圾。原理简单，效率高，但是在 Java 中很少使用，因为存在对象间循环引用的问题，导致计数器无法清零。

**可达性分析：**主流语言的内存管理都使用可达性分析判断对象是否存活。基本思路是通过一系列称为 GC Roots 的根对象作为起始节点集，从这些节点开始，根据引用关系向下搜索，搜索过程走过的路径称为引用链，如果某个对象到 GC Roots 没有任何引用链相连，则会被标记为垃圾。可作为 GC Roots 的对象包括虚拟机栈和本地方法栈中引用的对象、类静态属性引用的对象、常量引用的对象。


### [5、volatile 类型变量提供什么保证？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#5volatile-类型变量提供什么保证)  


volatile 变量提供顺序和可见性保证，例如，JVM 或者 JIT为了获得更好的性能会对语句重排序，但是 volatile 类型变量即使在没有同步块的情况下赋值也不会与其他语句重排序。 volatile 提供 happens-before 的保证，确保一个线程的修改能对其他线程是可见的。某些情况下，volatile 还能提供原子性，如读 64 位数据类型，像 long 和 double 都不是原子的，但 volatile 类型的 double 和 long 就是原子的。


### [6、在 Java 程序中怎么保证多线程的运行安全？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#6在-java-程序中怎么保证多线程的运行安全)  


**出现线程安全问题的原因一般都是三个原因：**

**1、** 线程切换带来的原子性问题 解决办法：使用多线程之间同步synchronized或使用锁(lock)。

**2、** 缓存导致的可见性问题 解决办法：synchronized、volatile、LOCK，可以解决可见性问题

**3、** 编译优化带来的有序性问题 解决办法：Happens-Before 规则可以解决有序性问题


### [7、线上常用的 JVM 参数有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#7线上常用的-jvm-参数有哪些)  


**数据区设置**

**1、** Xms：初始堆大小

**2、** Xmx：最大堆大小

**3、** Xss:Java 每个线程的Stack大小

**4、** XX:NewSize=n：设置年轻代大小

**5、** XX:NewRatio=n：设置年轻代和年老代的比值。如：为 3，表示年轻代与年老代比值为 1:3，年轻代占整个年轻代年老代和的 1/4。

**6、** XX：SurvivorRatio=n：年轻代中 Eden 区与两个 Survivor 区的比值。注意 Survivor 区有两个。如：3，表示 Eden：Survivor=3：2，一个 Survivor 区占整个年轻代的 1/5。

**7、** XX：MaxPermSize=n：设置持久代大小。

**收集器设置**

**1、** XX:+UseSerialGC：设置串行收集器

**2、** XX:+UseParallelGC:：设置并行收集器

**3、** XX:+UseParalledlOldGC：设置并行年老代收集器

**4、** XX:+UseConcMarkSweepGC：设置并发收集器

**GC日志打印设置**

**1、** XX:+PrintGC：打印 GC 的简要信息

**2、** XX:+PrintGCDetails：打印 GC 详细信息

**3、** XX:+PrintGCTimeStamps：输出 GC 的时间戳


### [8、volatile 关键字的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#8volatile-关键字的作用)  


**1、** 对于可见性，Java 提供了 volatile 关键字来保证可见性和禁止指令重排。 volatile 提供 happens-before 的保证，确保一个线程的修改能对其他线程是可见的。当一个共享变量被 volatile修饰时，它会保证修改的值会立即被更新到主内存中，当有其他线程需要读取时，它会去内存中读取新值。

**2、** 从实践角度而言，volatile 的一个重要作用就是和 CAS 结合，保证了原子性，详细的可以参见 java.util.concurrent.atomic 包下的类，比如 AtomicInteger。

**3、** volatile 常用于多线程环境下的单次操作(单次读或者单次写)。


### [9、解释何时在Tomcat使用SSL ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#9解释何时在tomcat使用ssl-)  


当你将Tomcat作为独立的web服务器运行时，需使用Tomcat来处理连接


### [10、使用js获取一个表单元素](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#10使用js获取一个表单元素)  


**1、** Document.getElementById()

**2、** Document.getElementsByName()

**3、** Document.getElementsByTagName()


### [11、Java 内存分配](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#11java-内存分配)  

### [12、什么是并发队列：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#12什么是并发队列：)  

### [13、什么是父类引用指向子类对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#13什么是父类引用指向子类对象)  

### [14、Thread类中的yield方法有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#14thread类中的yield方法有什么作用)  

### [15、继承和组合之间有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#15继承和组合之间有什么不同)  

### [16、HashMap 的长度为什么是2的幂次方](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#16hashmap-的长度为什么是2的幂次方)  

### [17、CAS 的会产生什么问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#17cas-的会产生什么问题)  

### [18、JAVA虚引用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#18java虚引用)  

### [19、环境变量Path和ClassPath的作用是什么？如何设置这两个环境变量？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#19环境变量path和classpath的作用是什么如何设置这两个环境变量)  

### [20、JVM垃圾回收机制，何时触发MinorGC等操作](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#20jvm垃圾回收机制何时触发minorgc等操作)  

### [21、Jsp指令有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#21jsp指令有那些)  

### [22、除了单例模式，你在生产环境中还用过什么设计模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#22除了单例模式你在生产环境中还用过什么设计模式)  

### [23、String和StringBuffer、StringBuilder的区别是什么？String为什么是不可变的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#23string和stringbufferstringbuilder的区别是什么string为什么是不可变的)  

### [24、两个对象值相同(x.equals(y) == true)，但却可有不同的hash code，这句话对不对？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#24两个对象值相同xequalsy--true但却可有不同的hash-code这句话对不对)  

### [25、给我一个符合开闭原则的设计模式的例子？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#25给我一个符合开闭原则的设计模式的例子)  

### [26、java中是值传递引用传递？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#26java中是值传递引用传递)  

### [27、线程同步的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#27线程同步的方法)  

### [28、final 在 java 中有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#28final-在-java-中有什么作用)  

### [29、使用JDBC操作数据库时，如何提升读取数据的性能？如何提升更新数据的性能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#29使用jdbc操作数据库时如何提升读取数据的性能如何提升更新数据的性能)  

### [30、HashMap中的key，可以是普通对象么？需要什么注意的地方？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#30hashmap中的key可以是普通对象么需要什么注意的地方)  

### [31、接口有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#31接口有什么特点)  

### [32、SWAP会影响性能么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#32swap会影响性能么)  

### [33、会话跟踪技术有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#33会话跟踪技术有那些)  

### [34、Xml的java解析有几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#34xml的java解析有几种方式)  

### [35、多线程应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#35多线程应用场景)  

### [36、什么是事务？事务有那些特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#36什么是事务事务有那些特点)  

### [37、事务的ACID是指什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#37事务的acid是指什么)  

### [38、CopyOnWriteArrayList 是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#38copyonwritearraylist-是什么)  

### [39、请说明select * from tab的输出结果是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#39请说明select-*-from-tab的输出结果是什么)  

### [40、说说你知道的几种主要的JVM参数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题附答案汇总（2021年Java面试题及答案大全）.md#40说说你知道的几种主要的jvm参数)  

### 41、日期和时间：




