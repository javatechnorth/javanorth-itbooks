# Python面试题带答案（2021年Python面试题及答案大汇总）

Python面试题及答案【最新版】Python高级面试题大全(2021版)，发现网上很多Python面试题及答案整理都没有答案，所以花了很长时间搜集，本套Python面试题大全，Python面试题大汇总，有大量经典的Python面试题以及答案，包含Python语言常见面试题、Python工程师高级面试题及一些大厂Python开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Python面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Python面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、讲讲Python中的位运算符](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#1讲讲python中的位运算符)  


该运算符按二进制位对值进行操作。

**1、**   与（&），按位与运算符：参与运算的两个值,如果两个相应位都为1,则该位的结果为1,否则为0

```
>>> 0b110 & 0b010
2
```

**2、** 或（|），按位或运算符：只要对应的二个二进位有一个为1时，结果位就为1。

```
>>> 3|2
3
```

**3、** 异或（^），按位异或运算符：当两对应的二进位相异时，结果为1

```
>>> 3^2
1
```

**4、** 取反（~），按位取反运算符：对数据的每个二进制位取反,即把1变为0,把0变为1

```
>>> ~2
-3
```

**5、** 左位移（<<），运算数的各二进位全部左移若干位，由 << 右边的数字指定了移动的位数，高位丢弃，低位补0

```
>>> 1<<2
4
```

**6、** 右位移（>>），把">>"左边的运算数的各二进位全部右移若干位，>> 右边的数字指定了移动的位数

```
>>> 4>>2
1
```

更多关于运算符的知识，参考这里：

[戳这里](https://data-flair.training/blogs/python-operators/)


### [2、如何修改本地hosts文件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#2如何修改本地hosts文件)  


进入c:\windows\system32\drivers\etc进行修改


### [3、python递归的最大层数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#3python递归的最大层数)  


1000


### [4、什么是codis](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#4什么是codis)  


Codis 是一个分布式 Redis 解决方案, 对于上层的应用来说, 连接到 Codis Proxy 和连接原生的 Redis Server 没有明显的区别 (有一些命令不支持), 上层应用可以像使用单机的 Redis 一样使用, Codis 底层会处理请求的转发, 不停机的数据迁移等工作, 所有后边的一切事情, 对于前面的客户端来说是透明的, 可以简单的认为后边连接的是一个内存无限大的 Redis 服务，当然，前段时间Redis官方的3.0出了稳定版，3.0支持集群功能，codis的实现原理和3.0的集群功能差不多。


### [5、python中如何使用进程池和线程池](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#5python中如何使用进程池和线程池)  


```python
from concurrent.futures import ThreadPoolExecutor,ProcessPoolExecutor
import os,time,random
from multiprocessing import Pool

def task(n):
print('%s is runing' %os.getpid())
time.sleep(random.randint(1,3))
return n**2

if __name__ == '__main__':
# 多进程方式一
pool2=Pool()
pool2.map(task,range(10))

# 多进程方式二，下面这种多进程和多线程的用法一模一样
executor=ThreadPoolExecutor(max_workers=3)
futures=[]
for i in range(11):
future=executor.submit(task,i)
futures.append(future)
executor.shutdown(True)
print('+++>')
for future in futures:
print(future.result())
```


### [6、Python有哪些应用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#6python有哪些应用)  


**1、**  Web开发

**2、**  桌面GUI开发

**3、**  人工智能和机器学习

**4、**  软件开发

**5、**  业务应用程序开发

**6、**  基于控制台的应用程序

**7、**  软件测试

**8、**  Web自动化

**9、**  基于音频或视频的应用程序

**10、**  图像处理应用程序


### [7、什么时GIL锁](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#7什么时gil锁)  


**1、** 即全局解释器锁，

**2、** 一个时间点只有一个线程处于执行状态。


### [8、python的底层网络交互模块有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#8python的底层网络交互模块有哪些)  


socket，urllib，requests，pycurl


### [9、IO多路复用的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#9io多路复用的作用)  


I/O多路复用是用于提升效率，单个进程可以同时监听多个网络连接IO。

与多进程和多线程技术相比，I/O多路复用技术的最大优势是系统开销小，系统不必创建进程/线程，也不必维护这些进程/线程，从而大大减小了系统的开销。


### [10、如何使用索引来反转Python中的字符串?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#10如何使用索引来反转python中的字符串)  


```
string = 'hello'

string[::-1]
>'olleh'
```


### [11、为什么Python执行速度慢，我们如何改进它？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#11为什么python执行速度慢我们如何改进它)  

### [12、写出邮箱的正则表达式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#12写出邮箱的正则表达式)  

### [13、列举字符串、列表、元组、字典每个常用的5个方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#13列举字符串列表元组字典每个常用的5个方法)  

### [14、解释一下Python中的//，%和 ** 运算符](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#14解释一下python中的//%和-**-运算符)  

### [15、求以下代码的输出结果](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#15求以下代码的输出结果)  

### [16、什么是Nginx](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#16什么是nginx)  

### [17、threading.local的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#17threadinglocal的作用)  

### [18、求出以下代码的输出结果](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#18求出以下代码的输出结果)  

### [19、把a='aaabbcccdddde'这种形式的字符串，压缩成a3b2c3d4e1这种形式。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#19把a='aaabbcccdddde'这种形式的字符串压缩成a3b2c3d4e1这种形式。)  

### [20、什么是twisted框架](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#20什么是twisted框架)  

### [21、MySQL常见的函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#21mysql常见的函数)  

### [22、python中进制转换](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#22python中进制转换)  

### [23、对字典d={'a':30,'g':17,'b':25,'c':18,'d':50,'e':36,'f':57,'h':25}按照value字段进行排序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#23对字典d={'a':30,'g':17,'b':25,'c':18,'d':50,'e':36,'f':57,'h':25}按照value字段进行排序)  

### [24、简述jsonp及其原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#24简述jsonp及其原理)  

### [25、简述Redis的有几种持久化策略以及比较？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#25简述redis的有几种持久化策略以及比较)  

### [26、解释一下Python中的三元运算子](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#26解释一下python中的三元运算子)  

### [27、如何保证Redis中的数据都是热点数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#27如何保证redis中的数据都是热点数据)  

### [28、请列举你所知道的python代码检测工具以及他们之间的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#28请列举你所知道的python代码检测工具以及他们之间的区别)  

### [29、MySQL的建表语句](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#29mysql的建表语句)  

### [30、通过什么途径学习python](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题带答案（2021年Python面试题及答案大汇总）.md#30通过什么途径学习python)  





