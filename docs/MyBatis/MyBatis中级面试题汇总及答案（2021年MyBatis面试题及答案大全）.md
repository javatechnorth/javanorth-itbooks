# MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）

MyBatis面试题及答案【最新版】MyBatis高级面试题大全(2021版)，发现网上很多MyBatis面试题及答案整理都没有答案，所以花了很长时间搜集，本套MyBatis面试题大全，MyBatis面试题大汇总，有大量经典的MyBatis面试题以及答案，包含MyBatis语言常见面试题、MyBatis工程师高级面试题及一些大厂MyBatis开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套MyBatis面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个MyBatis面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、#{}和${}的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#1#{}和${}的区别是什么)  


**1、** #{}是预编译处理，${}是字符串替换。

**2、** Mybatis 在处理#{}时，会将 sql 中的#{}替换为?号，调用 PreparedStatement 的 set 方法

来赋值；

**3、** Mybatis 在处理$${}时，就是把$${}替换成变量的值。

**4、** 使用#{}可以有效的防止 SQL 注入，提高系统安全性。


### [2、讲下 MyBatis 的缓存](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#2讲下-mybatis-的缓存)  


MyBatis 的缓存分为一级缓存和二级缓存,一级缓存放在 session 里面,默认就有,二级缓

存放在它的命名空间里,默认是不打开的,使用二级缓存属性类需要实现 Serializable 序列化

接口(可用来保存对象的状态),可在它的映射文件中配置


### [3、Mybatis 是如何将 sql 执行结果封装为目标对象并返回的？都有哪些映射形式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#3mybatis-是如何将-sql-执行结果封装为目标对象并返回的都有哪些映射形式)  


第一种是使用标签，逐一定义列名和对象属性名之间的映射关系。

第二种是使用 sql 列的别名功能，将列别名书写为对象属性名，比如 T_NAME AS NAME，对

象属性名一般是 name，小写，但是列名不区分大小写，Mybatis 会忽略列名大小写，智能

找到与之对应对象属性名，你甚至可以写成 T_NAME AS NaMe，Mybatis 一样可以正常工

作。

有了列名与属性名的映射关系后，Mybatis 通过反射创建对象，同时使用反射给对象的属性

逐一赋值并返回，那些找不到映射关系的属性，是无法完成赋值的。


### [4、为什么说Mybatis是半自动ORM映射工具？它与全自动的区别在哪里？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#4为什么说mybatis是半自动orm映射工具它与全自动的区别在哪里)  


Hibernate属于全自动ORM映射工具，使用Hibernate查询关联对象或者关联集合对象时，可以根据对象关系模型直接获取，所以它是全自动的。而Mybatis在查询关联对象或关联集合对象时，需要手动编写sql来完成，所以，称之为半自动ORM映射工具。


### [5、Mybatis是如何进行分页的？分页插件的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#5mybatis是如何进行分页的分页插件的原理是什么)  


Mybatis使用RowBounds对象进行分页，它是针对ResultSet结果集执行的内存分页，而非物理分页。可以在sql内直接书写带有物理分页的参数来完成物理分页功能，也可以使用分页插件来完成物理分页。

分页插件的基本原理是使用Mybatis提供的插件接口，实现自定义插件，在插件的拦截方法内拦截待执行的sql，然后重写sql，根据dialect方言，添加对应的物理分页语句和物理分页参数。


### [6、#{}和${}的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#6#{}和${}的区别是什么)  


Mybatis在处理#{}时，会将sql中的#{}替换为?号，调用Prepared Statement的set方法来赋值；Mybatis在处理$${}时，就是把$${}替换成变量的值；使用#{}可以有效的防止SQL注入，提高系统安全性。


### [7、Mybatis是如何将sql执行结果封装为目标对象并返回的？都有哪些映射形式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#7mybatis是如何将sql执行结果封装为目标对象并返回的都有哪些映射形式)  


第一种是使用`<resultMap>`标签，逐一定义数据库列名和对象属性名之间的映射关系。

第二种是使用sql列的别名功能，将列的别名书写为对象属性名。

有了列名与属性名的映射关系后，Mybatis通过反射创建对象，同时使用反射给对象的属性逐一赋值并返回，那些找不到映射关系的属性，是无法完成赋值的。


### [8、Mybatis如何执行批量操作](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#8mybatis如何执行批量操作)  


**使用foreach标签**

foreach的主要用在构建in条件中，它可以在SQL语句中进行迭代一个集合。foreach标签的属性主要有item，index，collection，open，separator，close。

**1、** item   表示集合中每一个元素进行迭代时的别名，随便起的变量名；

**2、** index   指定一个名字，用于表示在迭代过程中，每次迭代到的位置，不常用；

**3、** open   表示该语句以什么开始，常用“(”；

**4、** separator 表示在每次进行迭代之间以什么符号作为分隔符，常用“,”；

**5、** close   表示以什么结束，常用“)”。

在使用foreach的时候最关键的也是最容易出错的就是collection属性，该属性是必须指定的，但是在不同情况下，该属性的值是不一样的，主要有一下3种情况：

**1、** 如果传入的是单参数且参数类型是一个List的时候，collection属性值为list

**2、** 如果传入的是单参数且参数类型是一个array数组的时候，collection的属性值为array

**3、** 如果传入的参数是多个的时候，我们就需要把它们封装成一个Map了，当然单参数也可以封装成map，实际上如果你在传入参数的时候，在MyBatis里面也是会把它封装成一个Map的，

map的key就是参数名，所以这个时候collection属性值就是传入的List或array对象在自己封装的map里面的key

**具体用法如下：**

```
<!-- 批量保存(foreach插入多条数据两种方法)
   int addEmpsBatch(@Param("emps") List<Employee> emps); -->
<!-- MySQL下批量保存，可以foreach遍历 MySQL支持values(),(),()语法 --> //推荐使用

<insert id="addEmpsBatch">
INSERT INTO emp(ename,gender,email,did)
VALUES
<foreach collection="emps" item="emp" separator=",">
    (#{emp.eName},#{emp.gender},#{emp.email},#{emp.dept.id})
</foreach>
</insert>
```

```
<!-- 这种方式需要数据库连接属性allowMutiQueries=true的支持
如jdbc.url=jdbc:MySQL://localhost:3306/mybatis?allowMultiQueries=true -->  

<insert id="addEmpsBatch">
<foreach collection="emps" item="emp" separator=";">                                 
    INSERT INTO emp(ename,gender,email,did)
    VALUES(#{emp.eName},#{emp.gender},#{emp.email},#{emp.dept.id})
</foreach>
</insert>
```

**使用ExecutorType.BATCH**

Mybatis内置的ExecutorType有3种，默认为simple,该模式下它为每个语句的执行创建一个新的预处理语句，单条提交sql；而batch模式重复使用已经预处理的语句，并且批量执行所有更新语句，显然batch性能将更优； 但batch模式也有自己的问题，比如在Insert操作时，在事务没有提交之前，是没有办法获取到自增的id，这在某型情形下是不符合业务要求的

**具体用法如下：**

```
//批量保存方法测试
@Test  
public void testBatch() throws IOException{
    SqlSessionFactory sqlSessionFactory = getSqlSessionFactory();
    //可以执行批量操作的sqlSession
    SqlSession openSession = sqlSessionFactory.openSession(ExecutorType.BATCH);

    //批量保存执行前时间
    long start = System.currentTimeMillis();
    try {
        EmployeeMapper mapper = openSession.getMapper(EmployeeMapper.class);
        for (int i = 0; i < 1000; i++) {
            mapper.addEmp(new Employee(UUID.randomUUID().toString().substring(0, 5), "b", "1"));
        }

        openSession.commit();
        long end = System.currentTimeMillis();
        //批量保存执行后的时间
        System.out.println("执行时长" + (end - start));
        //批量 预编译sql一次==》设置参数==》10000次==》执行1次   677
        //非批量  （预编译=设置参数=执行 ）==》10000次   1121

    } finally {
        openSession.close();
    }
}
```

**mapper和mapper.xml如下**

```
    public interface EmployeeMapper {   
        //批量保存员工
        Long addEmp(Employee employee);
    }
```

```
    <mapper namespace="com.jourwon.mapper.EmployeeMapper"
         <!--批量保存员工 -->
        <insert id="addEmp">
            insert into employee(lastName,email,gender)
            values(#{lastName},#{email},#{gender})
        </insert>
    </mapper>
```


### [9、如何获取自动生成的(主)键值?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#9如何获取自动生成的主键值)  


insert 方法总是返回一个int值 ，这个值代表的是插入的行数。

如果采用自增长策略，自动生成的键值在 insert 方法执行完后可以被设置到传入的参数对象中。

**示例：**

```xml
<insert id=”insertname” usegeneratedkeys=”true” keyproperty=”id”>
        insert into names (name) values (#{name})
        </insert>
        name name = new name();
        name.setname(“fred”);

        int rows = mapper.insertname(name);
        // 完成后,id已经被设置到对象中
        system.out.println(“rows inserted = ” + rows);
        system.out.println(“generated key value = ” + name.getid());
```


### [10、使用Mybatis的mapper接口调用时候有哪些要求？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#10使用mybatis的mapper接口调用时候有哪些要求)  


**1、** Mapper接口方法名和Mapper.xml中定义的每个SQL的id相同；

**2、** Mapper接口方法的输入参数类型和mapper.xml中定义的每个sqlparameterType类型相同

**3、** Mapper接口方法的输入输出参数类型和mapper.xml中定义的每个sql的resultType的类型相同

**4、** Mapper.xml文件中的namespace，就是接口的类路径。


### [11、Mybatis是如何进行分页的？分页插件的原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#11mybatis是如何进行分页的分页插件的原理是什么)  

### [12、简述 Mybatis 的插件运行原理，以及如何编写一个插件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#12简述-mybatis-的插件运行原理以及如何编写一个插件)  

### [13、MyBatis的功能架构是怎样的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#13mybatis的功能架构是怎样的)  

### [14、Mybatis映射文件中，如果A标签通过include引用了B标签的内容](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#14mybatis映射文件中如果a标签通过include引用了b标签的内容)  

### [15、什么是 MyBatis 的接口绑定,有什么好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#15什么是-mybatis-的接口绑定,有什么好处)  

### [16、简述 Mybatis 的 Xml 映射文件和 Mybatis 内部数据结构之间的映射关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#16简述-mybatis-的-xml-映射文件和-mybatis-内部数据结构之间的映射关系)  

### [17、什么是DBMS](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#17什么是dbms)  

### [18、模糊查询like语句该怎么写](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#18模糊查询like语句该怎么写)  

### [19、简述Mybatis的插件运行原理，以及如何编写一个插件。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#19简述mybatis的插件运行原理以及如何编写一个插件。)  

### [20、简述Mybatis的Xml映射文件和Mybatis内部数据结构之间的映射关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#20简述mybatis的xml映射文件和mybatis内部数据结构之间的映射关系)  

### [21、MyBatis 与 Hibernate 有哪些不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#21mybatis-与-hibernate-有哪些不同)  

### [22、MyBatis框架适用场合：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#22mybatis框架适用场合：)  

### [23、MyBatis与hibernate有哪些不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#23mybatis与hibernate有哪些不同)  

### [24、Mybatis是如何将sql执行结果封装为目标对象并返回的？都有哪些映射形式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/MyBatis/MyBatis中级面试题汇总及答案（2021年MyBatis面试题及答案大全）.md#24mybatis是如何将sql执行结果封装为目标对象并返回的都有哪些映射形式)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
