# Redis面试题附答案汇总（2021年Redis面试题及答案大全）

Redis面试题及答案【最新版】Redis高级面试题大全(2021版)，发现网上很多Redis面试题及答案整理都没有答案，所以花了很长时间搜集，本套Redis面试题大全，Redis面试题大汇总，有大量经典的Redis面试题以及答案，包含Redis语言常见面试题、Redis工程师高级面试题及一些大厂Redis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Redis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Redis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、都有哪些办法可以降低Redis的内存使用情况呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#1都有哪些办法可以降低redis的内存使用情况呢)  


如果你使用的是32位的Redis实例，可以好好利用Hash,list,sorted set,set等集合类型数据，因为通常情况下很多小的Key-Value可以用更紧凑的方式存放到一起。


### [2、Memcache与Redis的区别都有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#2memcache与redis的区别都有哪些)  


**1、** 存储方式 Memecache把数据全部存在内存之中，断电后会挂掉，数据不能超过内存大小。 Redis有部份存在硬盘上，这样能保证数据的持久性。

**2、** 数据支持类型 Memcache对数据类型支持相对简单。 Redis有复杂的数据类型。

**3、** 使用底层模型不同 它们之间底层实现方式 以及与客户端之间通信的应用协议不一样。 Redis直接自己构建了VM 机制 ，因为一般的系统调用系统函数的话，会浪费一定的时间去移动和请求。


### [3、如何选择合适的持久化方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#3如何选择合适的持久化方式)  


一般来说， 如果想达到足以媲美PostgreSQL的数据安全性， 你应该同时使用两种持久化功能。如果你非常关心你的数据， 但仍然可以承受数分钟以内的数据丢失，那么你可以只使用RDB持久化。

有很多用户都只使用AOF持久化，但并不推荐这种方式：因为定时生成RDB快照（snapshot）非常便于进行数据库备份， 并且 RDB 恢复数据集的速度也要比AOF恢复的速度要快，除此之外， 使用RDB还可以避免之前提到的AOF程序的bug。


### [4、缓存并发问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#4缓存并发问题)  


这里的并发指的是多个Redis的client同时set key引起的并发问题。比较有效的解决方案就是把Redis.set操作放在队列中使其串行化，必须的一个一个执行，具体的代码就不上了，当然加锁也是可以的，至于为什么不用Redis中的事务，留给各位看官自己思考探究。


### [5、怎么理解Redis事务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#5怎么理解redis事务)  


事务是一个单独的隔离操作：事务中的所有命令都会序列化、按顺序地执行，事务在执行的过程中，不会被其他客户端发送来的命令请求所打断。

事务是一个原子操作：事务中的命令要么全部被执行，要么全部都不执行。


### [6、Redis常用管理命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#6redis常用管理命令)  


```
# dbsize 返回当前数据库 key 的数量。
# info 返回当前 Redis 服务器状态和一些统计信息。
# monitor 实时监听并返回Redis服务器接收到的所有请求信息。
# shutdown 把数据同步保存到磁盘上，并关闭Redis服务。
# config get parameter 获取一个 Redis 配置参数信息。（个别参数可能无法获取）
# config set parameter value 设置一个 Redis 配置参数信息。（个别参数可能无法获取）
# config resetstat 重置 info 命令的统计信息。（重置包括：keyspace 命中数、
# keyspace 错误数、 处理命令数，接收连接数、过期 key 数）
# debug object key 获取一个 key 的调试信息。
# debug segfault 制造一次服务器当机。
# flushdb 删除当前数据库中所有 key,此方法不会失败。小心慎用
# flushall 删除全部数据库中所有 key，此方法不会失败。小心慎用
```


### [7、Redis 相比Memcached 有哪些优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#7redis-相比memcached-有哪些优势)  


**1、** Memcached 所有的值均是简单的字符串， Redis 作为其替代者， 支持更为丰富的数据类

**2、** Redis 的速度比 Memcached 快很3、Redis 可以持久化其数据

**3、** 更多面试题关注微信公众号：Java2B


### [8、Redis key的过期时间和永久有效分别怎么设置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#8redis-key的过期时间和永久有效分别怎么设置)  


EXPIRE和PERSIST命令。


### [9、Redis有哪些适合的场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#9redis有哪些适合的场景)  


（1）、会话缓存（Session Cache）

最常用的一种使用Redis的情景是会话缓存（session cache）。用Redis缓存会话比其他存储（如Memcached）的优势在于：Redis提供持久化。当维护一个不是严格要求一致性的缓存时，如果用户的购物车信息全部丢失，大部分人都会不高兴的，现在，他们还会这样吗？

幸运的是，随着 Redis 这些年的改进，很容易找到怎么恰当的使用Redis来缓存会话的文档。甚至广为人知的商业平台Magento也提供Redis的插件。

（2）、全页缓存（FPC）

除基本的会话token之外，Redis还提供很简便的FPC平台。回到一致性问题，即使重启了Redis实例，因为有磁盘的持久化，用户也不会看到页面加载速度的下降，这是一个极大改进，类似PHP本地FPC。

再次以Magento为例，Magento提供一个插件来使用Redis作为全页缓存后端。

此外，对WordPress的用户来说，Pantheon有一个非常好的插件 wp-Redis，这个插件能帮助你以最快速度加载你曾浏览过的页面。

（3）、队列

Reids在内存存储引擎领域的一大优点是提供 list 和 set 操作，这使得Redis能作为一个很好的消息队列平台来使用。Redis作为队列使用的操作，就类似于本地程序语言（如Python）对 list 的 push/pop 操作。

如果你快速的在Google中搜索“Redis queues”，你马上就能找到大量的开源项目，这些项目的目的就是利用Redis创建非常好的后端工具，以满足各种队列需求。例如，Celery有一个后台就是使用Redis作为broker，你可以从这里去查看。

（4），排行榜/计数器

Redis在内存中对数字进行递增或递减的操作实现的非常好。集合（Set）和有序集合（Sorted Set）也使得我们在执行这些操作的时候变的非常简单，Redis只是正好提供了这两种数据结构。所以，我们要从排序集合中获取到排名最靠前的10个用户–我们称之为“user_scores”，我们只需要像下面一样执行即可：

当然，这是假定你是根据你用户的分数做递增的排序。如果你想返回用户及用户的分数，你需要这样执行：

ZRANGE user_scores 0 10 WITHSCORES

Agora Games就是一个很好的例子，用Ruby实现的，它的排行榜就是使用Redis来存储数据的，你可以在这里看到。

（5）、/订阅

最后（但肯定不是最不重要的）是Redis的/订阅功能。/订阅的使用场景确实非常多。我已看见人们在社交网络连接中使用，还可作为基于/订阅的脚本触发器，甚至用Redis的/订阅功能来建立聊天系统！（不，这是真的，你可以去核实）。


### [10、说说 Redis 哈希槽的概念？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#10说说-redis-哈希槽的概念)  


Redis 集群没有使用一致性 hash,而是引入了哈希槽的概念， Redis 集群有16384 个哈希槽，每个 key 通过 CRC16 校验后对 16384 取模来决定放置哪个槽， 集群的每个节点负责一部分 hash 槽。


### [11、Redis哨兵](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#11redis哨兵)  

### [12、假如 Redis 里面有 1 亿个key，其中有 10w 个key 是以某个固定的已知的前缀开头的，如果将它们全部找出来？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#12假如-redis-里面有-1-亿个key其中有-10w-个key-是以某个固定的已知的前缀开头的如果将它们全部找出来)  

### [13、Redis内存模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#13redis内存模型)  

### [14、Redis 如何设置密码及验证密码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#14redis-如何设置密码及验证密码)  

### [15、Redis 集群如何选择数据库？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#15redis-集群如何选择数据库)  

### [16、Redis有哪几种数据淘汰策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#16redis有哪几种数据淘汰策略)  

### [17、数据分片模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#17数据分片模型)  

### [18、Redis有哪几种数据淘汰策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#18redis有哪几种数据淘汰策略)  

### [19、Redis分区有什么缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#19redis分区有什么缺点)  

### [20、Redis事务相关的命令有哪几个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#20redis事务相关的命令有哪几个)  

### [21、Memcache 与Redis 的区别都有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#21memcache-与redis-的区别都有哪些)  

### [22、定时删除](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#22定时删除)  

### [23、为什么要做Redis分区？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#23为什么要做redis分区)  

### [24、，免费领取架构资料。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#24免费领取架构资料。)  

### [25、Redis回收进程如何工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#25redis回收进程如何工作的)  

### [26、一个字符串类型的值能存储最大容量是多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#26一个字符串类型的值能存储最大容量是多少)  

### [27、Redis 中设置过期时间主要通过以下四种方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#27redis-中设置过期时间主要通过以下四种方式)  

### [28、进程本身运行需要的内存](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#28进程本身运行需要的内存)  

### [29、Redis主要消耗什么物理资源？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案汇总（2021年Redis面试题及答案大全）.md#29redis主要消耗什么物理资源)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
