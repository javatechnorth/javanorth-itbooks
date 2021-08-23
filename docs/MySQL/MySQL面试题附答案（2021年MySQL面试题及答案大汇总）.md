# MySQL面试题附答案（2021年MySQL面试题及答案大汇总）

MySQL面试题及答案【最新版】MySQL高级面试题大全(2021版)，发现网上很多MySQL面试题及答案整理都没有答案，所以花了很长时间搜集，本套MySQL面试题大全，MySQL面试题大汇总，有大量经典的MySQL面试题以及答案，包含MySQL语言常见面试题、MySQL工程师高级面试题及一些大厂MySQL开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MySQL面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MySQL面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、主从同步延迟的原因](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#1主从同步延迟的原因)  


一个服务器开放Ｎ个链接给客户端来连接的，这样有会有大并发的更新操作, 但是从服务器的里面读取binlog的线程仅有一个，当某个SQL在从服务器上执行的时间稍长 或者由于某个SQL要进行锁表就会导致，主服务器的SQL大量积压，未被同步到从服务器里。这就导致了主从不一致， 也就是主从延迟。


### [2、数据库中的事务是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#2数据库中的事务是什么)  


事务（transaction）是作为一个单元的一组有序的数据库操作。如果组中的所有操作都成功，则认为事务成功，即使只有一个操作失败，事务也不成功。如果所有操作完成，事务则提交，其修改将作用于所有其他数据库进程。如果一个操作失败，则事务将回滚，该事务所有操作的影响都将取消。

**事务特性：**

**1、** 原子性：即不可分割性，事务要么全部被执行，要么就全部不被执行。

**2、** 一致性或可串性。事务的执行使得数据库从一种正确状态转换成另一种正确状态

**3、** 隔离性。在事务正确提交之前，不允许把该事务对数据的任何改变提供给任何其他事务，

**4、** 持久性。事务正确提交后，其结果将永久保存在数据库中，即使在事务提交后有了其他故障，事务的处理结果也会得到保存。

**或者这样理解：**

事务就是被绑定在一起作为一个逻辑工作单元的SQL语句分组，如果任何一个语句操作失败那么整个操作就被失败，以后操作就会回滚到操作前状态，或者是上有个节点。为了确保要么执行，要么不执行，就可以使用事务。要将有组语句作为事务考虑，就需要通过ACID测试，即原子性，一致性，隔离性和持久性。


### [3、索引的一些潜规则](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#3索引的一些潜规则)  


**1、** 覆盖索引

2、回表

**3、** 索引数据结构（B+树）

**4、** 最左前缀原则

**5、** 索引下推


### [4、MySql, Oracle，Sql Service的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#4mysql,-oraclesql-service的区别)  


**1、** Sql Service只能在Windows上使用，而MySql和Oracle可以在其他系统上使用， 而且可以支持数据库不同系统之间的移植

**2、** MySql开源免费的，Sql Service和Oracle要钱。

**3、** 我从小到大排序哈，MySql很小，Sql Service居中，Oracle最大

**4、** Oracle支持大并发量，大访问量，Sql Service还行，而MySql的话压力没这么大，因此现在的MySql的话最好是要使用集群或者缓存来搭配使用

**5、** Oracle支持多用户不同权限来进行操作，而MySql只要有登录权限就可操作全部数据库

**6、** 安装所用的空间差别也是很大的，MySQL安装完后才几百M而Oracle有几G左右，且使用的时候Oracle占用特别大的内存空间和其他机器性能。

**7、** 做分页的话，MySql使用Limit，Sql Service使用top，Oracle使用row

**8、** Oracle没有自动增长类型，MySQL和Sql Service一般使用自动增长类型


### [5、为表中得字段选择合适得数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#5为表中得字段选择合适得数据类型)  


字段类型优先级: 整形>date,time>enum,char>varchar>blob,text

优先考虑数字类型，其次是日期或者二进制类型，最后是字符串类型，同级别得数据类型，应该优先选择占用空间小的数据类型



### [6、MySQL一条SQL加锁分析](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#6mysql一条sql加锁分析)  


一条SQL加锁，可以分9种情况进行：

**1、** 组合一：id列是主键，RC隔离级别

**2、** 组合二：id列是二级唯一索引，RC隔离级别

**3、** 组合三：id列是二级非唯一索引，RC隔离级别

**4、** 组合四：id列上没有索引，RC隔离级别

**5、** 组合五：id列是主键，RR隔离级别

**6、** 组合六：id列是二级唯一索引，RR隔离级别

**7、** 组合七：id列是二级非唯一索引，RR隔离级别

**8、** 组合八：id列上没有索引，RR隔离级别

**9、** 组合九：Serializable隔离级别

### [7、事务的隔离级别有哪些？MySQL的默认隔离级别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#7事务的隔离级别有哪些mysql的默认隔离级别是什么)  


**1、** 读未提交（Read Uncommitted）

**2、** 读已提交（Read Committed）

**3、** 可重复读（Repeatable Read）

**4、** 串行化（Serializable）

MySQL默认的事务隔离级别是可重复读(Repeatable Read)


### [8、MySQL中in 和exists的区别。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#8mysql中in-和exists的区别。)  


这个，跟一下demo来看更刺激吧，啊哈哈

假设表A表示某企业的员工表，表B表示部门表，查询所有部门的所有员工，很容易有以下SQL:

```
select * from A where deptId in (select deptId from B);
```

**这样写等价于：**

**1、** 先查询部门表B

**2、** select deptId from B

**3、** 再由部门deptId，查询A的员工

**4、** select * from A where A.deptId = B.deptId

可以抽象成这样的一个循环：

```
List<> resultSet ;
 for(int i=0;i<B.length;i++) {
       for(int j=0;j<A.length;j++) {
       if(A[i].id==B[j].id) {
          resultSet.add(A[i]);
          break;
       }
    }
 }
```

显然，除了使用in，我们也可以用exists实现一样的查询功能，如下：

```
select * from A where exists (select 1 from B where A.deptId = B.deptId);
```

因为exists查询的理解就是，先执行主查询，获得数据后，再放到子查询中做条件验证，根据验证结果（true或者false），来决定主查询的数据结果是否得意保留。

那么，这样写就等价于：

> select * from A,先从A表做循环

> select * from B where A.deptId = B.deptId,再从B表做循环.


同理，可以抽象成这样一个循环：

```
   List<> resultSet ;
    for(int i=0;i<A.length;i++) {
          for(int j=0;j<B.length;j++) {
          if(A[i].deptId==B[j].deptId) {
             resultSet.add(A[i]);
             break;
          }
       }
    }
```

数据库最费劲的就是跟程序链接释放。假设链接了两次，每次做上百万次的数据集查询，查完就走，这样就只做了两次；相反建立了上百万次链接，申请链接释放反复重复，这样系统就受不了了。即MySQL优化原则，就是小表驱动大表，小的数据集驱动大的数据集，从而让性能更优。

因此，我们要选择最外层循环小的，也就是，如果**B的数据量小于A，适合使用in，如果B的数据量大于A，即适合选择exists**，这就是in和exists的区别。


### [9、500台db，在最快时间之内重启。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#9500台db在最快时间之内重启。)  


可以使用批量 ssh 工具 pssh 来对需要重启的机器执行重启命令。

也可以使用 salt（前提是客户端有安装 salt）或者 ansible（ ansible 只需要 ssh 免登通了就行）等多线程工具同时操作多台服务


### [10、数据库经常使用的函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#10数据库经常使用的函数)  


**1、** count(*/column)：返回行数

**2、** sum(column)： 返回指定列中唯一值的和

**3、** max(column)：返回指定列或表达式中的数值最大值

**4、** min(column)：返回指定列或表达式中的数值最小值

**5、** avg(column)：返回指定列或表达式中的数值平均值

**6、** date（Expression）: 返回指定表达式代表的日期值


### [11、优化特定类型的查询语句](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#11优化特定类型的查询语句)  

### [12、什么是数据库事务？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#12什么是数据库事务)  

### [13、数据表损坏的修复方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#13数据表损坏的修复方式有哪些)  

### [14、索引具体采用那种数据结构呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#14索引具体采用那种数据结构呢)  

### [15、读写分离常见方案？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#15读写分离常见方案)  

### [16、乐观锁：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#16乐观锁：)  

### [17、为什么要使用数据库](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#17为什么要使用数据库)  

### [18、什么是最左前缀原则？什么是最左匹配原则？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#18什么是最左前缀原则什么是最左匹配原则)  

### [19、MySQL中in 和exists的区别。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#19mysql中in-和exists的区别。)  

### [20、字段为什么要求定义为not null？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#20字段为什么要求定义为not-null)  

### [21、什么是最左前缀原则？什么是最左匹配原则](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#21什么是最左前缀原则什么是最左匹配原则)  

### [22、MySQL5.6和MySQL5.7对索引做了哪些优化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#22mysql56和mysql57对索引做了哪些优化)  

### [23、NOW（）和CURRENT_DATE（）有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#23now和current_date有什么区别)  

### [24、优化子查询](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#24优化子查询)  

### [25、日志的存放形式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#25日志的存放形式)  

### [26、SQL语句优化的一些方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#26sql语句优化的一些方法)  

### [27、事务特性：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#27事务特性：)  

### [28、怎样才能找出最后一次插入时分配了哪个自动增量？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#28怎样才能找出最后一次插入时分配了哪个自动增量)  

### [29、事务是如何通过日志来实现的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#29事务是如何通过日志来实现的)  

### [30、NULL是什么意思](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MySQL/MySQL面试题附答案（2021年MySQL面试题及答案大汇总）.md#30null是什么意思)  





