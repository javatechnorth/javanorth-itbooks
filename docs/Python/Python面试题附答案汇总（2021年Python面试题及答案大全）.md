# Python面试题附答案汇总（2021年Python面试题及答案大全）

Python面试题及答案【最新版】Python高级面试题大全(2021版)，发现网上很多Python面试题及答案整理都没有答案，所以花了很长时间搜集，本套Python面试题大全，Python面试题大汇总，有大量经典的Python面试题以及答案，包含Python语言常见面试题、Python工程师高级面试题及一些大厂Python开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Python面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Python面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、re的match和search的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#1re的match和search的区别)  


match()函数是在string的开始位置匹配，如果不匹配，则返回None

search()会扫描整个string查找匹配；也就是说match()只有在0位置匹配成功的话才有返回，


### [2、简述OSI七层协议](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#2简述osi七层协议)  


为了实现计算机系统的互连，OSI参考模型把整个网络的通信功能划分为7个层次，同时也定义了层次之间的相互关系以及各层所包括的服务及每层的功能。OSI的七层由低到高依次为：物理层、数据链路层、网络层、传输层、会话层、表示层、应用层，下三层（物理层、数据链路层、网络层）面向数据通信，而上三层（会话层、表示层、应用层）则面向资源子网，而传输层则是七层中最为重要的一层。它位于上层和下层中间，起承上启下的作用。


### [3、在Python中如何实现多线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#3在python中如何实现多线程)  


一个线程就是一个轻量级进程，多线程能让我们一次执行多个线程。我们都知道，Python是多线程语言，其内置有多线程工具包。

Python中的GIL（全局解释器锁）确保一次执行单个线程。一个线程保存GIL并在将其传递给下个线程之前执行一些操作，这会让我们产生并行运行的错觉。但实际上，只是线程在CPU上轮流运行。当然，所有的传递会增加程序执行的内存压力。


### [4、什么是asyncio](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#4什么是asyncio)  


asyncio是并发的一种方式，是一个协程相关的库。也叫异步IO


### [5、举例说明Python中的range函数?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#5举例说明python中的range函数)  


range：range函数返回从起点到终点的一系列序列。

range(start, end, step)，第三个参数是用于定义范围内的步数。

```
# number
for i in range(5):
    print(i)
> 0,1,2,3,4

# (start, end)
for i in range(1, 5):
    print(i)
> 1,2,3,4

# (start, end, step)
for i in range(0, 5, 2):
    print(i)
>0,2,4
```


### [6、query作为sql模板，args为将要传入的参数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#6query作为sql模板args为将要传入的参数)  


execute(query, args=None)


### [7、解释Python中的help()和dir()函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#7解释python中的help和dir函数)  


Help()函数是一个内置函数，用于查看函数或模块用途的详细说明：

```
>>> import copy
>>> help(copy.copy)
```

运行结果为：

```
Help on function copy in module copy:

 
 
copy(x)
 
Shallow copy operation on arbitrary Python objects.
 
See the module’s __doc__ string for more info.
```

Dir()函数也是Python内置函数，dir() 函数不带参数时，返回当前范围内的变量、方法和定义的类型列表；带参数时，返回参数的属性、方法列表。

以下实例展示了 dir 的使用方法：

```
>>> dir(copy.copy)
```

运行结果为：

```
[‘__annotations__’, ‘__call__’, ‘__class__’, ‘__closure__’, ‘__code__’, ‘__defaults__’, ‘__delattr__’, ‘__dict__’, ‘__dir__’, ‘__doc__’, ‘__eq__’, ‘__format__’, ‘__ge__’, ‘__get__’, ‘__getattribute__’, ‘__globals__’, ‘__gt__’, ‘__hash__’, ‘__init__’, ‘__init_subclass__’, ‘__kwdefaults__’, ‘__le__’, ‘__lt__’, ‘__module__’, ‘__name__’, ‘__ne__’, ‘__new__’, ‘__qualname__’, ‘__reduce__’, ‘__reduce_ex__’, ‘__repr__’, ‘__setattr__’, ‘__sizeof__’, ‘__str__’, ‘__subclasshook__’]
```


### [8、简述线程死锁是怎么造成的。如何避免？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#8简述线程死锁是怎么造成的。如何避免)  


**1、** 死锁的产生原因？

**2、** 系统资源的竞争

**3、** 进程运行推进顺序不当

**4、** 解决死锁

**5、** 加锁顺序：线程按照一定的顺序加锁

**6、** 加锁时限：线程尝试获取锁的时候加上一定的时限，超过时限，则放弃对该锁的请求，并释放自己占有的锁。

**7、** 死锁检测


### [9、MySQL索引种类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#9mysql索引种类)  


**1、** 普通索引：仅加速查询

**2、** 唯一索引：加速查询 + 列值唯一（可以有null）

**3、** 主键索引：加速查询 + 列值唯一（不可以有null）+ 表中只有一个

**4、** 组合索引：多列值组成一个索引，专门用于组合搜索，其效率大于索引合并

**5、** 全文索引：对文本的内容进行分词，进行搜索


### [10、现有mydict和变量onekey，请写出从mydict中取出onekey的值的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#10现有mydict和变量onekey请写出从mydict中取出onekey的值的方法)  


> 方法一：mydict[onekey]

这种方法，如果mydict中键不存在的时候程序会报错

方法二：mydict.get(onekey)

这种方法，如果存在，返回值，不存在返回None

方法三：mydict.setdefault(onekey,[])

这种方法：存在的话返回值，不存在的时候创建一个值，值得内容为第二个参数+



### [11、什么是闭包](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#11什么是闭包)  

### [12、如何在Python中管理内存？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#12如何在python中管理内存)  

### [13、Redis如何实现事务](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#13redis如何实现事务)  

### [14、logging模块的作用以及应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#14logging模块的作用以及应用场景)  

### [15、数据库锁的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#15数据库锁的作用)  

### [16、有一个列表lis=['This','is','a','Man','B','!']，对它进行大小写无关的排序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#16有一个列表lis=['this','is','a','man','b','']对它进行大小写无关的排序)  

### [17、python如何定义函数时如何书写可变参数和关键字参数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#17python如何定义函数时如何书写可变参数和关键字参数)  

### [18、MySQL慢日志](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#18mysql慢日志)  

### [19、实现99乘法表（使用两种方法）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#19实现99乘法表使用两种方法)  

### [20、解释一下Python中的继承？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#20解释一下python中的继承)  

### [21、请编写一个函数将ip地址转换成一个整数。如10.3.9.12转换成00001010 00000011 00001001 00001100，然后转换成整数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#21请编写一个函数将ip地址转换成一个整数。如103912转换成00001010-00000011-00001001-00001100然后转换成整数)  

### [22、解释Python中reduce函数的用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#22解释python中reduce函数的用法)  

### [23、Python有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#23python有什么特点)  

### [24、求下面代码结果](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#24求下面代码结果)  

### [25、列举创建索引但是无法命中索引的情况](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#25列举创建索引但是无法命中索引的情况)  

### [26、写代码：如何由tuple1=('a','b','c','d','e')，和tuple2=(1,2,3,4,5)得到res={'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#26写代码：如何由tuple1='a','b','c','d','e'和tuple2=1,2,3,4,5得到res={'a':-1,-'b':-2,-'c':-3,-'d':-4,-'e':-5})  

### [27、or 和 and](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#27or-和-and)  

### [28、简述python的深浅拷贝](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#28简述python的深浅拷贝)  

### [29、生成器与函数的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#29生成器与函数的区别)  

### [30、编写程序，计算文件中单词的出现频率](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案汇总（2021年Python面试题及答案大全）.md#30编写程序计算文件中单词的出现频率)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
