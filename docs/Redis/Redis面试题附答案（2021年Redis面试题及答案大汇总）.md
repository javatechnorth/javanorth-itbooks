# Redis面试题附答案（2021年Redis面试题及答案大汇总）

Redis面试题及答案【最新版】Redis高级面试题大全(2021版)，发现网上很多Redis面试题及答案整理都没有答案，所以花了很长时间搜集，本套Redis面试题大全，Redis面试题大汇总，有大量经典的Redis面试题以及答案，包含Redis语言常见面试题、Redis工程师高级面试题及一些大厂Redis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Redis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Redis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、都有哪些办法可以降低 Redis 的内存使用情况呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#1都有哪些办法可以降低-redis-的内存使用情况呢)  


如果你使用的是 32 位的 Redis 实例，可以好好利用 Hash,list,sorted set,set 等集合类型数据， 因为通常情况下很多小的 Key-Value 可以用更紧凑的方式存放到一起。


### [2、Redis有哪些适合的场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#2redis有哪些适合的场景)  


**会话缓存（Session Cache）**

最常用的一种使用Redis的情景是会话缓存（sessioncache），用Redis缓存会话比其他存储（如Memcached）的优势在于：Redis提供持久化。当维护一个不是严格要求一致性的缓存时，如果用户的购物车信息全部丢失，大部分人都会不高兴的，现在，他们还会这样吗？

幸运的是，随着 Redis 这些年的改进，很容易找到怎么恰当的使用Redis来缓存会话的文档。甚至广为人知的商业平台Magento也提供Redis的插件。

**全页缓存（FPC）**

除基本的会话token之外，Redis还提供很简便的FPC平台。回到一致性问题，即使重启了Redis实例，因为有磁盘的持久化，用户也不会看到页面加载速度的下降，这是一个极大改进，类似PHP本地FPC。

再次以Magento为例，Magento提供一个插件来使用Redis作为全页缓存后端。

此外，对WordPress的用户来说，Pantheon有一个非常好的插件wp-Redis，这个插件能帮助你以最快速度加载你曾浏览过的页面。

**队列**

Reids在内存存储引擎领域的一大优点是提供list和set操作，这使得Redis能作为一个很好的消息队列平台来使用。Redis作为队列使用的操作，就类似于本地程序语言（如Python）对 list 的 push/pop 操作。

如果你快速的在Google中搜索“Redis queues”，你马上就能找到大量的开源项目，这些项目的目的就是利用Redis创建非常好的后端工具，以满足各种队列需求。例如，Celery有一个后台就是使用Redis作为broker，你可以从这里去查看。

**排行榜/计数器**

Redis在内存中对数字进行递增或递减的操作实现的非常好。集合（Set）和有序集合（SortedSet）也使得我们在执行这些操作的时候变的非常简单，Redis只是正好提供了这两种数据结构。

所以，我们要从排序集合中获取到排名最靠前的10个用户–我们称之为“user_scores”，我们只需要像下面一样执行即可：

当然，这是假定你是根据你用户的分数做递增的排序。如果你想返回用户及用户的分数，你需要这样执行：

ZRANGE user_scores 0 10 WITHSCORES

Agora Games就是一个很好的例子，用Ruby实现的，它的排行榜就是使用Redis来存储数据的，你可以在这里看到。

**发布/订阅**

最后（但肯定不是最不重要的）是Redis的发布/订阅功能。发布/订阅的使用场景确实非常多。我已看见人们在社交网络连接中使用，还可作为基于发布/订阅的脚本触发器，甚至用Redis的发布/订阅功能来建立聊天系统！


### [3、是否使用过Redis集群，集群的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#3是否使用过redis集群集群的原理是什么)  


**1、** Redis Sentinal着眼于高可用，在master宕机时会自动将slave提升为master，继续提供服务。

**2、** Redis Cluster着眼于扩展性，在单个Redis内存不足时，使用Cluster进行分片存储。


### [4、Redis如何做内存优化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#4redis如何做内存优化)  


尽可能使用散列表（hashes），散列表（是说散列表里面存储的数少）使用的内存非常小，所以你应该尽可能的将你的数据模型抽象到一个散列表里面。比如你的web系统中有一个用户对象，不要为这个用户的名称，姓氏，邮箱，密码设置单独的key,而是应该把这个用户的所有信息存储到一张散列表里面.


### [5、Redis集群方案应该怎么做？都有哪些方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#5redis集群方案应该怎么做都有哪些方案)  


**1、** twemproxy，大概概念是，它类似于一个代理方式，使用方法和普通Redis无任何区别，设置好它下属的多个Redis实例后，使用时在本需要连接Redis的地方改为连接twemproxy，它会以一个代理的身份接收请求并使用一致性hash算法，将请求转接到具体Redis，将结果再返回twemproxy。使用方式简便(相对Redis只需修改连接端口)，对旧项目扩展的首选。 问题：twemproxy自身单端口实例的压力，使用一致性hash后，对Redis节点数量改变时候的计算值的改变，数据无法自动移动到新的节点。

**2、** codis，目前用的最多的集群方案，基本和twemproxy一致的效果，但它支持在 节点数量改变情况下，旧节点数据可恢复到新hash节点。

**3、** Redis cluster3.0自带的集群，特点在于他的分布式算法不是一致性hash，而是hash槽的概念，以及自身支持节点设置从节点。具体看官方文档介绍。

**4、** 在业务代码层实现，起几个毫无关联的Redis实例，在代码层，对key 进行hash计算，然后去对应的Redis实例操作数据。 这种方式对hash层代码要求比较高，考虑部分包括，节点失效后的替代算法方案，数据震荡后的自动脚本恢复，实例的监控，等等。


### [6、怎么测试Redis的连通性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#6怎么测试redis的连通性)  


使用ping命令。


### [7、Redis的并发竞争问题如何解决?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#7redis的并发竞争问题如何解决)  


Redis为单进程单线程模式，采用队列模式将并发访问变为串行访问。Redis本身没有锁的概念，Redis对于多个客户端连接并不存在竞争，但是在Jedis客户端对Redis进行并发访问时会发生连接超时、数据转换错误、阻塞、客户端关闭连接等问题，这些问题均是由于客户端连接混乱造成。

**对此有2种解决方法：**

**1、** 客户端角度，为保证每个客户端间正常有序与Redis进行通信，对连接进行池化，同时对客户端读写Redis操作采用内部锁synchronized。

**2、** 服务器角度，利用setnx实现锁。

_注：对于第一种，需要应用程序自己处理资源的同步，可以使用的方法比较通俗，可以使用synchronized也可以使用lock；第二种需要用到Redis的setnx命令，但是需要注意一些问题。_


### [8、使用Redis 有哪些好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#8使用redis-有哪些好处)  


**1、** 速度快， 因为数据存在内存中， 类似于 HashMap， HashMap 的优势就是查找和操作的时间复杂度都是 O1)

**2、** 支持丰富数据类型， 支持 string， list， set， Zset， hash 等

**3、** 支持事务， 操作都是原子性， 所谓的原子性就是对数据的更改要么全部执行， 要么全部不执行

**4、** 丰富的特性：可用于缓存，消息，按 key 设置过期时间，过期后将会自动删除


### [9、Redis回收进程如何工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#9redis回收进程如何工作的)  


一个客户端运行了新的命令，添加了新的数据。Redi检查内存使用情况，如果大于maxmemory的限制, 则根据设定好的策略进行回收。一个新的命令被执行，等等。所以我们不断地穿越内存限制的边界，通过不断达到边界然后不断地回收回到边界以下。如果一个命令的结果导致大量内存被使用（例如很大的集合的交集保存到一个新的键），不用多久内存限制就会被这个内存使用量超越。


### [10、Redis最适合的场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#10redis最适合的场景)  


**1、** 会话缓存（Session Cache）

最常用的一种使用Redis的情景是会话缓存（session cache）。用Redis缓存会话比其他存储（如Memcached）的优势在于：Redis提供持久化。当维护一个不是严格要求一致性的缓存时，如果用户的购物车信息全部丢失，大部分人都会不高兴的，现在，他们还会这样吗？ 幸运的是，随着 Redis 这些年的改进，很容易找到怎么恰当的使用Redis来缓存会话的文档。甚至广为人知的商业平台Magento也提供Redis的插件。

**2、** 全页缓存（FPC）

除基本的会话token之外，Redis还提供很简便的FPC平台。回到一致性问题，即使重启了Redis实例，因为有磁盘的持久化，用户也不会看到页面加载速度的下降，这是一个极大改进，类似PHP本地FPC。 再次以Magento为例，Magento提供一个插件来使用Redis作为全页缓存后端。 此外，对WordPress的用户来说，Pantheon有一个非常好的插件 wp-Redis，这个插件能帮助你以最快速度加载你曾浏览过的页面。

3、队列

Reids在内存存储引擎领域的一大优点是提供 list 和 set 操作，这使得Redis能作为一个很好的消息队列平台来使用。Redis作为队列使用的操作，就类似于本地程序语言（如Python）对 list 的 push/pop 操作。 如果你快速的在Google中搜索“Redis queues”，你马上就能找到大量的开源项目，这些项目的目的就是利用Redis创建非常好的后端工具，以满足各种队列需求。例如，Celery有一个后台就是使用Redis作为broker，你可以从这里去查看。

4，排行榜/计数器

Redis在内存中对数字进行递增或递减的操作实现的非常好。集合（Set）和有序集合（Sorted Set）也使得我们在执行这些操作的时候变的非常简单，Redis只是正好提供了这两种数据结构。所以，我们要从排序集合中获取到排名最靠前的10个用户–我们称之为“user_scores”，我们只需要像下面一样执行即可： 当然，这是假定你是根据你用户的分数做递增的排序。如果你想返回用户及用户的分数，你需要这样执行： ZRANGE user_scores 0 10 WITHSCORES Agora Games就是一个很好的例子，用Ruby实现的，它的排行榜就是使用Redis来存储数据的，你可以在这里看到。

**5、** 发布/订阅

最后（但肯定不是最不重要的）是Redis的发布/订阅功能。发布/订阅的使用场景确实非常多。我已看见人们在社交网络连接中使用，还可作为基于发布/订阅的脚本触发器，甚至用Redis的发布/订阅功能来建立聊天系统！


### [11、Redis 集群会有写操作丢失吗？为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#11redis-集群会有写操作丢失吗为什么)  

### [12、Twemproxy是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#12twemproxy是什么)  

### [13、删除key](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#13删除key)  

### [14、Redis与其他key-value存储有什么不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#14redis与其他key-value存储有什么不同)  

### [15、Redis常见性能问题和解决方案：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#15redis常见性能问题和解决方案：)  

### [16、Redis的回收策略（淘汰策略）?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#16redis的回收策略淘汰策略)  

### [17、mySQL里有2000w数据，Redis中只存20w的数据，如何保证Redis中的数据都是热点数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#17mysql里有2000w数据redis中只存20w的数据如何保证redis中的数据都是热点数据)  

### [18、Redis key 的过期时间和永久有效分别怎么设置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#18redis-key-的过期时间和永久有效分别怎么设置)  

### [19、Redis集群之间是如何复制的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#19redis集群之间是如何复制的)  

### [20、Redis 事务相关的命令有哪几个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#20redis-事务相关的命令有哪几个)  

### [21、Redis官方为什么不提供Windows版本？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#21redis官方为什么不提供windows版本)  

### [22、Redis是单进程单线程的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#22redis是单进程单线程的)  

### [23、Redis常见性能问题和解决方案：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#23redis常见性能问题和解决方案：)  

### [24、Redis的内存用完了会发生什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#24redis的内存用完了会发生什么)  

### [25、Redis的全称是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#25redis的全称是什么)  

### [26、什么是Redis？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#26什么是redis)  

### [27、Redis集群会有写操作丢失吗？为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#27redis集群会有写操作丢失吗为什么)  

### [28、一个 Redis 实例最多能存放多少的 keys？List、Set、Sorted Set 他们最多能存放多少元素?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#28一个-redis-实例最多能存放多少的-keyslistsetsorted-set-他们最多能存放多少元素)  

### [29、Reids持久化触发条件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#29reids持久化触发条件)  

### [30、什么是Redis?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题附答案（2021年Redis面试题及答案大汇总）.md#30什么是redis)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
