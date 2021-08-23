# Python中级面试题汇总及答案（2021年Python面试题及答案大全）

Python面试题及答案【最新版】Python高级面试题大全(2021版)，发现网上很多Python面试题及答案整理都没有答案，所以花了很长时间搜集，本套Python面试题大全，Python面试题大汇总，有大量经典的Python面试题以及答案，包含Python语言常见面试题、Python工程师高级面试题及一些大厂Python开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Python面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Python面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、22、iterables和iterators之间的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#122iterables和iterators之间的区别)  


iterable：可迭代是一个对象，可以对其进行迭代。在可迭代的情况下，整个数据一次存储在内存中。

iterators：迭代器是用来在对象上迭代的对象。它只在被调用时被初始化或存储在内存中。迭代器使用next从对象中取出元素。

```
# List is an iterable
lst = [1,2,3,4,5]
for i in lst:
    print(i)

# iterator
lst1 = iter(lst)
next(lst1)
>1
next(lst1)
>2
for i in lst1:
    print(i)
>3,4,5
```


### [2、关于Python程序的运行方面，有什么手段能提升性能？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#2关于python程序的运行方面有什么手段能提升性能)  


**1、** 使用多进程，充分利用机器的多核性能

**2、** 对于性能影响较大的部分代码，可以使用C或C++编写

**3、** 对于IO阻塞造成的性能影响，可以使用IO多路复用来解决

**4、** 尽量使用Python的内建函数5、尽量使用局部变量


### [3、使用with语句的好处是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#3使用with语句的好处是什么)  


**1、** 使用with后不管with中的代码出现什么错误，都会进行对当前对象进行清理工作。例如file的file.close()方法，无论with中出现任何错误，都会执行file.close（）方法

**2、** 只有支持上下文管理器的对象才能使用with，即在对象内实现了两个方法：**enter**()和**exit**()


### [4、如何使用python删除一个文件或者文件夹？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#4如何使用python删除一个文件或者文件夹)  


```python
import os
import shutil
os.remove(path) # 删除文件
os.removedirs(path) # 删除空文件夹
shutil.rmtree(path) # 删除文件夹，可以为空也可以不为空
```


### [5、数据库的导入与导出命令](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#5数据库的导入与导出命令)  


**1、** 导出(MySQLdump)

**2、** 导出数据和表结构

**3、** MySQLdump -uroot -p dbname > dbname .sql

**4、** 只导出表结构

**5、** MySQLdump -uroot -p -d dbname > dbname .sql

6、导入

**7、** MySQL -u用户名 -p密码 数据库名 < 数据库名.sql


### [6、a=range(10),则a[::-3]的值是？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#6a=range10,则a[::-3]的值是)  


[9,6,3,0] 或者 range(9,-1,-3)


### [7、实现一个装饰器，通过一次调用，使函数重复执行5次](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#7实现一个装饰器通过一次调用使函数重复执行5次)  


```python
from functools import wraps
def dec(func):
@wraps(func)
def inner(*args,**kwargs):
result=[func(*args,**kwargs) for i in range(5)]
return result
return inner

@dec
def add(x,y):
return x+y
print(add(1,2))
```


### [8、实现一个单例模式。(尽可能多的方法)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#8实现一个单例模式。尽可能多的方法)  


```python
# 方法一：使用__new__()
import threading
class Singleton(object):
_instance_lock = threading.Lock()
def __init__(self):
pass

def __new__(cls, *args, **kwargs):
if not hasattr(Singleton, "_instance"):
with Singleton._instance_lock:
    if not hasattr(Singleton, "_instance"):
        Singleton._instance = object.__new__(cls)
return Singleton._instance

obj1 = Singleton()
obj2 = Singleton()
print(obj1 is obj2)

# 方法二：使用元类来创建
import threading

class SingletonType(type):
_instance_lock = threading.Lock()
def __call__(cls, *args, **kwargs):
if not hasattr(cls, "_instance"):
with SingletonType._instance_lock:
    if not hasattr(cls, "_instance"):
        cls._instance = super().__call__(*args, **kwargs)
return cls._instance

class Singleton(metaclass=SingletonType):
def __init__(self):
pass

obj1 = Singleton()
obj2 = Singleton()
print(obj1 is obj2)
```


### [9、Redis如何实现主从复制？以及数据同步机制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#9redis如何实现主从复制以及数据同步机制)  


Redis从主从结构可以采用一主多从或者级联结构，主从复制可以根据是否全量分为全量同步和增量同步。

**全量同步：**

Redis全量复制一般发生在slave初始化阶段，这时slave需要将master上的所有数据都复制一份步骤如下：

**1、** 从服务器连接主服务器，发送SYNC命令；

**2、** 主服务器接收到SYNC命名后，开始执行BGSAVE命令生成RDB文件并使用缓冲区记录此后执行的所有写命令；

**3、** 主服务器BGSAVE执行完后，向所有从服务器发送快照文件，并在发送期间继续记录被执行的写命令；

**4、** 从服务器收到快照文件后丢弃所有旧数据，载入收到的快照；

**5、** 主服务器快照发送完毕后开始向从服务器发送缓冲区中的写命令；

**6、** 从服务器完成对快照的载入，开始接收命令请求，并执行来自主服务器缓冲区的写命令；

**增量同步：**

**1、** Redis增量复制是指Slave初始化后开始正常工作时主服务器发生的写操作同步到从服务器的过程。 增量复制的过程主要是主服务器每执行一个写命令就会向从服务器发送相同的写命令，从服务器接收并执行收到的写命令。

**2、** Redis主从同步策略

**3、** 主从刚刚连接的时候，进行全量同步；全同步结束后，进行增量同步。当然，如果有需要，slave 在任何时候都可以发起全量同步。Redis 策略是，无论如何，首先会尝试进行增量同步，如不成功，要求从机进行全量同步


### [10、编写程序，输出给定序列中的所有质数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#10编写程序输出给定序列中的所有质数)  


```
lower = int(input("Enter the lower range:"))
upper = int(input("Enter the upper range:"))
list(filter(lambda x:all(x % y != 0 for y in range(2, x)), range(lower, upper)))

-------------------------------------------------
Enter the lower range:10
Enter the upper range:50
[11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]
```


### [11、b、B、kB、MB、GB的关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#11bbkbmbgb的关系)  

### [12、找出两个列表中相同的元素和不同的元素](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#12找出两个列表中相同的元素和不同的元素)  

### [13、如何更改列表的数据类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#13如何更改列表的数据类型)  

### [14、解释Python中map()函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#14解释python中map函数)  

### [15、什么是索引合并](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#15什么是索引合并)  

### [16、如何打乱一个排好序的列表](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#16如何打乱一个排好序的列表)  

### [17、简述python字符串的驻留机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#17简述python字符串的驻留机制)  

### [18、怎样获取字典中所有键的列表？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#18怎样获取字典中所有键的列表)  

### [19、==和is的区别是？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#19和is的区别是)  

### [20、什么是轮询和长轮询](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#20什么是轮询和长轮询)  

### [21、解释Python的内置数据结构？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#21解释python的内置数据结构)  

### [22、解释一下Python中的成员运算符](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#22解释一下python中的成员运算符)  

### [23、Python中的Map Function是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#23python中的map-function是什么)  

### [24、什么是socket？简述基于tcp协议的socket通信流程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#24什么是socket简述基于tcp协议的socket通信流程)  

### [25、如何高效的找到Redis中所有以felix开头的key](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#25如何高效的找到redis中所有以felix开头的key)  

### [26、在Python中有多少种运算符？解释一下算数运算符。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#26在python中有多少种运算符解释一下算数运算符。)  

### [27、阅读以下代码，写输出结果](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#27阅读以下代码写输出结果)  

### [28、输入某年某月某日，判断这是这一年的第几天？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#28输入某年某月某日判断这是这一年的第几天)  

### [29、python3和python2中int和long的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#29python3和python2中int和long的区别)  

### [30、解决哈希冲突的算法有哪几种？分别有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题汇总及答案（2021年Python面试题及答案大全）.md#30解决哈希冲突的算法有哪几种分别有什么特点)  





