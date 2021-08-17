# Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）

Redis面试题及答案【最新版】Redis高级面试题大全(2021版)，发现网上很多Redis面试题及答案整理都没有答案，所以花了很长时间搜集，本套Redis面试题大全，Redis面试题大汇总，有大量经典的Redis面试题以及答案，包含Redis语言常见面试题、Redis工程师高级面试题及一些大厂Redis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Redis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Redis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、Redis集群方案应该怎么做？都有哪些方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#1redis集群方案应该怎么做都有哪些方案)  


**1、** codis

**2、** 目前用的最多的集群方案，基本和twemproxy一致的效果，但它支持在节点数量改变情况下，旧节点数据可恢复到新hash节点。 Redis cluster3.0自带的集群，特点在于他的分布式算法不是一致性hash，而是hash槽的概念，以及自身支持节点设置从节点。具体看官方文档介绍。

**3、** 在业务代码层实现，起几个毫无关联的Redis实例，在代码层，对key进行hash计算，然后去对应的Redis实例操作数据。这种方式对hash层代码要求比较高，考虑部分包括，节点失效后的替代算法方案，数据震荡后的自动脚本恢复，实例的监控，等等。


### [2、Redis的持久化机制是什么？各自的优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#2redis的持久化机制是什么各自的优缺点)  


**Redis提供两种持久化机制RDB和AOF机制:**

**1、** RDBRedis DataBase)持久化方式： 是指用数据集快照的方式半持久化模式)记录Redis数据库的所有键值对,在某个时间点将数据写入一个临时文件，持久化结束后，用这个临时文件替换上次持久化的文件，达到数据恢复。

**优点：**

**1、** 只有一个文件dump.rdb，方便持久化。

**2、** 容灾性好，一个文件可以保存到安全的磁盘。

**3、** 性能最大化，fork子进程来完成写操作，让主进程继续处理命令，所以是IO最大化。使用单独子进程来进行持久化，主进程不会进行任何IO操作，保证了Redis的高性能) 4.相对于数据集大时，比AOF的启动效率更高。

**缺点：**

**1、** 数据安全性低。RDB是间隔一段时间进行持久化，如果持久化之间Redis发生故障，会发生数据丢失。所以这种方式更适合数据要求不严谨的时候)

**2、** AOFAppend-only file)持久化方式： 是指所有的命令行记录以Redis命令请求协议的格式完全持久化存储)保存为aof文件。

**优点：**

**1、** 数据安全，aof持久化可以配置appendfsync属性，有always，每进行一次命令操作就记录到aof文件中一次。

**2、** 通过append模式写文件，即使中途服务器宕机，可以通过Redis-check-aof工具解决数据一致性问题。

**3、** AOF机制的rewrite模式。AOF文件没被rewrite之前（文件过大时会对命令进行合并重写），可以删除其中的某些命令（比如误操作的flushall）)

**缺点：**

**1、** AOF文件比RDB文件大，且恢复速度慢。

**2、** 数据集大的时候，比rdb启动效率低。


### [3、请用Redis和任意语言实现一段恶意登录保护的代码，](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#3请用redis和任意语言实现一段恶意登录保护的代码)  


限制1小时内每用户Id最多只能登录5次。具体登录函数或功能用空函数即可，不用详细写出。

用列表实现:列表中每个元素代表登陆时间,只要最后的第5次登陆时间和现在时间差不超过1小时就禁止登陆.用Python写的代码如下：

```
#!/usr/bin/env python3
import Redis  
import sys  
import time  
 
r = Redis.StrictRedis(host=’127.0.0.1′, port=6379, db=0)  
try:       
    id = sys.argv[1]
except:      
    print(‘input argument error’)    
    sys.exit(0)  
if r.llen(id) >= 5 and time.time() – float(r.lindex(id, 4)) <= 3600:      
    print(“you are forbidden logining”)
else:       
    print(‘you are allowed to login’)    
    r.lpush(id, time.time())    
    # login_func()
```


### [4、为什么Redis需要把所有数据放到内存中？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#4为什么redis需要把所有数据放到内存中)  


Redis为了达到最快的读写速度将数据都读到内存中，并通过异步的方式将数据写入磁盘。所以Redis具有快速和数据持久化的特征。如果不将数据放在内存中，磁盘I/O速度为严重影响Redis的性能。在内存越来越便宜的今天，Redis将会越来越受欢迎。

如果设置了最大使用的内存，则数据已有记录数达到内存限值后不能继续插入新值。


### [5、多节点 Redis 分布式锁：Redlock 算法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#5多节点-redis-分布式锁：redlock-算法)  


获取当前时间（start）。

依次向 N 个 `Redis`节点请求锁。请求锁的方式与从单节点 `Redis`获取锁的方式一致。为了保证在某个 `Redis`节点不可用时该算法能够继续运行，获取锁的操作都需要设置超时时间，需要保证该超时时间远小于锁的有效时间。这样才能保证客户端在向某个 `Redis`节点获取锁失败之后，可以立刻尝试下一个节点。

计算获取锁的过程总共消耗多长时间（consumeTime = end - start）。如果客户端从大多数 `Redis`节点（>= N/2 + 1) 成功获取锁，并且获取锁总时长没有超过锁的有效时间，这种情况下，客户端会认为获取锁成功，否则，获取锁失败。

如果最终获取锁成功，锁的有效时间应该重新设置为锁最初的有效时间减去 `consumeTime`。

如果最终获取锁失败，客户端应该立刻向所有 `Redis`节点发起释放锁的请求。


### [6、Redis 集群最大节点个数是多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#6redis-集群最大节点个数是多少)  


16384 个。


### [7、Redis缓存被击穿处理机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#7redis缓存被击穿处理机制)  


使用mutex。简单地来说，就是在缓存失效的时候（判断拿出来的值为空），不是立即去load db，而是先使用缓存工具的某些带成功操作返回值的操作（比如Redis的SETNX或者Memcache的ADD）去set一个mutex key，当操作返回成功时，再进行load db的操作并回设缓存；否则，就重试整个get缓存的方法


### [8、Reids常用5种数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#8reids常用5种数据类型)  


string，list，set，sorted set，hash


### [9、假如Redis里面有1亿个key，其中有10w个key是以某个固定的已知的前缀开头的，如果将它们全部找出来？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#9假如redis里面有1亿个key其中有10w个key是以某个固定的已知的前缀开头的如果将它们全部找出来)  


使用keys指令可以扫出指定模式的key列表。

对方接着追问：如果这个Redis正在给线上的业务提供服务，那使用keys指令会有什么问题？

这个时候你要回答Redis关键的一个特性：Redis的单线程的。keys指令会导致线程阻塞一段时间，线上服务会停顿，直到指令执行完毕，服务才能恢复。这个时候可以使用scan指令，scan指令可以无阻塞的提取出指定模式的key列表，但是会有一定的重复概率，在客户端做一次去重就可以了，但是整体所花费的时间会比直接用keys指令长。


### [10、怎么理解Redis事务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#10怎么理解redis事务)  


事务是一个单独的隔离操作：事务中的所有命令都会序列化、按顺序地执行。事务在执行的过程中，不会被其他客户端发送来的命令请求所打断。

事务是一个原子操作：事务中的命令要么全部被执行，要么全部都不执行。


### [11、怎么理解 Redis 事务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#11怎么理解-redis-事务)  

### [12、Jedis 与 Redisson 对比有什么优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#12jedis-与-redisson-对比有什么优缺点)  

### [13、Redis集群最大节点个数是多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#13redis集群最大节点个数是多少)  

### [14、使用过Redis分布式锁么，它是什么回事？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#14使用过redis分布式锁么它是什么回事)  

### [15、什么是Redis？简述它的优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#15什么是redis简述它的优缺点)  

### [16、Reids的特点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#16reids的特点)  

### [17、Redis回收进程如何工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#17redis回收进程如何工作的)  

### [18、缓存和数据库间数据一致性问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#18缓存和数据库间数据一致性问题)  

### [19、Redis 到底是怎么实现“附近的人”](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#19redis-到底是怎么实现“附近的人)  

### [20、怎么测试Redis的连通性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#20怎么测试redis的连通性)  

### [21、Reids三种不同删除策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#21reids三种不同删除策略)  

### [22、Reids6种淘汰策略：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#22reids6种淘汰策略：)  

### [23、Redis是单进程单线程的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#23redis是单进程单线程的)  

### [24、Redis中的管道有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#24redis中的管道有什么用)  

### [25、Redis回收进程如何工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#25redis回收进程如何工作的)  

### [26、Redis 管道 Pipeline](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#26redis-管道-pipeline)  

### [27、微信公众号：Java资讯库，回复“架构”](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#27微信公众号：java资讯库回复“架构)  

### [28、Redis没有直接使用C字符串](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#28redis没有直接使用c字符串)  

### [29、Redis是单线程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Redis/Redis中级面试题汇总及答案（2021年Redis面试题及答案大全）.md#29redis是单线程)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
