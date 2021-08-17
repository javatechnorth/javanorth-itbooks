# Python面试题附答案（2021年Python面试题及答案大汇总）

Python面试题及答案【最新版】Python高级面试题大全(2021版)，发现网上很多Python面试题及答案整理都没有答案，所以花了很长时间搜集，本套Python面试题大全，Python面试题大汇总，有大量经典的Python面试题以及答案，包含Python语言常见面试题、Python工程师高级面试题及一些大厂Python开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Python面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Python面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、使用python将数据库的student表中的数据写入db.txt](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#1使用python将数据库的student表中的数据写入dbtxt)  


```python
import pyMySQL
connect=pyMySQL.Connect(
host='',
port=,
user='',
passwd='',
db='',
charset='',
)

cursor=connect.cursor()
sql='select from student'
cursor.execute(sql)
students=cursor.fetchall()

with open('db.txt','w') as f:
for student in students:
f.write(student)

cursor.close()
connect.close()
```


### [2、py2项目如何迁移成py3](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#2py2项目如何迁移成py3)  


**1、** 先备份原文件，然后使用python3自带工具2to3.py将py2文件转换位py3文件

**2、** 手动将不兼容的代码改写成兼容py3的代码


### [3、有一个多层嵌套的列表A=[1,2,3,[4,1,['j1',1,[1,2,3,'aa']]]],请写一段代码将A中的元素全部打印出来](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#3有一个多层嵌套的列表a=[1,2,3,[4,1,['j1',1,[1,2,3,'aa']]]],请写一段代码将a中的元素全部打印出来)  


```python
A=[1,2,3,[4,1,['j1',1,[1,2,3,'aa']]]]
def my_print(lis):
for i in lis:
if type(i)==list:
my_print(i)
else:
print(i)
my_print(A)
```


### [4、python代码如何获取命令行参数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#4python代码如何获取命令行参数)  


[获取命令行参数的方法参考](https://www.cnblogs.com/ouyangpeng/p/8537616.html)

**1、** 使用sys模块

通过sys.argv来获取

**2、** 使用getopt模块


### [5、Python有哪些特点和优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#5python有哪些特点和优点)  


作为一门编程入门语言，Python主要有以下特点和优点：

**1、** 可解释

**2、** 具有动态特性

**3、** 面向对象

**4、** 简明简单

5、开源

**6、** 具有强大的社区支持

当然，实际上Python的优点远不止如此，


### [6、如何判断一个值是方法还是函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#6如何判断一个值是方法还是函数)  


**1、** 使用type()来判断，如果是method为方法，如果是function则是函数。

**2、** 与类和实例无绑定关系的function都属于函数（function）

**3、** 与类和实例有绑定关系的function都属于方法


### [7、描述以下字典的items()方法和iteritems()方法有啥不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#7描述以下字典的items方法和iteritems方法有啥不同)  


**1、** 字典的items方法作用：是可以将字典中的所有项，以列表方式返回。因为字典是无序的，所以用items方法返回字典的所有项，也是没有顺序的。

**2、** 字典的iteritems方法作用：与items方法相比作用大致相同，只是它的返回值不是列表，而是一个迭代器


### [8、Python的局限性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#8python的局限性)  


**1、**  速度

**2、**  移动开发

**3、**  内存消耗(与其他语言相比非常高)

**4、**  两个版本的不兼容(2，3)

**5、**  运行错误(需要更多测试，并且错误仅在运行时显示)

**6、**  简单性


### [9、如何用一行代码生成[1,4,9,16,25,36,49,64,81,100]?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#9如何用一行代码生成[1,4,9,16,25,36,49,64,81,100])  


```python
lis=[i**2 for i in range(1,11)]
```


### [10、lambda表达式格式以及应用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#10lambda表达式格式以及应用场景)  


格式：lambda 参数列表 : 返回表达式

应用场景：常见的在filter，reduce以及map中使用。


### [11、如何保证api调用时数据的安全性](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#11如何保证api调用时数据的安全性)  

### [12、曾经使用过哪些前端框架](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#12曾经使用过哪些前端框架)  

### [13、了解过Hbase，DB2，SQLServer，Access吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#13了解过hbasedb2sqlserveraccess吗)  

### [14、axios的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#14axios的作用)  

### [15、python的垃圾回收机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#15python的垃圾回收机制)  

### [16、什么是Twemproxy](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#16什么是twemproxy)  

### [17、如何实现['1','2','3']变成[1,2,3]](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#17如何实现['1','2','3']变成[1,2,3])  

### [18、守护线程，守护进程是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#18守护线程守护进程是什么)  

### [19、编写程序，查找文本文件中最长的单词](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#19编写程序查找文本文件中最长的单词)  

### [20、下面代码的执行结果是](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#20下面代码的执行结果是)  

### [21、为什么学python](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#21为什么学python)  

### [22、为什么基于tcp协议的通信比基于udp协议的通信更可靠](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#22为什么基于tcp协议的通信比基于udp协议的通信更可靠)  

### [23、Python中使用的zip函数是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#23python中使用的zip函数是什么)  

### [24、以下代码输出什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#24以下代码输出什么)  

### [25、使用async语法实现一个协程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#25使用async语法实现一个协程)  

### [26、文件操作时，xreadlines和readlines的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#26文件操作时xreadlines和readlines的区别)  

### [27、Python中OOPS是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#27python中oops是什么)  

### [28、python的可变类型和不可变类型的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#28python的可变类型和不可变类型的区别)  

### [29、对列表[3,1,-4,-2]按照绝对值排序](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#29对列表[3,1,-4,-2]按照绝对值排序)  

### [30、索引再什么情况下遵循最左前缀的规则？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python面试题附答案（2021年Python面试题及答案大汇总）.md#30索引再什么情况下遵循最左前缀的规则)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
