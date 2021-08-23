# ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）

ZooKeeper面试题及答案【最新版】ZooKeeper高级面试题大全(2021版)，发现网上很多ZooKeeper面试题及答案整理都没有答案，所以花了很长时间搜集，本套ZooKeeper面试题大全，ZooKeeper面试题大汇总，有大量经典的ZooKeeper面试题以及答案，包含ZooKeeper语言常见面试题、ZooKeeper工程师高级面试题及一些大厂ZooKeeper开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套ZooKeeper面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个ZooKeeper面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、四种类型的znode](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#1四种类型的znode)  


**1、** PERSISTENT-持久化目录节点

客户端与zookeeper断开连接后，该节点依旧存在

**2、** PERSISTENT_SEQUENTIAL-持久化顺序编号目录节点

客户端与zookeeper断开连接后，该节点依旧存在，只是Zookeeper给该节点名称进行顺序编号

**3、** EPHEMERAL-临时目录节点

客户端与zookeeper断开连接后，该节点被删除

**4、** EPHEMERAL_SEQUENTIAL-临时顺序编号目录节点

客户端与zookeeper断开连接后，该节点被删除，只是Zookeeper给该节点名称进行顺序编号

![](https://segmentfault.com/img/bV8Xel?w=371&h=463#alt=clipboard.png)


### [2、Zookeeper的典型应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#2zookeeper的典型应用场景)  


Zookeeper是一个典型的发布/订阅模式的分布式数据管理与协调框架，开发人员可以使用它来进行分布式数据的发布和订阅。

通过对Zookeeper中丰富的数据节点进行交叉使用，配合Watcher事件通知机制，可以非常方便的构建一系列分布式应用中年都会涉及的核心功能，如：

**1、** 数据发布/订阅

**2、** 负载均衡

**3、** 命名服务

**4、** 分布式协调/通知

**5、** 集群管理

**6、** Master选举

**7、** 分布式锁

**8、** 分布式队列

**数据发布/订阅**

**介绍**

数据发布/订阅系统，即所谓的配置中心，顾名思义就是发布者发布数据供订阅者进行数据订阅。

**目的**

**1、** 动态获取数据（配置信息）

**2、** 实现数据（配置信息）的集中式管理和数据的动态更新

设计模式

**1、** Push 模式

**2、** Pull 模式

**数据（配置信息）特性**

**1、** 数据量通常比较小

**2、** 数据内容在运行时会发生动态更新

**3、** 集群中各机器共享，配置一致

如：机器列表信息、运行时开关配置、数据库配置信息等

**基于Zookeeper的实现方式**

**1、** 数据存储：将数据（配置信息）存储到Zookeeper上的一个数据节点

**2、** 数据获取：应用在启动初始化节点从Zookeeper数据节点读取数据，并在该节点上注册一个数据变更Watcher

**3、** 数据变更：当变更数据时，更新Zookeeper对应节点数据，Zookeeper会将数据变更通知发到各客户端，客户端接到通知后重新读取变更后的数据即可。

**负载均衡**

**zk的命名服务**

命名服务是指通过指定的名字来获取资源或者服务的地址，利用zk创建一个全局的路径，这个路径就可以作为一个名字，指向集群中的集群，提供的服务的地址，或者一个远程的对象等等。

**分布式通知和协调**

对于系统调度来说：操作人员发送通知实际是通过控制台改变某个节点的状态，然后zk将这些变化发送给注册了这个节点的watcher的所有客户端。

对于执行情况汇报：每个工作进程都在某个目录下创建一个临时节点。并携带工作的进度数据，这样汇总的进程可以监控目录子节点的变化获得工作进度的实时的全局情况。

**zk的命名服务（文件系统）**

命名服务是指通过指定的名字来获取资源或者服务的地址，利用zk创建一个全局的路径，即是唯一的路径，这个路径就可以作为一个名字，指向集群中的集群，提供的服务的地址，或者一个远程的对象等等。

**zk的配置管理（文件系统、通知机制）**

程序分布式的部署在不同的机器上，将程序的配置信息放在zk的znode下，当有配置发生改变时，也就是znode发生变化时，可以通过改变zk中某个目录节点的内容，利用watcher通知给各个客户端，从而更改配置。

**Zookeeper集群管理（文件系统、通知机制）**

所谓集群管理无在乎两点：是否有机器退出和加入、选举master。

对于第一点，所有机器约定在父目录下创建临时目录节点，然后监听父目录节点的子节点变化消息。一旦有机器挂掉，该机器与 zookeeper的连接断开，其所创建的临时目录节点被删除，所有其他机器都收到通知：某个兄弟目录被删除，于是，所有人都知道：它上船了。

新机器加入也是类似，所有机器收到通知：新兄弟目录加入，highcount又有了，对于第二点，我们稍微改变一下，所有机器创建临时顺序编号目录节点，每次选取编号最小的机器作为master就好。

**Zookeeper分布式锁（文件系统、通知机制）**

有了zookeeper的一致性文件系统，锁的问题变得容易。锁服务可以分为两类，一个是保持独占，另一个是控制时序。

对于第一类，我们将zookeeper上的一个znode看作是一把锁，通过createznode的方式来实现。所有客户端都去创建 /distribute_lock 节点，最终成功创建的那个客户端也即拥有了这把锁。用完删除掉自己创建的distribute_lock 节点就释放出锁。

对于第二类， /distribute_lock 已经预先存在，所有客户端在它下面创建临时顺序编号目录节点，和选master一样，编号最小的获得锁，用完删除，依次方便。

**Zookeeper队列管理（文件系统、通知机制）**

**两种类型的队列：**

**1、** 同步队列，当一个队列的成员都聚齐时，这个队列才可用，否则一直等待所有成员到达。

**2、** 队列按照 FIFO 方式进行入队和出队操作。

第一类，在约定目录下创建临时目录节点，监听节点数目是否是我们要求的数目。

第二类，和分布式锁服务中的控制时序场景基本原理一致，入列有编号，出列按编号。在特定的目录下创建PERSISTENT_SEQUENTIAL节点，创建成功时Watcher通知等待的队列，队列删除序列号最小的节点用以消费。此场景下Zookeeper的znode用于消息存储，znode存储的数据就是消息队列中的消息内容，SEQUENTIAL序列号就是消息的编号，按序取出即可。由于创建的节点是持久化的，所以不必担心队列消息的丢失问题。


### [3、Zookeeper 的典型应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#3zookeeper-的典型应用场景)  


Zookeeper 是一个典型的发布/订阅模式的分布式数据管理与协调框架，开发人员可以使用它来进行分布式数据的发布和订阅。

通过对 Zookeeper 中丰富的数据节点进行交叉使用，配合 Watcher 事件通知机制，可以非常方便的构建一系列分布式应用中年都会涉及的核心功能，如：

**1、** 数据发布/订阅

**2、** 负载均衡

**3、** 命名服务

**4、** 分布式协调/通知

**5、** 集群管理

**6、** Master 选举

**7、** 分布式锁

**8、** 分布式队列

#
### [4、zk的命名服务（文件系统）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#4zk的命名服务文件系统)  


命名服务是指通过指定的名字来获取资源或者服务的地址，利用zk创建一个全局的路径，即是唯一的路径，这个路径就可以作为一个名字，指向集群中的集群，提供的服务的地址，或者一个远程的对象等等。


### [5、Zookeeper文件系统](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#5zookeeper文件系统)  


Zookeeper提供一个多层级的节点命名空间（节点称为znode）。与文件系统不同的是，这些节点都可以设置关联的数据，而文件系统中只有文件节点可以存放数据而目录节点不行。Zookeeper为了保证高吞吐和低延迟，在内存中维护了这个树状的目录结构，这种特性使得Zookeeper不能用于存放大量的数据，每个节点的存放数据上限为1M。


### [6、Zookeeper 和 Dubbo 的关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#6zookeeper-和-dubbo-的关系)  


**Zookeeper的作用：**

zookeeper用来注册服务和进行负载均衡，哪一个服务由哪一个机器来提供必需让调用者知道，简单来说就是ip地址和服务名称的对应关系。当然也可以通过硬编码的方式把这种对应关系在调用方业务代码中实现，但是如果提供服务的机器挂掉调用者无法知晓，如果不更改代码会继续请求挂掉的机器提供服务。zookeeper通过心跳机制可以检测挂掉的机器并将挂掉机器的ip和服务对应关系从列表中删除。至于支持高并发，简单来说就是横向扩展，在不更改代码的情况通过添加机器来提高运算能力。通过添加新的机器向zookeeper注册服务，服务的提供者多了能服务的客户就多了。

**dubbo：**

dubbo是管理中间层的工具，在业务层到数据仓库间有非常多服务的接入和服务提供者需要调度，dubbo提供一个框架解决这个问题。

注意这里的dubbo只是一个框架，至于你架子上放什么是完全取决于你的，就像一个汽车骨架，你需要配你的轮子引擎。这个框架中要完成调度必须要有一个分布式的注册中心，储存所有服务的元数据，你可以用zk，也可以用别的，只是大家都用zk。

**zookeeper和dubbo的关系：**

Dubbo 的将注册中心进行抽象，它可以外接不同的存储媒介给注册中心提供服务，有 ZooKeeper，Memcached，Redis 等。

引入了 ZooKeeper 作为存储媒介，也就把 ZooKeeper 的特性引进来。首先是负载均衡，单注册中心的承载能力是有限的，在流量达到一定程度的时 候就需要分流，负载均衡就是为了分流而存在的，一个 ZooKeeper 群配合相应的 Web 应用就可以很容易达到负载均衡；资源同步，单单有负载均衡还不 够，节点之间的数据和资源需要同步，ZooKeeper 集群就天然具备有这样的功能；命名服务，将树状结构用于维护全局的服务地址列表，服务提供者在启动 的时候，向 ZooKeeper 上的指定节点 /dubbo/${serviceName}/providers 目录下写入自己的 URL 地址，这个操作就完成了服务的发布。 其他特性还有 Mast 选举，分布式锁等。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/052/19/71_2.png#alt=71%5C_2.png)


### [7、ZooKeeper是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#7zookeeper是什么)  


**1、** ZooKeeper是一个分布式的，开放源码的分布式应用程序协调服务，是Google的Chubby一个开源的实现，它是集群的管理者，监视着集群中各个节点的状态根据节点提交的反馈进行下一步合理操作。最终，将简单易用的接口和性能高效、功能稳定的系统提供给用户。

**2、** 客户端的读请求可以被集群中的任意一台机器处理，如果读请求在节点上注册了监听器，这个监听器也是由所连接的zookeeper机器来处理。对于写请求，这些请求会同时发给其他zookeeper机器并且达成一致后，请求才会返回成功。因此，随着zookeeper的集群机器增多，读请求的吞吐会提高但是写请求的吞吐会下降。

**3、** 有序性是zookeeper中非常重要的一个特性，所有的更新都是全局有序的，每个更新都有一个唯一的时间戳，这个时间戳称为zxid（Zookeeper Transaction Id）。而读请求只会相对于更新有序，也就是读请求的返回结果中会带有这个zookeeper最新的zxid。


### [8、Zookeeper集群管理（文件系统、通知机制）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#8zookeeper集群管理文件系统通知机制)  


**1、** 所谓集群管理无在乎两点：是否有机器退出和加入、选举master。

**2、** 对于第一点，所有机器约定在父目录下创建临时目录节点，然后监听父目录节点的子节点变化消息。一旦有机器挂掉，该机器与 zookeeper的连接断开，其所创建的临时目录节点被删除，所有其他机器都收到通知：某个兄弟目录被删除，于是，所有人都知道：它上船了。

**3、** 新机器加入也是类似，所有机器收到通知：新兄弟目录加入，highcount又有了，对于第二点，我们稍微改变一下，所有机器创建临时顺序编号目录节点，每次选取编号最小的机器作为master就好。


### [9、Zookeeper 文件系统](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#9zookeeper-文件系统)  


Zookeeper 提供一个多层级的节点命名空间（节点称为 znode）。与文件系统不同的是，这些节点都可以设置关联的数据，而文件系统中只有文件节点可以存放数据而目录节点不行。

Zookeeper 为了保证高吞吐和低延迟，在内存中维护了这个树状的目录结构，这种特性使得 Zookeeper 不能用于存放大量的数据，每个节点的存放数据上限为1M。


### [10、Chroot特性](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#10chroot特性)  


3.2.0版本后，添加了 Chroot特性，该特性允许每个客户端为自己设置一个命名空间。如果一个客户端设置了Chroot，那么该客户端对服务器的任何操作，都将会被限制在其自己的命名空间下。

通过设置Chroot，能够将一个客户端应用于Zookeeper服务端的一颗子树相对应，在那些多个应用公用一个Zookeeper进群的场景下，对实现不同应用间的相互隔离非常有帮助。


### [11、服务器的3中角色？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#11服务器的3中角色)  

### [12、客户端注册 Watcher 实现](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#12客户端注册-watcher-实现)  

### [13、Zookeeper 的 java 客户端都有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#13zookeeper-的-java-客户端都有哪些)  

### [14、Zookeeper 专门设计的一种支持崩溃恢复的原子广 播协议是?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#14zookeeper-专门设计的一种支持崩溃恢复的原子广-播协议是)  

### [15、Zookeeper Watcher 机制 -- 数据变更通知](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#15zookeeper-watcher-机制----数据变更通知)  

### [16、说一下 Zookeeper 的通知机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#16说一下-zookeeper-的通知机制)  

### [17、数据发布/订阅](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#17数据发布/订阅)  

### [18、Zookeeper通知机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#18zookeeper通知机制)  

### [19、为什么叫ZooKeeper?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#19为什么叫zookeeper)  

### [20、zk节点宕机如何处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#20zk节点宕机如何处理)  

### [21、zookeeper是如何保证事务的顺序一致性的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#21zookeeper是如何保证事务的顺序一致性的)  

### [22、什么是会话Session?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#22什么是会话session)  

### [23、ZooKeeper 面试题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#23zookeeper-面试题)  

### [24、如何查看子节点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#24如何查看子节点)  

### [25、说几个 zookeeper 常用的命令。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#25说几个-zookeeper-常用的命令。)  

### [26、客户端如何获取配置信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#26客户端如何获取配置信息)  

### [27、Zookeeper 下 Server工作状态](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#27zookeeper-下-server工作状态)  

### [28、几种部署方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#28几种部署方式)  

### [29、ZooKeeper提供了什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#29zookeeper提供了什么)  

### [30、zookeeper 是如何保证事务的顺序一致性的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题附答案（2021年ZooKeeper面试题及答案大汇总）.md#30zookeeper-是如何保证事务的顺序一致性的)  





