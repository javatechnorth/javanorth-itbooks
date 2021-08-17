# Python高级面试题附答案汇总（2021年Python面试题及答案大全）

Python面试题及答案【最新版】Python高级面试题大全(2021版)，发现网上很多Python面试题及答案整理都没有答案，所以花了很长时间搜集，本套Python面试题大全，Python面试题大汇总，有大量经典的Python面试题以及答案，包含Python语言常见面试题、Python工程师高级面试题及一些大厂Python开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Python面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Python面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、sys.path.append('xxx')的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#1syspathappend'xxx'的作用)  


添加搜索路径


### [2、Python中的标识符长度能有多长？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#2python中的标识符长度能有多长)  


在Python中，标识符可以是任意长度。此外，我们在命名标识符时还必须遵守以下规则：

**1、**   只能以下划线或者 A-Z/a-z 中的字母开头

**2、**   其余部分可以使用 A-Z/a-z/0-9

**3、**   区分大小写

**4、**   关键字不能作为标识符，Python中共有如下关键字：

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/4/30/200/33/53_3.png#alt=53%5C_3.png)


### [3、写出如下代码的输出结果](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#3写出如下代码的输出结果)  


```python
def decorator_a(func):
print('Get in decorator_a')
def inner_a(*args, **kwargs):
print('Get in inner_a')
return func(*args, **kwargs)
return inner_a

def decorator_b(func):
print('Get in decorator_b')
def inner_b(*args, **kwargs):
print('Get in inner_b')
return func(*args, **kwargs)
return inner_b

@decorator_b #f=decorator_b(f)
@decorator_a #f=decorator_a(f)
def f(x):
print('Get in f')
return x 2
f(1)
```

答案

> Get in decorator_a

Get in decorator_b

Get in inner_b

Get in inner_a

Get in f


解释

> 当我们对f传入参数1进行调用时，inner_b被调用了，他会先打印Get in inner_b,然后在inner_b内部调用了inner_a,所以会再打印Get in inner_a,然后再inner_a内部调用原来的f,并且将结果作为最终的返回总结：装饰器函数在被装饰函数定义好后立即执行从下往上执行函数调用时从上到下执行



### [4、vuex的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#4vuex的作用)  


**1、** 组件之间的数据通信

**2、** 使用单向数据流的方式进行数据的去中心化管理


### [5、将列表alist=[{'name':'a','age':25},{'name':'b','age':30},{'name':'c','age':20}]，按照age的值从大到小排列。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#5将列表alist=[{'name':'a','age':25},{'name':'b','age':30},{'name':'c','age':20}]按照age的值从大到小排列。)  


```python
alist=[{'name':'a','age':25},{'name':'b','age':30},{'name':'c','age':20}]
blist=sorted(alist,key=lambda x:x['age'],reverse=True)
print(blist)
```


### [6、编写程序，检查数字是否为Armstrong](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#6编写程序检查数字是否为armstrong)  


将每个数字依次分离，并累加其立方(位数)。

最后，如果发现总和等于原始数，则称为阿姆斯特朗数(Armstrong)。

```
num = int(input("Enter the number:\n"))
order = len(str(num))

sum = 0
temp = num

while temp > 0:
   digit = temp % 10
   sum += digit ** order
   temp //= 10

if num == sum:
   print(num,"is an Armstrong number")
else:
   print(num,"is not an Armstrong number")
```


### [7、什么是gevent](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#7什么是gevent)  


gevent是一个pythn网络框架，它为各种并发和网络相关的任务提供了整洁的API


### [8、你对Python类中的self有什么了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#8你对python类中的self有什么了解)  


self表示类的实例。

通过使用self关键字，我们可以在Python中访问类的属性和方法。

注意，在类的函数当中，必须使用self，因为类中没有用于声明变量的显式语法。


### [9、什么是粘包？出现粘包的原因？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#9什么是粘包出现粘包的原因)  


**1、** 粘包：多个数据包被连续存储于连续的缓存中，在对数据包进行读取时由于无法确定发生方的发送边界，而采用某一估测值大小来进行数据读出，若双方的size不一致时就会使指发送方发送的若干包数据到接收方接收时粘成一包，从接收缓冲区看，后一包数据的头紧接着前一包数据的尾。

**2、** 出现粘包现象的原因是多方面的，它既可能由发送方造成，也可能由接收方造成。

**3、** 发送方引起的粘包是由TCP协议本身造成的，TCP为提高传输效率，发送方往往要收集到足够多的数据后才发送一包数据。若连续几次发送的数据都很少，通常TCP会根据优化算法把这些数据合成一包后一次发送出去，这样接收方就收到了粘包数据。

**4、** 接收方引起的粘包是由于接收方用户进程不及时接收数据，从而导致粘包现象。这是因为接收方先把收到的数据放在系统接收缓冲区，用户进程从该缓冲区取数据，若下一包数据到达时前一包数据尚未被用户进程取走，则下一包数据放到系统接收缓冲区时就接到前一包数据之后，而用户进程根据预先设定的缓冲区大小从系统接收缓冲区取数据，这样就一次取到了多包数据。


### [10、请列出至少5个PEP8规范](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#10请列出至少5个pep8规范)  


**1、** 每个缩进级别使用4个空格

**2、** 每行代码的最大长度限制为79个字符

**3、** 若是导入多个库函数，应该分开依次导入

**4、** 道路应按照以下顺序导入

a、标准库导入

b、相关的第三方库导入

c、本地应用程序的库导入

**1、** 在表达式中避免无关的空格

**2、** 在括号或者大括号内

**3、** 在尾随逗号和后面的右括号之间

**4、** 在逗号，分号或者冒号前面

**5、** 函数名的与后面的参数的括号之间

**6、** 代码更改时，相应的注释也要随之更改

**7、** 命名要规范，通俗易懂


### [11、实现一个装饰器，限制该函数被调用的频率，如10秒一次](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#11实现一个装饰器限制该函数被调用的频率如10秒一次)  

### [12、有如下链表类，请实现单链表逆置。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#12有如下链表类请实现单链表逆置。)  

### [13、什么是Python？为什么它会如此流行？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#13什么是python为什么它会如此流行)  

### [14、如何以就地操作方式打乱一个列表的元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#14如何以就地操作方式打乱一个列表的元素)  

### [15、介绍一下try except的用法和作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#15介绍一下try-except的用法和作用)  

### [16、简述解释型和编译型编程语言](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#16简述解释型和编译型编程语言)  

### [17、简述TCP三次握手，四次挥手的流程。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#17简述tcp三次握手四次挥手的流程。)  

### [18、列举面向对象中带双下划线的特殊方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#18列举面向对象中带双下划线的特殊方法)  

### [19、为什么数据很大的时候使用limit offset分页时，越往后翻速度越慢，如何优化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#19为什么数据很大的时候使用limit-offset分页时越往后翻速度越慢如何优化)  

### [20、比较：a=[1,2,3]和b=[(1),(2),(3)]以及c=[(1,),(2,),(3,)]的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#20比较：a=[1,2,3]和b=[1,2,3]以及c=[1,,2,,3,]的区别)  

### [21、深拷贝和浅拷贝之间的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#21深拷贝和浅拷贝之间的区别是什么)  

### [22、从0-99这100个数中随机取出10个，要求不能重复](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#22从0-99这100个数中随机取出10个要求不能重复)  

### [23、常用字符串格式化有哪几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#23常用字符串格式化有哪几种)  

### [24、Python中的装饰器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#24python中的装饰器是什么)  

### [25、简述left join和right join的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#25简述left-join和right-join的区别)  

### [26、Redis默认多少个db](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#26redis默认多少个db)  

### [27、Python中的生成器是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#27python中的生成器是什么)  

### [28、什么是负索引？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#28什么是负索引)  

### [29、列表中保留顺序和不保留顺序去重](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#29列表中保留顺序和不保留顺序去重)  

### [30、xrange和range的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题附答案汇总（2021年Python面试题及答案大全）.md#30xrange和range的区别)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
