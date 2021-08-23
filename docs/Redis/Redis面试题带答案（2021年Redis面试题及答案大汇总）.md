# Redis面试题带答案（2021年Redis面试题及答案大汇总）

Redis面试题及答案【最新版】Redis高级面试题大全(2021版)，发现网上很多Redis面试题及答案整理都没有答案，所以花了很长时间搜集，本套Redis面试题大全，Redis面试题大汇总，有大量经典的Redis面试题以及答案，包含Redis语言常见面试题、Redis工程师高级面试题及一些大厂Redis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Redis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Redis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、持久化策略选择](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#1持久化策略选择)  


**1、** 如果Redis中的数据完全丢弃也没有关系（如Redis完全用作DB层数据的cache），那么无论是单机，还是主从架构，都可以不进行任何持久化。

**2、** 在单机环境下（对于个人开发者，这种情况可能比较常见），如果可以接受十几分钟或更多的数据丢失，选择RDB对Redis的性能更加有利；如果只能接受秒级别的数据丢失，应该选择AOF。

**3、** 但在多数情况下，我们都会配置主从环境，slave的存在既可以实现数据的热备，也可以进行读写分离分担Redis读请求，以及在master宕掉后继续提供服务。


### [2、Redis常见性能问题和解决方案：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#2redis常见性能问题和解决方案：)  


**1、** Master最好不要写内存快照，如果Master写内存快照，save命令调度rdbSave函数，会阻塞主线程的工作，当快照比较大时对性能影响是非常大的，会间断性暂停服务

**2、** 如果数据比较重要，某个Slave开启AOF备份数据，策略设置为每秒同步一

**3、** 为了主从复制的速度和连接的稳定性，Master和Slave最好在同一个局域网

**4、** 尽量避免在压力很大的主库上增加从

**5、** 主从复制不要用图状结构，用单向链表结构更为稳定，即：Master <- Slave1 <- Slave2 <- Slave3…这样的结构方便解决单点故障问题，实现Slave对Master的替换。如果Master挂了，可以立刻启用Slave1做Master，其他不变。


### [3、修改配置不重启Redis会实时生效吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#3修改配置不重启redis会实时生效吗)  


针对运行实例，有许多配置选项可以通过 CONFIG SET 命令进行修改，而无需执行任何形式的重启。 从 Redis 2.2 开始，可以从 AOF 切换到 RDB 的快照持久性或其他方式而不需要重启 Redis。检索 ‘CONFIG GET *’ 命令获取更多信息。

但偶尔重新启动是必须的，如为升级 Redis 程序到新的版本，或者当你需要修改某些目前 CONFIG 命令还不支持的配置参数的时候。


### [4、Redis过期键的删除策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#4redis过期键的删除策略)  


**1、** 定时删除:在设置键的过期时间的同时，创建一个定时器timer)、让定时器在键的过期时间来临时，立即执行对键的删除操作。

**2、** 惰性删除:放任键过期不管，但是每次从键空间中获取键时，都检查取得的键是否过期，如果过期的话，就删除该键;如果没有过期，就返回该键。

**3、** 定期删除:每隔一段时间程序就对数据库进行一次检查，删除里面的过期键。至于要删除多少过期键，以及要检查多少个数据库，则由算法决定。


### [5、Redis与Memcached相比有哪些优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#5redis与memcached相比有哪些优势)  


**1、** Memcached所有的值均是简单的字符串，Redis作为其替代者，支持更为丰富的数据类型

**2、** Redis的速度比Memcached快很多Redis的速度比Memcached快很多

**3、** Redis可以持久化其数据Redis可以持久化其数据


### [6、Redis持久化的几种方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#6redis持久化的几种方式)  


**1、** 快照（snapshots）

缺省情况情况下，Redis把数据快照存放在磁盘上的二进制文件中，文件名为dump.rdb。你可以配置Redis的持久化策略，例如数据集中每N秒钟有超过M次更新，就将数据写入磁盘；或者你可以手工调用命令SAVE或BGSAVE。

**工作原理**

1. Redis forks.
2. 子进程开始将数据写到临时RDB文件中。
3. 当子进程完成写RDB文件，用新文件替换老文件。
4. 这种方式可以使Redis使用copy-on-write技术。

**2、** AOF

快照模式并不十分健壮，当系统停止，或者无意中Redis被kill掉，最后写入Redis的数据就会丢失。

这对某些应用也许不是大问题，但对于要求高可靠性的应用来说，Redis就不是一个合适的选择。Append-only文件模式是另一种选择。你可以在配置文件中打开AOF模式

**3、** 虚拟内存方式

当你的key很小而value很大时,使用VM的效果会比较好.因为这样节约的内存比较大.

当你的key不小时,可以考虑使用一些非常方法将很大的key变成很大的value,比如你可以考虑将key,value组合成一个新的value.

vm-max-threads这个参数,可以设置访问swap文件的线程数,设置最好不要超过机器的核数,如果设置为0,那么所有对swap文件的操作都是串行的.可能会造成比较长时间的延迟,但是对数据完整性有很好的保证.

自己测试的时候发现用虚拟内存性能也不错。如果数据量很大，可以考虑分布式或者其他数据库。


### [7、为什么Redis需要把所有数据放到内存中？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#7为什么redis需要把所有数据放到内存中)  


Redis为了达到最快的读写速度将数据都读到内存中，并通过异步的方式将数据写入磁盘。

所以Redis具有快速和数据持久化的特征，如果不将数据放在内存中，磁盘I/O速度为严重影响Redis的性能。

在内存越来越便宜的今天，Redis将会越来越受欢迎， 如果设置了最大使用的内存，则数据已有记录数达到内存限值后不能继续插入新值。


### [8、Redis集群方案应该怎么做？都有哪些方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#8redis集群方案应该怎么做都有哪些方案)  


**1、** codis。

目前用的最多的集群方案，基本和twemproxy一致的效果，但它支持在 节点数量改变情况下，旧节点数据可恢复到新hash节点。

**2、** Redis cluster3.0自带的集群，特点在于他的分布式算法不是一致性hash，而是hash槽的概念，以及自身支持节点设置从节点。具体看官方文档介绍。

**3、** 在业务代码层实现，起几个毫无关联的Redis实例，在代码层，对key 进行hash计算，然后去对应的Redis实例操作数据。 这种方式对hash层代码要求比较高，考虑部分包



### [9、Redis 的回收策略（淘汰策略）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#9redis-的回收策略淘汰策略)  


volatile-lru：从已设置过期时间的数据集（ server.db[i].expires）中挑选最近最少使用的数据淘汰

volatile-ttl： 从已设置过期时间的数据集（ server.db[i].expires） 中挑选将要过期的数据淘汰

volatile-random： 从已设置过期时间的数据集（ server.db[i].expires） 中任意选择数据淘汰

allkeys-lru： 从数据集（ server.db[i].dict） 中挑选最近最少使用的数据淘汰

allkeys-random： 从数据集（ server.db[i].dict） 中任意选择数据淘汰

no-enviction（ 驱逐） ： 禁止驱逐数据

注意这里的 6 种机制，volatile 和 allkeys 规定了是对已设置过期时间的数据集淘汰数据还是从全部数据集淘汰数据， 后面的 lru、ttl 以及 random 是三种不同的淘汰策略， 再加上一种 no-enviction 永不回收的策略。

使用策略规则：

**1、** 如果数据呈现幂律分布，也就是一部分数据访问频率高，一部分数据访问频率   低， 则使用 allkeys-lru

**2、** 如果数据呈现平等分布， 也就是所有的数据访问频率都相同， 则使用allkeys-random


### [10、AOF常用配置总结](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#10aof常用配置总结)  


下面是AOF常用的配置项，以及默认值；前面介绍过的这里不再详细介绍。

**1、** appendonly no：是否开启AOF

**2、** appendfilename "appendonly.aof"：AOF文件名

**3、** dir ./：RDB文件和AOF文件所在目录

**4、** appendfsync everysec：fsync持久化策略

**5、** no-appendfsync-on-rewrite no：AOF重写期间是否禁止fsync；如果开启该选项，可以减轻文件重写时CPU和硬盘的负载（尤其是硬盘），但是可能会丢失AOF重写期间的数据；需要在负载和安全性之间进行平衡

**6、** auto-aof-rewrite-percentage 100：文件重写触发条件之一

**7、** auto-aof-rewrite-min-size 64mb：文件重写触发提交之一

**8、** aof-load-truncated yes：如果AOF文件结尾损坏，Redis启动时是否仍载入AOF文件


### [11、MySQL里有2000w数据，Redis中只存20w的数据，如何保证Redis中的数据都是热点数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#11mysql里有2000w数据redis中只存20w的数据如何保证redis中的数据都是热点数据)  

### [12、Redis的同步机制了解么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#12redis的同步机制了解么)  

### [13、Redis 支持的Java 客户端都有哪些？官方推荐用哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#13redis-支持的java-客户端都有哪些官方推荐用哪个)  

### [14、使用过 Redis 分布式锁么，它是什么回事？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#14使用过-redis-分布式锁么它是什么回事)  

### [15、Redis集群方案什么情况下会导致整个集群不可用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#15redis集群方案什么情况下会导致整个集群不可用)  

### [16、Redis和Redisson有什么关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#16redis和redisson有什么关系)  

### [17、为什么edis需要把所有数据放到内存中？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#17为什么edis需要把所有数据放到内存中)  

### [18、Redis支持的Java客户端都有哪些？官方推荐用哪个？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#18redis支持的java客户端都有哪些官方推荐用哪个)  

### [19、Redis如何做大量数据插入？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#19redis如何做大量数据插入)  

### [20、什么是Redis?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#20什么是redis)  

### [21、Redis中的管道有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#21redis中的管道有什么用)  

### [22、Jedis与Redisson对比有什么优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#22jedis与redisson对比有什么优缺点)  

### [23、RDB和AOF的优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#23rdb和aof的优缺点)  

### [24、MySQL里有2000w数据，Redis中只存20w的数据，如何保证Redis中的数据都是热点数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#24mysql里有2000w数据redis中只存20w的数据如何保证redis中的数据都是热点数据)  

### [25、Redis 的同步机制了解么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#25redis-的同步机制了解么)  

### [26、Redis集群最大节点个数是多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#26redis集群最大节点个数是多少)  

### [27、Memcached 与Redis 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#27memcached-与redis-的区别)  

### [28、支持一致性哈希的客户端有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#28支持一致性哈希的客户端有哪些)  

### [29、Redis 的内存用完了会发生什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#29redis-的内存用完了会发生什么)  

### [30、Redis提供了哪几种持久化方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis面试题带答案（2021年Redis面试题及答案大汇总）.md#30redis提供了哪几种持久化方式)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
