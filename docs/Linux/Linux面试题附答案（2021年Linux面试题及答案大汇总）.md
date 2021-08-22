# Linux面试题附答案（2021年Linux面试题及答案大汇总）

Linux面试题及答案【最新版】Linux高级面试题大全(2021版)，发现网上很多Linux面试题及答案整理都没有答案，所以花了很长时间搜集，本套Linux面试题大全，Linux面试题大汇总，有大量经典的Linux面试题以及答案，包含Linux语言常见面试题、Linux工程师高级面试题及一些大厂Linux开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Linux面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Linux面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、ping （用于检测与目标的连通性）语法：ping ip地址](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#1ping-用于检测与目标的连通性语法：ping-ip地址)  


```
测试：
**1、** 在Windows操作系统中?cmd?ipconfig，查看本机IP地址：

**2、** 再到LInux系统中输入 ping ip地址

（公司电脑，我就不暴露Ip了,没图片  自己去试）
按Ctrl + C 可以停止测试。
```


### [2、使用什么命令查看 ip 地址及接口信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#2使用什么命令查看-ip-地址及接口信息)  


**答案：**

ifconfig


### [3、服务器开不了机怎么解决一步步的排查](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#3服务器开不了机怎么解决一步步的排查)  


A、造成服务器故障的原因可能有以下几点：

图片

B、如何排查服务器故障的处理步骤如下：

图片


### [4、netstat 命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#4netstat-命令)  


```
#Linux netstat命令用于显示网络状态。
#利用netstat指令可让你得知整个Linux系统的网络情况。
#语法：
netstat [-acCeFghilMnNoprstuvVwx][-A<网络类型>][--ip]
```


### [5、cd （change directory：英文释义是改变目录）切换目录](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#5cd-change-directory：英文释义是改变目录切换目录)  


```
cd ../ ;跳到上级目录
cd /opt ;不管现在到那直接跳到指定的opt文件夹中
cd ~ ;切换当前用户的家目录。root用户的家目录就是root目录。
```


### [6、把后台任务调到前台执行使用什么命令?把停下的后台任务在后台执行起来用什么命令?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#6把后台任务调到前台执行使用什么命令把停下的后台任务在后台执行起来用什么命令)  


**答案：**

把后台任务调到前台执行 fg

把停下的后台任务在后台执行起来 bg


### [7、一台 Linux 系统初始化环境后需要做一些什么安全工作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#7一台-linux-系统初始化环境后需要做一些什么安全工作)  


添加普通用户登陆，禁止 root 用户登陆，更改 SSH 端口号。

> 修改 SSH 端口不一定绝对哈。当然，如果要暴露在外网，建议改下。


**1、** 服务器使用密钥登陆，禁止密码登陆。

**2、** 开启防火墙，关闭 SElinux ，根据业务需求设置相应的防火墙规则。

**3、** 装 fail2ban 这种防止 SSH 暴力破击的软件。

**4、** 设置只允许公司办公网出口 IP 能登陆服务器(看公司实际需要)

> 也可以安装 VPN 等软件，只允许连接 VPN 到服务器上。


**1、** 修改历史命令记录的条数为 10 条。

**2、** 只允许有需要的服务器可以访问外网，其它全部禁止。

**3、** 做好软件层面的防护。

**4、** 设置 nginx_waf 模块防止 SQL 注入。

**5、** 把 Web 服务使用 www 用户启动，更改网站目录的所有者和所属组为 www


### [8、利用 ps 怎么显示所有的进程? 怎么利用 ps 查看指定进程的信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#8利用-ps-怎么显示所有的进程-怎么利用-ps-查看指定进程的信息)  


**答案：**

```
ps -ef (system v 输出) 

ps -aux bsd 格式输出

ps -ef | grep pid
```


### [9、BASH和DOS之间的基本区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#9bash和dos之间的基本区别是什么)  


**BASH和DOS控制台之间的主要区别在于3个方面：**

**1、** BASH命令区分大小写，而DOS命令则不区分;

**2、** 在BASH下，/ character是目录分隔符，\作为转义字符。在DOS下，/用作命令参数分隔符，\是目录分隔符

**3、** DOS遵循命名文件中的约定，即8个字符的文件名后跟一个点，扩展名为3个字符。BASH没有遵循这样的惯例。


### [10、bash手册](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#10bash手册)  


大多数linux发行版自带以查找shell命令及其他GNU工具信息的在线手册。man命令用来访问linux系统上的手册页面。当用man命令查看手册，使用分页的程序来现实的。


### [11、cp（copy单词缩写，复制功能）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#11cpcopy单词缩写复制功能)  

### [12、讲述一下LVS三种模式的工作过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#12讲述一下lvs三种模式的工作过程)  

### [13、使用什么命令查看网络是否连通?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#13使用什么命令查看网络是否连通)  

### [14、什么是CLI？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#14什么是cli)  

### [15、awk 详解。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#15awk-详解。)  

### [16、搜索文件用什么命令? 格式是怎么样的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#16搜索文件用什么命令-格式是怎么样的)  

### [17、请列出你了解的web服务器负载架构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#17请列出你了解的web服务器负载架构)  

### [18、实时抓取并显示当前系统中tcp 80端口的网络数据信息，请写出完整操作命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#18实时抓取并显示当前系统中tcp-80端口的网络数据信息请写出完整操作命令)  

### [19、启动shell](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#19启动shell)  

### [20、ps （process status：进程状态，类似于windows的任务管理器）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#20ps-process-status：进程状态类似于windows的任务管理器)  

### [21、哪个文件包含了主机名和ip的映射关系?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#21哪个文件包含了主机名和ip的映射关系)  

### [22、快速判断某个特定目录是否有超大文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#22快速判断某个特定目录是否有超大文件)  

### [23、touch （touch：创建文件）创建文件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#23touch-touch：创建文件创建文件)  

### [24、clear 清屏命令。（强迫症患者使用）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#24clear-清屏命令。强迫症患者使用)  

### [25、修改权限?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#25修改权限)  

### [26、移动文件用哪个命令？改名用哪个命令？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#26移动文件用哪个命令改名用哪个命令)  

### [27、已知 apache 服务的访问日志按天记录在服务器本地目录/app/logs 下，由于磁盘空间紧张现在要求只能保留最近 7 天的访问日志！请问如何解决？请给出解决办法或配置或处理命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#27已知-apache-服务的访问日志按天记录在服务器本地目录/app/logs-下由于磁盘空间紧张现在要求只能保留最近-7-天的访问日志请问如何解决请给出解决办法或配置或处理命令)  

### [28、Linux广泛使用的归档数据方法?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#28linux广泛使用的归档数据方法)  

### [29、Linux系统缺省的运行级别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux面试题附答案（2021年Linux面试题及答案大汇总）.md#29linux系统缺省的运行级别)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
