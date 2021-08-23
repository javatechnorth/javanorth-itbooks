# Netty面试题带答案（2021年Netty面试题及答案大汇总）

Netty面试题及答案【最新版】Netty高级面试题大全(2021版)，发现网上很多Netty面试题及答案整理都没有答案，所以花了很长时间搜集，本套Netty面试题大全，Netty面试题大汇总，有大量经典的Netty面试题以及答案，包含Netty语言常见面试题、Netty工程师高级面试题及一些大厂Netty开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Netty面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Netty面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、BIO、NIO 和 AIO 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#1bionio-和-aio-的区别)  


**BIO：**一个连接一个线程，客户端有连接请求时服务器端就需要启动一个线程进行处理。线程开销大。

**伪异步 IO：**将请求连接放入线程池，一对多，但线程还是很宝贵的资源。

**NIO：**一个请求一个线程，但客户端发送的连接请求都会注册到多路复用器上，多路复用器轮询到连接有 I/O 请求时才启动一个线程进行处理。

**AIO：**一个有效请求一个线程，客户端的 I/O 请求都是由 OS 先完成了再通知服务器应用去启动线程进行处理。

BIO 是面向流的，NIO 是面向缓冲区的；BIO 的各种流是阻塞的。而 NIO 是非阻塞的；BIO的 Stream 是单向的，而 NIO 的 channel 是双向的。

**NIO 的特点：**事件驱动模型、单线程处理多任务、非阻塞 I/O，I/O 读写不再阻塞，而是返回 0、基于 block 的传输比基于流的传输更高效、更高级的 IO 函数 zero-copy、IO 多路复用大大提高了 Java 网络应用的可伸缩性和实用性。基于 Reactor 线程模型。

在 Reactor 模式中，事件分发器等待某个事件或者可应用或个操作的状态发生，事件分发器就把这个事件传给事先注册的事件处理函数或者回调函数，由后者来做实际的读写操作。如在 Reactor 中实现读：注册读就绪事件和相应的事件处理器、事件分发器等待事件、事件到来，激活分发器，分发器调用事件对应的处理器、事件处理器完成实际的读操作，处理读到的数据，注册新的事件，然后返还控制权。


### [2、NIOEventLoopGroup源码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#2nioeventloopgroup源码)  


NioEventLoopGroup(其实是MultithreadEventExecutorGroup) 内部维护一个类型为 EventExecutor children [], 默认大小是处理器核数 * 2, 这样就构成了一个线程池，初始化EventExecutor时NioEventLoopGroup重载newChild方法，所以children元素的实际类型为NioEventLoop。

线程启动时调用SingleThreadEventExecutor的构造方法，执行NioEventLoop类的run方法，首先会调用hasTasks()方法判断当前taskQueue是否有元素。如果taskQueue中有元素，执行 selectNow() 方法，最终执行selector.selectNow()，该方法会立即返回。如果taskQueue没有元素，执行 select(oldWakenUp) 方法

select ( oldWakenUp) 方法解决了 Nio 中的 bug，selectCnt 用来记录selector.select方法的执行次数和标识是否执行过selector.selectNow()，若触发了epoll的空轮询bug，则会反复执行selector.select(timeoutMillis)，变量selectCnt 会逐渐变大，当selectCnt 达到阈值（默认512），则执行rebuildSelector方法，进行selector重建，解决cpu占用100%的bug。

rebuildSelector方法先通过openSelector方法创建一个新的selector。然后将old selector的selectionKey执行cancel。最后将old selector的channel重新注册到新的selector中。rebuild后，需要重新执行方法selectNow，检查是否有已ready的selectionKey。

接下来调用processSelectedKeys 方法（处理I/O任务），当selectedKeys != null时，调用processSelectedKeysOptimized方法，迭代 selectedKeys 获取就绪的 IO 事件的selectkey存放在数组selectedKeys中, 然后为每个事件都调用 processSelectedKey 来处理它，processSelectedKey 中分别处理OP_READ；OP_WRITE；OP_CONNECT事件。

最后调用runAllTasks方法（非IO任务），该方法首先会调用fetchFromScheduledTaskQueue方法，把scheduledTaskQueue中已经超过延迟执行时间的任务移到taskQueue中等待被执行，然后依次从taskQueue中取任务执行，每执行64个任务，进行耗时检查，如果已执行时间超过预先设定的执行时间，则停止执行非IO任务，避免非IO任务太多，影响IO任务的执行。

每个NioEventLoop对应一个线程和一个Selector，NioServerSocketChannel会主动注册到某一个NioEventLoop的Selector上，NioEventLoop负责事件轮询。

Outbound 事件都是请求事件, 发起者是 Channel，处理者是 unsafe，通过 Outbound 事件进行通知，传播方向是 tail到head。Inbound 事件发起者是 unsafe，事件的处理者是 Channel, 是通知事件，传播方向是从头到尾。

内存管理机制，首先会预申请一大块内存Arena，Arena由许多Chunk组成，而每个Chunk默认由2048个page组成。Chunk通过AVL树的形式组织Page，每个叶子节点表示一个Page，而中间节点表示内存区域，节点自己记录它在整个Arena中的偏移地址。当区域被分配出去后，中间节点上的标记位会被标记，这样就表示这个中间节点以下的所有节点都已被分配了。大于8k的内存分配在poolChunkList中，而PoolSubpage用于分配小于8k的内存，它会把一个page分割成多段，进行内存分配。

ByteBuf的特点：支持自动扩容（4M），保证put方法不会抛出异常、通过内置的复合缓冲类型，实现零拷贝（zero-copy）；不需要调用flip()来切换读/写模式，读取和写入索引分开；方法链；引用计数基于AtomicIntegerFieldUpdater用于内存回收；PooledByteBuf采用二叉树来实现一个内存池，集中管理内存的分配和释放，不用每次使用都新建一个缓冲区对象。UnpooledHeapByteBuf每次都会新建一个缓冲区对象。


### [3、Bootstrap 和 ServerBootstrap 了解么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#3bootstrap-和-serverbootstrap-了解么)  


你再说说自己对 Bootstrap 和 ServerBootstrap 的了解吧！

Bootstrap 是客户端的启动引导类/辅助类，具体使用方法如下：

```
        EventLoopGroup group = new NioEventLoopGroup();
        try {
            //创建客户端启动引导/辅助类：Bootstrap
            Bootstrap b = new Bootstrap();
            //指定线程模型
            b.group(group).
                    ......
            // 尝试建立连接
            ChannelFuture f = b.connect(host, port).sync();
            f.channel().closeFuture().sync();
        } finally {
            // 优雅关闭相关线程组资源
            group.shutdownGracefully();
        }
```

ServerBootstrap 客户端的启动引导类/辅助类，具体使用方法如下：

```
        // 1.bossGroup 用于接收连接，workerGroup 用于具体的处理
        EventLoopGroup bossGroup = new NioEventLoopGroup(1);
        EventLoopGroup workerGroup = new NioEventLoopGroup();
        try {
            //2.创建服务端启动引导/辅助类：ServerBootstrap
            ServerBootstrap b = new ServerBootstrap();
            //3.给引导类配置两大线程组,确定了线程模型
            b.group(bossGroup, workerGroup).
                   ......
            // 6.绑定端口
            ChannelFuture f = b.bind(port).sync();
            // 等待连接关闭
            f.channel().closeFuture().sync();
        } finally {
            //7.优雅关闭相关线程组资源
            bossGroup.shutdownGracefully();
            workerGroup.shutdownGracefully();
        }
    }
```

**从上面的示例中，我们可以看出：**

**1、**  Bootstrap 通常使用 connet() 方法连接到远程的主机和端口，作为一个 Netty TCP 协议通信中的客户端。另外，Bootstrap 也可以通过 bind() 方法绑定本地的一个端口，作为 UDP 协议通信中的一端。

**2、**  ServerBootstrap通常使用 bind() 方法绑定本地的端口上，然后等待客户端的连接。

**3、**  Bootstrap 只需要配置一个线程组— EventLoopGroup ,而 ServerBootstrap需要配置两个线程组— EventLoopGroup ，一个用于接收连接，一个用于具体的处理。


### [4、了解哪几种序列化协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#4了解哪几种序列化协议)  


序列化（编码）是将对象序列化为二进制形式（字节数组），主要用于网络传输、数据持久化等；而反序列化（解码）则是将从网络、磁盘等读取的字节数组还原成原始对象，主要用于网络传输对象的解码，以便完成远程调用。

影响序列化性能的关键因素：序列化后的码流大小（网络带宽的占用）、序列化的性能（CPU资源占用）；是否支持跨语言（异构系统的对接和开发语言切换）。

Java默认提供的序列化：无法跨语言、序列化后的码流太大、序列化的性能差

XML，优点：人机可读性好，可指定元素或特性的名称。缺点：序列化数据只包含数据本身以及类的结构，不包括类型标识和程序集信息；只能序列化公共属性和字段；不能序列化方法；文件庞大，文件格式复杂，传输占带宽。适用场景：当做配置文件存储数据，实时数据转换。

JSON，是一种轻量级的数据交换格式，优点：兼容性高、数据格式比较简单，易于读写、序列化后数据较小，可扩展性好，兼容性好、与XML相比，其协议比较简单，解析速度比较快。缺点：数据的描述性比XML差、不适合性能要求为ms级别的情况、额外空间开销比较大。适用场景（可替代ＸＭＬ）：跨防火墙访问、可调式性要求高、基于Web browser的Ajax请求、传输数据量相对小，实时性要求相对低（例如秒级别）的服务。

Fastjson，采用一种“假定有序快速匹配”的算法。优点：接口简单易用、目前java语言中最快的json库。缺点：过于注重快，而偏离了“标准”及功能性、代码质量不高，文档不全。适用场景：协议交互、Web输出、Android客户端

Thrift，不仅是序列化协议，还是一个RPC框架。优点：序列化后的体积小, 速度快、支持多种语言和丰富的数据类型、对于数据字段的增删具有较强的兼容性、支持二进制压缩编码。缺点：使用者较少、跨防火墙访问时，不安全、不具有可读性，调试代码时相对困难、不能与其他传输层协议共同使用（例如HTTP）、无法支持向持久层直接读写数据，即不适合做数据持久化序列化协议。适用场景：分布式系统的RPC解决方案

Avro，Hadoop的一个子项目，解决了JSON的冗长和没有IDL的问题。优点：支持丰富的数据类型、简单的动态语言结合功能、具有自我描述属性、提高了数据解析速度、快速可压缩的二进制数据形式、可以实现远程过程调用RPC、支持跨编程语言实现。缺点：对于习惯于静态类型语言的用户不直观。适用场景：在Hadoop中做Hive、Pig和MapReduce的持久化数据格式。

Protobuf，将数据结构以.proto文件进行描述，通过代码生成工具可以生成对应数据结构的POJO对象和Protobuf相关的方法和属性。优点：序列化后码流小，性能高、结构化数据存储格式（XML JSON等）、通过标识字段的顺序，可以实现协议的前向兼容、结构化的文档更容易管理和维护。缺点：需要依赖于工具生成代码、支持的语言相对较少，官方只支持Java 、C++ 、python。适用场景：对性能要求高的RPC调用、具有良好的跨防火墙的访问属性、适合应用层对象的持久化

**其它**

protostuff 基于protobuf协议，但不需要配置proto文件，直接导包即可

Jboss marshaling 可以直接序列化java类， 无须实java.io.Serializable接口

Message pack 一个高效的二进制序列化格式

Hessian 采用二进制协议的轻量级remoting onhttp工具

kryo 基于protobuf协议，只支持java语言,需要注册（Registration），然后序列化（Output），反序列化（Input）


### [5、Netty如何实现重连](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#5netty如何实现重连)  


**1、** 客户端，通过 IdleStateHandler 实现定时检测是否空闲

**2、** 如果空闲，则向服务端发起心跳*

**3、** 如果多次心跳失败，则关闭和服务端的连接，然后重新发起连接

**4、** 服务端，通过 IdleStateHandler 实现定时检测客户端是否空闲

**5、** 如果检测到空闲，则关闭客户端

**6、** 如果接收到客户端的心跳请求，要反馈一个心跳响应给客户端。


### [6、Netty的线程模型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#6netty的线程模型)  


Netty通过Reactor模型基于多路复用器接收并处理用户请求，内部实现了两个线程池，boss线程池和work线程池，其中boss线程池的线程负责处理请求的accept事件，当接收到accept事件的请求时，把对应的socket封装到一个NioSocketChannel中，并交给work线程池，其中work线程池负责请求的read和write事件，由对应的Handler处理。

单线程模型：所有I/O操作都由一个线程完成，即多路复用、事件分发和处理都是在一个Reactor线程上完成的。既要接收客户端的连接请求,向服务端发起连接，又要发送/读取请求或应答/响应消息。一个NIO 线程同时处理成百上千的链路，性能上无法支撑，速度慢，若线程进入死循环，整个程序不可用，对于高负载、大并发的应用场景不合适。

多线程模型：有一个NIO 线程（Acceptor） 只负责监听服务端，接收客户端的TCP 连接请求；NIO 线程池负责网络IO 的操作，即消息的读取、解码、编码和发送；1 个NIO 线程可以同时处理N 条链路，但是1 个链路只对应1 个NIO 线程，这是为了防止发生并发操作问题。但在并发百万客户端连接或需要安全认证时，一个Acceptor 线程可能会存在性能不足问题。

主从多线程模型：Acceptor 线程用于绑定监听端口，接收客户端连接，将SocketChannel 从主线程池的Reactor 线程的多路复用器上移除，重新注册到Sub 线程池的线程上，用于处理I/O 的读写等操作，从而保证mainReactor只负责接入认证、握手等操作；


### [7、NioEventLoopGroup 默认的构造函数会起多少线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#7nioeventloopgroup-默认的构造函数会起多少线程)  


看过 Netty 的源码了么？NioEventLoopGroup 默认的构造函数会起多少线程呢？

嗯嗯！看过部分。

回顾我们在上面写的服务器端的代码：

```
// 1.bossGroup 用于接收连接，workerGroup 用于具体的处理
EventLoopGroup bossGroup = new NioEventLoopGroup(1);
EventLoopGroup workerGroup = new NioEventLoopGroup();
```

为了搞清楚NioEventLoopGroup 默认的构造函数 到底创建了多少个线程，我们来看一下它的源码。

```
    /**
     * 无参构造函数。
     * nThreads:0
     */
    public NioEventLoopGroup() {
        //调用下一个构造方法
        this(0);
    }

    /**
     * Executor：null
     */
    public NioEventLoopGroup(int nThreads) {
        //继续调用下一个构造方法
        this(nThreads, (Executor) null);
    }

    //中间省略部分构造函数

    /**
     * RejectedExecutionHandler（）：RejectedExecutionHandlers.reject()
     */
    public NioEventLoopGroup(int nThreads, Executor executor, final SelectorProvider selectorProvider,final SelectStrategyFactory selectStrategyFactory) {
       //开始调用父类的构造函数
        super(nThreads, executor, selectorProvider, selectStrategyFactory, RejectedExecutionHandlers.reject());
    }
```

一直向下走下去的话，你会发现在 MultithreadEventLoopGroup 类中有相关的指定线程数的代码，如下：

```
    // 从1，系统属性，CPU核心数*2 这三个值中取出一个最大的
    //可以得出 DEFAULT_EVENT_LOOP_THREADS 的值为CPU核心数*2
    private static final int DEFAULT_EVENT_LOOP_THREADS = Math.max(1, SystemPropertyUtil.getInt("io.netty.eventLoopThreads", NettyRuntime.availableProcessors() * 2));

    // 被调用的父类构造函数，NioEventLoopGroup 默认的构造函数会起多少线程的秘密所在
    // 当指定的线程数nThreads为0时，使用默认的线程数DEFAULT_EVENT_LOOP_THREADS
    protected MultithreadEventLoopGroup(int nThreads, ThreadFactory threadFactory, Object..、args) {
        super(nThreads == 0 ? DEFAULT_EVENT_LOOP_THREADS : nThreads, threadFactory, args);
    }
```

综上，我们发现 NioEventLoopGroup 默认的构造函数实际会起的线程数为 **CPU核心数_2_。

另外，如果你继续深入下去看构造函数的话，你会发现每个NioEventLoopGroup对象内部都会分配一组NioEventLoop，其大小是 nThreads, 这样就构成了一个线程池， 一个NIOEventLoop 和一个线程相对应，这和我们上面说的 EventloopGroup 和 EventLoop关系这部分内容相对应。


### [8、Netty 高性能表现在哪些方面？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#8netty-高性能表现在哪些方面)  


**1、** IO 线程模型：同步非阻塞，用最少的资源做更多的事。

**2、** 内存零拷贝：尽量减少不必要的内存拷贝，实现了更高效率的传输。

**3、** 内存池设计：申请的内存可以重用，主要指直接内存。内部实现是用一颗二叉查找树管理内存分配情况。

**4、** 串形化处理读写：避免使用锁带来的性能开销。

**5、** 高性能序列化协议：支持 protobuf 等高性能序列化协议。


### [9、Netty 长连接、心跳机制了解么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#9netty-长连接心跳机制了解么)  


TCP 长连接和短连接了解么？

我们知道 TCP 在进行读写之前，server 与 client 之间必须提前建立一个连接。建立连接的过程，需要我们常说的三次握手，释放/关闭连接的话需要四次挥手。这个过程是比较消耗网络资源并且有时间延迟的。

所谓，短连接说的就是 server 端 与 client 端建立连接之后，读写完成之后就关闭掉连接，如果下一次再要互相发送消息，就要重新连接。短连接的有点很明显，就是管理和实现都比较简单，缺点也很明显，每一次的读写都要建立连接必然会带来大量网络资源的消耗，并且连接的建立也需要耗费时间。

长连接说的就是 client 向 server 双方建立连接之后，即使 client 与 server 完成一次读写，它们之间的连接并不会主动关闭，后续的读写操作会继续使用这个连接。长连接的可以省去较多的 TCP 建立和关闭的操作，降低对网络资源的依赖，节约时间。对于频繁请求资源的客户来说，非常适用长连接。


### [10、Netty 空闲检测](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#10netty-空闲检测)  


IdleStateHandler ，用于检测连接的读写是否处于空闲状态。如果是，则会触发 IdleStateEvent 。


### [11、Netty 如何实现高性能](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#11netty-如何实现高性能)  

### [12、Netty怎样实现零拷贝](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#12netty怎样实现零拷贝)  

### [13、Netty为什么说使用简单](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#13netty为什么说使用简单)  

### [14、NIO 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#14nio-是什么)  

### [15、了解哪几种序列化协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#15了解哪几种序列化协议)  

### [16、Netty 的使用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#16netty-的使用场景)  

### [17、Netty自己实现的ByteBuf有什么优点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#17netty自己实现的bytebuf有什么优点)  

### [18、Netty 的优势有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#18netty-的优势有哪些)  

### [19、AIO 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#19aio-是什么)  

### [20、NIOEventLoopGroup 源码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#20nioeventloopgroup-源码)  

### [21、如何选择序列化协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#21如何选择序列化协议)  

### [22、TCP 粘包/拆包的原因及解决方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#22tcp-粘包/拆包的原因及解决方法)  

### [23、Netty 的核心组件介绍下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#23netty-的核心组件介绍下)  

### [24、什么是Netty](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#24什么是netty)  

### [25、什么是 TCP 粘包/拆包?有什么解决办法呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#25什么是-tcp-粘包/拆包有什么解决办法呢)  

### [26、为什么需要心跳机制？Netty 中心跳机制了解么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#26为什么需要心跳机制netty-中心跳机制了解么)  

### [27、Netty 的线程模型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#27netty-的线程模型)  

### [28、原生的NIO存在Epoll Bug有什么BUG、Netty 是怎么解决的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#28原生的nio存在epoll-bug有什么bugnetty-是怎么解决的)  

### [29、详细看说下 Netty 中的线程模型吧！](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#29详细看说下-netty-中的线程模型吧)  

### [30、Netty的特点是什么（ 为什么选择 Netty ）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#30netty的特点是什么-为什么选择-netty-)  

### [31、默认情况 Netty 起多少线程？何时启动？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#31默认情况-netty-起多少线程何时启动)  

### [32、BIO、NIO 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#32bionio-有什么区别)  

### [33、为什么要用 Netty？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#33为什么要用-netty)  

### [34、Netty 支持哪些心跳类型设置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题带答案（2021年Netty面试题及答案大汇总）.md#34netty-支持哪些心跳类型设置)  





