# Python中级面试题大全带答案（2021年Python面试题及答案整理）

Python面试题及答案【最新版】Python高级面试题大全(2021版)，发现网上很多Python面试题及答案整理都没有答案，所以花了很长时间搜集，本套Python面试题大全，Python面试题大汇总，有大量经典的Python面试题以及答案，包含Python语言常见面试题、Python工程师高级面试题及一些大厂Python开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Python面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Python面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、MySQL的半同步复制原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#1mysql的半同步复制原理)  


半同步复制，介于异步复制和全同步复制之间，主库在执行完客户端提交的事务后不是立刻返回给客户端，而是等待至少一个从库接收到并写到relay log中才返回给客户端。相对于异步复制，半同步复制牺牲了一定的性能，提高了数据的安全性。

异步复制，MySQL默认的复制是异步的，主库在执行完客户端提交的事务后会立即将结果返给给客户端，并不关心从库是否已经接收并处理。原理最简单，性能最好，但是主从之间数据不一致的概率很大。

全同步复制，指当主库执行完一个事务，所有的从库都执行了该事务才返回给客户端。因为需要等待所有从库执行完该事务才能返回，所以全同步复制的性能必然会收到严重的影响。


### [2、TCP和UDP的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#2tcp和udp的区别)  


**1、** TCP面向连接（如打电话要先拨号建立连接）;UDP是无连接的，即发送数据之前不需要建立连接

**2、** TCP提供可靠的服务。也就是说，通过TCP连接传送的数据，无差错，不丢失，不重复，且按序到达;UDP尽最大努力交付，即不保证可靠交付

**3、** UDP具有较好的实时性，工作效率比TCP高，适用于对高速传输和实时性有较高的通信或广播通信。

**4、** 每一条TCP连接只能是点到点的;UDP支持一对一，一对多，多对一和多对多的交互通信

**5、** TCP对系统资源要求较多，UDP对系统资源要求较少。


### [3、写python爬虫分别用到了哪些模块？分别有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#3写python爬虫分别用到了哪些模块分别有什么用)  


模块

request，发起请求

pyquery，解析html数据

beautifulsoup，解析html数据

aiohttp，异步发送请求

框架

pyspider，web界面的爬虫框架

scrapy，爬虫框架

selenium，模拟浏览器的爬虫框架


### [4、索引有什么作用，有哪些分类，有什么好处和坏处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#4索引有什么作用有哪些分类有什么好处和坏处)  


作用：为了增加查询速度，提高系统性能

**分类：**

**1、** 唯一索引：不允许其中任何两行具有相同索引值的索引。

**2、** 非唯一索引：允许其中任何两行具有相同索引值的索引。

**3、** 主键索引：有一列或列组合，其值唯一标识表中的每一行。

**4、** 聚集索引：表中行的物理顺序与键值的逻辑（索引）顺序相同。一个表只能包含一个聚集索引。

**好处：**

**1、** 帮助用户提高查询速度

**2、** 利用索引的唯一性来控制记录的唯一性

**3、** 可以加速表与表之间的连接

**4、** 降低查询中分组和排序的时间

**坏处：**

**1、** 存储索引占用磁盘空间

**2、** 执行数据修改操作(INSERT、UPDATE、DELETE)产生索引维护


### [5、编写一个函数，找出数组中没有重复的值的和](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#5编写一个函数找出数组中没有重复的值的和)  


```python
def func(lis):
lis1=[]
del_lis=[]
for i in lis:
if i not in lis1:
if i not in del_lis:
    lis1.append(i)
else:
del_lis.append(i)
lis1.remove(i)
return sum(lis1)

def func2(lis):
return sum([i for i in set(lis) if lis.count(i)==1])

print(func2([3,4,1,2,5,6,6,5,4,3,3]))
```


### [6、用一行Python代码，从给定列表中取出所有的偶数和奇数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#6用一行python代码从给定列表中取出所有的偶数和奇数)  


```
a = [1,2,3,4,5,6,7,8,9,10]
odd, even = [el for el in a if el % 2==1], [el for el in a if el % 2==0]

print(odd,even)
> ([1, 3, 5, 7, 9], [2, 4, 6, 8, 10])
```


### [7、在Python中是如何管理内存的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#7在python中是如何管理内存的)  


Python有一个私有堆空间来保存所有的对象和数据结构。作为开发者，我们无法访问它，是解释器在管理它。但是有了核心API后，我们可以访问一些工具。Python内存管理器控制内存分配。

另外，内置垃圾回收器会回收使用所有的未使用内存，所以使其适用于堆空间。


### [8、GIL锁对python性能的影响](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#8gil锁对python性能的影响)  


**1、** 会降低多线程的效率。可以说python就是个单线程的程序。

**2、** 如何避免：

**3、** 用多进程代替多线程

**4、** 使用其他解释器


### [9、DNS域名解析过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#9dns域名解析过程)  


**1、** 浏览器检查缓存中有没有这个域名对应的解析后的IP地址，如果缓存中有，解析过程结束。缓存大小、时间都有限制，时间由TTL属性决定；

**2、** 如果浏览器缓存中么有，浏览器会查找操作系统缓存中有无这个域名DNS解析后的结果。操作系统也有一个域名解析的过程，windows通过C:\Windows\System32\drivers\etc\hosts，浏览器会优先使用这个解析结果（Win7已将hosts设置为只读），linux系统中/etc/named.conf。目前为止都是在本机完成，如果未完成，才会真正请求域名服务器解析域名。

**3、** “网络配置”中都会有“DNX服务器地址”，操作系统会把域名发送给这个LDNS，本地区的域名服务器，通常都会提供一个本地互联网接入的DNS解析服务。就在你所在城市的某个角落，通过ipconfig可以看到。

**4、** 如果LDNS仍然没有命中，则向RootServer域名服务器请求解析。

**5、** 根域名服务器向本地域名服务器返回一个所查询域的主域名服务器（gTLD Server）。国际顶级域名服务器（.com、.cn、.org等），全球13台。

**6、** 本地域名服务器（Local DNS Server）再向上一步返回的gTLD发送请求。

**7、** gTLD返回域名对应NameServer域名服务器地址，通常由你购买域名的服务商提供。

**8、** NameServer服务器查询域名与IP映射关系表，返回目标IP记录和TTL值给DNS Server域名服务器。

**9、** Local DNS Server根据TTL缓存该IP解析。

**10、** 缓存结果返回给用户，用户根据TTL缓存到本地操作系统中，域名解析过程结束。


### [10、什么是抽象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#10什么是抽象)  


抽象(Abstraction)是将一个对象的本质或必要特征向外界展示，并隐藏所有其他无关信息的过程。


### [11、python中enumerate的意思是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#11python中enumerate的意思是什么)  

### [12、Python中append，insert和extend的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#12python中appendinsert和extend的区别)  

### [13、什么是反射，以及应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#13什么是反射以及应用场景)  

### [14、获取python解释器版本的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#14获取python解释器版本的方法)  

### [15、简述触发器、函数、视图和存储过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#15简述触发器函数视图和存储过程)  

### [16、简述多进程开发中join和deamon的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#16简述多进程开发中join和deamon的区别)  

### [17、一行代码实现删除列表中的所有的重复的值](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#17一行代码实现删除列表中的所有的重复的值)  

### [18、什么是断言(assert)?应用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#18什么是断言assert应用场景)  

### [19、简述进程，线程，协程的区别以及应用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#19简述进程线程协程的区别以及应用场景)  

### [20、ascii、Unicode、utf-8、gbk的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#20asciiunicodeutf-8gbk的区别)  

### [21、什么是多态？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#21什么是多态)  

### [22、MySQL如何创建索引](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#22mysql如何创建索引)  

### [23、有如下代码：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#23有如下代码：)  

### [24、如何实现字符串的反转？如：name=felix，反转成name=xilef](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#24如何实现字符串的反转如：name=felix反转成name=xilef)  

### [25、super的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#25super的作用)  

### [26、写个函数接收一个文件夹名称作为参数，显示文件夹中文件的路径，以及其中包含的文件夹中文件的如今](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#26写个函数接收一个文件夹名称作为参数显示文件夹中文件的路径以及其中包含的文件夹中文件的如今)  

### [27、简述数据库的读写分离](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#27简述数据库的读写分离)  

### [28、traceroute使用哪种网络协议](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#28traceroute使用哪种网络协议)  

### [29、给定一个非空的字符串，判断它是否可以由它的一个子串重复多次构成。给定的字符串只含有小写英文字母，并且长度不超过10000。例如：'ababab',返回True，'ababa'，返回False](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题大全带答案（2021年Python面试题及答案整理）.md#29给定一个非空的字符串判断它是否可以由它的一个子串重复多次构成。给定的字符串只含有小写英文字母并且长度不超过10000。例如：'ababab',返回true'ababa'返回false)  





