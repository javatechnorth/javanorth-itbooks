# ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）

ZooKeeper面试题及答案【最新版】ZooKeeper高级面试题大全(2021版)，发现网上很多ZooKeeper面试题及答案整理都没有答案，所以花了很长时间搜集，本套ZooKeeper面试题大全，ZooKeeper面试题大汇总，有大量经典的ZooKeeper面试题以及答案，包含ZooKeeper语言常见面试题、ZooKeeper工程师高级面试题及一些大厂ZooKeeper开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套ZooKeeper面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个ZooKeeper面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、分布式集群中为什么会有Master？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#1分布式集群中为什么会有master)  


在分布式环境中，有些业务逻辑只需要集群中的某一台机器进行执行，其他的机器可以共享这个结果，这样可以大大减少重复计算，提高性能，于是就需要进行leader选举。


### [2、会话管理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#2会话管理)  


分桶策略：将类似的会话放在同一区块中进行管理，以便于Zookeeper对会话进行不同区块的隔离处理以及同一区块的统一处理。

分配原则：每个会话的“下次超时时间点”（ExpirationTime）

**计算公式：**

```
ExpirationTime_ = currentTime + sessionTimeout
ExpirationTime = (ExpirationTime_ / ExpirationInrerval + 1) * ExpirationInterval , ExpirationInterval 是指 Zookeeper 会话超时检查时间间隔，默认 tickTime
```


### [3、四种类型的数据节点 Znode](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#3四种类型的数据节点-znode)  


**1、** PERSISTENT-持久节点

除非手动删除，否则节点一直存在于Zookeeper上

**2、** EPHEMERAL-临时节点

临时节点的生命周期与客户端会话绑定，一旦客户端会话失效（客户端与zookeeper连接断开不一定会话失效），那么这个客户端创建的所有临时节点都会被移除。

**3、** PERSISTENT_SEQUENTIAL-持久顺序节点

基本特性同持久节点，只是增加了顺序属性，节点名后边会追加一个由父节点维护的自增整型数字。

**4、** EPHEMERAL_SEQUENTIAL-临时顺序节点

基本特性同临时节点，增加了顺序属性，节点名后边会追加一个由父节点维护的自增整型数字。


### [4、获取分布式锁的流程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#4获取分布式锁的流程)  


![](https://segmentfault.com/img/bV8WZ1?w=605&h=483#alt=clipboard.png)

**1、** 在获取分布式锁的时候在locker节点下创建临时顺序节点，释放锁的时候删除该临时节点。客户端调用createNode方法在locker下创建临时顺序节点，

**2、** 然后调用getChildren(“locker”)来获取locker下面的所有子节点，注意此时不用设置任何Watcher。客户端获取到所有的子节点path之后，如果发现自己创建的节点在所有创建的子节点序号最小，那么就认为该客户端获取到了锁。如果发现自己创建的节点并非locker所有子节点中最小的，说明自己还没有获取到锁，此时客户端需要找到比自己小的那个节点，然后对其调用exist()方法，同时对其注册事件监听器。之后，让这个被关注的节点删除，则客户端的Watcher会收到相应通知，此时再次判断自己创建的节点是否是locker子节点中序号最小的，如果是则获取到了锁，如果不是则重复以上步骤继续获取到比自己小的一个节点并注册监听。当前这个过程中还需要许多的逻辑判断。

![](https://segmentfault.com/img/bV8WVn?w=665&h=355#alt=clipboard.png)

代码的实现主要是基于互斥锁，获取分布式锁的重点逻辑在于BaseDistributedLock，实现了基于Zookeeper实现分布式锁的细节。


### [5、删除指定节点？注意？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#5删除指定节点注意)  


delete path [version]

[zk: localhost:2181(CONNECTED) 8] delete /app

Node not empty: /app

如果没有子节点，就能删除成功。如果有会提示，该节点不为空。


### [6、Zookeeper Watcher 机制 – 数据变更通知](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#6zookeeper-watcher-机制-–-数据变更通知)  


Zookeeper 允许客户端向服务端的某个 Znode 注册一个 Watcher 监听，当服务端的一些指定事件触发了这个 Watcher，服务端会向指定客户端发送一个事件通知来实现分布式的通知功能，然后客户端根据 Watcher 通知状态和事件类型做出业务上的改变。

**工作机制：**

**1、** 客户端注册 watcher

**2、** 服务端处理 watcher

**3、** 客户端回调 watcher


### [7、ZAB协议？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#7zab协议)  


ZAB协议是为分布式协调服务Zookeeper专门设计的一种支持崩溃恢复的原子广播协议。

ZAB协议包括两种基本的模式：崩溃恢复和消息广播。

当整个zookeeper集群刚刚启动或者Leader服务器宕机、重启或者网络故障导致不存在过半的服务器与Leader服务器保持正常通信时，所有进程（服务器）进入崩溃恢复模式，首先选举产生新的Leader服务器，然后集群中Follower服务器开始与新的Leader服务器进行数据同步，当集群中超过半数机器与该Leader服务器完成数据同步之后，退出恢复模式进入消息广播模式，Leader服务器开始接收客户端的事务请求生成事物提案来进行事务请求处理。


### [8、zk节点宕机如何处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#8zk节点宕机如何处理)  


Zookeeper本身也是集群，推荐配置不少于3个服务器。Zookeeper自身也要保证当一个节点宕机时，其他节点会继续提供服务。

如果是一个Follower宕机，还有2台服务器提供访问，因为Zookeeper上的数据是有多个副本的，数据并不会丢失；

如果是一个Leader宕机，Zookeeper会选举出新的Leader。

ZK集群的机制是只要超过半数的节点正常，集群就能正常提供服务。只有在ZK节点挂得太多，只剩一半或不到一半节点能工作，集群才失效。

所以

3个节点的cluster可以挂掉1个节点(leader可以得到2票>1.5)

2个节点的cluster就不能挂掉任何1个节点了(leader可以得到1票<=1)


### [9、服务端处理 Watcher 实现](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#9服务端处理-watcher-实现)  


**1、** 服务端接收 Watcher 并存储 接收到客户端请求，处理请求判断是否需要注册 Watcher，需要的话将数据节点的节点路径和 ServerCnxn（ServerCnxn 代表一个客户端和服务端的连接，实现了 Watcher 的 process 接口，此时可以看成一个 Watcher 对象）存储在WatcherManager 的 WatchTable 和 watch2Paths 中去。

**2、** Watcher 触发 以服务端接收到 setData() 事务请求触发 NodeDataChanged 事件为例：

2.1 封装 WatchedEvent 将通知状态（SyncConnected）、事件类型（NodeDataChanged）以及节点路径封装成一个 WatchedEvent 对象

2.2 查询 Watcher 从 WatchTable 中根据节点路径查找 Watcher

2.3 没找到；说明没有客户端在该数据节点上注册过 Watcher

2.4 找到；提取并从 WatchTable 和 Watch2Paths 中删除对应 Watcher（从这里可以看出 Watcher 在服务端是一次性的，触发一次就失效了）

**3、**  调用 process 方法来触发 Watcher 这里 process 主要就是通过 ServerCnxn 对应的 TCP 连接发送 Watcher 事件通知。


### [10、在sessionTimeout之内的会话，因服务器压力大、网络故障或客户端主动断开情况下，之前的会话还有效吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#10在sessiontimeout之内的会话因服务器压力大网络故障或客户端主动断开情况下之前的会话还有效吗)  


有效。


### [11、zookeeper watch机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#11zookeeper-watch机制)  

### [12、更新指定节点信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#12更新指定节点信息)  

### [13、哪些情况会导致ZAB进入恢复模式并选取新的Leader?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#13哪些情况会导致zab进入恢复模式并选取新的leader)  

### [14、ZAB的两种基本模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#14zab的两种基本模式)  

### [15、广播模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#15广播模式)  

### [16、集群最少要几台机器，集群规则是怎样的？集群中有 3 台服务器，其中一个节点宕机，这个时候 Zookeeper 还可以使用吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#16集群最少要几台机器集群规则是怎样的集群中有-3-台服务器其中一个节点宕机这个时候-zookeeper-还可以使用吗)  

### [17、ZAB 和 Paxos 算法的联系与区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#17zab-和-paxos-算法的联系与区别)  

### [18、Zookeeper分布式锁（文件系统、通知机制）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#18zookeeper分布式锁文件系统通知机制)  

### [19、chubby 是什么，和 zookeeper 比你怎么看？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#19chubby-是什么和-zookeeper-比你怎么看)  

### [20、Zookeeper 下 Server工作状态](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#20zookeeper-下-server工作状态)  

### [21、发布订阅的两种设计模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#21发布订阅的两种设计模式)  

### [22、会话管理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#22会话管理)  

### [23、Zookeeper 对节点的 watch 监听通知是永久的吗？为什么不是永久的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#23zookeeper-对节点的-watch-监听通知是永久的吗为什么不是永久的)  

### [24、分布式集群中为什么会有 Master主节点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#24分布式集群中为什么会有-master主节点)  

### [25、ZNode的类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#25znode的类型)  

### [26、同进程组的两个进程消息网络通信有哪两个特性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#26同进程组的两个进程消息网络通信有哪两个特性)  

### [27、ZooKeeper定义了几种权限？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#27zookeeper定义了几种权限)  

### [28、Stat记录了哪些版本相关数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#28stat记录了哪些版本相关数据)  

### [29、Zookeeper 下 Server 工作状态](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#29zookeeper-下-server-工作状态)  

### [30、zookeeper是如何保证事务的顺序一致性的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper中级面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#30zookeeper是如何保证事务的顺序一致性的)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
