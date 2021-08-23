# Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）

Redis面试题及答案【最新版】Redis高级面试题大全(2021版)，发现网上很多Redis面试题及答案整理都没有答案，所以花了很长时间搜集，本套Redis面试题大全，Redis面试题大汇总，有大量经典的Redis面试题以及答案，包含Redis语言常见面试题、Redis工程师高级面试题及一些大厂Redis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Redis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Redis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、查看Redis使用情况及状态信息用什么命令？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#1查看redis使用情况及状态信息用什么命令)  


info


### [2、Redis key的过期时间和永久有效分别怎么设置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#2redis-key的过期时间和永久有效分别怎么设置)  


EXPIRE和PERSIST命令


### [3、Redis做异步队列](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#3redis做异步队列)  


一般使用list结构作为队列，rpush生产消息，lpop消费消息。当lpop没有消息的时候，要适当sleep一会再重试。缺点：在消费者下线的情况下，生产的消息会丢失，得使用专业的消息队列如rabbitmq等。能不能生产一次消费多次呢？使用pub/sub主题订阅者模式，可以实现1:N的消息队列。


### [4、你知道有哪些Redis分区实现方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#4你知道有哪些redis分区实现方案)  


客户端分区就是在客户端就已经决定数据会被存储到哪个Redis节点或者从哪个Redis节点读取。大多数客户端已经实现了客户端分区。

代理分区 意味着客户端将请求发送给代理，然后代理决定去哪个节点写数据或者读数据。代理根据分区规则决定请求哪些Redis实例，然后根据Redis的响应结果返回给客户端。Redis和Memcached的一种代理实现就是Twemproxy

查询路由(Query routing) 的意思是客户端随机地请求任意一个Redis实例，然后由Redis将请求转发给正确的Redis节点。Redis Cluster实现了一种混合形式的查询路由，但并不是直接将请求从一个Redis节点转发到另一个Redis节点，而是在客户端的帮助下直接redirected到正确的Redis节点。


### [5、使用Redis有哪些好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#5使用redis有哪些好处)  


**1、** 速度快，因为数据存在内存中，类似于HashMap，HashMap的优势就是查找和操作的时间复杂度都是O1)

**2、** 支持丰富数据类型，支持string，list，set，Zset，hash等

**3、** 支持事务，操作都是原子性，所谓的原子性就是对数据的更改要么全部执行，要么全部不执行

**4、** 丰富的特性：可用于缓存，消息，按key设置过期时间，过期后将会自动删除


### [6、Pipeline 有什么好处，为什么要用pipeline？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#6pipeline-有什么好处为什么要用pipeline)  


可以将多次 IO 往返的时间缩减为一次，前提是 pipeline 执行的指令之间没有因果相关性。使用 Redis-benchmark 进行压测的时候可以发现影响 Redis 的 QPS 峰值的一个重要因素是 pipeline 批次指令的数目。


### [7、Redis 常见性能问题和解决方案：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#7redis-常见性能问题和解决方案：)  


**1、** Master 最好不要写内存快照，如果 Master 写内存快照，save 命令调度 rdbSave函数， 会阻塞主线程的工作， 当快照比较大时对性能影响是非常大的， 会间断性暂停服务

**2、** 如果数据比较重要， 某个 Slave 开启 AOF 备份数据， 策略设置为每秒同步一

**3、** 为了主从复制的速度和连接的稳定性， Master 和 Slave 最好在同一个局域网

**4、** 尽量避免在压力很大的主库上增加从

**5、** 主从复制不要用图状结构， 用单向链表结构更为稳定， 即：Master <- Slave1

<- Slave2 <- Slave3… 这样的结构方便解决单点故障问题，实现 Slave 对 Master 的替换。如果 Master 挂了， 可以立刻启用 Slave1 做 Master， 其他不变。


### [8、Redis还提供的高级工具](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#8redis还提供的高级工具)  


像慢查询分析、性能测试、Pipeline、事务、Lua自定义命令、Bitmaps、HyperLogLog、/订阅、Geo等个性化功能。


### [9、Redis 最适合的场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#9redis-最适合的场景)  


**1、** 会话缓存（ Session  Cache）

最常用的一种使用 Redis 的情景是会话缓存（ session cache）。用 Redis 缓存会话比其他存储（ 如 Memcached）的优势在于：Redis 提供持久化。当维护一个不是严格要求一致性的缓存时， 如果用户的购物车信息全部丢失， 大部分人都会不高兴的， 现在， 他们还会这样吗？ 幸运的是， 随着 Redis 这些年的改进， 很容易找到怎么恰当的使用 Redis 来缓存会话的文档。甚至广为人知的商业平台Magento 也提供 Redis 的插件。

**2、** 全页缓存（ FPC）

除基本的会话 token 之外， Redis 还提供很简便的 FPC 平台。回到一致性问题， 即使重启了 Redis 实例， 因为有磁盘的持久化， 用户也不会看到页面加载速度的下降，这是一个极大改进，类似 PHP 本地 FPC。 再次以 Magento 为例，Magento 提供一个插件来使用 Redis 作为全页缓存后端。 此外， 对 WordPress 的用户来说， Pantheon 有一个非常好的插件 wp-Redis， 这个插件能帮助你以最快速度加载你曾浏览过的页面。

3、队列

Reids 在内存存储引擎领域的一大优点是提供 list 和 set 操作， 这使得 Redis 能作为一个很好的消息队列平台来使用。Redis 作为队列使用的操作，就类似于本地程序语言（ 如 Python）对 list 的 push/pop 操作。 如果你快速的在 Google 中搜索“ Redis  queues”， 你马上就能找到大量的开源项目， 这些项目的目的就是利用 Redis 创建非常好的后端工具， 以满足各种队列需求。例如， Celery 有一个后台就是使用 Redis 作为 broker， 你可以从这里去查看。

4， 排行榜/计数器

Redis 在内存中对数字进行递增或递减的操作实现的非常好。集合（ Set） 和有序集合（ Sorted Set）也使得我们在执行这些操作的时候变的非常简单，Redis 只是正好提供了这两种数据结构。所以， 我们要从排序集合中获取到排名最靠前的 10 个用户– 我们称之为“ user_scores”， 我们只需要像下面一样执行即可：   当然，这是假定你是根据你用户的分数做递增的排序。如果你想返回用户及用户的分数，   你需要这样执行：  ZRANGE user_scores 0 10 WITHSCORES Agora Games 就是一个很好的例子， 用 Ruby 实现的， 它的排行榜就是使用 Redis 来存储数据的， 你可以在这里看到。

**5、** 发布/订阅

最后（ 但肯定不是最不重要的）是 Redis 的发布/订阅功能。发布/订阅的使用场景确实非常多。我已看见人们在社交网络连接中使用， 还可作为基于发布/订阅的脚本触发器， 甚至用 Redis 的发布/订阅功能来建立聊天系统！


### [10、Redis如何做内存优化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#10redis如何做内存优化)  


尽可能使用散列表（hashes），散列表（是说散列表里面存储的数少）使用的内存非常小，所以你应该尽可能的将你的数据模型抽象到一个散列表里面。

比如你的web系统中有一个用户对象，不要为这个用户的名称，姓氏，邮箱，密码设置单独的key,而是应该把这个用户的所有信息存储到一张散列表里面。


### [11、Redis 如何做内存优化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#11redis-如何做内存优化)  

### [12、如果有大量的key需要设置同一时间过期，一般需要注意什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#12如果有大量的key需要设置同一时间过期一般需要注意什么)  

### [13、使用过Redis做异步队列么，你是怎么用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#13使用过redis做异步队列么你是怎么用的)  

### [14、Redis相比Memcached有哪些优势：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#14redis相比memcached有哪些优势：)  

### [15、Redis常见性能问题和解决方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#15redis常见性能问题和解决方案)  

### [16、一个Redis实例最多能存放多少的keys？List、Set、Sorted Set他们最多能存放多少元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#16一个redis实例最多能存放多少的keyslistsetsorted-set他们最多能存放多少元素)  

### [17、一个Redis实例最多能存放多少的keys？List、Set、Sorted Set他们最多能存放多少元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#17一个redis实例最多能存放多少的keyslistsetsorted-set他们最多能存放多少元素)  

### [18、怎么理解Redis事务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#18怎么理解redis事务)  

### [19、Redis分布式锁实现](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#19redis分布式锁实现)  

### [20、Redis的内存占用情况怎么样？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#20redis的内存占用情况怎么样)  

### [21、手写一个 LRU 算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#21手写一个-lru-算法)  

### [22、使用过 Redis 做异步队列么，你是怎么用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#22使用过-redis-做异步队列么你是怎么用的)  

### [23、为什么Redis是单线程的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#23为什么redis是单线程的)  

### [24、Redis Module 实现布隆过滤器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#24redis-module-实现布隆过滤器)  

### [25、判断key是否存在](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#25判断key是否存在)  

### [26、缓冲内存](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#26缓冲内存)  

### [27、Redis常见的几种缓存策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#27redis常见的几种缓存策略)  

### [28、Redis如何设置密码及验证密码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#28redis如何设置密码及验证密码)  

### [29、Reids工具命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题附答案汇总（2021年Redis面试题及答案大全）.md#29reids工具命令)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
