# Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）

Linux面试题及答案【最新版】Linux高级面试题大全(2021版)，发现网上很多Linux面试题及答案整理都没有答案，所以花了很长时间搜集，本套Linux面试题大全，Linux面试题大汇总，有大量经典的Linux面试题以及答案，包含Linux语言常见面试题、Linux工程师高级面试题及一些大厂Linux开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Linux面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Linux面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、使用什么命令查看磁盘使用空间？ 空闲空间呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#1使用什么命令查看磁盘使用空间-空闲空间呢)  


答案：

```
df -hl
```

文件系统 容量 已用 可用 已用% 挂载点

```
Filesystem Size Used Avail Use% Mounted on /dev/hda2 45G 19G 24G 44% /
/dev/hda1 494M 19M 450M 4% /boot
```


### [2、什么是交换空间？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#2什么是交换空间)  


交换空间是Linux使用的一定空间，用于临时保存一些并发运行的程序。当RAM没有足够的内存来容纳正在执行的所有程序时，就会发生这种情况。


### [3、怎么清屏？怎么退出当前命令？怎么执行睡眠？怎么查看当前用户 id？查看指定帮助用什么命令？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#3怎么清屏怎么退出当前命令怎么执行睡眠怎么查看当前用户-id查看指定帮助用什么命令)  


**答案：**

**1、** 清屏： clear

**2、** 退出当前命令： ctrl+c 彻底退出

**3、** 执行睡眠 ： ctrl+z 挂起当前进程fg 恢复后台

**4、** 查看当前用户 id： ”id“：查看显示目前登陆账户的 uid 和 gid 及所属分组及用户名

**5、** 查看指定帮助： 如 man adduser 这个很全 而且有例子； adduser --help 这个告诉你一些常用参数； info adduesr；


### [4、yum install -y lrzsz 命令（实现win到Linux文件互相简单上传文件）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#4yum-install--y-lrzsz-命令实现win到linux文件互相简单上传文件)  


```
#（实际上就是在Linux系统中下载了一个插件）下了了此安装包后就可以实现win系统到linux之间拉文件拉文件
#等待下载完了就可以输入：

rz  从win系统中选择文件上传到Linux系统中

sz  文件名 选择Linux系统的文件复制到win系统中
```


### [5、mkdir （mkdir：创建目录） 创建目录](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#5mkdir-mkdir：创建目录-创建目录)  


```
mkdir 文件夹名称 ;在此目录创建文件夹
mkdir /opt/java/jdk ;在指定目录创建文件夹
```


### [6、查找匹配数据？反向搜？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#6查找匹配数据反向搜)  


语法: grep [options] pattern [file]

该命令会查找匹配执行模式的字符串的行，并输出。

```
?  apache grep start tomcat
start
restart
```

-v 反向搜

```
?  apache grep -v start tomcat
text
text
 stop
end
```

-n 显示行号

-c 显示匹配的行数


### [7、| 管道命令（把多个命令组合起来使用）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#7|-管道命令把多个命令组合起来使用)  


```
管道命令的语法：命令1 | 命令2 | 命令3。
```


### [8、复制文件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#8复制文件)  


语法: cp source target

如果target不存在则直接创建，如果存在，默认不会提醒你是否需要覆盖，需要加-i就会询问你是否覆盖,n否y是。

```
?  xktest cp a c
?  xktest cp -i a c
overwrite c? (y/n [n]) y
?  xktest ls
a c
```


### [9、Squid、Varinsh和Nginx有什么区别，工作中你怎么选择？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#9squidvarinsh和nginx有什么区别工作中你怎么选择)  


Squid、Varinsh和Nginx都是代理服务器

什么是代理服务器：

能当替用户去访问公网，并且能把访问到的数据缓存到服务器本地，等用户下次再访问相同的资

源的时候，代理服务器直接从本地回应给用户，当本地没有的时候，我代替你去访问公网，我接

收你的请求，我先在我自已的本地缓存找，如果我本地缓存有，我直接从我本地的缓存里回复你

如果我在我本地没有找到你要访问的缓存的数据，那么代理服务器就会代替你去访问公网

区别：

1）Nginx本来是反向代理/web服务器，用了插件可以做做这个副业

但是本身不支持特性挺多，只能缓存静态文件

2）从这些功能上。varnish和squid是专业的cache服务，而nginx这些是第三方模块完成

3）varnish本身的技术上优势要高于squid，它采用了可视化页面缓存技术

在内存的利用上，Varnish比Squid具有优势，性能要比Squid高。

还有强大的通过Varnish管理端口，可以使用正则表达式快速、批量地清除部分缓存

它是内存缓存，速度一流，但是内存缓存也限制了其容量，缓存页面和图片一般是挺好的

4）squid的优势在于完整的庞大的cache技术资料，和很多的应用生产环境

工作中选择：

要做cache服务的话，我们肯定是要选择专业的cache服务，优先选择squid或者varnish。


### [10、如何重置MySQL root密码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#10如何重置mysql-root密码)  


**一、 在已知MYSQL数据库的ROOT用户密码的情况下，修改密码的方法：**

**1、** 在SHELL环境下，使用MySQLadmin命令设置：

MySQLadmin –u root –p password “新密码” ? 回车后要求输入旧密码

**2、** 在MySQL>环境中,使用update命令，直接更新MySQL库user表的数据：

Update ?MySQL.user ?set ?password=password(‘新密码’) ?where ?user=’root’;

flush ? privileges;

注意：MySQL语句要以分号”；”结束

3 在MySQL>环境中，使用grant命令，修改root用户的授权权限。

grant ?all ?on ?_._ ?to ? root@’localhost’ ?identified ?by ?‘新密码’；

**二、 如查忘记了MySQL数据库的ROOT用户的密码，又如何做呢？方法如下：**

**1、** 关闭当前运行的MySQLd服务程序：service ?MySQLd ?stop（要先将MySQLd添加为系统服务）

**2、** 使用MySQLd_safe脚本以安全模式（不加载授权表）启动MySQLd 服务

/usr/local/MySQL/bin/MySQLd_safe ?--skip-grant-table ?&

**3、** 使用空密码的root用户登录数据库，重新设置ROOT用户的密码

＃MySQL ?-u ? root

MySQL> Update ?MySQL.user ?set ?password=password(‘新密码’) ?where ?user=’root’;

MySQL> flush ? privileges;


### [11、vi （VIsual：视觉）文本编辑器 类似win的记事本 （操作类似于地下的vim命令，看底下vim 的操作）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#11vi-visual：视觉文本编辑器-类似win的记事本-操作类似于地下的vim命令看底下vim-的操作)  

### [12、请写出下面 linux SecureCRT 命令行快捷键命令的功能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#12请写出下面-linux-securecrt-命令行快捷键命令的功能)  

### [13、MySQL数据备份工具](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#13mysql数据备份工具)  

### [14、制表符自动补全？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#14制表符自动补全)  

### [15、什么是 Linux 内核？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#15什么是-linux-内核)  

### [16、发现一个病毒文件你删了他又自动创建怎么解决](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#16发现一个病毒文件你删了他又自动创建怎么解决)  

### [17、du 和 df 的定义，以及区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#17du-和-df-的定义以及区别)  

### [18、同步时间命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#18同步时间命令)  

### [19、file （可查看文件类型）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#19file-可查看文件类型)  

### [20、写一个脚本，实现判断192.168.1.0/24网络里，当前在线的IP有哪些，能ping通则认为在线](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#20写一个脚本实现判断19216810/24网络里当前在线的ip有哪些能ping通则认为在线)  

### [21、如何把一个进程放到后台运行？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#21如何把一个进程放到后台运行)  

### [22、Windows和Linux的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#22windows和linux的区别)  

### [23、什么是运维？什么是游戏运维？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#23什么是运维什么是游戏运维)  

### [24、tar （解压 压缩 命令）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#24tar-解压-压缩-命令)  

### [25、查看文件内容有哪些命令可以使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#25查看文件内容有哪些命令可以使用)  

### [26、rm（remove：移除的意思）删除文件，或文件夹](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#26rmremove：移除的意思删除文件或文件夹)  

### [27、什么是BASH？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#27什么是bash)  

### [28、源码安装通常的路子?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#28源码安装通常的路子)  

### [29、Grep 命令有什么用？ 如何忽略大小写？ 如何查找不含该串的行?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Linux/Linux高级面试题汇总及答案（2021年Linux面试题及答案大全）.md#29grep-命令有什么用-如何忽略大小写-如何查找不含该串的行)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
