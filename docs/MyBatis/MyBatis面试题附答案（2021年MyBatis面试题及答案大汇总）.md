# MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）

MyBatis面试题及答案【最新版】MyBatis高级面试题大全(2021版)，发现网上很多MyBatis面试题及答案整理都没有答案，所以花了很长时间搜集，本套MyBatis面试题大全，MyBatis面试题大汇总，有大量经典的MyBatis面试题以及答案，包含MyBatis语言常见面试题、MyBatis工程师高级面试题及一些大厂MyBatis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MyBatis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MyBatis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、#{}和${}的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#1#{}和${}的区别)  


**1、** #{}是占位符，预编译处理；${}是拼接符，字符串替换，没有预编译处理。

**2、** Mybatis在处理#{}时，#{}传入参数是以字符串传入，会将SQL中的#{}替换为?号，调用PreparedStatement的set方法来赋值。

**3、** #{} 可以有效的防止SQL注入，提高系统安全性；${} 不能防止SQL 注入

**4、** #{} 的变量替换是在DBMS 中；${} 的变量替换是在 DBMS 外


### [2、IBatis 和 MyBatis 在核心处理类分别叫什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#2ibatis-和-mybatis-在核心处理类分别叫什么)  


IBatis 里面的核心处理类交 SqlMapClient,MyBatis 里面的核心处理类叫做 SqlSession。


### [3、Mybatis动态sql是做什么的？都有哪些动态sql？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#3mybatis动态sql是做什么的都有哪些动态sql)  


**能简述一下动态sql的执行原理吗？**

Mybatis动态sql可以让我们在Xml映射文件内，以标签的形式编写动态sql，完成逻辑判断和动态拼接sql的功能，Mybatis提供了9种动态sql标签trim|where|set|foreach|if|choose|when|otherwise|bind。

其执行原理为，使用OGNL从sql参数对象中计算表达式的值，根据表达式的值动态拼接sql，以此来完成动态sql的功能。


### [4、Mybatis 中如何指定使用哪一种 Executor 执行器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#4mybatis-中如何指定使用哪一种-executor-执行器)  


在 Mybatis 配置文件中，可以指定默认的 ExecutorType 执行器类型，也可以手动给

DefaultSqlSessionFactory 的创建 SqlSession 的方法传递 ExecutorType 类型参数。


### [5、当实体类中的属性名和表中的字段名不一样 ，怎么办 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#5当实体类中的属性名和表中的字段名不一样-怎么办-)  


第1种： 通过在查询的sql语句中定义字段名的别名，让字段名的别名和实体类的属性名一致。

```
<select id=”selectorder” parametertype=”int” resultetype=”me.gacl.domain.order”>
       select order_id id, order_no orderno ,order_price price form orders where order_id=#{id};
</select>
```

第2种： 通过`<resultMap>`来映射字段名和实体类属性名的一一对应的关系。

```
<select id="getOrder" parameterType="int" resultMap="orderresultmap">
select * from orders where order_id=#{id}
</select>

<resultMap type=”me.gacl.domain.order” id=”orderresultmap”>
    <!–用id属性来映射主键字段–>
    <id property=”id” column=”order_id”>

    <!–用result属性来映射非主键字段，property为实体类属性名，column为数据表中的属性–>
    <result property = “orderno” column =”order_no”/>
    <result property=”price” column=”order_price” />
</reslutMap>
```


### [6、Mybatis与Spring 的整合？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#6mybatis与spring-的整合)  


**1、** Spring Spring是一个轻量级控制反转(IOC)和面向切面(AOP)的容器框架；AOP和IOC是Spring框架重要的两个模块；控制反转就是改变对象的创建方式，将对象的创建和维护有开发人员创建改为由容器帮我们完成创建和维护。

**2、** Mybatis是支持SQL查询，存储过程和高级映射的优秀持久成框架。Mybatis几乎是消除了使用JDBC存在的重复创建和关闭连接，以及结果集查询的问题。它使用简单的xml或者注解用于配置和映射，将java的POjOs映射成数据库中的记录。

**3、** 整合，涉及的常用包： ![](https://atts.w3cschool.cn/attachments/image/20171124/1511515685952292.png#alt=)


### [7、什么是MyBatis的接口绑定？有哪些实现方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#7什么是mybatis的接口绑定有哪些实现方式)  


接口绑定，就是在MyBatis中任意定义接口，然后把接口里面的方法和SQL语句绑定，我们直接调用接口方法就可以，这样比起原来了SqlSession提供的方法我们可以有更加灵活的选择和设置。

**接口绑定有两种实现方式**

**1、** 通过注解绑定，就是在接口的方法上面加上 @Select、@Update等注解，里面包含Sql语句来绑定；

**2、** 通过xml里面写SQL来绑定， 在这种情况下，要指定xml映射文件里面的namespace必须为接口的全路径名。当Sql语句比较简单时候，用注解绑定， 当SQL语句比较复杂时候，用xml绑定，一般用xml绑定的比较多。


### [8、为什么说Mybatis是半自动ORM映射工具？它与全自动的区别在哪里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#8为什么说mybatis是半自动orm映射工具它与全自动的区别在哪里)  


Hibernate属于全自动ORM映射工具，使用Hibernate查询关联对象或者关联集合对象时，可以根据对象关系模型直接获取，所以它是全自动的。

而Mybatis在查询关联对象或关联集合对象时，需要手动编写sql来完成，所以，称之为半自动ORM映射工具。


### [9、简述Mybatis的插件运行原理，以及如何编写一个插件。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#9简述mybatis的插件运行原理以及如何编写一个插件。)  


Mybatis仅可以编写针对ParameterHandler、ResultSetHandler、StatementHandler、Executor这4种接口的插件，Mybatis使用JDK的动态代理，为需要拦截的接口生成代理对象以实现接口方法拦截功能，每当执行这4种接口对象的方法时，就会进入拦截方法，具体就是InvocationHandler的invoke()方法，当然，只会拦截那些你指定需要拦截的方法。

实现Mybatis的Interceptor接口并复写intercept()方法，然后在给插件编写注解，指定要拦截哪一个接口的哪些方法即可，记住，别忘了在配置文件中配置你编写的插件。


### [10、Mybatis动态sql有什么用？执行原理？有哪些动态sql？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#10mybatis动态sql有什么用执行原理有哪些动态sql)  


Mybatis动态sql可以在Xml映射文件内，以标签的形式编写动态sql，执行原理是根据表达式的值 完成逻辑判断并动态拼接sql的功能。

Mybatis提供了9种动态sql标签：`trim | where | set | foreach | if | choose | when | otherwise | bind`。


### [11、Mybatis 映射文件中，如果 A 标签通过 include 引用了 B 标签的内容，请问，B 标签能](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#11mybatis-映射文件中如果-a-标签通过-include-引用了-b-标签的内容请问b-标签能)  

### [12、什么是Mybatis？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#12什么是mybatis)  

### [13、Mybais 常用注解 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#13mybais-常用注解-)  

### [14、Xml映射文件中，除了常见的select|insert|updae|delete标签之外，还有哪些标签？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#14xml映射文件中除了常见的select|insert|updae|delete标签之外还有哪些标签)  

### [15、Mybatis的编程步骤是什么样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#15mybatis的编程步骤是什么样的)  

### [16、ORM是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#16orm是什么)  

### [17、Mybatis的Xml映射文件中，不同的Xml映射文件，id是否可以重复？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#17mybatis的xml映射文件中不同的xml映射文件id是否可以重复)  

### [18、MyBatis 里面的动态 Sql 是怎么设定的?用什么语法?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#18mybatis-里面的动态-sql-是怎么设定的用什么语法)  

### [19、MyBatis框架的缺点：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#19mybatis框架的缺点：)  

### [20、Mybatis是如何将sql执行结果封装为目标对象并返回的？都有哪些映射形式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#20mybatis是如何将sql执行结果封装为目标对象并返回的都有哪些映射形式)  

### [21、MyBatis实现一对多有几种方式,怎么操作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#21mybatis实现一对多有几种方式,怎么操作的)  

### [22、Mybatis的Xml映射文件中，不同的Xml映射文件，id是否可以重复？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#22mybatis的xml映射文件中不同的xml映射文件id是否可以重复)  

### [23、为什么需要预编译](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#23为什么需要预编译)  

### [24、Mybatis的映射文件 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#24mybatis的映射文件-)  

### [25、Xml 映射文件中，除了常见的 select|insert|updae|delete 标签之外，还有哪些标签？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题附答案（2021年MyBatis面试题及答案大汇总）.md#25xml-映射文件中除了常见的-select|insert|updae|delete-标签之外还有哪些标签)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
