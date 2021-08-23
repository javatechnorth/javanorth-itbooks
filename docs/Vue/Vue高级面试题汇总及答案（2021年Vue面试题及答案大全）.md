# Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）

Vue面试题及答案【最新版】Vue高级面试题大全(2021版)，发现网上很多Vue面试题及答案整理都没有答案，所以花了很长时间搜集，本套Vue面试题大全，Vue面试题大汇总，有大量经典的Vue面试题以及答案，包含Vue语言常见面试题、Vue工程师高级面试题及一些大厂Vue开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Vue面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Vue面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Vue事件绑定原理说一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#1vue事件绑定原理说一下)  


原生事件绑定是通过`addEventListener`绑定给真实元素的，组件事件绑定是通过Vue自定义的`$on`实现的。


### [2、active-class 是哪个组件的属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#2active-class-是哪个组件的属性)  


vue-router模块的router-link组件。children数组来定义子路由


### [3、解释一下 "use strict" ? “](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#3解释一下-"use-strict"--“)  


use strict”是Es5中引入的js指令。 使用“use strict”指令的目的是强制执行严格模式下的代码。 在严格模式下，咱们不能在不声明变量的情况下使用变量。 早期版本的js忽略了“use strict”。


### [4、什么是动态 prop？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#4什么是动态-prop)  


当使用 v-bind 指令为 prop 分配值作为绑定到属性的函数时，被称为动态 prop。例如以下组件的 `tweet` 属性绑定到名为tweetText的数据属性。这与静态硬编码值相反。这种绑定始终是单向的，这意味着数据可以从父组件流到子组件，而绝不会反过来。

```
<TweetBox :tweet=”tweetText”>
```


### [5、$route 和 $router 的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#5$route-和-$router-的区别)  


$$router是VueRouter的实例，在script标签中想要导航到不同的URL,使用$$router.push方法。返回上一个历史history用$$router.to(-1)
$$route为当前router跳转对象。里面可以获取当前路由的name,path,query,parmas等。


### [6、vue初始化页面闪动问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#6vue初始化页面闪动问题)  


使用vue开发时，在vue初始化之前，由于div是不归vue管的，所以我们写的代码在还没有解析的情况下会容易出现花屏现象，看到类似于{{message}}的字样，虽然一般情况下这个时间很短暂，但是我们还是有必要让解决这个问题的。

首先：在css里加上[v-cloak] {

display: none;

}。

如果没有彻底解决问题，则在根元素加上style="display: none;" :style="{display: 'block'}"


### [7、iframe的优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#7iframe的优缺点)  


iframe也称作嵌入式框架，嵌入式框架和框架网页类似，它可以把一个网页的框架和内容嵌入在现有的网页中。

**优点：**

**1、** 解决加载缓慢的第三方内容如图标和广告等的加载问题

**2、** Security sandbox

**3、** 并行加载脚本

**4、** 方便制作导航栏

**缺点：**

**1、** iframe会阻塞主页面的Onload事件

**2、** 即时内容为空，加载也需要时间

**3、** 没有语意


### [8、解释一下什么是箭头函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#8解释一下什么是箭头函数)  


箭头函数是在es6或更高版本中编写函数表达式的简明方法。箭头函数不能用作构造函数，也不支持this，arguments，super或new.target关键字，它最适合非方法函数。 通常，箭头函数看起来像 const function_name =（）=> {}。

```
const greet=()=>{console.log('hello');}
 greet();
```


### [9、打包优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#9打包优化)  


**1、** 压缩代码

**2、** Tree Shaking/Scope Hoisting

**3、** 使用cdn加载第三方模块

**4、** 多线程打包happypack

**5、** splitChunks抽离公共文件

**6、** sourceMap优化


### [10、vue组件中data为什么必须是一个函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#10vue组件中data为什么必须是一个函数)  


因为JavaScript的特性所导致，在component中，data必须以函数的形式存在，不可以是对象。

组建中的data写成一个函数，数据以函数返回值的形式定义，这样每次复用组件的时候，都会返回一份新的data，相当于每个组件实例都有自己私有的数据空间，它们只负责各自维护的数据，不会造成混乱。而单纯的写成对象形式，就是所有的组件实例共用了一个data，这样改一个全都改了。


### [11、vue-router实现懒加载的方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#11vue-router实现懒加载的方式)  

### [12、组件中的data为什么是一个函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#12组件中的data为什么是一个函数)  

### [13、vue的solt的用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#13vue的solt的用法)  

### [14、第一次页面加载会触发哪几个钩子？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#14第一次页面加载会触发哪几个钩子)  

### [15、为什么使用key?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#15为什么使用key)  

### [16、nextTick知道吗，实现原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#16nexttick知道吗实现原理是什么)  

### [17、vue-router 是什么?它有哪些组件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#17vue-router-是什么它有哪些组件)  

### [18、delete和Vue.delete删除数组的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#18delete和vuedelete删除数组的区别)  

### [19、vue中template编译的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#19vue中template编译的理解)  

### [20、JS 中 == 和 === 区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#20js-中--和-=-区别是什么)  

### [21、v-on可以监听多个方法吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#21v-on可以监听多个方法吗)  

### [22、如何从子组件发出自定义事件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#22如何从子组件发出自定义事件)  

### [23、vue更新数组时触发视图更新的方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#23vue更新数组时触发视图更新的方法)  

### [24、请详细说下你对vue生命周期的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#24请详细说下你对vue生命周期的理解)  

### [25、与React的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#25与react的区别)  

### [26、vue优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#26vue优点)  

### [27、vue-router的两种模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#27vue-router的两种模式)  

### [28、那你能讲一讲MVVM吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题汇总及答案（2021年Vue面试题及答案大全）.md#28那你能讲一讲mvvm吗)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
