# Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）

Redis面试题及答案【最新版】Redis高级面试题大全(2021版)，发现网上很多Redis面试题及答案整理都没有答案，所以花了很长时间搜集，本套Redis面试题大全，Redis面试题大汇总，有大量经典的Redis面试题以及答案，包含Redis语言常见面试题、Redis工程师高级面试题及一些大厂Redis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Redis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Redis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、Redis 开启AOF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#1redis-开启aof)  


Redis服务器默认开启RDB，关闭AOF；要开启AOF，需要在配置文件中配置：

appendonly yes


### [2、Redis集群的主从复制模型是怎样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#2redis集群的主从复制模型是怎样的)  


为了使在部分节点失败或者大部分节点无法通信的情况下集群仍然可用，所以集群使用了主从复制模型,每个节点都会有N-1个复制品.


### [3、Redis相比Memcached有哪些优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#3redis相比memcached有哪些优势)  


**1、** Memcached所有的值均是简单的字符串，Redis作为其替代者，支持更为丰富的数据类

**2、** Redis的速度比Memcached快很

**3、** Redis可以持久化其数据


### [4、什么是Redis?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#4什么是redis)  


Redis 是完全开源免费的，遵守BSD协议，是一个高性能的key-value数据库。

**Redis 与其他 key - value 缓存产品有以下三个特点：**

**1、** Redis支持数据的持久化，可以将内存中的数据保存在磁盘中，重启的时候可以再次加载进行使用。

**2、** Redis不仅仅支持简单的key-value类型的数据，同时还提供list，set，zset，hash等数据结构的存储。

**3、** Redis支持数据的备份，即master-slave模式的数据备份。

**Redis 优势**

**1、** 性能极高 – Redis能读的速度是110000次/s,写的速度是81000次/s 。

**2、** 丰富的数据类型 – Redis支持二进制案例的 Strings, Lists, Hashes, Sets 及 Ordered Sets 数据类型操作。

**3、** 原子 – Redis的所有操作都是原子性的，意思就是要么成功执行要么失败完全不执行。单个操作是原子性的。多个操作也支持事务，即原子性，通过MULTI和EXEC指令包起来。

**4、** 丰富的特性 – Redis还支持 publish/subscribe, 通知, key 过期等等特性。

**Redis与其他key-value存储有什么不同？**

Redis有着更为复杂的数据结构并且提供对他们的原子性操作，这是一个不同于其他数据库的进化路径。Redis的数据类型都是基于基本数据结构的同时对程序员透明，无需进行额外的抽象。

Redis运行在内存中但是可以持久化到磁盘，所以在对不同数据集进行高速读写时需要权衡内存，因为数据量不能大于硬件内存。在内存数据库方面的另一个优点是，相比在磁盘上相同的复杂的数据结构，在内存中操作起来非常简单，这样Redis可以做很多内部复杂性很强的事情。同时，在磁盘格式方面他们是紧凑的以追加的方式产生的，因为他们并不需要进行随机访问。


### [5、Redis相比Memcached有哪些优势？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#5redis相比memcached有哪些优势)  


**1、** Memcached所有的值均是简单的字符串，Redis作为其替代者，支持更为丰富的数据类型

**2、** Redis的速度比Memcached快很多

**3、** Redis可以持久化其数据


### [6、怎么测试 Redis 的连通性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#6怎么测试-redis-的连通性)  


使用 ping 命令。


### [7、Redis 过期键的删除策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#7redis-过期键的删除策略)  


**1、** 定时删除:在设置键的过期时间的同时，创建一个定时器 timer). 让定时器在键的过期时间来临时， 立即执行对键的删除操作。

**2、** 惰性删除:放任键过期不管，但是每次从键空间中获取键时，都检查取得的键是   否过期， 如果过期的话， 就删除该键;如果没有过期， 就返回该键。

**3、** 定期删除:每隔一段时间程序就对数据库进行一次检查，删除里面的过期键。至   于要删除多少过期键， 以及要检查多少个数据库， 则由算法决定。


### [8、Redis对象有5种类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#8redis对象有5种类型)  


无论是哪种类型，Redis都不会直接存储，而是通过RedisObject对象进行存储。


### [9、Redis中海量数据的正确操作方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#9redis中海量数据的正确操作方式)  


利用SCAN系列命令（SCAN、SSCAN、HSCAN、ZSCAN）完成数据迭代。


### [10、Redis事物的了解CAS(check-and-set 操作实现乐观锁 )?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#10redis事物的了解cascheck-and-set-操作实现乐观锁-)  


和众多其它数据库一样，Redis作为NoSQL数据库也同样提供了事务机制。在Redis中，MULTI/EXEC/DISCARD/WATCH这四个命令是我们实现事务的基石。

相信对有关系型数据库开发经验的开发者而言这一概念并不陌生，即便如此，我们还是会简要的列出Redis中事务的实现特征：

**1、** 在事务中的所有命令都将会被串行化的顺序执行，事务执行期间，Redis不会再为其它客户端的请求提供任何服务，从而保证了事物中的所有命令被原子的执行。

**2、** 和关系型数据库中的事务相比，在Redis事务中如果有某一条命令执行失败，其后的命令仍然会被继续执行。

**3、** 我们可以通过MULTI命令开启一个事务，有关系型数据库开发经验的人可以将其理解为"BEGIN TRANSACTION"语句。在该语句之后执行的命令都将被视为事务之内的操作，最后我们可以通过执行EXEC/DISCARD命令来提交/回滚该事务内的所有操作。这两个Redis命令可被视为等同于关系型数据库中的COMMIT/ROLLBACK语句。

**4、** 在事务开启之前，如果客户端与服务器之间出现通讯故障并导致网络断开，其后所有待执行的语句都将不会被服务器执行。然而如果网络中断事件是发生在客户端执行EXEC命令之后，那么该事务中的所有命令都会被服务器执行。

**5、** 当使用Append-Only模式时，Redis会通过调用系统函数write将该事务内的所有写操作在本次调用中全部写入磁盘。然而如果在写入的过程中出现系统崩溃，如电源故障导致的宕机，那么此时也许只有部分数据被写入到磁盘，而另外一部分数据却已经丢失。

Redis服务器会在重新启动时执行一系列必要的一致性检测，一旦发现类似问题，就会立即退出并给出相应的错误提示。

此时，我们就要充分利用Redis工具包中提供的Redis-check-aof工具，该工具可以帮助我们定位到数据不一致的错误，并将已经写入的部分数据进行回滚。修复之后我们就可以再次重新启动Redis服务器了。


### [11、布隆过滤器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#11布隆过滤器)  

### [12、Reids支持的语言：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#12reids支持的语言：)  

### [13、Redis的并发竞争问题如何解决?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#13redis的并发竞争问题如何解决)  

### [14、分布式Redis是前期做还是后期规模上来了再做好？为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#14分布式redis是前期做还是后期规模上来了再做好为什么)  

### [15、如果有大量的 key 需要设置同一时间过期，一般需要注意什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#15如果有大量的-key-需要设置同一时间过期一般需要注意什么)  

### [16、Redis 集群方案什么情况下会导致整个集群不可用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#16redis-集群方案什么情况下会导致整个集群不可用)  

### [17、Redis 提供 6种数据淘汰策略：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#17redis-提供-6种数据淘汰策略：)  

### [18、Redis的数据类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#18redis的数据类型)  

### [19、Redis 的持久化机制是什么？各自的优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#19redis-的持久化机制是什么各自的优缺点)  

### [20、WATCH命令和基于CAS的乐观锁：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#20watch命令和基于cas的乐观锁：)  

### [21、缓存雪崩问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#21缓存雪崩问题)  

### [22、读写分离模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#22读写分离模型)  

### [23、Redis 集群之间是如何复制的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#23redis-集群之间是如何复制的)  

### [24、Redis 是单进程单线程的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#24redis-是单进程单线程的)  

### [25、Redis持久化数据和缓存怎么做扩容？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#25redis持久化数据和缓存怎么做扩容)  

### [26、，或是关注](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#26或是关注)  

### [27、MySQL里有2000w数据，Redis中只存20w的数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#27mysql里有2000w数据redis中只存20w的数据)  

### [28、Redis 的数据类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#28redis-的数据类型)  

### [29、惰性删除](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis高级面试题汇总及答案（2021年Redis面试题及答案大全）.md#29惰性删除)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
