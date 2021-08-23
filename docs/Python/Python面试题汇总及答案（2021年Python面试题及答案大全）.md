# Python面试题汇总及答案（2021年Python面试题及答案大全）

Python面试题及答案【最新版】Python高级面试题大全(2021版)，发现网上很多Python面试题及答案整理都没有答案，所以花了很长时间搜集，本套Python面试题大全，Python面试题大汇总，有大量经典的Python面试题以及答案，包含Python语言常见面试题、Python工程师高级面试题及一些大厂Python开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Python面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Python面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是keepalived](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#1什么是keepalived)  


Keepalived是Linux下一个轻量级别的高可用解决方案


### [2、二叉树是非线性结构，栈和队列以及线性表都是线性结构，对吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#2二叉树是非线性结构栈和队列以及线性表都是线性结构对吗)  


对的


### [3、char和varchar的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#3char和varchar的区别)  


**1、** 保存方式不一样

**2、** char有固定的长度，而varchar属于可变长的字符类型

**3、** char的效率比varchar高


### [4、Python中的pass语句是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#4python中的pass语句是什么)  


在用Python写代码时，有时可能还没想好函数怎么写，只写了函数声明，但为了保证语法正确，必须输入一些东西，在这种情况下，我们会使用pass语句。

```
 >>> def func(*args):
           pass 
>>>
```

同样，break语句能让我们跳出循环。

```
>>> for i in range(7):
    if i==3: break
print(i)
```

结果：

```
0
 
1
 
2
```

最后，continue语句能让我们跳到下个循环。

```
>>> for i in range(7):
    if i==3: continue
print(i)
```

结果：

```
0
 
1
 
2
 
4
 
5
 
6
```


### [5、进程之间如何进行通信？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#5进程之间如何进行通信)  


**1、** 共享内存

通过mmap模块实现

2、信号

**3、** 通过Queue队列

**4、** 通过Pipe管道

**5、** 通过socket


### [6、将下面列表中的元素根据位数合并成字典：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#6将下面列表中的元素根据位数合并成字典：)  


```python

lst = [1,2,4,8,16,32,64,128,256,512,1024,32769,65536,4294967296]

# 结果
{1: [1, 2, 4, 8], 2: [16, 32, 64], 3: [128, 256, 512], 4: [1024], 5: [32769, 65536], 10: [4294967296]}
```

```python

lst = [1,2,4,8,16,32,64,128,256,512,1024,32769,65536,4294967296]
dic={}
for i in lst:
len_i=len(str(i))
dic.setdefault(len_i,[]).append(i)
print(dic)
```


### [7、解释一下Python中的逻辑运算符](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#7解释一下python中的逻辑运算符)  


Python中有3个逻辑运算符：and，or，not。

```
>>> False and True
False
 
>>> 7<7 or True
True
 
>>> not 2==2
False
```


### [8、如何在函数中设置一个全局变量？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#8如何在函数中设置一个全局变量)  


在函数中使用global关键字定义变量


### [9、JavaScript(或者jQuery)如何选择一个id为main的容器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#9javascript或者jquery如何选择一个id为main的容器)  


**1、** jquery：$('#id')

**2、** JavaScript：document.getElementById("id"))


### [10、简述SQL注入原理，以及如何在代码层面房子sql注入](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#10简述sql注入原理以及如何在代码层面房子sql注入)  


通俗点讲，SQL注入的根本原因是: "用户输入数据"意外变成了代码被执行。

"用户输入数据"我这里可以指Web前端$_POST,$_GET获取的数据，也可以指从数据库获取的数据，当然也不排除程序猿无意中使用的特殊字符串。

在SQL语句的拼接中，一些含特殊字符的变量在拼接时破坏了SQL语句的结构，导致"用户输入数据"意外变成了代码被执行。

**规避方法：**

**1、** 理语句法  (解析协议层面上完全规避SQL注入)

**2、** 字符串转义（不要在sql中拼接字符）


### [11、什么是c3算法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#11什么是c3算法)  

### [12、什么是switch语句。如何在Python中创建switch语句？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#12什么是switch语句。如何在python中创建switch语句)  

### [13、Redis是单进程单线程的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#13redis是单进程单线程的吗)  

### [14、什么是rpc](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#14什么是rpc)  

### [15、简述数据库分库分表](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#15简述数据库分库分表)  

### [16、pass的使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#16pass的使用)  

### [17、编写程序，打印斐波那契数列的前十项](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#17编写程序打印斐波那契数列的前十项)  

### [18、列表推导式[i for i in range(10)]和生成式表达式(i for i in range(10))的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#18列表推导式[i-for-i-in-range10]和生成式表达式i-for-i-in-range10的区别)  

### [19、解释//、％、* *运算符？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#19解释//％*-*运算符)  

### [20、filter、map、reduce的作用。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#20filtermapreduce的作用。)  

### [21、什么是鸭子模型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#21什么是鸭子模型)  

### [22、css如何隐藏一个元素](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#22css如何隐藏一个元素)  

### [23、发生粘包现象如何处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#23发生粘包现象如何处理)  

### [24、Python中的闭包是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#24python中的闭包是什么)  

### [25、一个大小为100G的文件etl_log.txt，要读取文件的内容，写出具体过程代码](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#25一个大小为100g的文件etl_logtxt要读取文件的内容写出具体过程代码)  

### [26、一个数如果恰好等于它的因子之和，这个数就称为‘完数’，比如6=1+2+3，编程找出1000以内的所有的完数。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#26一个数如果恰好等于它的因子之和这个数就称为‘完数’比如6=1+2+3编程找出1000以内的所有的完数。)  

### [27、python是如何进行内存管理的？python的程序会内存泄漏吗？说说有没有什么方面阻止或者检测内存泄漏？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#27python是如何进行内存管理的python的程序会内存泄漏吗说说有没有什么方面阻止或者检测内存泄漏)  

### [28、区分Python中的remove，del和pop？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#28区分python中的removedel和pop)  

### [29、有两个字符串列表a和b，每个字符串是由逗号隔开的一些字符](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#29有两个字符串列表a和b每个字符串是由逗号隔开的一些字符)  

### [30、解释一下Python中的身份运算符](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题汇总及答案（2021年Python面试题及答案大全）.md#30解释一下python中的身份运算符)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
