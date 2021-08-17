# Redis面试题汇总及答案（2021年Redis面试题及答案大全）

Redis面试题及答案【最新版】Redis高级面试题大全(2021版)，发现网上很多Redis面试题及答案整理都没有答案，所以花了很长时间搜集，本套Redis面试题大全，Redis面试题大汇总，有大量经典的Redis面试题以及答案，包含Redis语言常见面试题、Redis工程师高级面试题及一些大厂Redis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Redis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Redis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、使用Redis有哪些好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#1使用redis有哪些好处)  


**1、** 速度快，因为数据存在内存中，类似于HashMap，HashMap的优势就是查找和操作的时间复杂度都是O(1)

**2、** 支持丰富数据类型，支持string，list，set，sorted set，hash

**3、** 支持事务，操作都是原子性，所谓的原子性就是对数据的更改要么全部执行，要么全部不执行

**4、** 丰富的特性：可用于缓存，消息，按key设置过期时间，过期后将会自动删除


### [2、说说Redis哈希槽的概念？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#2说说redis哈希槽的概念)  


Redis集群没有使用一致性hash,而是引入了哈希槽的概念，Redis集群有16384个哈希槽，每个key通过CRC16校验后对16384取模来决定放置哪个槽，集群的每个节点负责一部分hash槽。


### [3、Redis支持哪几种数据类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#3redis支持哪几种数据类型)  


String、List、Set、Sorted Set、hashes


### [4、Pipeline有什么好处，为什么要用pipeline？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#4pipeline有什么好处为什么要用pipeline)  


可以将多次IO往返的时间缩减为一次，前提是pipeline执行的指令之间没有因果相关性。使用Redis-benchmark进行压测的时候可以发现影响Redis的QPS峰值的一个重要因素是pipeline批次指令的数目。


### [5、Redis的缓存失效策略和主键失效机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#5redis的缓存失效策略和主键失效机制)  


作为缓存系统都要定期清理无效数据，就需要一个主键失效和淘汰策略.

在Redis当中，有生存期的key被称为volatile。在创建缓存时，要为给定的key设置生存期，当key过期的时候（生存期为0），它可能会被删除。

**1、** 影响生存时间的一些操作

生存时间可以通过使用 DEL 命令来删除整个 key 来移除，或者被 SET 和 GETSET 命令覆盖原来的数据，也就是说，修改key对应的value和使用另外相同的key和value来覆盖以后，当前数据的生存时间不同。

比如说，对一个 key 执行INCR命令，对一个列表进行LPUSH命令，或者对一个哈希表执行HSET命令，这类操作都不会修改 key 本身的生存时间。另一方面，如果使用RENAME对一个 key 进行改名，那么改名后的 key的生存时间和改名前一样。

RENAME命令的另一种可能是，尝试将一个带生存时间的 key 改名成另一个带生存时间的 another_key ，这时旧的 another_key (以及它的生存时间)会被删除，然后旧的 key 会改名为 another_key ，因此，新的 another_key 的生存时间也和原本的 key 一样。使用PERSIST命令可以在不删除 key 的情况下，移除 key 的生存时间，让 key 重新成为一个persistent key 。

**2、** 如何更新生存时间

可以对一个已经带有生存时间的 key 执行EXPIRE命令，新指定的生存时间会取代旧的生存时间。过期时间的精度已经被控制在1ms之内，主键失效的时间复杂度是O（1），EXPIRE和TTL命令搭配使用，TTL可以查看key的当前生存时间。设置成功返回 1；当 key 不存在或者不能为 key 设置生存时间时，返回 0 。

**最大缓存配置：**

在 Redis 中，允许用户设置最大使用内存大小，server.maxmemory默认为0，没有指定最大缓存，如果有新的数据添加，超过最大内存，则会使Redis崩溃，所以一定要设置。Redis 内存数据集大小上升到一定大小的时候，就会实行数据淘汰策略。

**Redis 提供 6种数据淘汰策略：**

**1、** volatile-lru：从已设置过期时间的数据集（server.db[i].expires）中挑选最近最少使用的数据淘汰

**2、** volatile-ttl：从已设置过期时间的数据集（server.db[i].expires）中挑选将要过期的数据淘汰

**3、** volatile-random：从已设置过期时间的数据集（server.db[i].expires）中任意选择数据淘汰

**4、** allkeys-lru：从数据集（server.db[i].dict）中挑选最近最少使用的数据淘汰

**5、** allkeys-random：从数据集（server.db[i].dict）中任意选择数据淘汰

**6、** no-enviction（驱逐）：禁止驱逐数据

注意这里的6种机制，volatile和allkeys规定了是对已设置过期时间的数据集淘汰数据还是从全部数据集淘汰数据，后面的lru、ttl以及random是三种不同的淘汰策略，再加上一种no-enviction永不回收的策略。

**使用策略规则：**

**1、**   如果数据呈现幂律分布，也就是一部分数据访问频率高，一部分数据访问频率低，则使用allkeys-lru

**2、**   如果数据呈现平等分布，也就是所有的数据访问频率都相同，则使用allkeys-random

**三种数据淘汰策略：**

ttl和random比较容易理解，实现也会比较简单。主要是Lru最近最少使用淘汰策略，设计上会对key 按失效时间排序，然后取最先失效的key进行淘汰


### [6、Redis是单线程的，如何提高多核CPU的利用率？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#6redis是单线程的如何提高多核cpu的利用率)  


可以在同一个服务器部署多个Redis的实例，并把他们当作不同的服务器来使用，在某些时候，无论如何一个服务器是不够的， 所以，如果你想使用多个CPU，你可以考虑一下分片（shard）。


### [7、后端开发群：943918498](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#7后端开发群：943918498)  

### [8、Redis通讯协议](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#8redis通讯协议)  


RESP 是Redis客户端和服务端之前使用的一种通讯协议；RESP 的特点：实现简单、快速解析、可读性好


### [9、Redis前端启动命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#9redis前端启动命令)  


./Redis-server


### [10、MySQL 里有 2000w 数据，Redis 中只存 20w 的数据，如何保证Redis 中的数据都是热点数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#10mysql-里有-2000w-数据redis-中只存-20w-的数据如何保证redis-中的数据都是热点数据)  


Redis 内存数据集大小上升到一定大小的时候， 就会施行数据淘汰策略。相关知识： Redis 提供 6 种数据淘汰策略：

volatile-lru：从已设置过期时间的数据集（ server.db[i].expires）中挑选最近最

少使用的数据淘汰

volatile-ttl： 从已设置过期时间的数据集（ server.db[i].expires） 中挑选将要过期的数据淘汰

volatile-random： 从已设置过期时间的数据集（ server.db[i].expires） 中任意选择数据淘汰

allkeys-lru： 从数据集（ server.db[i].dict） 中挑选最近最少使用的数据淘汰

allkeys-random： 从数据集（ server.db[i].dict） 中任意选择数据淘汰

no-enviction（ 驱逐） ： 禁止驱逐数据


### [11、SCAN系列命令注意事项](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#11scan系列命令注意事项)  

### [12、Redis 集群的主从复制模型是怎样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#12redis-集群的主从复制模型是怎样的)  

### [13、Redis是单线程的，但Redis为什么这么快？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#13redis是单线程的但redis为什么这么快)  

### [14、Reids主从复制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#14reids主从复制)  

### [15、内存碎片](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#15内存碎片)  

### [16、Redis集群如何选择数据库？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#16redis集群如何选择数据库)  

### [17、Redis回收使用的是什么算法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#17redis回收使用的是什么算法)  

### [18、为什么需要持久化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#18为什么需要持久化)  

### [19、Jedis与Redisson对比有什么优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#19jedis与redisson对比有什么优缺点)  

### [20、如何实现集群中的 session 共享存储？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#20如何实现集群中的-session-共享存储)  

### [21、为什么Redis需要把所有数据放到内存中?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#21为什么redis需要把所有数据放到内存中)  

### [22、为什么 edis 需要把所有数据放到内存中？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#22为什么-edis-需要把所有数据放到内存中)  

### [23、定期删除](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#23定期删除)  

### [24、Redis 回收进程如何工作的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#24redis-回收进程如何工作的)  

### [25、Redis 最适合的场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#25redis-最适合的场景)  

### [26、Redis分布式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#26redis分布式)  

### [27、是否使用过 Redis 集群，集群的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#27是否使用过-redis-集群集群的原理是什么)  

### [28、Redis 的主从复制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#28redis-的主从复制)  

### [29、Redis 持久化方案：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题汇总及答案（2021年Redis面试题及答案大全）.md#29redis-持久化方案：)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
