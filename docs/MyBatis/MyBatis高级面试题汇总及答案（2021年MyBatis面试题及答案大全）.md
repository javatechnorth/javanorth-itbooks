# MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）

MyBatis面试题及答案【最新版】MyBatis高级面试题大全(2021版)，发现网上很多MyBatis面试题及答案整理都没有答案，所以花了很长时间搜集，本套MyBatis面试题大全，MyBatis面试题大汇总，有大量经典的MyBatis面试题以及答案，包含MyBatis语言常见面试题、MyBatis工程师高级面试题及一些大厂MyBatis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MyBatis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MyBatis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、{}里面的名称对应的是Map里面的key名称。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#1{}里面的名称对应的是map里面的key名称。)  


这种方法适合传递多个参数，且参数易变能灵活传递的情况。（推荐使用）。

**方法4：Java Bean传参法**

```
public User selectUser(User user);

<select id="selectUser" parameterType="com.jourwon.pojo.User" resultMap="UserResultMap">
select * from user
where user_name ={userName} and dept_id ={deptId}
</select>
```

**1、** #{}里面的名称对应的是User类里面的成员属性。

**2、** 这种方法直观，需要建一个实体类，扩展不容易，需要加属性，但代码可读性强，业务逻辑处理方便，推荐使用。（推荐使用）。


### [2、IBatis 和 MyBatis 在细节上的不同有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#2ibatis-和-mybatis-在细节上的不同有哪些)  


**1、** 在 sql 里面变量命名有原来的#变量# 变成了#{变量}

**2、** 原来的$$变量$$变成了${变量}

**3、** 原来在 sql 节点里面的 class 都换名字交 type

**4、** 原来的 queryForObject queryForList 变成了 selectOne selectList5、原来的别名设置在映


### [3、什么是Mybatis？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#3什么是mybatis)  


**1、** Mybatis是一个半ORM（对象关系映射）框架，它内部封装了JDBC，开发时只需要关注SQL语句本身，不需要花费精力去处理加载驱动、创建连接、创建statement等繁杂的过程；

**2、** MyBatis 可以使用 XML 或注解来配置和映射原生信息，将 POJO映射成数据库中的记录，避免了几乎所有的 JDBC 代码和手动设置参数以及获取结果集；

**3、** 通过xml 文件或注解的方式将要执行的各种 statement 配置起来，并通过java对象和 statement中[MySQL](https://www.wkcto.com/courses/MySQL.html)的动态参数进行映射生成最终执行的sql语句，最后由mybatis框架执行sql并将结果映射为java对象并返回。


### [4、请说说MyBatis的工作原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#4请说说mybatis的工作原理)  


在学习 MyBatis 程序之前，需要了解一下 MyBatis 工作原理，以便于理解程序。MyBatis 的工作原理如下图 ![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/041/14/55_1.png#alt=55%5C_1.png)

**1、** 读取 MyBatis 配置文件：mybatis-config.xml 为 MyBatis 的全局配置文件，配置了 MyBatis 的运行环境等信息，例如数据库连接信息。

**2、** 加载映射文件。映射文件即 SQL 映射文件，该文件中配置了操作数据库的 SQL 语句，需要在 MyBatis 配置文件 mybatis-config.xml 中加载。mybatis-config.xml 文件可以加载多个映射文件，每个文件对应数据库中的一张表。

**3、** 构造会话工厂：通过 MyBatis 的环境等配置信息构建会话工厂 SqlSessionFactory。

**4、** 创建会话对象：由会话工厂创建 SqlSession 对象，该对象中包含了执行 SQL 语句的所有方法。

**5、** Executor 执行器：MyBatis 底层定义了一个 Executor 接口来操作数据库，它将根据 SqlSession 传递的参数动态地生成需要执行的 SQL 语句，同时负责查询缓存的维护。

**6、** MappedStatement 对象：在 Executor 接口的执行方法中有一个 MappedStatement 类型的参数，该参数是对映射信息的封装，用于存储要映射的 SQL 语句的 id、参数等信息。

**7、** 输入参数映射：输入参数类型可以是 Map、List 等集合类型，也可以是基本数据类型和 POJO 类型。输入参数映射过程类似于 JDBC 对 preparedStatement 对象设置参数的过程。

**8、** 输出结果映射：输出结果类型可以是 Map、 List 等集合类型，也可以是基本数据类型和 POJO 类型。输出结果映射过程类似于 JDBC 对结果集的解析过程。


### [5、Mybatis编程步骤 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#5mybatis编程步骤-)  


**1、** 创建SQLSessionFactory

**2、** 通过SQLSessionFactory创建SQLSession

**3、** 通过SQLSession执行数据库操作

**4、** 调用session.commit()提交事物 Step5：调用session.close()关闭会话


### [6、Mybatis 都有哪些 Executor 执行器？它们之间的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#6mybatis-都有哪些-executor-执行器它们之间的区别是什么)  


Mybatis 有三种基本的 Executor 执行器，SimpleExecutor、ReuseExecutor、

BatchExecutor。1、SimpleExecutor：每执行一次 update 或 select，就开启一个 Statement 对

象，用完立刻关闭 Statement 对象。2、ReuseExecutor：执行 update 或 select，以 sql 作为

key 查找 Statement 对象，存在就使用，不存在就创建，用完后，不关闭 Statement 对象，

而是放置于 Map3、BatchExecutor：完成批处理。


### [7、MyBatis框架的缺点有什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#7mybatis框架的缺点有什么)  


**1、** SQL语句的编写工作量较大，尤其当字段多、关联表多时，对开发人员编写SQL语句的功底有一定要求；

**2、** SQL语句依赖于数据库，导致数据库移植性差，不能随意更换数据库。


### [8、Mybatis的一级缓存和二级缓存？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#8mybatis的一级缓存和二级缓存)  


**1、** 一级缓存 Mybatis的一级缓存是指SQLSession，一级缓存的作用域是SQlSession, Mabits默认开启一级缓存。 在同一个SqlSession中，执行相同的SQL查询时；第一次会去查询数据库，并写在缓存中，第二次会直接从缓存中取。 当执行SQL时候两次查询中间发生了增删改的操作，则SQLSession的缓存会被清空。 每次查询会先去缓存中找，如果找不到，再去数据库查询，然后把结果写到缓存中。 Mybatis的内部缓存使用一个HashMap，key为hashcode+statementId+sql语句。Value为查询出来的结果集映射成的java对象。 SqlSession执行insert、update、delete等操作commit后会清空该SQLSession缓存。

**2、** 二级缓存 二级缓存是mapper级别的，Mybatis默认是没有开启二级缓存的。 第一次调用mapper下的SQL去查询用户的信息，查询到的信息会存放代该mapper对应的二级缓存区域。 第二次调用namespace下的mapper映射文件中，相同的sql去查询用户信息，会去对应的二级缓存内取结果。 如果调用相同namespace下的mapepr映射文件中增删改sql，并执行了commit操作，此时会情况该


### [9、Mybatis 中如何执行批处理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#9mybatis-中如何执行批处理)  


使用 BatchExecutor 完成批处理。


### [10、什么情况下用注解绑定,什么情况下用 xml 绑定？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#10什么情况下用注解绑定,什么情况下用-xml-绑定)  


当 Sql 语句比较简单时候,用注解绑定；当 SQL 语句比较复杂时候,用 xml 绑定,一般用

xml 绑定的比较多


### [11、Mybatis 是如何进行分页的？分页插件的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#11mybatis-是如何进行分页的分页插件的原理是什么)  

### [12、这个Dao接口的工作原理是什么？Dao接口里的方法，参数不同时，方法能重载吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#12这个dao接口的工作原理是什么dao接口里的方法参数不同时方法能重载吗)  

### [13、Mapper编写有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#13mapper编写有哪几种方式)  

### [14、Mybatis优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#14mybatis优缺点)  

### [15、Mapper 编写有哪几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#15mapper-编写有哪几种方式)  

### [16、Mybatis是如何进行分页的？分页插件的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#16mybatis是如何进行分页的分页插件的原理是什么)  

### [17、使用 MyBatis 的 mapper 接口调用时有哪些要求？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#17使用-mybatis-的-mapper-接口调用时有哪些要求)  

### [18、使用MyBatis的mapper接口调用时有哪些要求？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#18使用mybatis的mapper接口调用时有哪些要求)  

### [19、一对一、一对多的关联查询 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#19一对一一对多的关联查询-)  

### [20、Mybatis的一级、二级缓存:](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#20mybatis的一级二级缓存:)  

### [21、MyBatis与Hibernate有哪些不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#21mybatis与hibernate有哪些不同)  

### [22、Mybatis是否可以映射Enum枚举类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#22mybatis是否可以映射enum枚举类)  

### [23、Mybatis 分页查询？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#23mybatis-分页查询)  

### [24、Mybatis 执行批量插入，能返回数据库主键列表吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis高级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#24mybatis-执行批量插入能返回数据库主键列表吗)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
