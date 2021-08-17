# MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）

MyBatis面试题及答案【最新版】MyBatis高级面试题大全(2021版)，发现网上很多MyBatis面试题及答案整理都没有答案，所以花了很长时间搜集，本套MyBatis面试题大全，MyBatis面试题大汇总，有大量经典的MyBatis面试题以及答案，包含MyBatis语言常见面试题、MyBatis工程师高级面试题及一些大厂MyBatis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MyBatis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MyBatis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、Mybatis 比 IBatis 比较大的几个改进是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#1mybatis-比-ibatis-比较大的几个改进是什么)  


**1、** 有接口绑定,包括注解绑定 sql 和 xml 绑定 Sql

**2、** 动态 sql 由原来的节点配置变成 OGNL 表达式 3、 在一对一,一对多的时候引进了

association,在一对多的时候引入了 collection 节点,不过都是在 resultMap 里面配置


### [2、MyBatis 的好处是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#2mybatis-的好处是什么)  


**1、** MyBatis 把 sql 语句从 Java 源程序中独立出来，放在单独的 XML 文件中编写，给程序的

维护带来了很大便利。

**2、** MyBatis 封装了底层 JDBC API 的调用细节，并能自动将结果集转换成 Java Bean 对象，

大大简化了 Java 数据库编程的重复工作。

**3、** 因为 MyBatis 需要程序员自己去编写 sql 语句，程序员可以结合数据库自身的特点灵活

控制 sql 语句，因此能够实现比 Hibernate 等全自动 orm 框架更高的查询效率，能够完成复

杂查询。


### [3、resultType resultMap 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#3resulttype-resultmap-的区别)  


**1、** 类的名字和数据库相同时，可以直接设置 resultType 参数为 Pojo 类

**2、** 若不同，需要设置 resultMap 将结果名字和 Pojo 名字进行转换


### [4、Xml映射文件中，除了常见的select|insert|updae|delete标签之外，还有哪些标签？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#4xml映射文件中除了常见的select|insert|updae|delete标签之外还有哪些标签)  


还有很多其他的标签，`<resultMap>`、`<parameterMap>`、`<sql>`、`<include>`、`<selectKey>`，加上动态sql的9个标签，trim|where|set|foreach|if|choose|when|otherwise|bind等，其中`<sql>`为sql片段标签，通过`<include>`标签引入sql片段，`<selectKey>`为不支持自增的主键生成策略标签。


### [5、使用MyBatis的mapper接口调用时有哪些要求？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#5使用mybatis的mapper接口调用时有哪些要求)  


**1、** Mapper接口方法名和mapper.xml中定义的每个sql的id相同。

**2、** Mapper接口方法的输入参数类型和mapper.xml中定义的每个sql 的parameterType的类型相同。

**3、** Mapper接口方法的输出参数类型和mapper.xml中定义的每个sql的resultType的类型相同。

**4、** Mapper.xml文件中的namespace即是mapper接口的类路径。


### [6、在 mapper 中如何传递多个参数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#6在-mapper-中如何传递多个参数)  


**1、** 直接在方法中传递参数，xml 文件用#{0} #{1}来获取

**2、** 使用 [@param ](/param ) 注解:这样可以直接在 xml 文件中通过#{name}来获取


### [7、Mybatis 动态 sql 是做什么的？都有哪些动态 sql？能简述一下动态 sql 的执行原理不？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#7mybatis-动态-sql-是做什么的都有哪些动态-sql能简述一下动态-sql-的执行原理不)  


**1、** Mybatis 动态 sql 可以让我们在 Xml 映射文件内，以标签的形式编写动态 sql，完成逻辑

判断和动态拼接 sql 的功能。

**2、** Mybatis 提供了 9 种动态 sql 标签：

trim|where|set|foreach|if|choose|when|otherwise|bind。

**3、** 其执行原理为，使用 OGNL 从 sql 参数对象中计算表达式的值，根据表达式的值动态拼

接 sql，以此来完成动态 sql 的功能。


### [8、为什么说 Mybatis 是半自动 ORM 映射工具？它与全自动的区别在哪里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#8为什么说-mybatis-是半自动-orm-映射工具它与全自动的区别在哪里)  


Hibernate 属于全自动 ORM 映射工具，使用 Hibernate 查询关联对象或者关联集合对象

时，可以根据对象关系模型直接获取，所以它是全自动的。而 Mybatis 在查询关联对象或

关联集合对象时，需要手动编写 sql 来完成，所以，称之为半自动 ORM 映射工具。


### [9、Mybatis是否支持延迟加载？如果支持，它的实现原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#9mybatis是否支持延迟加载如果支持它的实现原理是什么)  


Mybatis仅支持association关联对象和collection关联集合对象的延迟加载，association指的就是一对一，collection指的就是一对多查询。在Mybatis配置文件中，可以配置是否启用延迟加载lazyLoadingEnabled=true|false。

它的原理是，使用CGLIB创建目标对象的代理对象，当调用目标方法时，进入拦截器方法，比如调用a.getB().getName()，拦截器invoke()方法发现a.getB()是null值，那么就会单独发送事先保存好的查询关联B对象的sql，把B查询上来，然后调用a.setB(b)，于是a的对象b属性就有值了，接着完成a.getB().getName()方法的调用。这就是延迟加载的基本原理。

当然了，不光是Mybatis，几乎所有的包括Hibernate，支持延迟加载的原理都是一样的。


### [10、模糊查询like语句该怎么写?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#10模糊查询like语句该怎么写)  


第1种：在Java代码中添加sql通配符。

```xml
string wildcardname = “%smi%”;
        list<name> names = mapper.selectlike(wildcardname);

    <select id=”selectlike”>
    select * from foo where bar like #{value}
</select>
```

第2种：在sql语句中拼接通配符，会引起sql注入

```xml
string wildcardname = “smi”;
        list<name> names = mapper.selectlike(wildcardname);


    <select id=”selectlike”>
    select * from foo where bar like "%"#{value}"%"
</select>
```


### [11、Mybatis中如何指定使用哪一种Executor执行器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#11mybatis中如何指定使用哪一种executor执行器)  

### [12、Mybatis的表关联的映射？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#12mybatis的表关联的映射)  

### [13、通常一个 Xml 映射文件，都会写一个 Dao 接口与之对应, Dao 的工作原理，是否可以重](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#13通常一个-xml-映射文件都会写一个-dao-接口与之对应,-dao-的工作原理是否可以重)  

### [14、Mybaits的优点有什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#14mybaits的优点有什么)  

### [15、MyBatis实现一对一有几种方式?具体怎么操作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#15mybatis实现一对一有几种方式具体怎么操作的)  

### [16、JDBC编程有哪些不足之处，MyBatis是如何解决的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#16jdbc编程有哪些不足之处mybatis是如何解决的)  

### [17、Mybaits的优点：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#17mybaits的优点：)  

### [18、Mybatis 的 Xml 映射文件中，不同的 Xml 映射文件，id 是否可以重复？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#18mybatis-的-xml-映射文件中不同的-xml-映射文件id-是否可以重复)  

### [19、通常一个Xml映射文件，都会写一个Dao接口与之对应](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#19通常一个xml映射文件都会写一个dao接口与之对应)  

### [20、MyBatis的框架架构设计是怎么样的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#20mybatis的框架架构设计是怎么样的)  

### [21、Mybatis 能执行一对一、一对多的关联查询吗？都有哪些实现方式，以及它们之间的区](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#21mybatis-能执行一对一一对多的关联查询吗都有哪些实现方式以及它们之间的区)  

### [22、Mybatis 是否可以映射 Enum 枚举类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#22mybatis-是否可以映射-enum-枚举类)  

### [23、Hibernate 和 MyBatis 的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#23hibernate-和-mybatis-的区别)  

### [24、Mybatis能执行一对多，一对一的联系查询吗，有哪些实现方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#24mybatis能执行一对多一对一的联系查询吗有哪些实现方法)  

### [25、MyBatis编程步骤是什么样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#25mybatis编程步骤是什么样的)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
