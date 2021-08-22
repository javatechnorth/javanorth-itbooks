# ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）

ZooKeeper面试题及答案【最新版】ZooKeeper高级面试题大全(2021版)，发现网上很多ZooKeeper面试题及答案整理都没有答案，所以花了很长时间搜集，本套ZooKeeper面试题大全，ZooKeeper面试题大汇总，有大量经典的ZooKeeper面试题以及答案，包含ZooKeeper语言常见面试题、ZooKeeper工程师高级面试题及一些大厂ZooKeeper开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套ZooKeeper面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个ZooKeeper面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Zookeeper做了什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#1zookeeper做了什么)  


**1、** 命名服务

**2、** 配置管理

**3、** 集群管理

**4、** 分布式锁

**5、** 队列管理


### [2、说几个zookeeper常用的命令。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#2说几个zookeeper常用的命令。)  


常用命令：ls get set create delete等。


### [3、服务器角色](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#3服务器角色)  


**Leader**

**1、** 事务请求的唯一调度和处理者，保证集群事务处理的顺序性

**2、** 集群内部各服务的调度者

**Follower**

**1、** 处理客户端的非事务请求，转发事务请求给Leader服务器

**2、** 参与事务请求Proposal的投票

**3、** 参与Leader选举投票

**Observer**

**1、** 3.0版本以后引入的一个服务器角色，在不影响集群事务处理能力的基础上提升集群的非事务处理能力

**2、** 处理客户端的非事务请求，转发事务请求给Leader服务器

**3、** 不参与任何形式的投票


### [4、ZooKeeper的数据模型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#4zookeeper的数据模型)  


共享的、树形结构，由一系列的 ZNode数据节点组成，类似文件系统(目录不能存数据）。ZNode存有数据信息，如版本号等等。ZNode之间的层级关系，像文件系统中的目录结构一样。并且它是将数据存在内存中，这样可以提高吞吐、减少延迟。


### [5、ACL权限控制机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#5acl权限控制机制)  


UGO（User/Group/Others）

目前在Linux/Unix文件系统中使用，也是使用最广泛的权限控制方式。是一种粗粒度的文件系统权限控制模式。

ACL（Access Control List）访问控制列表

**包括三个方面：**

**权限模式（Scheme）**

**1、** IP：从IP地址粒度进行权限控制

**2、** Digest：最常用，用类似于 username:password 的权限标识来进行权限配置，便于区分不同应用来进行权限控制

**3、** World：最开放的权限控制方式，是一种特殊的digest模式，只有一个权限标识“world:anyone”

**4、** Super：超级用户

**授权对象**

授权对象指的是权限赋予的用户或一个指定实体，例如IP地址或是机器灯。

**权限 Permission**

**1、** CREATE：数据节点创建权限，允许授权对象在该Znode下创建子节点

**2、** DELETE：子节点删除权限，允许授权对象删除该数据节点的子节点

**3、** READ：数据节点的读取权限，允许授权对象访问该数据节点并读取其数据内容或子节点列表等

**4、** WRITE：数据节点更新权限，允许授权对象对该数据节点进行更新操作

**5、** ADMIN：数据节点管理权限，允许授权对象对该数据节点进行ACL相关设置操作


### [6、Zookeeper对节点的watch监听通知是永久的吗？为什么不是永久的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#6zookeeper对节点的watch监听通知是永久的吗为什么不是永久的)  


不是。官方声明：一个Watch事件是一个一次性的触发器，当被设置了Watch的数据发生了改变的时候，则服务器将这个改变发送给设置了Watch的客户端，以便通知它们。

为什么不是永久的，举个例子，如果服务端变动频繁，而监听的客户端很多情况下，每次变动都要通知到所有的客户端，给网络和服务器造成很大压力。

一般是客户端执行getData(“/节点A”,true)，如果节点A发生了变更或删除，客户端会得到它的watch事件，但是在之后节点A又发生了变更，而客户端又没有设置watch事件，就不再给客户端发送。

在实际应用中，很多情况下，我们的客户端不需要知道服务端的每一次变动，我只要最新的数据即可。


### [7、Zookeeper 有哪几种几种部署模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#7zookeeper-有哪几种几种部署模式)  


**Zookeeper 有三种部署模式**：

**1、** 单机部署：一台集群上运行；

**2、** 集群部署：多台集群运行；

**3、** 伪集群部署：一台集群启动多个 Zookeeper 实例运行。


### [8、服务端处理Watcher实现](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#8服务端处理watcher实现)  


**1、** 服务端接收Watcher并存储

接收到客户端请求，处理请求判断是否需要注册Watcher，需要的话将数据节点的节点路径和ServerCnxn（ServerCnxn代表一个客户端和服务端的连接，实现了Watcher的process接口，此时可以看成一个Watcher对象）存储在WatcherManager的WatchTable和watch2Paths中去。

**2、** Watcher触发

以服务端接收到 setData() 事务请求触发NodeDataChanged事件为例：

2.1 封装WatchedEvent

将通知状态（SyncConnected）、事件类型（NodeDataChanged）以及节点路径封装成一个WatchedEvent对象

2.2 查询Watcher

从WatchTable中根据节点路径查找Watcher

2.3 没找到；说明没有客户端在该数据节点上注册过Watcher

2.4 找到；提取并从WatchTable和Watch2Paths中删除对应Watcher（从这里可以看出Watcher在服务端是一次性的，触发一次就失效了）

**3、** 调用process方法来触发Watcher

这里process主要就是通过ServerCnxn对应的TCP连接发送Watcher事件通知。


### [9、ACL 权限控制机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#9acl-权限控制机制)  


**1、** UGO（User/Group/Others）

**2、** 目前在 Linux/Unix 文件系统中使用，也是使用最广泛的权限控制方式。是一种粗粒度的文件系统权限控制模式。

**3、** ACL（Access Control List）访问控制列表

**包括三个方面：**

**权限模式（Scheme）**

**1、** IP：从 IP 地址粒度进行权限控制

**2、** Digest：最常用，用类似于 username:password 的权限标识来进行权限配置，便于区分不同应用来进行权限控制

**3、** World：最开放的权限控制方式，是一种特殊的 digest 模式，只有一个权限标识“world:anyone”

**4、** Super：超级用户

**授权对象** 授权对象指的是权限赋予的用户或一个指定实体，例如 IP 地址或是机器灯。

**权限 Permission**

**1、** CREATE：数据节点创建权限，允许授权对象在该 Znode 下创建子节点

**2、** DELETE：子节点删除权限，允许授权对象删除该数据节点的子节点

**3、** READ：数据节点的读取权限，允许授权对象访问该数据节点并读取其数据内容或子节点列表等

**4、** WRITE：数据节点更新权限，允许授权对象对该数据节点进行更新操作

**5、** ADMIN：数据节点管理权限，允许授权对象对该数据节点进行 ACL 相关设置操作


### [10、Zookeeper工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#10zookeeper工作原理)  


Zookeeper 的核心是原子广播，这个机制保证了各个Server之间的同步。实现这个机制的协议叫做Zab协议。Zab协议有两种模式，它们分别是恢复模式（选主）和广播模式（同步）。当服务启动或者在领导者崩溃后，Zab就进入了恢复模式，当领导者被选举出来，且大多数Server完成了和 leader的状态同步以后，恢复模式就结束了。状态同步保证了leader和Server具有相同的系统状态。


### [11、集群最少要几台机器，集群规则是怎样的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#11集群最少要几台机器集群规则是怎样的)  

### [12、客户端注册Watcher实现](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#12客户端注册watcher实现)  

### [13、ZooKeeper可以保证哪些分布式一致性特性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#13zookeeper可以保证哪些分布式一致性特性)  

### [14、客户端回调 Watcher](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#14客户端回调-watcher)  

### [15、Zookeeper队列管理（文件系统、通知机制）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#15zookeeper队列管理文件系统通知机制)  

### [16、zk的配置管理（文件系统、通知机制）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#16zk的配置管理文件系统通知机制)  

### [17、Zookeeper有哪几种几种部署模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#17zookeeper有哪几种几种部署模式)  

### [18、ZAB三个阶段？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#18zab三个阶段)  

### [19、服务器角色](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#19服务器角色)  

### [20、如何创建一个ZNode?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#20如何创建一个znode)  

### [21、四种类型的数据节点 Znode](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#21四种类型的数据节点-znode)  

### [22、zk 节点宕机如何处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#22zk-节点宕机如何处理)  

### [23、分布式通知和协调](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#23分布式通知和协调)  

### [24、BASE理论？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#24base理论)  

### [25、恢复模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#25恢复模式)  

### [26、获取指定节点信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#26获取指定节点信息)  

### [27、负载均衡](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#27负载均衡)  

### [28、A是根节点，如何表达A子节点下的B节点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#28a是根节点如何表达a子节点下的b节点)  

### [29、CAP理论？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#29cap理论)  

### [30、ZooKeeper 提供了什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#30zookeeper-提供了什么)  

### [31、数据同步](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题带答案（2021年ZooKeeper面试题及答案大汇总）.md#31数据同步)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
