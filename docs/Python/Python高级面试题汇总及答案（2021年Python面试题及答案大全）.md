# Python高级面试题汇总及答案（2021年Python面试题及答案大全）

Python面试题及答案【最新版】Python高级面试题大全(2021版)，发现网上很多Python面试题及答案整理都没有答案，所以花了很长时间搜集，本套Python面试题大全，Python面试题大汇总，有大量经典的Python面试题以及答案，包含Python语言常见面试题、Python工程师高级面试题及一些大厂Python开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Python面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Python面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、你了解哪些数据库优化方案](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#1你了解哪些数据库优化方案)  


**1、** 减少数据访问-创建并正确使用索引

**2、** 返回更少的数据

**3、** 数据分页处理

**4、** 只返回需要的字段

**5、** 减少交互次数

**6、** 使用存储过程

**7、** 优化业务逻辑

**8、** 减少服务器的cpu运算

**9、** 使用绑定变量

**10、** 合理使用排序

**11、** 减少比较操作

**12、** 大量复杂运算在客户端处理

**13、** 利用更多资源

**14、** 客户端多进程访问

**15、** 数据库并行处理


### [2、解释什么是异步非阻塞](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#2解释什么是异步非阻塞)  


**1、** 同步和异步：

**2、** 同步：就是在发出一个功能调用时，在没有得到结果之前，该调用就不返回。

**3、** 异步：当一个异步过程调用发出后，调用者不会立刻得到结果。实际处理这个调用的部件是在调用发出后，通过状态、通知来通知调用者，或通过回调函数处理这个调用。

**4、** 阻塞和非阻塞

**5、** 阻塞：阻塞调用是指调用结果返回之前，当前线程会被挂起。函数只有在得到结果之后才会返回。

**6、** 非阻塞：指在不能立刻得到结果之前，该函数不会阻塞当前线程，而会立刻返回。

**7、** 阻塞，非阻塞：进程/线程要访问的数据是否就绪，进程/线程是否需要等待；

**8、** 同步，异步：访问数据的方式，同步需要主动读写数据，在读写数据的过程中还是会阻塞；异步只需要I/O操作完成的通知，并不主动读写数据，由操作系统内核完成数据的读写。


### [3、写一个函数，计算出以下字母所代表的数字，每个字母值不一样](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#3写一个函数计算出以下字母所代表的数字每个字母值不一样)  


```python
for A in range(1,10):
for B in range(10):
if A==B:
continue
for C in range(1,10):
if C in [A,B]:
    continue
for D in range(10):
    if D in [A,B,C]:
        continue
    for E in range(1,10):
        if E in [A,B,C,D]:
            continue
        for F in range(10):
            if F in [A,B,C,D,E]:
                continue
            for G in range(1,10):
                if G in [A,B,C,D,E,F]:
                    continue
                for H in range(10):
                    if H in [A,B,C,D,E,F,G]:
                        continue
                    for P in range(1,10):
                        if P in [A,B,C,D,E,F,G,H]:
                            continue
                        if (A*10+B)-(C*10+D)==(E*10+F) and (E*10+F)+(G*10+H)==(P*100+P*10+P):
                        print(A,B,C,D,E,F,G,H,P)
```


### [4、如何实现"1.2.3"变成['1','2','3']?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#4如何实现"123"变成['1','2','3'])  


```python
s="1,2,3"
s=s.split(',')
```


### [5、MySQL的增删改查](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#5mysql的增删改查)  


**增**

**指定字段名**

语法：INSERT INTO 表名（字段名1，字段名2，…）VALUES（值1，值2，…）；

举例：INSERT INTO student(id,name,grade) VALUES(1,'zhangshan',98);

**不指定字段名**

语法：INSERT INTO 表名 VALUES(值11，值2，…）；

举例：INSERT INTO student VALUES (2,'lisi',62);

**其他写法**

语法：INSERT INTO 表名 SET 字段名1=值1[,字段名2=值2，…]

举例：INSERT INTO student SET id=4，name='zhaoliu',grade=72;

**同时添加多条数据**

语法：INSERT INTO 表名[(字段名1，字段名2，…)] VALUES （值1，值2，…），（值1，值2，…），…（值1，值2，…）

举例：INSERT INTO student VALUES (5，‘lilei’,99), (6,'hanmeimei',87), (8,'poly',76);

**删**

**删除部分数据**

语法：DELETE FROM 表名 [WHERE 条件表达式]

命令：DELETE  FROM student WHERE id=7;

**删除全部数据**

语法：DELETE FROM 表名

命令：DELETE FROM student；

**推荐的删除全部数据**

语法：TRUNCTE [TABLE ] 表名

举例：TRUNCATE TABLE student

**改**

**更新部分数据**

语法：UPDATE 表名 SET 字段名1=值1，[ ，字段名2=值2，…] [ WHERE 条件表达式 ]

命令：UPDATE student SET name=‘caocao’,grade=50 WHERE id=1;

**更新全部数据**

语法：UPDATE 表名 SET 字段名=值

命令：UPDATE student SET grade=80；

**查**

**查询所有字段**

语法：SELECT 字段名1，字段名2，… FROM 表名 （该语法也可以查询部分字段）

语法：SELECT FROM 表名；

**按条件查询**

语法：SELECT 字段名1，字段名2，… FROM 表名 WHERE 条件表达式

命令：SELECT id，name FROM student2  WHERE id=4;

**带IN关键字的查询**

**1、** 语法：SELECT | 字段名1，字段名2，… FROM 表名 WHERE 字段名 [ NOT ]  IN （元素1，元素2，…）

**2、** 命令：SELECT FROM student2 WHERE id IN （1,2,3）；

**3、** 带 BETWEEN AND  关键字的查询

**4、** 语法：SELECT | { 字段名1，字段名2，… } FROM  表名 WHERE 字段名 [ NOT ] BETWEEN  值1  AND  值2；

**5、** 命令：SELECT id,name FROM students WHERE id BETWEEN 2 AND 5;

**空值查询**

语法：SELECT | 字段名1，字段名2，… FROM 表名 WHERE 字段名 IS [ NOT ] NULL

命令：SELECT FROM student2 WHERE gender IS NULL;

**带 DISTINCT 关键字的查询**

语法：SELECT DISTINCT 字段名 FROM 表名；

命令：SELECT DISTINCT gender FROM student2;

**带 LIKE 关键字的查询**

语法：SELECT | 字段名1，字段名2，… FROM 表名 WHERE 字段名 [ NOT ] LIKE ‘匹配字符串’;

**注意：%表示匹配任意长度的字符串，_表示匹配单个字符串**

**3、** 命令：SELECT id,name FROM student2  WHERE name LIKE "S%";

**4、** 命令：SELECT id,name FROM student2 WHERE name LIKE 'w%g';

**5、** 命令：SELECT id,name FROM student2 WHERE name NOT LIKE '%y%';

**6、** 命令：SELECT FROM student2 WHERE name LIKE 'wu_ong';

**带 AND 关键字的多条件查询**

**1、** 语法：SELECT | 字段名1，字段名2，… FROM 表名 WHERE 条件表达式1 AND 条件表达式2 [ … AND 条件表达式 n ];

**2、** 命令：SELECT id,name FROM student2 WHERE id<5 AND gender='女';

**带 OR 关键字的多条件查询**

**1、** 语法：SELECT | 字段名1，字段名2，… FROM 表名 WHERE 条件表达式1 OR 条件表达式2 [ … OR 条件表达式 n ];

**2、** 命令：SELECT id,name ,gender FROM student2 WHERE id<3 OR gender='女';

**AND和OR一起使用时，AND的优先级高于OR**

**聚合函数**

**COUNT()函数：统计记录的条数**

语法：SELECT COUNT(*) FROM 表名举例：

命令：SELECT COUNT(*) FROM student2;

**SUM()函数：求出表中某个字段所有值的总和**

语法：SELECT  SUM(字段名) FROM 表名；

命令：SELECT SUM(grade) FROM student2;

**AVG()函数：求出表中某个字段所有值的平均值**

语法：SELECT AVG(字段名) FROM 表名；

命令：SELECT AVG(grade) FROM student2;

**MAX()函数：求出表中某个字段所有值的最大值**

语法：SELECT MAX(字段名) FROM 表名；

命令：SELECT MAX(grade) FROM student2;

**MIN()函数：求出表中某个字段所有值的最小值**

语法：SELECT MIN(字段名) FROM 表名；

命令：SELECT MIN(grade) FROM student2;

**对查询结果进行排序**

语法：SELECT 字段名1，字段名2，… FROM 表名 ORDER BY 字段名1 [ ASC | DESC ],字段名2 [ ASC | DESC ]

(升序)命令：SELECT FROM student2 ORDER BY grade;

(降序)命令：命令：SELECT FROM student2 ORDER BY grade DESC;

**分组查询**

语法：SELECT  字段名1，字段名2，… FROM 表名 GROUP BY 字段名1，字段名2，… [ HAVING 条件表达式 ];

**单独使用 GROUP BY 进行分组**

命令：SELECT FROM student2 GROUP BY gender;

**GROUP BY 和聚合函数一起使用**

命令：SELECT COUNT(*) ,gender FROM student2 GROUP BY gender;

**GROUP BY 和 HAVING 关键字一起使用**

命令：SELECT sum(grade),gender FROM student2 GROUP BY gender HAVING SUM(grade) < 300;

**使用 LIMIT 限制查询结果的数量**

语法：SELECT 字段名2，字段名2，… FROM 表名 LIMIT [ OFFSET ,] 记录数

(从0开始的4条)命令：SELECT FROM student LIMIT 4;

(从第五条开始的4条)命令：SELECT FROM student2 ORDER BY grade DESC LIMIT 4,4;

**为表和字段取别名**

语法：SELECT FROM 表名 [ AS ] 别名；

命令：SELECT FROM student2 AS s WHERE s.gender='女';

**为字段取别名**

语法：SELECT 字段名 [ AS ] 别名 [ ,字段名 [AS] 别名，…]  FROM 表名 ；

命令：SELECT name AS stu_name,gender AS stu_gender FROM student2;


### [6、写出以下代码的输出结果：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#6写出以下代码的输出结果：)  


```python
def test():
try:
raise ValueError('something wrong')
except ValueError as e:
print('error occured')
return
finally:
print('ok')
test()
```

结果(finally无论怎样都会执行)

> error occured

ok



### [7、什么是lambda函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#7什么是lambda函数)  


Lambda函数是不带名称的单行函数，可以具有n个参数，但只能有一个表达式。也称为匿名函数。

```
a = lambda x, y：x + y 
print(a(5, 6))

> 11
```


### [8、解释一下Python中的赋值运算符](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#8解释一下python中的赋值运算符)  


这在Python面试中是个重要的面试问题。

我们将所有的算术运算符和赋值符号放在一起展示：

```
>>> a=7
>>> a+=1
>>> a
8
 
>>> a-=1
>>> a
7
 
>>> a*=2
>>> a
14
 
>>> a/=2
>>> a
7.0 
 
>>> a**=2
>>> a
49
 
>>> a//=3
>>> a
16.0
 
>>> a%=4
>>> a
0.0
```


### [9、使用两个队列实现一个栈](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#9使用两个队列实现一个栈)  


```python
class Stack(object):
def __init__(self):
self.queueA=[]
self.queueB=[]
def push(self,node):
self.queueA.append(node)
def pop(self):
if len(self.queueA)==0:
return None
while len(self.queueA)!=1:
self.queueB.append(self.queueA.pop(0))
self.queueA,self.queueB=self.queueB,self.queueA
return self.queueB.pop()

st=Stack()
print(st.pop())
st.push(1)
print(st.pop())
st.push(1)
st.push(1)
st.push(1)
print(st.pop())
print(st.pop())
print(st.pop())
```

注意上面两个栈的实现方法，第一种的效率高，队列的这种方法效率低


### [10、用尽量简洁的方法将二维数组合并成一维数组](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#10用尽量简洁的方法将二维数组合并成一维数组)  


```python
lst = [[1,2,3],[4,5,6],[7,8,9]]
ll=[]
for l in lst:
# ll+=l
ll.extend(l)
print(ll)
```


### [11、什么是防火墙？防火墙的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#11什么是防火墙防火墙的作用是什么)  

### [12、yield from 和 yield 的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#12yield-from-和-yield-的区别)  

### [13、Redis和Memcached的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#13redis和memcached的区别)  

### [14、在Python中如何使用多进制数字？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#14在python中如何使用多进制数字)  

### [15、json序列化时可以处理的数据类型有哪些？如何定制支持datetime类型？序列化时，遇到中文转成unicode，如何保持中文形式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#15json序列化时可以处理的数据类型有哪些如何定制支持datetime类型序列化时遇到中文转成unicode如何保持中文形式)  

### [16、Python是否有main函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#16python是否有main函数)  

### [17、位和字节的关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#17位和字节的关系)  

### [18、三元运算编写格式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#18三元运算编写格式)  

### [19、什么是haproxy？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#19什么是haproxy)  

### [20、编写一个函数实现十进制转62进制，分别用0-9A-Za-z,表示62位字母](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#20编写一个函数实现十进制转62进制分别用0-9a-za-z,表示62位字母)  

### [21、判断dict中有没有某个key。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#21判断dict中有没有某个key。)  

### [22、解释Python中的Filter？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#22解释python中的filter)  

### [23、用一行代码实现数值交换](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#23用一行代码实现数值交换)  

### [24、是否使用过functools中的函数？他的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#24是否使用过functools中的函数他的作用是什么)  

### [25、简述生成器，迭代器，装饰器以及应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#25简述生成器迭代器装饰器以及应用场景)  

### [26、Python代码是如何执行的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#26python代码是如何执行的)  

### [27、一行代码通过filter和lambda函数输出alist=[1,22,2,33,23,32]中索引为奇数的值](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#27一行代码通过filter和lambda函数输出alist=[1,22,2,33,23,32]中索引为奇数的值)  

### [28、如何查找一个字符串中特定的字符？find和index的差异？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#28如何查找一个字符串中特定的字符find和index的差异)  

### [29、将列表按照下列规则排序：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#29将列表按照下列规则排序：)  

### [30、输入一个字符串，输出该字符串的字符的所有组合。如输入'abc',输出a,b,c,ab,ac,bc,abc.](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Python/Python高级面试题汇总及答案（2021年Python面试题及答案大全）.md#30输入一个字符串输出该字符串的字符的所有组合。如输入'abc',输出a,b,c,ab,ac,bc,abc)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
