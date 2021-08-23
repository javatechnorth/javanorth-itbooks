# Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）

Linux面试题及答案【最新版】Linux高级面试题大全(2021版)，发现网上很多Linux面试题及答案整理都没有答案，所以花了很长时间搜集，本套Linux面试题大全，Linux面试题大汇总，有大量经典的Linux面试题以及答案，包含Linux语言常见面试题、Linux工程师高级面试题及一些大厂Linux开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Linux面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Linux面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、tail（尾巴） 查看文件命令（看最后多少行）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#1tail尾巴-查看文件命令看最后多少行)  


```
tail -10 ;文件名 看最后10行
```


### [2、8.迷路，我的当前位置在哪？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#28迷路我的当前位置在哪)  


pwd 显示当前目录

```
[root@iz2ze76ybn73dvwmdij06zz local]# pwd
/usr/local
```


### [3、vim编辑器几种操作模式？基本操作?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#3vim编辑器几种操作模式基本操作)  


操作模式:

**1、** 普通模式

**2、** 插入模式

基础操作:

**1、** h:左移一个字符。

**2、** j:下移一行(文本中的下一行)。

**3、** k:上移一行(文本中的上一行)。

**4、** l:右移一个字符。

vim提供了一些能够提高移动速度的命令:

**1、** PageDown(或Ctrl+F):下翻一屏

**2、** PageUp(或Ctrl+B):上翻一屏。

**3、** G:移到缓冲区的最后一行。

**4、** num G:移动到缓冲区中的第num行。

**5、** gg:移到缓冲区的第一行。

退出vim:

**1、** q:如果未修改缓冲区数据，退出。

**2、** q!:取消所有对缓冲区数据的修改并退出。

**3、** w filename:将文件保存到另一个文件中。

**4、** wq:将缓冲区数据保存到文件中并退出。


### [4、重新命名文件？移动文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#4重新命名文件移动文件)  


语法 ： mv soucre target

重命名:

```
?  xktest ls
?  xktest touch java
?  xktest ls
java
?  xktest mv java java1.8
?  xktest ls
java1.8
```

移动文件:

新建jdk目录把java1.8文件移动到jdk目录下。

```
?  xktest ls
java1.8
?  xktest mkdir jdk
?  xktest mv java1.8 jdk
?  xktest ls -R
jdk
 ./jdk:
java1.8
```


### [5、你的系统目前有许多正在运行的任务，在不重启机器的条件下，有什么方法可以把所有正在运行的进程移除呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#5你的系统目前有许多正在运行的任务在不重启机器的条件下有什么方法可以把所有正在运行的进程移除呢)  


**答案：**

使用linux命令 ’disown -r ’可以将所有正在运行的进程移除。


### [6、如何中断一个进程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#6如何中断一个进程)  


在一个终端中， Ctrl + c

通过这个命令许多（不是全部）命令行程序都可以被中断。


### [7、Linux 有哪些系统日志文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#7linux-有哪些系统日志文件)  


比较重要的是 `/var/log/messages` 日志文件。

该日志文件是许多进程日志文件的汇总，从该文件可以看出任何入侵企图或成功的入侵。

> 另外，如果胖友的系统里有 ELK 日志集中收集，它也会被收集进去。



### [8、什么叫网站灰度发布？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#8什么叫网站灰度发布)  


灰度发布是指在黑与白之间，能够平滑过渡的一种发布方式

AB test就是一种灰度发布方式，让一部用户继续用A，一部分用户开始用B

如果用户对B没有什么反对意见，那么逐步扩大范围，把所有用户都迁移到B上面 来

灰度发布可以保证整体系统的稳定，在初始灰度的时候就可以发现、调整问题，以保证其影响度


### [9、什么是Linux？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#9什么是linux)  


是一套免费使用和自由传播的类UNIX操作系统，其内核由林纳斯·本纳第克特·托瓦兹于1991年第一次释出，它主要受到Minix和Unix思想的启发，是一个基于POSIX和Unix的多用户、多任务、支持多线程和多CPU的操作系统。它能运行主要的Unix工具软件、应用程序和网络协议。它支持32位和64位硬件。


### [10、如何选择 Linux 操作系统版本?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#10如何选择-linux-操作系统版本)  


一般来讲，桌面用户首选 Ubuntu ；服务器首选 RHEL 或 CentOS ，两者中首选 CentOS

**根据具体要求：**

**1、** 安全性要求较高，则选择 Debian 或者 FreeBSD 。

**2、** 需要使用数据库高级服务和电子邮件网络应用的用户可以选择 SUSE 。

**3、** 想要新技术新功能可以选择 Feddora ，Feddora 是 RHEL 和 CentOS 的一个测试版和预发布版本。

**4、** 【重点】根据现有状况，绝大多数互联网公司选择 CentOS 。现在比较常用的是7系列，现在市场占有大概一半左右。另外的原因是 CentOS 更侧重服务器领域，并且无版权约束

> CentOS 8 系列，也慢慢使用的会比较多了。



### [11、用tcpdump嗅探80端口的访问看看谁最高](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#11用tcpdump嗅探80端口的访问看看谁最高)  

### [12、什么是LILO？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#12什么是lilo)  

### [13、文件描述符?每个描述符的含义?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#13文件描述符每个描述符的含义)  

### [14、Tomcat和Resin有什么区别，工作中你怎么选择？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#14tomcat和resin有什么区别工作中你怎么选择)  

### [15、Linux内核主要负责哪些功能](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#15linux内核主要负责哪些功能)  

### [16、cat （concatenate：显示或把多个文本文件连接起来）查看文件命令（可以快捷查看当前文件的内容）（不能快速定位到最后一页）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#16cat-concatenate：显示或把多个文本文件连接起来查看文件命令可以快捷查看当前文件的内容不能快速定位到最后一页)  

### [17、pwd （print working directory：显示当前工作目录的绝对路径）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#17pwd-print-working-directory：显示当前工作目录的绝对路径)  

### [18、查看时间命令：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#18查看时间命令：)  

### [19、绝对文件路径?相对文件路径？快捷方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#19绝对文件路径相对文件路径快捷方式)  

### [20、哪个命令专门用来查看后台任务?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#20哪个命令专门用来查看后台任务)  

### [21、终端是哪个文件夹下的哪个文件？黑洞文件是哪个文件夹下的哪个命令？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#21终端是哪个文件夹下的哪个文件黑洞文件是哪个文件夹下的哪个命令)  

### [22、账户默认信息？添加账户？删除用户？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#22账户默认信息添加账户删除用户)  

### [23、列出已经安装的包？安装软件？更新软件？卸载?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#23列出已经安装的包安装软件更新软件卸载)  

### [24、LVS、Nginx、HAproxy有什么区别？工作中你怎么选择？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#24lvsnginxhaproxy有什么区别工作中你怎么选择)  

### [25、怎么查看当前进程？怎么执行退出？怎么查看当前路径？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#25怎么查看当前进程怎么执行退出怎么查看当前路径)  

### [26、储存用户的文件是?包括哪些信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#26储存用户的文件是包括哪些信息)  

### [27、Linux系统中病毒怎么解决](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#27linux系统中病毒怎么解决)  

### [28、什么是GUI？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#28什么是gui)  

### [29、Linux的基本组件是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux中级面试题汇总及答案（2021年Linux面试题及答案大全）.md#29linux的基本组件是什么)  





