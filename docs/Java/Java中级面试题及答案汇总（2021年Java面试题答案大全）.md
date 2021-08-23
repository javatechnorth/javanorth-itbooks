# Java中级面试题及答案汇总（2021年Java面试题答案大全）

Java面试题及答案【最新版】Java高级面试题大全(2021版)，发现网上很多Java面试题及答案整理都没有答案，所以花了很长时间搜集，本套Java面试题大全，Java面试题大汇总，有大量经典的Java面试题以及答案，包含Java语言常见面试题、Java工程师高级面试题及一些大厂Java开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Java面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Java面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、说说G1垃圾收集器的工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#1说说g1垃圾收集器的工作原理)  


优点：指定最大停顿时间、分Region的内存布局、按收益动态确定回收集

**1、** G1开创的基于Region的堆内存布局是它能够实现这个目标的关键。虽然G1也仍是遵循分代收集理论设计的，但其堆内存的布局与其他收集器有非常明显的差异：G1不再坚持固定大小以及固定数量的分代区域划分，而是把连续的Java堆划分为多个大小相等的独立区域（Region），每一个Region都可以根据需要，扮演新生代的Eden空间、Survivor空间，或者老年代空间。收集器能够对扮演不同角色的Region采用不同的策略去处理，这样无论是新创建的对象还是已经存活了一段时间、熬过多次收集的旧对象都能获取很好的收集效果。

**2、** 虽然G1仍然保留新生代和老年代的概念，但新生代和老年代不再是固定的了，它们都是一系列区域（不需要连续）的动态集合。G1收集器之所以能建立可预测的停顿时间模型，是因为它将Region作为单次回收的最小单元，即每次收集到的内存空间都是Region大小的整数倍，这样可以有计划地避免在整个Java堆中进行全区域的垃圾收集。更具体的处理思路是让G1收集器去跟踪各个Region里面的垃圾堆积的“价值”大小，价值即回收所获得的空间大小以及回收所需时间的经验值，然后在后台维护一个优先级列表，每次根据用户设定允许的收集停顿时间（使用参数-XX：MaxGCPauseMillis指定，默认值是200毫秒），优先处理回收价值收益最大的那些Region，这也就是“Garbage First”名字的由来。这种使用Region划分内存空间，以及具有优先级的区域回收方式，保证了G1收集器在有限的时间内获取尽可能高的收集效率。

**3、** G1收集器的运作过程大致可划分为以下四个步骤：·初始标记 （Initial Marking）：仅仅只是标记一下GC Roots能直接关联到的对象，并且修改TAMS指针的值，让下一阶段用户线程并发运行时，能正确地在可用的Region中分配新对象。这个阶段需要停顿线程，但耗时很短，而且是借用进行Minor GC的时候同步完成的，所以G1收集器在这个阶段实际并没有额外的停顿。·并发标记 （Concurrent Marking）：从GC Root开始对堆中对象进行可达性分析，递归扫描整个堆里的对象图，找出要回收的对象，这阶段耗时较长，但可与用户程序并发执行。当对象图扫描完成以后，还要重新处理SATB记录下的在并发时有引用变动的对象。·最终标记 （Final Marking）：对用户线程做另一个短暂的暂停，用于处理并发阶段结束后仍遗留下来的最后那少量的SATB记录。·筛选回收 （Live Data Counting and Evacuation）：负责更新Region的统计数据，对各个Region的回收价值和成本进行排序，根据用户所期望的停顿时间来制定回收计划，可以自由选择任意多个Region构成回收集，然后把决定回收的那一部分Region的存活对象复制到空的Region中，再清理掉整个旧Region的全部空间。这里的操作涉及存活对象的移动，是必须暂停用户线程，由多条收集器线程并行完成的。从上述阶段的描述可以看出，G1收集器除了并发标记外，其余阶段也是要完全暂停用户线程的 。


### [2、JRE、JDK、JVM 及 JIT 之间有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#2jrejdkjvm-及-jit-之间有什么不同)  


JRE 代表 Java 运行时（Java run-time），是运行 Java 引用所必须的。JDK 代表 Java 开发工具（Java development kit），是 Java 程序的开发工具，如 Java编译器，它也包含 JRE。JVM 代表 Java 虚拟机（Java virtual machine），它的责任是运行 Java 应用。JIT 代表即时编译（Just In Time compilation），当代码执行的次数超过一定的阈值时，会将 Java 字节码转换为本地代码，如，主要的热点代码会被准换为本地代码，这样有利大幅度提高 Java 应用的性能。


### [3、当父类引用指向子类对象的时候，子类重写了父类方法和属性，那么当访问属性的时候，访问是谁的属性？调用方法时，调用的是谁的方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#3当父类引用指向子类对象的时候子类重写了父类方法和属性那么当访问属性的时候访问是谁的属性调用方法时调用的是谁的方法)  


子类重写了父类方法和属性，访问的是父类的属性，调用的是子类的方法


### [4、堆溢出的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#4堆溢出的原因)  


堆用于存储对象实例，只要不断创建对象并保证 GC Roots 到对象有可达路径避免垃圾回收，随着对象数量的增加，总容量触及最大堆容量后就会 OOM，例如在 while 死循环中一直 new 创建实例。

堆 OOM 是实际应用中最常见的 OOM，处理方法是通过内存映像分析工具对 Dump 出的堆转储快照分析，确认内存中导致 OOM 的对象是否必要，分清到底是内存泄漏还是内存溢出。

如果是内存泄漏，通过工具查看泄漏对象到 GC Roots 的引用链，找到泄露对象是通过怎样的引用路径、与哪些 GC Roots 关联才导致无法回收，一般可以准确定位到产生内存泄漏代码的具***置。

如果不是内存泄漏，即内存中对象都必须存活，应当检查 JVM 堆参数，与机器内存相比是否还有向上调整的空间。再从代码检查是否存在某些对象生命周期过长、持有状态时间过长、存储结构设计不合理等情况，尽量减少程序运行期的内存消耗。


### [5、说一下 runnable 和 callable 有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#5说一下-runnable-和-callable-有什么区别)  


**相同点：**

**1、** 都是接口

**2、** 都可以编写多线程程序

**3、** 都采用Thread.start()启动线程

**主要区别：**

Runnable 接口 run 方法无返回值；Callable 接口 call 方法有返回值，是个泛型，和Future、FutureTask配合可以用来获取异步执行的结果

Runnable 接口 run 方法只能抛出运行时异常，且无法捕获处理；Callable 接口 call 方法允许抛出异常，可以获取异常信息 注：Callalbe接口支持返回执行结果，需要调用FutureTask.get()得到，此方法会阻塞主进程的继续往下执行，如果不调用不会阻塞。


### [6、JVM 类加载机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#6jvm-类加载机制)  


JVM 类加载机制分为五个部分：加载，验证，准备，解析，初始化。

**加载**

加载是类加载过程中的一个阶段， 这个阶段会在内存中生成一个代表这个类的 java.lang.Class 对象， 作为方法区这个类的各种数据的入口。注意这里不一定非得要从一个 Class 文件获取，这里既可以从 ZIP 包中读取（比如从 jar 包和 war 包中读取），也可以在运行时计算生成（动态代理），也可以由其它文件生成（比如将 JSP 文件转换成对应的 Class 类）。

**验证**

这一阶段的主要目的是为了确保 Class 文件的字节流中包含的信息是否符合当前虚拟机的要求，并且不会危害虚拟机自身的安全。

**准备**

准备阶段是正式为类变量分配内存并设置类变量的初始值阶段，即在方法区中分配这些变量所使用的内存空间。注意这里所说的初始值概念，比如一个类变量定义为：

实际上变量 v 在准备阶段过后的初始值为 0 而不是 8080， 将 v 赋值为 8080 的 put static 指令是程序被编译后， 存放于类构造器方法之中。

**但是注意如果声明为：**

public static final int v = 8080;

在编译阶段会为 v 生成 ConstantValue 属性，在准备阶段虚拟机会根据 ConstantValue 属性将 v赋值为 8080。

**解析**

解析阶段是指虚拟机将常量池中的符号引用替换为直接引用的过程。符号引用就是 class 文件中的

public static int v = 8080;

实际上变量 v 在准备阶段过后的初始值为 0 而不是 8080， 将 v 赋值为 8080 的 put static 指令是程序被编译后， 存放于类构造器方法之中。但是注意如果声明为：

在编译阶段会为 v 生成 ConstantValue 属性，在准备阶段虚拟机会根据 ConstantValue 属性将 v赋值为 8080。

**解析**

解析阶段是指虚拟机将常量池中的符号引用替换为直接引用的过程。符号引用就是 class 文件中的

public static final int v = 8080;

在编译阶段会为 v 生成 ConstantValue 属性，在准备阶段虚拟机会根据 ConstantValue 属性将 v赋值为 8080。

**解析**

解析阶段是指虚拟机将常量池中的符号引用替换为直接引用的过程。符号引用就是 class 文件中的：

**1、** CONSTANT_Class_info

**2、** CONSTANT_Field_info

**3、** CONSTANT_Method_info

等类型的常量。

**符号引用**

符号引用与虚拟机实现的布局无关， 引用的目标并不一定要已经加载到内存中。各种虚拟机实现的内存布局可以各不相同，但是它们能接受的符号引用必须是一致的，因为符号引用的字面量形式明确定义在 Java 虚拟机规范的 Class 文件格式中。

**直接引用**

直接引用可以是指向目标的指针，相对偏移量或是一个能间接定位到目标的句柄。如果有了直接引用，那引用的目标必定已经在内存中存在。

**初始化**

初始化阶段是类加载最后一个阶段，前面的类加载阶段之后，除了在加载阶段可以自定义类加载器以外，其它操作都由 JVM 主导。到了初始阶段，才开始真正执行类中定义的 Java 程序代码。

**类构造器**

初始化阶段是执行类构造器方法的过程。方法是由编译器自动收集类中的类变量的赋值操作和静态语句块中的语句合并而成的。虚拟机会保证子方法执行之前，父类的方法已经执行完毕， 如果一个类中没有对静态变量赋值也没有静态语句块，那么编译器可以不为这个类生成()方法。

**注意以下几种情况不会执行类初始化：**

**1、** 通过子类引用父类的静态字段，只会触发父类的初始化，而不会触发子类的初始化。

**2、** 定义对象数组，不会触发该类的初始化。

**3、** 常量在编译期间会存入调用类的常量池中，本质上并没有直接引用定义常量的类，不会触发定义常量所在的类。

**4、** 通过类名获取 Class 对象，不会触发类的初始化。

**5、** 通过 Class.forName 加载指定类时，如果指定参数 initialize 为 false 时，也不会触发类初始化，其实这个参数是告诉虚拟机，是否要对类进行初始化。

**6、** 通过 ClassLoader 默认的 loadClass 方法，也不会触发初始化动作。


### [7、怎么打破双亲委派模型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#7怎么打破双亲委派模型)  


打破双亲委派机制则不仅要继承ClassLoader类，还要重写loadClass和findClass方法。


### [8、垃圾收集算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#8垃圾收集算法)  


GC最基础的算法有三种：标记 -清除算法、复制算法、标记-压缩算法，我们常用的垃圾回收器一般都采用分代收集算法。

**标记 -清除算法**

“标记-清除”（Mark-Sweep）算法，如它的名字一样，算法分为“标记”和“清除”两个阶段：首先标记出所有需要回收的对象，在标记完成后统一回收掉所有被标记的对象。

**复制算法**

“复制”（Copying）的收集算法，它将可用内存按容量划分为大小相等的两块，每次只使用其中的一块。当这一块的内存用完了，就将还存活着的对象复制到另外一块上面，然后再把已使用过的内存空间一次清理掉。

**标记-压缩算法**

标记过程仍然与“标记-清除”算法一样，但后续步骤不是直接对可回收对象进行清理，而是让所有存活的对象都向一端移动，然后直接清理掉端边界以外的内存

**分代收集算法**

“分代收集”（Generational Collection）算法，把Java堆分为新生代和老年代，这样就可以根据各个年代的特点采用最适当的收集算法


### [9、你有哪些手段来排查 OOM 的问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#9你有哪些手段来排查-oom-的问题)  


**1、** 增加两个参数 -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/tmp/heapdump.hprof，当 OOM 发生时自动 dump 堆内存信息到指定目录

**2、** 同时 jstat 查看监控 JVM 的内存和 GC 情况，先观察问题大概出在什么区域

**3、** 使用 MAT 工具载入到 dump 文件，分析大对象的占用情况，比如 HashMap 做缓存未清理，时间长了就会内存溢出，可以把改为弱引用


### [10、假设把实例化的数组的变量当成方法参数，当方法执行的时候改变了数组内的元素，那么在方法外，数组元素有发生改变吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#10假设把实例化的数组的变量当成方法参数当方法执行的时候改变了数组内的元素那么在方法外数组元素有发生改变吗)  


改变了，因为传递是对象的引用，操作的是引用所指向的对象


### [11、描述一下JVM加载class文件的原理机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#11描述一下jvm加载class文件的原理机制)  

### [12、解释什么是Jasper?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#12解释什么是jasper)  

### [13、volatile关键字的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#13volatile关键字的作用)  

### [14、什么是自旋](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#14什么是自旋)  

### [15、抽象类是什么？它与接口有什么区别？你为什么要使用过抽象类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#15抽象类是什么它与接口有什么区别你为什么要使用过抽象类)  

### [16、能够找到 Reference Chain 的对象，就一定会存活么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#16能够找到-reference-chain-的对象就一定会存活么)  

### [17、JVM内存模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#17jvm内存模型)  

### [18、什么叫线程安全？servlet 是线程安全吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#18什么叫线程安全servlet-是线程安全吗)  

### [19、请解释一下什么时候可以使用“.”，什么时候可以使用“[]”?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#19请解释一下什么时候可以使用“什么时候可以使用“[])  

### [20、Java中ConcurrentHashMap的并发度是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#20java中concurrenthashmap的并发度是什么)  

### [21、永久代](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#21永久代)  

### [22、多线程中 synchronized 锁升级的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#22多线程中-synchronized-锁升级的原理是什么)  

### [23、Collection 和 Collections 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#23collection-和-collections-有什么区别)  

### [24、Java对象创建过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#24java对象创建过程)  

### [25、说说线程栈](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#25说说线程栈)  

### [26、当一个线程进入某个对象的一个synchronized的实例方法后，其它线程是否可进入此对象的其它方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#26当一个线程进入某个对象的一个synchronized的实例方法后其它线程是否可进入此对象的其它方法)  

### [27、一个”.java”源文件中是否可以包含多个类（不是内部类）？有什么限制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#27一个java源文件中是否可以包含多个类不是内部类有什么限制)  

### [28、Java 面试中其他各式各样的问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#28java-面试中其他各式各样的问题)  

### [29、创建线程的三种方式的对比？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#29创建线程的三种方式的对比)  

### [30、线程的生命周期？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#30线程的生命周期)  

### [31、TreeMap 和 TreeSet 在排序时如何比较元素？Collections 工具类中的 sort()方法如何比较元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#31treemap-和-treeset-在排序时如何比较元素collections-工具类中的-sort方法如何比较元素)  

### [32、对象分配规则](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#32对象分配规则)  

### [33、用 wait-notify 写一段代码来解决生产者-消费者问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#33用-wait-notify-写一段代码来解决生产者-消费者问题)  

### [34、如何通过反射调用对象的方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#34如何通过反射调用对象的方法)  

### [35、TCP编程与UDP编程有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#35tcp编程与udp编程有什么区别)  

### [36、请说出与线程同步以及线程调度相关的方法。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#36请说出与线程同步以及线程调度相关的方法。)  

### [37、死锁与活锁的区别，死锁与饥饿的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#37死锁与活锁的区别死锁与饥饿的区别)  

### [38、写一个方法，输入一个文件名和一个字符串，统计这个字符串在这个文件中出现的次数。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#38写一个方法输入一个文件名和一个字符串统计这个字符串在这个文件中出现的次数。)  

### [39、Java中notify 和 notifyAll有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#39java中notify-和-notifyall有什么区别)  

### [40、什么是同步任务？什么是异步任务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Java/Java中级面试题及答案汇总（2021年Java面试题答案大全）.md#40什么是同步任务什么是异步任务)  





