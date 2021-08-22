# Python中级面试题附答案汇总（2021年Python面试题及答案大全）

Python面试题及答案【最新版】Python高级面试题大全(2021版)，发现网上很多Python面试题及答案整理都没有答案，所以花了很长时间搜集，本套Python面试题大全，Python面试题大汇总，有大量经典的Python面试题以及答案，包含Python语言常见面试题、Python工程师高级面试题及一些大厂Python开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Python面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Python面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是arp协议](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#1什么是arp协议)  


**1、** ARP全称“Address Resolution Protocol”，地址解析协议。

**2、** 实现局域网内通过IP地址获取主机的MAC地址。

**3、** MAC地址48位主机的物理地址，局域网内唯一。

**4、** ARP协议类似DNS服务，但不需要配置服务。

**5、** ARP协议是三层协议。


### [2、什么是域名解析](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#2什么是域名解析)  


域名解析是把域名指向网站空间IP，让人们通过注册的域名可以方便地访问到网站一种服务。IP地址是网络上标识站点的数字地址，为方便记忆，采用域名来代替IP地址标识站点地址。域名解析就是域名到IP地址的转换过程。


### [3、使用生成器编写一个函数实现生成指定个数的斐波那契数列](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#3使用生成器编写一个函数实现生成指定个数的斐波那契数列)  


```python
def fib2(imax):
t,a,b=0,0,1
while t<imax:
yield b
a,b=b,a+b
t+=1

for i in fib2(10):
print(i)
```


### [4、生产者消费者模型的应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#4生产者消费者模型的应用场景)  


**说明**

生产者只在仓库未满时进行生产，仓库满时生产者进程被阻塞；消费者只在仓库非空时进行消费，仓库为空时消费者进程被阻塞；

应用场景：处理数据比较消耗时间，线程独占，生产数据不需要即时的反馈等。比如说写入日志，将多线程产生的日志放在队列中，然后写入。


### [5、如何判断一个对象是否可调用？哪些对象是可调用对象？如何定义一个类，使其对象本身就是可调用对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#5如何判断一个对象是否可调用哪些对象是可调用对象如何定义一个类使其对象本身就是可调用对象)  


**1、** 使用callable函数判断。

**2、** 可调用对象有7类：

**3、** 用户自定义函数

**4、** 内置函数

**5、** 内置方法

**6、** 方法(定义在类中的函数)

7、类

**8、** 类实例(如果类中定义了**call**方法，那么这个类的实例就是可调用对象)

**9、** 生成器函数

在类中定义**call**方法，实例对象加()是即调用**call**的方法


### [6、请列举布尔值位False的常见值](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#6请列举布尔值位false的常见值)  


0、''、[]、{}、tuple()、None、set()


### [7、当退出Python时，是否释放全部内存？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#7当退出python时是否释放全部内存)  


答案是No。循环引用其它对象或引用自全局命名空间的对象的模块，在Python退出时并非完全释放。

另外，也不会释放C库保留的内存部分。


### [8、isinstance和type的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#8isinstance和type的作用)  


**1、** 两者都用来判断对象的类型

**2、** 对于一个类的之类对象的类型判断，type就不行了，而isinstance可以。

```pyyhon
class A(object):
pass
class B(A):
pass

ba=B()
ab=A()
print(type(ba)==A) # False
print(type(ab)==A) # True
print(isinstance(ab,A)) # True
print(isinstance(ba,A)) # True
```


### [9、描述以下dict的items和iteritems的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#9描述以下dict的items和iteritems的区别)  


python3中没有iteritems

items和iteritems大致相同，只是items返回的是一个列表，iteritems返回的是一个迭代器。


### [10、路由器和交换机的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#10路由器和交换机的区别)  


交换机是一种用于电信号转发的网络设备。路由器是链接因特网中各局域网和广域网的设备。

区别

**1、** 交换机工作在第二层，数据链路层，路由器工作在第三层，网络层。

**2、** 路由器提供防火墙服务。

**3、** 传统交换机只能风格冲突域，不能分割广播域，二路由器可以分割广播域。


### [11、如何基于Redis实现发布和订阅](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#11如何基于redis实现发布和订阅)  

### [12、列表和元组之间的区别是？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#12列表和元组之间的区别是)  

### [13、什么是并发和并行](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#13什么是并发和并行)  

### [14、解释Python中的join()和split()函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#14解释python中的join和split函数)  

### [15、什么是封装？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#15什么是封装)  

### [16、什么是cdn](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#16什么是cdn)  

### [17、公司线上和开发环境使用的什么系统](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#17公司线上和开发环境使用的什么系统)  

### [18、什么是猴子补丁？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#18什么是猴子补丁)  

### [19、解释re模块的split()、sub()、subn()方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#19解释re模块的splitsubsubn方法)  

### [20、简述事务及其特性](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#20简述事务及其特性)  

### [21、列举Redis支持的过期策略](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#21列举redis支持的过期策略)  

### [22、什么是负载均衡](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#22什么是负载均衡)  

### [23、列举常见的关系型数据库和非关系型数据库。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#23列举常见的关系型数据库和非关系型数据库。)  

### [24、字节码和机器码的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#24字节码和机器码的区别)  

### [25、_init_在Python中有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#25_init_在python中有什么用)  

### [26、如果Redis中的某个列表中的数据量非常大，如何实现循环显示每一个值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#26如果redis中的某个列表中的数据量非常大如何实现循环显示每一个值)  

### [27、什么是Flask？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#27什么是flask)  

### [28、MySQL执行计划的作用和使用方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#28mysql执行计划的作用和使用方法)  

### [29、列举你所了解的所有Python2和Python3的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#29列举你所了解的所有python2和python3的区别)  

### [30、什么是覆盖索引](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python中级面试题附答案汇总（2021年Python面试题及答案大全）.md#30什么是覆盖索引)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
