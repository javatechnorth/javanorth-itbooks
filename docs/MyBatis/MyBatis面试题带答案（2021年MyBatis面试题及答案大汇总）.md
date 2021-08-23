# MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）

MyBatis面试题及答案【最新版】MyBatis高级面试题大全(2021版)，发现网上很多MyBatis面试题及答案整理都没有答案，所以花了很长时间搜集，本套MyBatis面试题大全，MyBatis面试题大汇总，有大量经典的MyBatis面试题以及答案，包含MyBatis语言常见面试题、MyBatis工程师高级面试题及一些大厂MyBatis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MyBatis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MyBatis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、#{}和${}的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#1#{}和${}的区别是什么)  


`#{}`是预编译处理，${}是字符串替换。

Mybatis在处理#{}时，会将sql中的#{}替换为?号，调用PreparedStatement的set方法来赋值；

Mybatis在处理$${}时，就是把$${}替换成变量的值。

使用#{}可以有效的防止SQL注入，提高系统安全性。


### [2、Mybatis动态SQL？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#2mybatis动态sql)  


**1、** 传统的JDBC的方法，在组合SQL语句的时候需要去拼接，稍微不注意就会少少了一个空格，标点符号，都会导致系统错误。Mybatis的动态SQL就是为了解决这种问题而产生的；Mybatis的动态SQL语句值基于OGNL表达式的，方便在SQL语句中实现某些逻辑；可以使用标签组合成灵活的sql语句，提供开发的效率。

**2、** Mybatis的动态SQL标签主要由以下几类： If语句（简单的条件判断） Choose(when/otherwise),相当于java语言中的switch，与jstl中choose类似 Trim(对包含的内容加上prefix，或者suffix) Where(主要是用来简化SQL语句中where条件判断，能智能的处理and/or 不用担心多余的语法导致的错误) Set(主要用于更新时候) Foreach(一般使用在mybatis in语句查询时特别有用)


### [3、模糊查询 like 语句该怎么写](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#3模糊查询-like-语句该怎么写)  


**1、** 在 java 中拼接通配符，通过#{}赋值

**2、** 在 Sql 语句中拼接通配符 （不安全 会引起 Sql 注入、


### [4、MyBatis和Hibernate的适用场景?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#4mybatis和hibernate的适用场景)  


**1、** MyBatis专注于SQL本身，是一个足够灵活的DAO层解决方案。

**2、** 对性能的要求很高，或者需求变化较多的项目，如互联网项目，MyBatis将是不错的选择。

**开发难易程度和学习成本**

Hibernate 是重量级框架，学习使用门槛高，适合于需求相对稳定，中小型的项目，比如：办公自动化系统

MyBatis 是轻量级框架，学习使用门槛低，适合于需求变化频繁，大型的项目，比如：互联网电子商务系统

**总结**

**1、** MyBatis 是一个小巧、方便、高效、简单、直接、半自动化的持久层框架，

**2、** Hibernate 是一个强大、方便、高效、复杂、间接、全自动化的持久层框架。


### [5、MyBatis框架适用场合：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#5mybatis框架适用场合：)  


**1、** MyBatis专注于SQL本身，是一个足够灵活的DAO层解决方案。

**2、** 对性能的要求很高，或者需求变化较多的项目，如互联网项目，MyBatis将是不错的选择。


### [6、在mapper中如何传递多个参数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#6在mapper中如何传递多个参数)  


**方法1：顺序传参法**

```
public User selectUser(String name, int deptId);

<select id="selectUser" resultMap="UserResultMap">
select * from user
where user_name ={0} and dept_id ={1}
</select>
```

**1、** #{}里面的数字代表传入参数的顺序。

**2、** 这种方法不建议使用，sql层表达不直观，且一旦顺序调整容易出错。

**方法2：@Param注解传参法**

```
public User selectUser(@Param("userName") String name, int @Param("deptId") deptId);

<select id="selectUser" resultMap="UserResultMap">
select * from user
where user_name ={userName} and dept_id ={deptId}
</select>
```

**1、** #{}里面的名称对应的是注解@Param括号里面修饰的名称。

**2、** 这种方法在参数不多的情况还是比较直观的，（推荐使用）

**方法3：Map传参法**

```
public User selectUser(Map<String, Object> params);

<select id="selectUser" parameterType="java.util.Map" resultMap="UserResultMap">
select * from user
where user_name ={userName} and dept_id ={deptId}
</select>
```


### [7、如何获取生成的主键](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#7如何获取生成的主键)  


**新增标签中添加：keyProperty=" ID " 即可**

```
<insert id="insert" useGeneratedKeys="true" keyProperty="userId" >
    insert into user( 
    user_name, user_password, create_time) 
    values(#{userName},{userPassword} ,{createTime, jdbcType= TIMESTAMP})
</insert>
```

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/5/2/041/14/55_4.png#alt=55%5C_4.png)


### [8、Mapper 编写有几种方式 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#8mapper-编写有几种方式-)  


**1、** 接口实现类集成`SQLSessionDaoSupport`** 此方法需要编写`mapper`接口，`mapper`接口的实现类,`mapper.xml`文件。

**2、** 使用`org.mybatis.spring.mapper.MapperFactoryBean`** 此方法需要在`SqlMapConfig.xml`中配置`mapper.xml`的位置，还需定义`mapper`接口。

**3、** 使用`mapper`扫描器** 需要编写`mapper.xml`文件，需要`mapper`接口，配置`mapper`扫描器，使用扫描器从`spring`容器中获取`mapper`的实现对象。


### [9、接口绑定有几种实现方式,分别是怎么实现的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#9接口绑定有几种实现方式,分别是怎么实现的)  


接口绑定有两种实现方式,一种是通过注解绑定,就是在接口的方法上面加上

@Select[@Update ](/Update ) 等注解里面包含 Sql 语句来绑定,另外一种就是通过 xml 里面写 SQL 来绑

定,在这种情况下,要指定 xml 映射文件里面的 namespace 必须为接口的全路径名.


### [10、Mybatis 是否支持延迟加载？如果支持，它的实现原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#10mybatis-是否支持延迟加载如果支持它的实现原理是什么)  


**1、** Mybatis 仅支持 association 关联对象和 collection 关联集合对象的延迟加载，association

指的就是一对一，collection 指的就是一对多查询。在 Mybatis 配置文件中，可以配置是否

启用延迟加载 lazyLoadingEnabled=true|false。

**2、** 它的原理是，使用 CGLIB 创建目标对象的代理对象，当调用目标方法时，进入拦截器方

法，比如调用 a.getB().getName()，拦截器 invoke()方法发现 a.getB()是 null 值，那么就会单

独发送事先保存好的查询关联 B 对象的 sql，把 B 查询上来，然后调用 a.setB(b)，于是 a 的

对象 b 属性就有值了，接着完成 a.getB().getName()方法的调用。这就是延迟加载的基本原

理。


### [11、传统JDBC开发存在什么问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#11传统jdbc开发存在什么问题)  

### [12、在mapper中如何传递多个参数?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#12在mapper中如何传递多个参数)  

### [13、SQLMapConfig.xml中配置有哪些内容？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#13sqlmapconfigxml中配置有哪些内容)  

### [14、MyBatis 实现一对一有几种方式?具体怎么操作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#14mybatis-实现一对一有几种方式具体怎么操作的)  

### [15、如何获取自动生成的(主)键值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#15如何获取自动生成的主键值)  

### [16、MyBatis与Hibernate有哪些不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#16mybatis与hibernate有哪些不同)  

### [17、MyBatis是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#17mybatis是什么)  

### [18、什么是MyBatis的接口绑定？有哪些实现方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#18什么是mybatis的接口绑定有哪些实现方式)  

### [19、Mybatis都有哪些Executor执行器？它们之间的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#19mybatis都有哪些executor执行器它们之间的区别是什么)  

### [20、当实体类中的属性名和表中的字段名不一样 ，怎么办](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#20当实体类中的属性名和表中的字段名不一样-怎么办)  

### [21、如何执行批量插入?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#21如何执行批量插入)  

### [22、Mybatis的一级、二级缓存](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#22mybatis的一级二级缓存)  

### [23、什么是 MyBatis？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#23什么是-mybatis)  

### [24、JDBC编程有哪些不足之处，MyBatis是如何解决这些问题的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#24jdbc编程有哪些不足之处mybatis是如何解决这些问题的)  

### [25、JDBC编程有哪些不足之处，Mybatis是如何解决这些问题的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis面试题带答案（2021年MyBatis面试题及答案大汇总）.md#25jdbc编程有哪些不足之处mybatis是如何解决这些问题的)  





