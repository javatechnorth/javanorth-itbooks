# Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）

Vue面试题及答案【最新版】Vue高级面试题大全(2021版)，发现网上很多Vue面试题及答案整理都没有答案，所以花了很长时间搜集，本套Vue面试题大全，Vue面试题大汇总，有大量经典的Vue面试题以及答案，包含Vue语言常见面试题、Vue工程师高级面试题及一些大厂Vue开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Vue面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Vue面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、列出JS基本和非基本数据类型之间的一些区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#1列出js基本和非基本数据类型之间的一些区别)  


**1、** 目前JS中有6种基本数据类型: Undefined、Null、Boolean、Number、Symbol 和 String。还有1种复杂的数据类型Object，Object本质上是由一组无序的名值对组成的。Object、Array和Function则属于引用类型。

**2、** 基本数据类型是不可变的，而非基本数据类型是可变的。

**3、** 基本数据类型是不可变的，因为它们一旦创建就无法更改，但非基本数据类型刚可更改，意味着一旦创建了对象，就可以更改它。

**4、** 将基本数据类型与其值进行比较，这意味着如果两个值具有相同的数据类型并具有相同的值，那么它们是严格相等的。

**5、** 非基本数据类型不与值进行比较。例如，如果两个对象具有相同的属性和值，则它们严格不相等。


### [2、vue-router实现路由懒加载（ 动态加载路由 ）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#2vue-router实现路由懒加载-动态加载路由-)  


**三种方式**

**1、** vue异步组件技术 ==== 异步加载，vue-router配置路由 , 使用vue的异步组件技术 , 可以实现按需加载 .但是,这种情况下一个组件生成一个js文件。

**2、** 路由懒加载(使用import)。

**3、** webpack提供的require.ensure()，vue-router配置路由，使用webpack的require.ensure技术，也可以实现按需加载。这种情况下，多个路由指定相同的chunkName，会合并打包成一个js文件。


### [3、route和router的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#3route和router的区别)  


**$router**

router是VueRouter的一个对象，通过Vue.use(VueRouter)和VueRouter构造函数得到一个router的实例对象，这个对象中是一个全局的对象，他包含了所有的路由包含了许多关键的对象和属性,常见的有：

1）push：向 history 栈添加一个新的记录，当我们点击浏览器的返回按钮时可以看到之前的页面

```
// 字符串
   this.$router.push('home')
// 对象
   this.$router.push({ path: 'home' })
// 命名的路由
   this.$router.push({ name: 'user', params: { userId: 123 }})
// 带查询参数，变成 /register?plan=123
   this.$router.push({ path: 'register', query: { plan: '123' }})
2）go：页面路由跳转 前进或者后退

// 页面路由跳转 前进或者后退
this.$router.go(-1) // 后退
```

3）replace：push方法会向 history 栈添加一个新的记录，而replace方法是替换当前的页面，不会向 history 栈添加一个新的记录

**$route**

**1、** $route对象表示当前的路由信息，包含了当前URL解析得到的信息。包含当前的路径、参数、query对象等。

**2、** $route.path：字符串，对应当前路由的路径，总是解析为绝对路径，如 "/foo/bar"。

**3、** $route.params：一个 key/value 对象，包含了 动态片段 和 全匹配片段，如果没有路由参数，就是一个空对象。

**4、** $route.query：一个 key/value 对象，表示 URL 查询参数。例如，对于路径 /foo?user=1，则有 $route.query.user == 1，如果没有查询参数，则是个空对象。

**5、** $route.hash：当前路由的 hash 值 (不带#) ，如果没有 hash 值，则为空字符串。

**6、** $route.fullPath：完成解析后的 URL，包含查询参数和 hash 的完整路径。

**7、** dollar;route.matched：数组，包含当前匹配的路径中所包含的所有片段所对应的配置参数对象。

**8、** $route.name：当前路径名字

**9、** $route.meta：路由元信息


### [4、说一下Vue的生命周期](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#4说一下vue的生命周期)  


`beforeCreate`是new Vue()之后触发的第一个钩子，在当前阶段data、methods、computed以及watch上的数据和方法都不能被访问。

`created`在实例创建完成后发生，当前阶段已经完成了数据观测，也就是可以使用数据，更改数据，在这里更改数据不会触发updated函数。可以做一些初始数据的获取，在当前阶段无法与Dom进行交互，如果非要想，可以通过vm.$nextTick来访问Dom。

`beforeMount`发生在挂载之前，在这之前template模板已导入渲染函数编译。而当前阶段虚拟Dom已经创建完成，即将开始渲染。在此时也可以对数据进行更改，不会触发updated。

`mounted`在挂载完成后发生，在当前阶段，真实的Dom挂载完毕，数据完成双向绑定，可以访问到Dom节点，使用$refs属性对Dom进行操作。

`beforeUpdate`发生在更新之前，也就是响应式数据发生更新，虚拟dom重新渲染之前被触发，你可以在当前阶段进行更改数据，不会造成重渲染。

`updated`发生在更新完成之后，当前阶段组件Dom已完成更新。要注意的是避免在此期间更改数据，因为这可能会导致无限循环的更新。

`beforeDestroy`发生在实例销毁之前，在当前阶段实例完全可以被使用，我们可以在这时进行善后收尾工作，比如清除计时器。

`destroyed`发生在实例销毁之后，这个时候只剩下了dom空壳。组件已被拆解，数据绑定被卸除，监听被移出，子实例也统统被销毁。

(关于Vue的生命周期详解感兴趣的也请移步我的另一篇专栏)


### [5、你如何捕获元素上的点击事件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#5你如何捕获元素上的点击事件)  


可以使用 `v-on:click` 指令捕获 Click 事件。该指令也可以用缩写符号 `@click` 表示。这是一个例子：

_v-on:click 符号_

```
<a v-on:click=”clickHandler”>Launch!</a>
```

_[@click ](/click ) 符号 _

```
<a @click=”clickHandler”>Launch!</a>
```


### [6、vue slot](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#6vue-slot)  


简单来说，假如父组件需要在子组件内放一些DOM，那么这些DOM是显示、不显示、在哪个地方显示、如何显示，就是slot分发负责的活。


### [7、解释JS中的高阶函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#7解释js中的高阶函数)  


高阶函数是JS函数式编程的最佳特性。它是以函数为参数并返回函数作为结果的函数。一些内置的高阶函数是map、filter、reduce 等等。


### [8、请讲述下VUE的MVVM的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#8请讲述下vue的mvvm的理解)  


MVVM 是 Model-View-ViewModel的缩写，即将数据模型与数据表现层通过数据驱动进行分离，从而只需要关系数据模型的开发，而不需要考虑页面的表现，具体说来如下：

**1、** Model代表数据模型：主要用于定义数据和操作的业务逻辑。

**2、** View代表页面展示组件（即dom展现形式）：负责将数据模型转化成UI 展现出来。

**3、** ViewModel为model和view之间的桥梁：监听模型数据的改变和控制视图行为、处理用户交互。通过双向数据绑定把 View 层和 Model 层连接了起来，而View 和 Model 之间的同步工作完全是自动的，无需人为干涉

**4、** 在MVVM架构下，View 和 Model 之间并没有直接的联系，而是通过ViewModel进行交互，Model 和 ViewModel 之间的交互是双向的， 因此View 数据的变化会同步到Model中，而Model 数据的变化也会立即反应到View 上。


### [9、说一下v-if和v-show的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#9说一下v-if和v-show的区别)  


当条件不成立时，`v-if`不会渲染DOM元素，`v-show`操作的是样式(display)，切换当前DOM的显示和隐藏。


### [10、JS中的宿主对象与原生对象有何不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#10js中的宿主对象与原生对象有何不同)  


宿主对象:这些是运行环境提供的对象。这意味着它们在不同的环境下是不同的。例如，浏览器包含像windows这样的对象，但是Node.js环境提供像Node List这样的对象。

原生对象:这些是JS中的内置对象。它们也被称为全局对象，因为如果使用JS，内置对象不受是运行环境影响。


### [11、如何在JS中克隆对象](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#11如何在js中克隆对象)  

### [12、自定义指令（v-check、v-focus）的方法有哪些？它有哪些钩子函数？还有哪些钩子函数参数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#12自定义指令v-checkv-focus的方法有哪些它有哪些钩子函数还有哪些钩子函数参数)  

### [13、JS的作用域链是什么及其作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#13js的作用域链是什么及其作用)  

### [14、开发人员经常使用字母 “vm” 作为变量名来声明根 Vue 实例。例如 const vm = new Vue()。在这种情况下，“vm”指的是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#14开发人员经常使用字母-“vm-作为变量名来声明根-vue-实例。例如-const-vm-=-new-vue。在这种情况下“vm指的是什么)  

### [15、什么是插槽（slot）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#15什么是插槽slot)  

### [16、怎么定义vue-router的动态路由？怎么获取传过来的动态参数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#16怎么定义vue-router的动态路由怎么获取传过来的动态参数)  

### [17、加载渲染过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#17加载渲染过程)  

### [18、vue的实现原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#18vue的实现原理)  

### [19、请说出vue.cli项目中src目录每个文件夹和文件的用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#19请说出vuecli项目中src目录每个文件夹和文件的用法)  

### [20、那你知道Vue3.x响应式数据原理吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#20那你知道vue3x响应式数据原理吗)  

### [21、delete和Vue.delete删除数组的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#21delete和vuedelete删除数组的区别)  

### [22、简述一下Sass、Less，且说明区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#22简述一下sassless且说明区别)  

### [23、vue的历史记录](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#23vue的历史记录)  

### [24、v-if和v-show的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#24v-if和v-show的区别)  

### [25、vue-router有哪几种导航钩子？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#25vue-router有哪几种导航钩子)  

### [26、vue-roter的钩子函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#26vue-roter的钩子函数)  

### [27、v-model是什么？怎么使用？ vue中标签怎么绑定事件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题附答案汇总（2021年Vue面试题及答案大全）.md#27v-model是什么怎么使用-vue中标签怎么绑定事件)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
