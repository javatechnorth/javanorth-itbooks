# Memcached面试题带答案（2021年Memcached面试题及答案大汇总）

Memcached面试题及答案【最新版】Memcached高级面试题大全(2021版)，发现网上很多Memcached面试题及答案整理都没有答案，所以花了很长时间搜集，本套Memcached面试题大全，Memcached面试题大汇总，有大量经典的Memcached面试题以及答案，包含Memcached语言常见面试题、Memcached工程师高级面试题及一些大厂Memcached开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Memcached面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Memcached面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何将Memcached中item批量导入导出？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#1如何将memcached中item批量导入导出)  


您不应该这样做！Memcached是一个非阻塞的服务器。任何可能导致Memcached暂停或瞬时拒绝服务的操作都应该值得深思熟虑。向 Memcached中批量导入数据往往不是您真正想要的！想象看，如果缓存数据在导出导入之间发生了变化，您就需要处理脏数据了；


### [2、Memcached的内存分配器是如何工作的？为什么不适用malloc/free！？为何要使用slabs？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#2memcached的内存分配器是如何工作的为什么不适用malloc/free为何要使用slabs)  


实际上，这是一个编译时选项。默认会使用内部的slab分配器。您确实确实应该使用内建的slab分配器。最早的时候，Memcached只使用 malloc/free来管理内存。然而，这种方式不能与OS的内存管理以前很好地工作。反复地malloc/free造成了内存碎片，OS最终花费大量的时间去查找连续的内存块来满足malloc的请求，而不是运行Memcached进程。如果您不同意，当然可以使用malloc！只是不要在邮件列表中抱怨啊

slab分配器就是为了解决这个问题而生的。内存被分配并划分成chunks，一直被重复使用。因为内存被划分成大小不等的slabs，如果item 的大小与被选择存放它的slab不是很合适的话，就会浪费一些内存。Steven Grimm正在这方面已经做出了有效的改进。


### [3、Memcached服务在企业集群架构中有哪些应用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#3memcached服务在企业集群架构中有哪些应用场景)  


**一、作为数据库的前端缓存应用**

**a、完整缓存（易），静态缓存**

例如：商品分类（京东），以及商品信息，可事先放在内存里，然后再对外提供数据访问，这种先放到内存，我们称之为预热，（先把数据存缓存中），用户访问时可以只读取Memcached缓存，不读取数据库了。

**b、执点缓存（难）**

需要前端web程序配合，只缓存热点的数据，即缓存经常被访问的数据。

先预热数据库里的基础数据，然后在动态更新，选读取缓存，如果缓存里没有对应的数据，程序再去读取数据库，然后程序把读取的新数据放入缓存存储。

**特殊说明 ：**

**1、** 如果碰到电商秒杀等高并发的业务，一定要事先预热，或者其它思想实现，例如：称杀只是获取资格，而不是瞬间秒杀到手商品。

那么什么是获取资格？_

**2、** 就是在数据库中，把0标成1.就有资格啦。再慢慢的去领取商品订单。因为秒杀过程太长会占用服务器资源。

**3、** 如果数据更新，同时触发缓存更新，防止给用户过期数据。

**4、** 对于持久化缓存存储系统，例如：Redis，可以替代一部分数据库的存储，一些简单的数据业务，投票，统计，好友关注，商品分类等。nosql= not only sql

**二、作业集群的session会话共享存储**

**1、** Memcached服务在不同企业业务应用场景中的工作流程

当web程序需要访问后端数据库获取数据时会优先访问Memcached内存缓存，如果缓存中有数据就直接获取返回前端服务及用户，如果没有数据（没有命中），在由程序请求后端的数据库服务器，获取到对应的数据后，除了返回给前端服务及用户数据外，还会把数据放到Memcached内存中进行缓存，等待下次请求被访问，Memcache内存始终是数据库的挡箭牌，从而大大的减轻数据库的访问压力，提高整个网站架构的响应速度，提升了用户体验。

当程序更新，修改或删除数据库中已有的数据时，会同时发送请求通知Memcached已经缓存的同一个ID内容的旧数据失效，从而保证Memcache中数据和数据库中的数据一致。

如果在高并发场合，除了通知Memcached过程的缓存失效外，还会通过相关机制，使得在用户访问新数据前，通过程序预先把更新过的数据推送到memcache中缓存起来，这样可以减少数据库的访问压力，提升Memcached中缓存命中率。

数据库插件可以再写入更新数据库后，自动抛给MC缓存起来，自身不Cache.

**2、** Memcached服务分布式集群如何实现？

**特殊说明：**

Memcached集群和web服务集群是不一样的，所有Memcached的数据总和才是数据库的数据。每台Memcached都是部分数据。

（一台Memcached的数据，就是一部分MySQL数据库的数据）

**1、** 程序端实现

程序加载所有mc的ip列表，通过对key做hash (一致性哈希算法)

例如：web1 (key)===>对应A,B,C,D,E,F,G…..若干台服务器。（通过哈希算法实现）

**2、** 负载均衡器

通过对key做hash (一致性哈希算法)

一致哈希算法的目的是不但保证每个对象只请求一个对应的服务器，而且当节点宕机，缓存服务器的更新重新分配比例降到最低。


### [4、如果缓存数据在导出导入之间过期了，您又怎么处理这些数据呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#4如果缓存数据在导出导入之间过期了您又怎么处理这些数据呢)  


因此，批量导出导入数据并不像您想象中的那么有用。不过在一个场景倒是很有用。如果您有大量的从不变化的数据，并且希望缓存很快热（warm）起来，批量导入缓存数据是很有帮助的。虽然这个场景并不典型，但却经常发生，因此我们会考虑在将来实现批量导出导入的功能。

如果一个Memcached节点down了让您很痛苦，那么您还会陷入其他很多麻烦。您的系统太脆弱了。您需要做一些优化工作。比如处理”惊群”问题（比如 Memcached节点都失效了，反复的查询让您的数据库不堪重负…这个问题在FAQ的其他提到过），或者优化不好的查询。记住，Memcached 并不是您逃避优化查询的借口。


### [5、Memcached是怎么工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#5memcached是怎么工作的)  


Memcached的神奇来自两阶段哈希（two-stage hash）。Memcached就像一个巨大的、存储了很多`<key,value>`对的哈希表。通过key，可以存储或查询任意的数据。

客户端可以把数据存储在多台Memcached上。当查询数据时，客户端首先参考节点列表计算出key的哈希值（阶段一哈希），进而选中一个节点；客户端将请求发送给选中的节点，然后Memcached节点通过一个内部的哈希算法（阶段二哈希），查找真正的数据（item）。


### [6、Memcached服务特点及工作原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#6memcached服务特点及工作原理是什么)  


**1、** 完全基于内存缓存的

**2、** 节点之间相互独立

**3、** C/S模式架构，C语言编写，总共2000行代码。

**4、** 异步Ｉ/O 模型，使用libevent作为事件通知机制。

**5、** 被缓存的数据以key/value键值对形式存在的。

**6、** 全部数据存放于内存中，无持久性存储的设计，重启服务器，内存里的数据会丢失。

**7、** 当内存中缓存的数据容量达到启动时设定的内存值时，就自动使用LRU算法删除过期的缓存数据。

**8、** 可以对存储的数据设置过期时间，这样过期后的数据自动被清除，服务本身不会监控过期，而是在访问的时候查看key的时间戳,判断是否过期。

**9、** memcache会对设定的内存进行分块，再把块分组，然后再提供服务。


### [7、Memcached最大的优势是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#7memcached最大的优势是什么)  


Memcached最大的好处就是它带来了极佳的水平可扩展性，特别是在一个巨大的系统中。由于客户端自己做了一次哈希，那么我们很容易增加大量Memcached到集群中。Memcached之间没有相互通信，因此不会增加 Memcached的负载；没有多播协议，不会网络通信量爆炸（implode）。Memcached的集群很好用。内存不够了？增加几台Memcached吧；CPU不够用了？再增加几台吧；有多余的内存？在增加几台吧，不要浪费了。

基于Memcached的基本原则，可以相当轻松地构建出不同类型的缓存架构。除了这篇FAQ，在其他地方很容易找到详细资料的。


### [8、Memcached如何处理容错的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#8memcached如何处理容错的)  


不处理！在Memcached节点失效的情况下，集群没有必要做任何容错处理。如果发生了节点失效，应对的措施完全取决于用户。

**节点失效时，下面列出几种方案供您选择：**

**1、** 忽略它！ 在失效节点被恢复或替换之前，还有很多其他节点可以应对节点失效带来的影响。

**2、** 把失效的节点从节点列表中移除。做这个操作千万要小心！在默认情况下（余数式哈希算法），客户端添加或移除节点，会导致所有的缓存数据不可用！因为哈希参照的节点列表变化了，大部分key会因为哈希值的改变而被映射到（与原来）不同的节点上。

**3、** 启动热备节点，接管失效节点所占用的IP。这样可以防止哈希紊乱（hashing chaos）。

**4、** 如果希望添加和移除节点，而不影响原先的哈希结果，可以使用一致性哈希算法（consistent hashing）。您可以百度一下一致性哈希算法。支持一致性哈希的客户端已经很成熟，而且被广泛使用。去尝试一下吧！

**5、** 两次哈希（reshing）。当客户端存取数据时，如果发现一个节点down了，就再做一次哈希（哈希算法与前一次不同），重新选择另一个节点（需要注意的时，客户端并没有把down的节点从节点列表中移除，下次还是有可能先哈希到它）。如果某个节点时好时坏，两次哈希的方法就有风险了，好的节点和坏的节点上都可能存在脏数据（stale data）。


### [9、Memcached的多线程是什么？如何使用它们？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#9memcached的多线程是什么如何使用它们)  


线程就是定律（threads rule）！在Steven Grimm和Facebook的努力下，Memcached 1.2及更高版本拥有了多线程模式。多线程模式允许Memcached能够充分利用多个CPU，并在CPU之间共享所有的缓存数据。Memcached使用一种简单的锁机制来保证数据更新操作的互斥。相比在同一个物理机器上运行多个Memcached实例，这种方式能够更有效地处理multi gets。

如果您的系统负载并不重，也许您不需要启用多线程工作模式。如果您在运行一个拥有大规模硬件的、庞大的网站，您将会看到多线程的好处。

简单地总结一下：命令解析（Memcached在这里花了大部分时间）可以运行在多线程模式下。Memcached内部对数据的操作是基于很多全局锁的（因此这部分工作不是多线程的）。未来对多线程模式的改进，将移除大量的全局锁，提高Memcached在负载极高的场景下的性能。


### [10、Memcached是原子的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#10memcached是原子的吗)  


所有的被发送到Memcached的单个命令是完全原子的。如果您针对同一份数据同时发送了一个set命令和一个get命令，它们不会影响对方。它们将被串行化、先后执行。即使在多线程模式，所有的命令都是原子的，除非程序有bug:)

命令序列不是原子的。如果您通过get命令获取了一个item，修改了它，然后想把它set回Memcached，我们不保证这个item没有被其他进程（process，未必是操作系统中的进程）操作过。在并发的情况下，您也可能覆写了一个被其他进程set的item。

Memcached 1.2.5以及更高版本，提供了gets和cas命令，它们可以解决上面的问题。如果您使用gets命令查询某个key的item，Memcached会给您返回该item当前值的唯一标识。如果您覆写了这个item并想把它写回到Memcached中，您可以通过cas命令把那个唯一标识一起发送给 Memcached。如果该item存放在Memcached中的唯一标识与您提供的一致，您的写操作将会成功。如果另一个进程在这期间也修改了这个 item，那么该item存放在Memcached中的唯一标识将会改变，您的写操作就会失败


### [11、Memcached能够更有效地使用内存吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#11memcached能够更有效地使用内存吗)  

### [12、如何实现集群中的session共享存储？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#12如何实现集群中的session共享存储)  

### [13、Memcached最大能存储多大的单个item？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#13memcached最大能存储多大的单个item)  

### [14、Memcached的cache机制是怎样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#14memcached的cache机制是怎样的)  

### [15、什么是二进制协议，我该关注吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#15什么是二进制协议我该关注吗)  

### [16、Memcached是如何做身份验证的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#16memcached是如何做身份验证的)  

### [17、Memcached能接受的key的最大长度是多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#17memcached能接受的key的最大长度是多少)  

### [18、Memcached是什么，有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#18memcached是什么有什么作用)  

### [19、简述Memcached内存管理机制原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#19简述memcached内存管理机制原理)  

### [20、Memcached与Redis的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#20memcached与redis的区别)  

### [21、Memcached和MySQL的query](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#21memcached和mysql的query)  

### [22、Memcached如何实现冗余机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#22memcached如何实现冗余机制)  

### [23、Memcached和服务器的local cache（比如PHP的APC、mmap文件等）相比，有什么优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Memcached/Memcached面试题带答案（2021年Memcached面试题及答案大汇总）.md#23memcached和服务器的local-cache比如php的apcmmap文件等相比有什么优缺点)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
