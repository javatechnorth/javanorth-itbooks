# Linux面试题带答案（2021年Linux面试题及答案大汇总）

Linux面试题及答案【最新版】Linux高级面试题大全(2021版)，发现网上很多Linux面试题及答案整理都没有答案，所以花了很长时间搜集，本套Linux面试题大全，Linux面试题大汇总，有大量经典的Linux面试题以及答案，包含Linux语言常见面试题、Linux工程师高级面试题及一些大厂Linux开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Linux面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Linux面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、怎样查看一个linux命令的概要与用法？假设你在/bin目录中偶然看到一个你从没见过的的命令，怎样才能知道它的作用和用法呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#1怎样查看一个linux命令的概要与用法假设你在/bin目录中偶然看到一个你从没见过的的命令怎样才能知道它的作用和用法呢)  


**答案：**

使用命令whatis 可以先出显示出这个命令的用法简要，比如，你可以使用whatis zcat 去查看‘zcat’的介绍以及使用简要。

```
[root@localhost ~]# whatis zcat
zcat [gzip] (1) – compress or expand files
```


### [2、哪一个bash内置命令能够进行数学运算。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#2哪一个bash内置命令能够进行数学运算。)  


**答案：**

bash shell 的内置命令let 可以进行整型数的数学运算。

```
#! /bin/bash
…
…
let c=a+b
…
…
```


### [3、通过什么命令指定命令提示符?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#3通过什么命令指定命令提示符)  


**答案：**

**1、** \u：显示当前用户账号

**2、** \h：显示当前主机名

**3、** \W：只显示当前路径最后一个目录

**4、** \w：显示当前绝对路径（当前用户目录会以~代替）

**5、** $PWD：显示当前全路径

**6、** $$：显示命令行’$$'或者’#'符号

**7、** #：下达的第几个命令

**8、** \d：代表日期，格式为week day month date，例如："MonAug1"

**9、** \t：显示时间为24小时格式，如：HH：MM：SS

**10、** \T：显示时间为12小时格式

**11、** \A：显示时间为24小时格式：HH：MM

**12、** \v：BASH的版本信息 如export PS1=’[\u@\h\w#]$‘


### [4、使用tcpdump监听主机为192.168.1.1，tcp端口为80的数据，同时将输出结果保存输出到tcpdump.log](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#4使用tcpdump监听主机为19216811tcp端口为80的数据同时将输出结果保存输出到tcpdumplog)  


tcpdump 'host 192.168.1.1 and port 80' > tcpdump.log


### [5、more （more：更多的意思）分页查看文件命令（不能快速定位到最后一页）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#5more-more：更多的意思分页查看文件命令不能快速定位到最后一页)  


```
回车：向下n行，需要定义，默认为1行。
空格键：向下滚动一屏或Ctrl+F
B：返回上一层或Ctrl+B
q：退出more
```


### [6、查看某端口是否被占用?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#6查看某端口是否被占用)  


netstat -ntulp|grep 8080

```
[root@iz2ze76ybn73dvwmdij06zz ~]# netstat -ntulp|grep 8080
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      4517/java
```

参数说明:

**1、** -t (tcp) 仅显示tcp相关选项

**2、** -u (udp)仅显示udp相关选项

**3、** -n 拒绝显示别名，能显示数字的全部转化为数字

**4、** -l 仅列出在Listen(监听)的服务状态

**5、** -p 显示建立相关链接的程序名


### [7、使用什么命令查看用过的命令列表?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#7使用什么命令查看用过的命令列表)  


**答案：**

history


### [8、如果一个linux新手想要知道当前系统支持的所有命令的列表，他需要怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#8如果一个linux新手想要知道当前系统支持的所有命令的列表他需要怎么做)  


**答案：**

使用命令compgen --c，可以打印出所有支持的命令列表。

```
[root@localhost ~]$ compgen -c
l.
ll
ls
which
if
then
else
elif
fi
case
esac
for
select
while
until
do
done
…
```


### [9、RabbitMQ是什么东西？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#9rabbitmq是什么东西)  


RabbitMQ也就是消息队列中间件，消息中间件是在消息的传息过程中保存消息的容器

消息中间件再将消息从它的源中到它的目标中标时充当中间人的作用

队列的主要目的是提供路由并保证消息的传递；如果发送消息时接收者不可用

消息队列不会保留消息，直到可以成功地传递为止，当然，消息队列保存消息也是有期限地


### [10、查看各类环境变量用什么命令?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#10查看各类环境变量用什么命令)  


**答案：**

**1、** 查看所有 env

**2、** 查看某个，如 home： env $HOME


### [11、什么是root帐户](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#11什么是root帐户)  

### [12、ll （ll：list的缩写，查看列表详情）查看当前目录下的所有详细信息和文件夹（ll 结果是详细,有时间,是否可读写等信息）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#12ll-ll：list的缩写查看列表详情查看当前目录下的所有详细信息和文件夹ll-结果是详细,有时间,是否可读写等信息)  

### [13、数据排序?对数字进行排序？对月份排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#13数据排序对数字进行排序对月份排序)  

### [14、重启linux](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#14重启linux)  

### [15、如何将本地80 端口的请求转发到8080 端口，当前主机IP 为192.168.2.1](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#15如何将本地80-端口的请求转发到8080-端口当前主机ip-为19216821)  

### [16、简单 Linux 文件系统？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#16简单-linux-文件系统)  

### [17、现在给你三百台服务器，你怎么对他们进行管理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#17现在给你三百台服务器你怎么对他们进行管理)  

### [18、Linux 下命令有哪几种可使用的通配符？分别代表什么含义?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#18linux-下命令有哪几种可使用的通配符分别代表什么含义)  

### [19、简述raid0 raid1 raid5 三种工作模式的工作原理及特点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#19简述raid0-raid1-raid5-三种工作模式的工作原理及特点)  

### [20、请问当用户反馈网站访问慢，你会如何处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#20请问当用户反馈网站访问慢你会如何处理)  

### [21、删除文件?强制删除？递归删除?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#21删除文件强制删除递归删除)  

### [22、ls （ls：list的缩写，查看列表）查看当前目录下的所有文件夹（ls 只列出文件名或目录名）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#22ls-ls：list的缩写查看列表查看当前目录下的所有文件夹ls-只列出文件名或目录名)  

### [23、查看部分文件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#23查看部分文件)  

### [24、什么是网站数据库注入？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#24什么是网站数据库注入)  

### [25、查找命令的可执行文件是去哪查找的? 怎么对其进行设置及添加?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#25查找命令的可执行文件是去哪查找的-怎么对其进行设置及添加)  

### [26、当你需要给命令绑定一个宏或者按键的时候，应该怎么做呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#26当你需要给命令绑定一个宏或者按键的时候应该怎么做呢)  

### [27、什么是链接文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#27什么是链接文件)  

### [28、通过什么命令查找执行命令?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#28通过什么命令查找执行命令)  

### [29、free 命令 （显示系统内存）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题带答案（2021年Linux面试题及答案大汇总）.md#29free-命令-显示系统内存)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
