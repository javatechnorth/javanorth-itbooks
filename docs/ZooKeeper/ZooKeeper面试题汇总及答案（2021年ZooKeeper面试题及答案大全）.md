# ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）

ZooKeeper面试题及答案【最新版】ZooKeeper高级面试题大全(2021版)，发现网上很多ZooKeeper面试题及答案整理都没有答案，所以花了很长时间搜集，本套ZooKeeper面试题大全，ZooKeeper面试题大汇总，有大量经典的ZooKeeper面试题以及答案，包含ZooKeeper语言常见面试题、ZooKeeper工程师高级面试题及一些大厂ZooKeeper开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套ZooKeeper面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个ZooKeeper面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、ZooKeeper用推/拉模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#1zookeeper用推/拉模式)  


推拉结合


### [2、集群角色？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#2集群角色)  


Leader、Follower、Observer


### [3、Zookeeper 怎么保证主从节点的状态同步？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#3zookeeper-怎么保证主从节点的状态同步)  


Zookeeper 的核心是原子广播机制，这个机制保证了各个 server 之间的同步。实现这个机制的协议叫做 Zab 协议。Zab 协议有两种模式，它们分别是恢复模式和广播模式。


### 4、发现?

Follower把自己最后的接受事务的Proposal值(CEPOCH(F.p)发送给Leader。

当收到过半Follower的消息后，Leader生成NEWEPOCH(e')给这些过半的Follower。

tips: e' = Max((CEPOCH(F.p)) + 1

Follower收到消息后，如果自己值小于e',则同步e'的值，同时向Leader发Ack消息。


### [5、zookeeper 负载均衡和 nginx 负载均衡区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#5zookeeper-负载均衡和-nginx-负载均衡区别)  


zk 的负载均衡是可以调控，nginx 只是能调权重，其他需要可控的都需要自己写插件；但是 nginx 的吞吐量比 zk 大很多，应该说按业务选择用哪种方式。


### [6、权限控制?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#6权限控制)  


Access Control Lists ,ACL。类似于UNIX文件系统的权限控制。


### [7、zookeeper是如何选取主leader的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#7zookeeper是如何选取主leader的)  


当leader崩溃或者leader失去大多数的follower，这时zk进入恢复模式，恢复模式需要重新选举出一个新的leader，让所有的Server都恢复到一个正确的状态。Zk的选举算法有两种：一种是基于basic paxos实现的，另外一种是基于fast paxos算法实现的。系统默认的选举算法为fast paxos。

**Zookeeper选主流程(basic paxos)**

**1、** 选举线程由当前Server发起选举的线程担任，其主要功能是对投票结果进行统计，并选出推荐的Server；

**2、** 选举线程首先向所有Server发起一次询问(包括自己)；

**3、** 选举线程收到回复后，验证是否是自己发起的询问(验证zxid是否一致)，然后获取对方的id(myid)，并存储到当前询问对象列表中，最后获取对方提议的leader相关信息(id,zxid)，并将这些信息存储到当次选举的投票记录表中；

**4、** 收到所有Server回复以后，就计算出zxid最大的那个Server，并将这个Server相关信息设置成下一次要投票的Server；

**5、** 线程将当前zxid最大的Server设置为当前Server要推荐的Leader，如果此时获胜的Server获得n/2 + 1的Server票数，设置当前推荐的leader为获胜的Server，将根据获胜的Server相关信息设置自己的状态，否则，继续这个过程，直到leader被选举出来。 通过流程分析我们可以得出：要使Leader获得多数Server的支持，则Server总数必须是奇数2n+1，且存活的Server的数目不得少于n+1\、每个Server启动后都会重复以上流程。在恢复模式下，如果是刚从崩溃状态恢复的或者刚启动的server还会从磁盘快照中恢复数据和会话信息，zk会记录事务日志并定期进行快照，方便在恢复时进行状态恢复。

![](https://segmentfault.com/img/bV8XeP?w=357&h=791#alt=clipboard.png)

**Zookeeper选主流程(basic paxos)**

fast paxos流程是在选举过程中，某Server首先向所有Server提议自己要成为leader，当其它Server收到提议以后，解决epoch和 zxid的冲突，并接受对方的提议，然后向对方发送接受提议完成的消息，重复这个流程，最后一定能选举出Leader。

![](https://segmentfault.com/img/bV8XeR?w=533&h=451#alt=clipboard.png)


### [8、zookeeper负载均衡和nginx负载均衡区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#8zookeeper负载均衡和nginx负载均衡区别)  


zk的负载均衡是可以调控，nginx只是能调权重，其他需要可控的都需要自己写插件；但是nginx的吞吐量比zk大很多，应该说按业务选择用哪种方式。


### [9、ZooKeeper 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#9zookeeper-是什么)  


**1、** ZooKeeper 是一个开源的分布式协调服务。它是一个为分布式应用提供一致性服务的软件，分布式应用程序可以基于 Zookeeper 实现诸如数据发布/订阅、负载均衡、命名服务、分布式协调/通知、集群管理、Master 选举、分布式锁和分布式队列等功能。

**2、** ZooKeeper 的目标就是封装好复杂易出错的关键服务，将简单易用的接口和性能高效、功能稳定的系统提供给用户。

**Zookeeper 保证了如下分布式一致性特性：**

**1、** 顺序一致性

**2、** 原子性

**3、** 单一视图

**4、** 可靠性

**5、** 实时性（最终一致性）

客户端的读请求可以被集群中的任意一台机器处理，如果读请求在节点上注册了监听器，这个监听器也是由所连接的 zookeeper 机器来处理。对于写请求，这些请求会同时发给其他 zookeeper 机器并且达成一致后，请求才会返回成功。因此，随着 zookeeper 的集群机器增多，读请求的吞吐会提高但是写请求的吞吐会下降。

有序性是 zookeeper 中非常重要的一个特性，所有的更新都是全局有序的，每个更新都有一个唯一的时间戳，这个时间戳称为 zxid（Zookeeper Transaction Id）。而读请求只会相对于更新有序，也就是读请求的返回结果中会带有这个zookeeper 最新的 zxid。


### [10、数据同步](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#10数据同步)  


整个集群完成 Leader 选举之后，Learner（Follower 和 Observer 的统称）回向Leader 服务器进行注册。当 Learner 服务器想 Leader 服务器完成注册后，进入数据同步环节。

**数据同步流程：**（均以消息传递的方式进行）

**1、** Learner 向 Learder 注册

**2、** 数据同步

**3、** 同步确认

**Zookeeper 的数据同步通常分为四类：**

**1、** 直接差异化同步（DIFF 同步）

**2、** 先回滚再差异化同步（TRUNC+DIFF 同步）

**3、** 仅回滚同步（TRUNC 同步）

**4、** 全量同步（SNAP 同步）

**在进行数据同步前，Leader服务器会完成数据同步初始化：**

**1、** peerLastZxid：从learner服务器注册时发送的ACKEPOCH消息中提取lastZxid（该Learner服务器最后处理的ZXID）

**2、** minCommittedLog：Leader服务器Proposal缓存队列committedLog中最小ZXID

**3、** maxCommittedLog：Leader服务器Proposal缓存队列committedLog中最大ZXID

**4、** 直接差异化同步（DIFF同步） 场景：peerLastZxid介于minCommittedLog和maxCommittedLog之间

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/052/19/71_1.png#alt=71%5C_1.png)

**先回滚再差异化同步（TRUNC+DIFF同步）**

场景：当新的Leader服务器发现某个Learner服务器包含了一条自己没有的事务记录，那么就需要让该Learner服务器进行事务回滚--回滚到Leader服务器上存在的，同时也是最接近于peerLastZxid的ZXID

**仅回滚同步（TRUNC同步）**

场景：peerLastZxid 大于 maxCommittedLog

**全量同步（SNAP同步）**

场景一：peerLastZxid 小于 minCommittedLog

场景二：Leader服务器上没有Proposal缓存队列且peerLastZxid不等于lastProcessZxid


### [11、Zookeeper的java客户端都有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#11zookeeper的java客户端都有哪些)  

### [12、机器中为什么会有leader？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#12机器中为什么会有leader)  

### [13、Zookeeper同步流程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#13zookeeper同步流程)  

### [14、ZooKeeper可以实现哪些功能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#14zookeeper可以实现哪些功能)  

### [15、什么是ZooKeeper?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#15什么是zookeeper)  

### [16、chubby是什么，和zookeeper比你怎么看？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#16chubby是什么和zookeeper比你怎么看)  

### [17、Zookeeper 都有哪些功能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#17zookeeper-都有哪些功能)  

### [18、Zookeeper数据复制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#18zookeeper数据复制)  

### [19、ZAB和Paxos算法的联系与区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#19zab和paxos算法的联系与区别)  

### [20、Chroot 特性](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#20chroot-特性)  

### [21、Zookeeper文件系统](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#21zookeeper文件系统)  

### [22、集群支持动态添加机器吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#22集群支持动态添加机器吗)  

### [23、客户端回调Watcher](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#23客户端回调watcher)  

### [24、Zookeeper默认端口？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#24zookeeper默认端口)  

### [25、集群支持动态添加机器吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#25集群支持动态添加机器吗)  

### [26、数据发布/订阅？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#26数据发布/订阅)  

### [27、如何识别请求的先后顺序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#27如何识别请求的先后顺序)  

### [28、Watcher事件监听器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#28watcher事件监听器)  

### [29、Quorum?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#29quorum)  

### [30、Watcher 特性总结](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/ZooKeeper/ZooKeeper面试题汇总及答案（2021年ZooKeeper面试题及答案大全）.md#30watcher-特性总结)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
