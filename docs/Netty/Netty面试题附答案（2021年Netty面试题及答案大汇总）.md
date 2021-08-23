# Netty面试题附答案（2021年Netty面试题及答案大汇总）

Netty面试题及答案【最新版】Netty高级面试题大全(2021版)，发现网上很多Netty面试题及答案整理都没有答案，所以花了很长时间搜集，本套Netty面试题大全，Netty面试题大汇总，有大量经典的Netty面试题以及答案，包含Netty语言常见面试题、Netty工程师高级面试题及一些大厂Netty开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Netty面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Netty面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是 Reactor 模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#1什么是-reactor-模型)  


反应器设计模式是一个事件处理模式，用于处理一个或多个输入并发地传递给服务处理程序的服务请求。然后，服务处理程序对传入请求进行多路复用，并将它们同步分派给相关的请求处理程序。

可以参考这篇文章：Reactor模型


### [2、Netty 核心组件有哪些？分别有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#2netty-核心组件有哪些分别有什么作用)  


Netty 核心组件有哪些？分别有什么作用？

**Channel**

Channel 接口是 Netty 对网络操作抽象类，它除了包括基本的 I/O 操作，如 bind()、connect()、read()、write() 等。

比较常用的Channel接口实现类是NioServerSocketChannel（服务端）和NioSocketChannel（客户端），这两个 Channel 可以和 BIO 编程模型中的ServerSocket以及Socket两个概念对应上。Netty 的 Channel 接口所提供的 API，大大地降低了直接使用 Socket 类的复杂性。

**EventLoop**

这么说吧！EventLoop（事件循环）接口可以说是 Netty 中最核心的概念了！

《Netty 实战》这本书是这样介绍它的：

EventLoop 定义了 Netty 的核心抽象，用于处理连接的生命周期中所发生的事件。

是不是很难理解？说实话，我学习 Netty 的时候看到这句话是没太能理解的。

说白了，**EventLoop 的主要作用实际就是负责监听网络事件并调用事件处理器进行相关 I/O 操作的处理。**

那 Channel 和 EventLoop 直接有啥联系呢？

Channel 为 Netty 网络操作(读写等操作)抽象类，EventLoop 负责处理注册到其上的Channel 处理 I/O 操作，两者配合参与 I/O 操作。

**ChannelFuture**

Netty 是异步非阻塞的，所有的 I/O 操作都为异步的。

因此，我们不能立刻得到操作是否执行成功，但是，你可以通过 ChannelFuture 接口的 addListener() 方法注册一个 ChannelFutureListener，当操作执行成功或者失败时，监听就会自动触发返回结果。

并且，你还可以通过ChannelFuture 的 channel() 方法获取关联的Channel

```
public interface ChannelFuture extends Future<Void> {
    Channel channel();

    ChannelFuture addListener(GenericFutureListener<? extends Future<? super Void>> var1);
     ......

    ChannelFuture sync() throws InterruptedException;
}
```

另外，我们还可以通过 ChannelFuture 接口的 sync()方法让异步的操作变成同步的。

**ChannelHandler 和 ChannelPipeline**

下面这段代码使用过 Netty 的小伙伴应该不会陌生，我们指定了序列化编解码器以及自定义的 ChannelHandler 处理消息。

```
b.group(eventLoopGroup)
        .handler(new ChannelInitializer<SocketChannel>() {
            @Override
            protected void initChannel(SocketChannel ch) {
                ch.pipeline().addLast(new NettyKryoDecoder(kryoSerializer, RpcResponse.class));
                ch.pipeline().addLast(new NettyKryoEncoder(kryoSerializer, RpcRequest.class));
                ch.pipeline().addLast(new KryoClientHandler());
            }
        });
```

ChannelHandler 是消息的具体处理器。他负责处理读写操作、客户端连接等事情。

ChannelPipeline 为 ChannelHandler 的链，提供了一个容器并定义了用于沿着链传播入站和出站事件流的 API 。当 Channel 被创建时，它会被自动地分配到它专属的 ChannelPipeline。

我们可以在 ChannelPipeline 上通过 addLast() 方法添加一个或者多个ChannelHandler ，因为一个数据或者事件可能会被多个 Handler 处理。当一个 ChannelHandler 处理完之后就将数据交给下一个 ChannelHandler 。


### [3、Netty的高可靠体现在哪几方面](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#3netty的高可靠体现在哪几方面)  


**1、** 链路有效性检测：由于长连接不需要每次发送消息都创建链路，也不需要在消息完成交互时关闭链路，因此相对于短连接性能更高。

**2、** 内存保护机制，Netty 提供多种机制对内存进行保护。通过对象引用计数器对 ByteBuf 进行细粒度的内存申请和释放，对非法的对象引用进行检测和保护。可设置的内存容量上限，包括 ByteBuf、线程池线程数等，避免异常请求耗光内存。

**3、** 优雅停机：优雅停机功能指的是当系统推出时，JVM 通过注册的 Shutdown Hook 拦截到退出信号量，然后执行推出操作，释放相关模块的资源占用，将缓冲区的消息处理完成或清空，将待刷新的数据持久化到磁盘和数据库中，等到资源回收和缓冲区消息处理完成之后，再退出。


### [4、Netty 的高性能表现在哪些方面？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#4netty-的高性能表现在哪些方面)  


**心跳，对服务端：**会定时清除闲置会话 inactive(netty5)，对客户端:用来检测会话是否断开，是否重来，检测网络延迟，其中 idleStateHandler 类 用来检测会话状态

**串行无锁化设计，**即消息的处理尽可能在同一个线程内完成，期间不进行线程切换，这样就避免了多线程竞争和同步锁。表面上看，串行化设计似乎 CPU 利用率不高，并发程度不够。但是，通过调整 NIO 线程池的线程参数，可以同时启动多个串行化的线程并行运行，这种局部无锁化的串行线程设计相比一个队列-多个工作线程模型性能更优。

**可靠性，链路有效性检测：**链路空闲检测机制，读/写空闲超时机制；内存保护机制：通过内存池重用 ByteBuf;ByteBuf 的解码保护；优雅停机：不再接收新消息、退出前的预处理操作、资源的释放操作。

**Netty 安全性：**支持的安全协议：SSL V2 和 V3，TLS，SSL 单向认证、双向认证和第三方 CA证。

**高效并发编程的体现：**volatile 的大量、正确使用；CAS 和原子类的广泛使用；线程安全容器的使用；通过读写锁提升并发性能。IO 通信性能三原则：传输（AIO）、协议（Http）、线程（主从多线程）

**流量整型的作用（变压器）：**防止由于上下游网元性能不均衡导致下游网元被压垮，业务流中断；防止由于通信模块接受消息过快，后端业务线程处理不及时导致撑死问题。

**TCP 参数配置：**SO_RCVBUF 和 SO_SNDBUF：通常建议值为 128K 或者 256K；

SO_TCPNODELAY：NAGLE 算法通过将缓冲区内的小封包自动相连，组成较大的封包，阻止大量小封包的发送阻塞网络，从而提高网络应用效率。但是对于时延敏感的应用场景需要关闭该优化算法；


### [5、Netty 线程模型了解么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#5netty-线程模型了解么)  


说一下 Netty 线程模型吧！

大部分网络框架都是基于 Reactor 模式设计开发的。

**Reactor 模式基于事件驱动，采用多路复用将事件分发给相应的 Handler 处理，非常适合处理海量 IO 的场景**。

在 Netty 主要靠 NioEventLoopGroup 线程池来实现具体的线程模型的 。

我们实现服务端的时候，一般会初始化两个线程组：

**1、** bossGroup :接收连接。

**2、** workerGroup ：负责具体的处理，交由对应的 Handler 处理。


### [6、BIO 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#6bio-是什么)  


**1、** BIO ，全称 Block-IO ，是一种阻塞 + 同步的通信模式。一种比较传统的通信方式，模式简单，使用方便。但并发处理能力低，通信耗时，依赖网速。

**2、** 原理：服务器通过一个 Acceptor 线程，负责监听客户端请求和为每个客户端创建一个新的线程进行链路处理。典型的一请求一应答模式。若客户端数量增多，频繁地创建和销毁线程会给服务器打开很大的压力。后改良为用线程池的方式代替新增线程，被称为伪异步 IO 。


### [7、Netty 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#7netty-是什么)  


Netty是 一个异步事件驱动的网络应用程序框架，用于快速开发可维护的高性能协议服务器和客户端。Netty是基于nio的，它封装了jdk的nio，让我们使用起来更加方法灵活。


### [8、JDK原生NIO程序的问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#8jdk原生nio程序的问题)  


JDK原生也有一套网络应用程序API，但是存在一系列问题，主要如下：

**1、** NIO的类库和API繁杂，使用麻烦，你需要熟练掌握Selector、ServerSocketChannel、SocketChannel、ByteBuffer等

**2、** 需要具备其它的额外技能做铺垫，例如熟悉Java多线程编程，因为NIO编程涉及到Reactor模式，你必须对多线程和网路编程非常熟悉，才能编写出高质量的NIO程序

**3、** 可靠性能力补齐，开发工作量和难度都非常大。例如客户端面临断连重连、网络闪断、半包读写、失败缓存、网络拥塞和异常码流的处理等等，NIO编程的特点是功能开发相对容易，但是可靠性能力补齐工作量和难度都非常大

**4、** JDK NIO的BUG，例如臭名昭著的epoll bug，它会导致Selector空轮询，最终导致CPU 100%。官方声称在JDK1.6版本的update18修复了该问题，但是直到JDK1.7版本该问题仍旧存在，只不过该bug发生概率降低了一些而已，它并没有被根本解决


### [9、Netty 的零拷贝实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#9netty-的零拷贝实现)  


Netty 的接收和发送 ByteBuffer 采用 DIRECT BUFFERS，使用堆外直接内存进行 Socket 读写，不需要进行字节缓冲区的二次拷贝。堆内存多了一次内存拷贝，JVM 会将堆内存Buffer 拷贝一份到直接内存中，然后才写入 Socket 中。ByteBuffer 由 ChannelConfig 分配，而 ChannelConfig 创建 ByteBufAllocator 默认使用 Direct Buffer

CompositeByteBuf 类可以将多个 ByteBuf 合并为一个逻辑上的 ByteBuf, 避免了传统通过内存拷贝的方式将几个小 Buffer 合并成一个大的 Buffer。addComponents 方法将header与 body 合并为一个逻辑上的 ByteBuf, 这两个 ByteBuf 在 CompositeByteBuf 内部都是单独存在的, CompositeByteBuf 只是逻辑上是一个整体。

通过 FileRegion 包装的 FileChannel.tranferTo 方法 实现文件传输, 可以直接将文件缓冲区的数据发送到目标 Channel，避免了传统通过循环 write 方式导致的内存拷贝问题。

通过 wrap 方法, 我们可以将 byte[] 数组、ByteBuf、ByteBuffer 等包装成一个 NettyByteBuf 对象, 进而避免了拷贝操作。

Selector  BUG：若 Selector 的轮询结果为空，也没有 wakeup 或新消息处理，则发生空轮询，CPU 使用率 100%，

Netty 的解决办法：对 Selector 的 select 操作周期进行统计，每完成一次空的 select 操作进行一次计数，若在某个周期内连续发生 N 次空轮询，则触发了 epoll 死循环 bug。重建Selector，判断是否是其他线程发起的重建请求，若不是则将原 SocketChannel 从旧的Selector 上去除注册，重新注册到新的 Selector 上，并将原来的 Selector 关闭。


### [10、Netty 的应用场景有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#10netty-的应用场景有哪些)  


典型的应用有：阿里分布式服务框架 Dubbo，默认使用 Netty 作为基础通信组件，还有 RocketMQ 也是使用 Netty 作为通讯的基础。


### [11、NIO 的组成？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#11nio-的组成)  

### [12、Netty 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#12netty-是什么)  

### [13、Netty 服务端和客户端的启动过程了解么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#13netty-服务端和客户端的启动过程了解么)  

### [14、Netty 发送消息有几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#14netty-发送消息有几种方式)  

### [15、Netty 的可扩展如何体现](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#15netty-的可扩展如何体现)  

### [16、TCP 粘包 / 拆包的产生原因，应该这么解决](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#16tcp-粘包-/-拆包的产生原因应该这么解决)  

### [17、客户端代码](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#17客户端代码)  

### [18、简单解析一下服务端的创建过程具体是怎样的：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#18简单解析一下服务端的创建过程具体是怎样的：)  

### [19、BIO、NIO和AIO的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#19bionio和aio的区别)  

### [20、TCP 粘包/拆包的原因及解决方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#20tcp-粘包/拆包的原因及解决方法)  

### [21、Netty 中的零拷贝体现在几个方面：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#21netty-中的零拷贝体现在几个方面：)  

### [22、NIO的组成？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#22nio的组成)  

### [23、Netty 的特点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#23netty-的特点是什么)  

### [24、Netty 的零拷贝了解么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#24netty-的零拷贝了解么)  

### [25、Netty 应用场景了解么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#25netty-应用场景了解么)  

### [26、如何选择序列化协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#26如何选择序列化协议)  

### [27、了解哪几种序列化协议](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#27了解哪几种序列化协议)  

### [28、Netty 和 Tomcat 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#28netty-和-tomcat-的区别)  

### [29、EventloopGroup 了解么?和 EventLoop 啥关系?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#29eventloopgroup-了解么和-eventloop-啥关系)  

### [30、什么是 Netty 的零拷贝？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#30什么是-netty-的零拷贝)  

### [31、Netty 中有哪种重要组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#31netty-中有哪种重要组件)  

### [32、Netty 的高性能体现在哪方面](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#32netty-的高性能体现在哪方面)  

### [33、Netty 的特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#33netty-的特点)  

### [34、Netty为什么要实现内存管理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Netty/Netty面试题附答案（2021年Netty面试题及答案大汇总）.md#34netty为什么要实现内存管理)  





