# Linux面试题附答案汇总（2021年Linux面试题及答案大全）

Linux面试题及答案【最新版】Linux高级面试题大全(2021版)，发现网上很多Linux面试题及答案整理都没有答案，所以花了很长时间搜集，本套Linux面试题大全，Linux面试题大汇总，有大量经典的Linux面试题以及答案，包含Linux语言常见面试题、Linux工程师高级面试题及一些大厂Linux开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Linux面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Linux面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、如何写一条规则，拒绝某个ip访问本机8080端口?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#1如何写一条规则拒绝某个ip访问本机8080端口)  


```
iptables -I INPUT -s ip -p tcp —dport 8080 -j REJECT
```


### [2、更改为北京时间命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#2更改为北京时间命令)  


```
rm -rf /etc/localtime
ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```


### [3、RAID 是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#3raid-是什么)  


RAID 全称为独立磁盘冗余阵列(Redundant Array of Independent Disks)，基本思想就是把多个相对便宜的硬盘组合起来，成为一个硬盘阵列组，使性能达到甚至超过一个价格昂贵、 容量巨大的硬盘。RAID 通常被用在服务器电脑上，使用完全相同的硬盘组成一个逻辑扇区，因此操作系统只会把它当做一个硬盘。

RAID 分为不同的等级，各个不同的等级均在数据可靠性及读写性能上做了不同的权衡。在实际应用中，可以依据自己的实际需求选择不同的 RAID 方案。

当然，因为很多公司都使用云服务，大家很难接触到 RAID 这个概念，更多的可能是普通云盘、SSD 云盘酱紫的概念。


### [4、MySQL的innodb如何定位锁问题，MySQL如何减少主从复制延迟？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#4mysql的innodb如何定位锁问题mysql如何减少主从复制延迟)  


MySQL的innodb如何定位锁问题:

在使用 show engine innodb status检查引擎状态时，发现了死锁问题

在5.5中，information_schema 库中增加了三个关于锁的表（MEMORY引擎）

innodb_trx ? ? ? ? ## 当前运行的所有事务

innodb_locks ? ? ## 当前出现的锁

innodb_lock_waits ?## 锁等待的对应关系

MySQL如何减少主从复制延迟:

**如果延迟比较大，就先确认以下几个因素：**

**1、** 从库硬件比主库差，导致复制延迟

**2、** 主从复制单线程，如果主库写并发太大，来不及传送到从库就会导致延迟。更高版本的MySQL可以支持多线程复制

**3、** 慢SQL语句过多

**4、** 网络延迟

**5、** master负载

主库读写压力大，导致复制延迟，架构的前端要加buffer及缓存层

**6、** slave负载

一般的做法是，使用多台slave来分摊读请求，再从这些slave中取一台专用的服务器

只作为备份用，不进行其他任何操作.另外， 2个可以减少延迟的参数:

–slave-net-timeout=seconds 单位为秒 默认设置为 3600秒

参数含义：当slave从主数据库读取log数据失败后，等待多久重新建立连接并获取数据

–master-connect-retry=seconds 单位为秒 默认设置为 60秒

参数含义：当重新建立主从连接时，如果连接建立失败，间隔多久后重试

通常配置以上2个参数可以减少网络问题导致的主从数据同步延迟

MySQL数据库主从同步延迟解决方案

最简单的减少slave同步延时的方案就是在架构上做优化，尽量让主库的DDL快速执行

还有就是主库是写，对数据安全性较高，比如sync_binlog=1，innodb_flush_log_at_trx_commit

= 1 之类的设置，而slave则不需要这么高的数据安全，完全可以讲sync_binlog设置为0或者关闭binlog

innodb_flushlog也可以设置为0来提高sql的执行效率。另外就是使用比主库更好的硬件设备作为slave


### [5、grep （grep ：正则表达式）正则表达式，用于字符串的搜索工作(模糊查询)。不懂可以先过](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#5grep-grep-：正则表达式正则表达式用于字符串的搜索工作模糊查询。不懂可以先过)  


```
单独使用：
grep String test.java ；在test.java文件中查找String的位置，返回整行
一般此命令不会单独使用下面列几个常用的命令（地下通过管道命令组合起来使用）

ps aux|grep java ；查找带java关键字的进程
ll |grep java ；查找带java关键字的文件夹及文件
```


### [6、压缩工具有哪些?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#6压缩工具有哪些)  


![80_1.png][80_1.png]image-20200421122324314


### [7、目录创建用什么命令？创建文件用什么命令？复制文件用什么命令？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#7目录创建用什么命令创建文件用什么命令复制文件用什么命令)  


**答案：**

**1、** 创建目录： mkdir

**2、** 创建文件：典型的如 touch，vi 也可以创建文件，其实只要向一个不存在的文件输出，都会创建文件

**3、** 复制文件： cp 7、文件权限修改用什么命令？格式是怎么样的？

**4、** 文件权限修改： chmod

**格式如下：**

**1、** chmodu+xfile给file的属主增加执行权限 chmod 751 file 给 file 的属主分配读、写、执行(7)的权限，给 file 的所在组分配读、执行(5)的权限，给其他用户分配执行(1)的权限

**2、** chmodu=rwx,g=rx,o=xfile上例的另一种形式 chmod =r file 为所有用户分配读权限

**3、** chmod444file同上例 chmod a-wx,a+r file同上例

**4、** $ chmod -R u+r directory 递归地给 directory 目录下所有文件和子目录的属主分配读的权限


### [8、如何规划一台 Linux 主机，步骤是怎样？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#8如何规划一台-linux-主机步骤是怎样)  


确定机器是做什么用的，比如是做 WEB 、DB、还是游戏服务器。

> 不同的用途，机器的配置会有所不同。


**1、** 确定好之后，就要定系统需要怎么安装，默认安装哪些系统、分区怎么做。

**2、** 需要优化系统的哪些参数，需要创建哪些用户等等的。


### [9、实时监测进程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#9实时监测进程)  


与ps相比，top可以实时监控进程信息。

![80_3.png][80_3.png]image-20200421114633852

平均负载有3个值:最近1分钟的、最近5分钟的和最近15分钟的平均负载。值越大说明系统 的负载越高。由于进程短期的突发性活动，出现最近1分钟的高负载值也很常见，但如果近15分 钟内的平均负载都很高，就说明系统可能有问题。


### [10、关机linux](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#10关机linux)  


```
Linux centos 关机命令：halt
```


### [11、随意写文件命令？怎么向屏幕输出带空格的字符串，比如”hello world”?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#11随意写文件命令怎么向屏幕输出带空格的字符串比如hello-world)  

### [12、如何优化 Linux系统（可以不说太具体）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#12如何优化-linux系统可以不说太具体)  

### [13、每天晚上 12 点，打包站点目录/var/www/html 备份到/data 目录下（最好每次备份按时间生成不同的备份包）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#13每天晚上-12-点打包站点目录/var/www/html-备份到/data-目录下最好每次备份按时间生成不同的备份包)  

### [14、用什么命令对一个文件的内容进行统计？(行号、单词数、字节数)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#14用什么命令对一个文件的内容进行统计行号单词数字节数)  

### [15、怎么查看系统支持的所有信号？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#15怎么查看系统支持的所有信号)  

### [16、什么叫CDN？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#16什么叫cdn)  

### [17、如何查找匹配的文件？基于文件属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#17如何查找匹配的文件基于文件属性)  

### [18、如何查看命令历史记录?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#18如何查看命令历史记录)  

### [19、复制文件用哪个命令？如果需要连同文件夹一块复制呢？如果需要有提示功能呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#19复制文件用哪个命令如果需要连同文件夹一块复制呢如果需要有提示功能呢)  

### [20、keepalive的工作原理和如何做到健康检查](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#20keepalive的工作原理和如何做到健康检查)  

### [21、lvs/nginx/haproxy优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#21lvs/nginx/haproxy优缺点)  

### [22、查看整个文件？按照有文本显示行号？无文本显示行号？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#22查看整个文件按照有文本显示行号无文本显示行号)  

### [23、Ls 命令执行什么功能？ 可以带哪些参数，有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#23ls-命令执行什么功能-可以带哪些参数有什么区别)  

### [24、Shell 脚本是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#24shell-脚本是什么)  

### [25、简述DNS进行域名解析的过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#25简述dns进行域名解析的过程)  

### [26、如何压缩文件？如何解压文件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#26如何压缩文件如何解压文件)  

### [27、查看http的并发请求数与其TCP连接状态](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#27查看http的并发请求数与其tcp连接状态)  

### [28、find （find：找到的意思）查找指定文件或目录](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#28find-find：找到的意思查找指定文件或目录)  

### [29、GNU项目的重要性是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案汇总（2021年Linux面试题及答案大全）.md#29gnu项目的重要性是什么)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
