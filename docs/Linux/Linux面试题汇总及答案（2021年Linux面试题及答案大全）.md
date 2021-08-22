# Linux面试题汇总及答案（2021年Linux面试题及答案大全）

Linux面试题及答案【最新版】Linux高级面试题大全(2021版)，发现网上很多Linux面试题及答案整理都没有答案，所以花了很长时间搜集，本套Linux面试题大全，Linux面试题大汇总，有大量经典的Linux面试题以及答案，包含Linux语言常见面试题、Linux工程师高级面试题及一些大厂Linux开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Linux面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Linux面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、你常用的Nginx模块，用来做什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#1你常用的nginx模块用来做什么)  


**1、** rewrite模块，实现重写功能

**2、** access模块：来源控制

**3、** ssl模块：安全加密

**4、** ngx_http_gzip_module：网络传输压缩模块

**5、** ngx_http_proxy_module 模块实现代理

**6、** ngx_http_upstream_module模块实现定义后端服务器列表

**7、** ngx_cache_purge实现缓存清除功能


### [2、简述raid0 raid1 raid5 三种工作模式的工作原理及特点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#2简述raid0-raid1-raid5-三种工作模式的工作原理及特点)  


RAID，可以把硬盘整合成一个大磁盘，还可以在大磁盘上再分区，放数据

还有一个大功能，多块盘放在一起可以有冗余（备份）

RAID整合方式有很多，常用的：0 1 5 10

RAID 0，可以是一块盘和N个盘组合

其优点读写快，是RAID中最好的

缺点：没有冗余，一块坏了数据就全没有了

RAID 1，只能2块盘，盘的大小可以不一样，以小的为准

10G+10G只有10G，另一个做备份。它有100%的冗余，缺点：浪费资源，成本高

RAID 5 ，3块盘，容量计算10*（n-1）,损失一块盘

特点，读写性能一般，读还好一点，写不好

冗余从好到坏：RAID1 RAID10 RAID 5 RAID0

性能从好到坏：RAID0 RAID10 RAID5 RAID1

成本从低到高：RAID0 RAID5 RAID1 RAID10

单台服务器：很重要盘不多，系统盘，RAID1

数据库服务器：主库：RAID10 从库 RAID5RAID0（为了维护成本，RAID10）

WEB服务器，如果没有太多的数据的话，RAID5,RAID0（单盘）

有多台，监控、应用服务器，RAID0 RAID5

我们会根据数据的存储和访问的需求，去匹配对应的RAID级别


### [3、Linux系统安装多个桌面环境有帮助吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#3linux系统安装多个桌面环境有帮助吗)  


通常，一个桌面环境，如KDE或Gnome，足以在没有问题的情况下运行。尽管系统允许从一个环境切换到另一个环境，但这对用户来说都是优先考虑的问题。有些程序在一个环境中工作而在另一个环境中无法工作，因此它也可以被视为选择使用哪个环境的一个因素。


### [4、mv（move单词缩写，移动功能，该文件名称功能）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#4mvmove单词缩写移动功能该文件名称功能)  


```
mv /opt/java/java.log /opt/MySQL/ ;移动文件到MySQL目录下
mv java.log MySQL.log ;把java.log改名为MySQL.log
```


### [5、统计ip访问情况，要求分析nginx访问日志，找出访问页面数量在前十位的ip](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#5统计ip访问情况要求分析nginx访问日志找出访问页面数量在前十位的ip)  


cat access.log | awk '{print $1}' | uniq -c | sort -rn | head -10


### [6、Linux 的体系结构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#6linux-的体系结构)  


从大的方面讲，Linux 体系结构可以分为两块：

![55_2.png][55_2.png]

**用户空间(User Space) ：**用户空间又包括用户的应用程序(User Applications)、C 库(C Library) 。

**内核空间(Kernel Space) ：**内核空间又包括系统调用接口(System Call Interface)、内核(Kernel)、平台架构相关的代码(Architecture-Dependent Kernel Code) 。

**为什么 Linux 体系结构要分为用户空间和内核空间的原因？**

**1、** 现代 CPU 实现了不同的工作模式，不同模式下 CPU 可以执行的指令和访问的寄存器不同。

**2、** Linux 从 CPU 的角度出发，为了保护内核的安全，把系统分成了两部分。

用户空间和内核空间是程序执行的**两种不同的状态**，我们可以通过两种方式完成用户空间到内核空间的转移：

**1、** 系统调用

**2、** 硬件中断


### [7、验证网络可链接命令是什么？什么原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#7验证网络可链接命令是什么什么原理)  


ping。这个 ping 命令发送一个特殊的网络数据包(叫做 IMCP ECHO REQUEST)到一台指定的主机。大多数接收这个包的网络设备将会回复它，来允许网络连接验证。

![80_5.png][80_5.png]image-20200421142307602

一旦启动，ping会持续在特定时间（默认1秒）发送数据包。


### [8、创建文件？创建目录？批量创建?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#8创建文件创建目录批量创建)  


创建文件:touch 文件名

批量创建文件: touch 文件名 文件名 …

```
?  test touch a
?  test ls
a
?  test touch b c
?  test ls
a b c
```

创建目录：mkdir 目录名

批量创建目录: mkdir 目录名 目录名 …

```
?  test mkdir aa
?  test mkdir bb cc
?  test ls
a  aa b  bb c  cc
?  test ls -F
a   aa/ b   bb/ c   cc/
```


### [9、top 命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#9top-命令)  


```
#显示当前系统正在执行的进程的相关信息，包括进程 ID、内存占用率、CPU 占用率等
-c 显示完整的进程命令
-s 保密模式
-p <进程号> 指定进程显示
-n <次数>循环显示次数
```


### [10、如何执行可以执行文件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#10如何执行可以执行文件)  


```
[root@xiaoka ~]# sh sleep.sh
hello,xiaoka
[root@xiaoka ~]# ./sleep.sh
hello,xiaoka
```


### [11、怎么对命令进行取别名？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#11怎么对命令进行取别名)  

### [12、怎么使一个命令在后台运行?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#12怎么使一个命令在后台运行)  

### [13、查看组信息？如何创建组？删除组？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#13查看组信息如何创建组删除组)  

### [14、less （lese：较少的意思）分页查看文件命令（可以快速定位到最后一页）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#14less-lese：较少的意思分页查看文件命令可以快速定位到最后一页)  

### [15、Linux 使用的进程间通信方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#15linux-使用的进程间通信方式)  

### [16、查看当前谁在使用该主机用什么命令? 查找自己所在的终端信息用什么命令?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#16查看当前谁在使用该主机用什么命令-查找自己所在的终端信息用什么命令)  

### [17、什么是Linux](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#17什么是linux)  

### [18、什么是环境变量？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#18什么是环境变量)  

### [19、什么是 inode ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#19什么是-inode-)  

### [20、如何查看当前主机名？如何修改？如何重启后生效？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#20如何查看当前主机名如何修改如何重启后生效)  

### [21、如果你的助手想要打印出当前的目录栈，你会建议他怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#21如果你的助手想要打印出当前的目录栈你会建议他怎么做)  

### [22、登陆后你在的位置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#22登陆后你在的位置)  

### [23、Unix和Linux有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#23unix和linux有什么区别)  

### [24、讲述一下Tomcat8005、8009、8080三个端口的含义？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#24讲述一下tomcat800580098080三个端口的含义)  

### [25、说说TCP/IP的七层模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#25说说tcp/ip的七层模型)  

### [26、请执行命令取出 linux 中 eth0 的 IP 地址(请用 cut，有能力者也可分别用 awk,sed 命令答)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#26请执行命令取出-linux-中-eth0-的-ip-地址请用-cut有能力者也可分别用-awk,sed-命令答)  

### [27、打印文件第一行到第三行?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#27打印文件第一行到第三行)  

### [28、交互方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#28交互方式)  

### [29、如何切换目录？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题汇总及答案（2021年Linux面试题及答案大全）.md#29如何切换目录)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
