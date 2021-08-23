# Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）

Linux面试题及答案【最新版】Linux高级面试题大全(2021版)，发现网上很多Linux面试题及答案整理都没有答案，所以花了很长时间搜集，本套Linux面试题大全，Linux面试题大汇总，有大量经典的Linux面试题以及答案，包含Linux语言常见面试题、Linux工程师高级面试题及一些大厂Linux开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Linux面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Linux面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何停止一个进程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#1如何停止一个进程)  


kill命令被用来给程序发送信号。如果没有指定信号，默认发送TERM(终止）信号。

语法 : kill [-signal] PID …

![80_4.png][80_4.png]image-20200421141556974


### [2、使用哪一个命令可以查看自己文件系统的磁盘空间配额呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#2使用哪一个命令可以查看自己文件系统的磁盘空间配额呢)  


**答案：**

使用命令repquota 能够显示出一个文件系统的配额信息

【附】只有root用户才能够查看其它用户的配额。


### [3、查看已有别名?建立属于自己的别名?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#3查看已有别名建立属于自己的别名)  


alias -p 查看当前可用别名

```
[root@iz2ze76ybn73dvwmdij06zz ~]# alias -p
alias cp='cp -i'
alias egrep='egrep —color=auto'
alias fgrep='fgrep —color=auto'
alias grep='grep —color=auto'
alias l.='ls -d .* —color=auto'
alias ll='ls -l —color=auto'
```

alias li = 'ls -li' 创建别名


### [4、如何查看目录中的文件？区分哪些是文件哪些是目录?递归查?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#4如何查看目录中的文件区分哪些是文件哪些是目录递归查)  


ls 命令会用最基本的形式显示当前目录下的文件和目录：

```
?  local ls
Caskroom   Frameworks bin        go         lib        sbin       var
Cellar     Homebrew   etc        include    opt        share
```

可以看出默认是按照字母序展示的

一般来说，ls命令回显示不同的颜色区分不同的文件类型,如果没有安装颜色插件可以用ls -F来区分哪些是目录（目录带/)，哪些是文件（文件不带/)

ls -R 递归展示出目录下以及子目录的文件，目录越多输出越多


### [5、什么是硬链接和软链接？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#5什么是硬链接和软链接)  


**硬链接**：

由于 Linux 下的文件是通过索引节点(inode)来识别文件，硬链接可以认为是一个指针，指向文件索引节点的指针，系统并不为它重新分配 inode 。每添加一个一个硬链接，文件的链接数就加 1 。

**不足：**

**1、** 不可以在不同文件系统的文件间建立链接；

**2、** 只有超级用户才可以为目录创建硬链接。

**软链接**：

软链接克服了硬链接的不足，没有任何文件系统的限制，任何用户可以创建指向目录的符号链接。因而现在更为广泛使用，它具有更大的灵活性，甚至可以跨越不同机器、不同网络对文件进行链接。

**不足：**

因为链接文件包含有原文件的路径信息，所以当原文件从一个目录下移到其他目录中，再访问链接文件，系统就找不到了，而硬链接就没有这个缺陷，你想怎么移就怎么移；还有它要系统分配额外的空间用于建立新的索引节点和保存原文件的路径。

**实际场景下，基本是使用软链接**。

总结区别如下：

**1、** 硬链接不可以跨分区，软件链可以跨分区。

**2、** 硬链接指向一个 inode 节点，而软链接则是创建一个新的 inode 节点。

**3、** 删除硬链接文件，不会删除原文件，删除软链接文件，会把原文件删除。


### [6、ifconfig命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#6ifconfig命令)  


```
用于查看和更改网络接口的地址和参数，包括IP地址、网络掩码、广播地址，使用权限是超级用户。（一般是用来查看的，很少更改）
如果此命令输入无效，先输入yum -y install net-tools
ifconfig
```


### [7、开源的优势是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#7开源的优势是什么)  


开源允许你将软件（包括源代码）免费分发给任何感兴趣的人。然后，人们可以添加功能，甚至可以调试和更正源代码中的错误。它们甚至可以让它运行得更好，然后再次自由地重新分配这些增强的源代码。这最终使社区中的每个人受益。


### [8、数据字典属于哪一个用户的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#8数据字典属于哪一个用户的)  


**答案：**

数据字典是属于’SYS’用户的，用户‘SYS’ 和 ’SYSEM’是由系统默认自动创建的


### [9、Linux 中进程有哪几种状态？在 ps 显示出来的信息中，分别用什么符号表示的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#9linux-中进程有哪几种状态在-ps-显示出来的信息中分别用什么符号表示的)  


**答案：**

**1、** 不可中断状态：进程处于睡眠状态，但是此刻进程是不可中断的。不可中断， 指进程不响应异步信号。

**2、** 暂停状态/跟踪状态：向进程发送一个 SIGSTOP 信号，它就会因响应该信号 而进入 TASK_STOPPED 状态;当进程正在被跟踪时，它处于 TASK_TRACED 这个特殊的状态。

正被跟踪”指的是进程暂停下来，等待跟踪它的进程对它进行操作。

**3、** 就绪状态：在 run_queue 队列里的状态

**4、** 运行状态：在 run_queue 队列里的状态

**5、** 可中断睡眠状态：处于这个状态的进程因为等待某某事件的发生（比如等待 socket 连接、等待信号量），而被挂起

**6、** zombie 状态（僵尸）：父亲没有通过 wait 系列的系统调用会顺便将子进程的尸体（task_struct）也释放掉

**7、** 退出状态

> D 不可中断 Uninterruptible（usually IO）

R 正在运行，或在队列中的进程

S 处于休眠状态

T 停止或被追踪

Z 僵尸进程

W 进入内存交换（从内核 2.6 开始无效）

X 死掉的进程



### [10、你对现在运维工程师的理解和以及对其工作的认识](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#10你对现在运维工程师的理解和以及对其工作的认识)  


运维工程师在公司当中责任重大，需要保证时刻为公司及客户提供最高、最快、最稳定、最安全的服务

运维工程师的一个小小的失误，很有可能会对公司及客户造成重大损失

因此运维工程师的工作需要严谨及富有创新精神


### [11、默认进程信息显示?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#11默认进程信息显示)  

### [12、讲一下Keepalived的工作原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#12讲一下keepalived的工作原理)  

### [13、删除文件用哪个命令？如果需要连目录及目录下文件一块删除呢？删除空文件夹用什么命令？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#13删除文件用哪个命令如果需要连目录及目录下文件一块删除呢删除空文件夹用什么命令)  

### [14、在工作中，运维人员经常需要跟运营人员打交道，请问运营人员是做什么工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#14在工作中运维人员经常需要跟运营人员打交道请问运营人员是做什么工作的)  

### [15、如何用sed只打印第5行?删除第一行？替换字符串?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#15如何用sed只打印第5行删除第一行替换字符串)  

### [16、Linux 性能调优都有哪几种方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#16linux-性能调优都有哪几种方法)  

### [17、vim （VI IMproved：改进版视觉）改进版文本编辑器 （不管是文件查看还是文件编辑 按 Shift + 上或者下可以上下移动查看视角）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#17vim-vi-improved：改进版视觉改进版文本编辑器-不管是文件查看还是文件编辑-按-shift-+-上或者下可以上下移动查看视角)  

### [18、如何用awk查看第2行倒数第3个字段?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#18如何用awk查看第2行倒数第3个字段)  

### [19、Linux 开机启动过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#19linux-开机启动过程)  

### [20、Linux 的目录结构是怎样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#20linux-的目录结构是怎样的)  

### [21、怎样一页一页地查看一个大文件的内容呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#21怎样一页一页地查看一个大文件的内容呢)  

### [22、终止进程用什么命令? 带什么参数?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#22终止进程用什么命令-带什么参数)  

### [23、什么叫 CC 攻击？什么叫 DDOS 攻击？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#23什么叫-cc-攻击什么叫-ddos-攻击)  

### [24、绝对路径用什么符号表示？当前目录、上层目录用什么表示？主目录用什么表示? 切换目录用什么命令？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#24绝对路径用什么符号表示当前目录上层目录用什么表示主目录用什么表示-切换目录用什么命令)  

### [25、bash shell 中的hash 命令有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#25bash-shell-中的hash-命令有什么作用)  

### [26、什么是中间件？什么是jdk？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#26什么是中间件什么是jdk)  

### [27、建立软链接(快捷方式)，以及硬链接的命令。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#27建立软链接快捷方式以及硬链接的命令。)  

### [28、查看设备还有多少磁盘空间?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#28查看设备还有多少磁盘空间)  

### [29、查看文件类型?字符编码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题附答案汇总（2021年Linux面试题及答案大全）.md#29查看文件类型字符编码)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
