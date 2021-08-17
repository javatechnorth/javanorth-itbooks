# Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）

Vue面试题及答案【最新版】Vue高级面试题大全(2021版)，发现网上很多Vue面试题及答案整理都没有答案，所以花了很长时间搜集，本套Vue面试题大全，Vue面试题大汇总，有大量经典的Vue面试题以及答案，包含Vue语言常见面试题、Vue工程师高级面试题及一些大厂Vue开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Vue面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Vue面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、JS中判断数据类型的方法有几种?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#1js中判断数据类型的方法有几种)  


**1、** 最常见的判断方法：typeof

**2、** 判断已知对象类型的方法： instanceof

**3、** 根据对象的constructor判断： constructor

**4、** 无敌万能的方法：jquery.type()


### [2、axios的特点有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#2axios的特点有哪些)  


**1、** 从浏览器中创建XMLHttpRequests；

**2、** node.js创建http请求；

**3、** 支持Promise API；

**4、** 拦截请求和响应；

**5、** 转换请求数据和响应数据；

**6、** 取消请求；

**7、** 自动换成json。

**8、** axios中的发送字段的参数是data跟params两个，两者的区别在于params是跟请求地址一起发送的，data的作为一个请求体进行发送

**9、** params一般适用于get请求，data一般适用于post put 请求。


### [3、vue开发遇到的问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#3vue开发遇到的问题)  


**样式污染**

在编写样式中，如果需要防止样式的污染，可以使用两种方式，一种是在组件的根元素上增加一个唯一的class或者id，然后在编写组件的样式时候在根元素对应的class或者id下进行编写；另一种方式是在对应的style上添加scoped关键字，不过该关键字对引用的框架UI无效

**router-link在安卓上不起作用**

不起作用的原因是因为转码编译的问题，可以使用babel来进行处理，安装babel polypill插件解决

**初始化页面出现闪屏乱码的问题**

这是因为vue还没有解析的情况下会容易出现花屏现象，看到类似于{{data}}的字样，可以使用两种方式来进行处理，一种为：在设置index.html的根元素的元素的样式为display:none，然后在mounted中的$nextTick函数中display:block展示；另一种方式是使用vue的内置指令：v-cloak,并且在css中设置样式

```
[v-cloak] {
    display: none;
}
```

**router-link上事件无效解决方法**

使用@click.native来进行调用原生的js事件。原因：router-link会阻止click事件，.native指直接监听一个原生事件。



### [4、解释一下JS的展开操作符？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#4解释一下js的展开操作符)  


展开运算符在需要多个参数/变量/元素的位置展开表达式，它用三个点（...）。如：

```
var mid = [3, 4];

var newarray = [1, 2, ...mid, 5, 6];

console.log(newarray);

// [1, 2, 3, 4, 5, 6]
```


### [5、说出至少4种vue当中的指令和它的用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#5说出至少4种vue当中的指令和它的用法)  


v-if：判断是否隐藏；v-for：数据循环出来；v-bind:class：绑定一个属性；v-model：实现双向绑定


### [6、vue生命周期总共有几个阶段？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#6vue生命周期总共有几个阶段)  


它可以总共分为8个阶段：创建前/后, 载入前/后,更新前/后,销毁前/销毁后


### [7、vue与react、angular的比较？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#7vue与reactangular的比较)  


**Vue**

轻量级框架：只关注视图层，是一个构建数据的视图集合，大小只有几十kb；

简单易学：国人开发，中文文档，不存在语言障碍 ，易于理解和学习；

双向数据绑定：保留了angular的特点，在数据操作方面更为简单；

组件化：保留了react的优点，实现了html的封装和重用，在构建单页面应用方面有着独特的优势；

视图，数据，结构分离：使数据的更改更为简单，不需要进行逻辑代码的修改，只需要操作数据就能完成相关操作；

虚拟DOM：dom操作是非常耗费性能的， 不再使用原生的dom操作节点，极大解放dom操作，但具体操作的还是dom不过是换了另一种方式；

运行速度更快:相比较与react而言，同样是操作虚拟dom，就性能而言，vue存在很大的优势。

**React**

**相同点：**

React采用特殊的JSX语法，Vue.js在组件开发中也推崇编写.vue特殊文件格式，对文件内容都有一些约定，两者都需要编译后使用；中心思想相同：一切都是组件，组件实例之间可以嵌套；都提供合理的钩子函数，可以让开发者定制化地去处理需求；都不内置列数AJAX，Route等功能到核心包，而是以插件的方式加载；在组件开发中都支持mixins的特性。

**不同点：**

React采用的Virtual DOM会对渲染出来的结果做脏检查；Vue.js在模板中提供了指令，过滤器等，可以非常方便，快捷地操作Virtual DOM。

**Angular**

**相同点：**

都支持指令：内置指令和自定义指令；都支持过滤器：内置过滤器和自定义过滤器；都支持双向数据绑定；都不支持低端浏览器。

**不同点：**

AngularJS的学习成本高，比如增加了Dependency Injection特性，而Vue.js本身提供的API都比较简单、直观；在性能上，AngularJS依赖对数据做脏检查，所以Watcher越多越慢；Vue.js使用基于依赖追踪的观察并且使用异步队列更新，所有的数据都是独立触发的。


### [8、Vue.js 中的指令是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#8vuejs-中的指令是什么)  


指令是一系列特殊属性，你可以通过将其添加到模板 HTML 标记中来赋予它们特殊的响应功能。指令允许模板中的元素使用数据属性、方法、计算或监视的属性和内联表达式根据定义的逻辑对更改做出反应。例如以下代码使用 v-on 指令在组件上实现 click 事件侦听器。

```
<SignUpButton v-on:click=”doSignup” />
```

或者

```
<SignUpButton @click=”doSignup” />
```

在这个例子中，我们使用 v-if 指令基于名为 showButton 的数据属性显示或删除元素与组件。指令以 **v-** 开头来指示 Vue 特定的属性。此规则的例外是 v-on 和 v-bind 的简写形式。

```
<SignUpButton v-if=”showButton” />
```

Vue 还允许定义自己的自定义指令。


### [9、module.exports 和 exports 之间有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#9moduleexports-和-exports-之间有什么区别)  


module和exports是Node.js给每个js文件内置的两个对象。可以通过console.log(module)和console.log(exports)打印出来。如果你在main.js中写入下面两行，然后运行$ node main.js:

```
console.log(exports);//输出：{}
console.log(module);//输出：Module {..., exports: {}, ...} （注：...代表省略了其他一些属性）
```

从打印咱们可以看出，module.exports和exports一开始都是一个空对象{}，实际上，这两个对象指向同一块内存。这也就是说module.exports和exports是等价的（有个前提：不去改变它们指向的内存地址）。

例如：exports.age = 18和module.export.age = 18，这两种写法是一致的（都相当于给最初的空对象{}添加了一个属性，通过require得到的就是{age: 18}）。


### [10、vue-loader是什么？使用它的用途有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#10vue-loader是什么使用它的用途有哪些)  


解析.vue文件的一个加载器，跟template/js/style转换成js模块。

用途：js可以写es6、style样式可以scss或less、template可以加jade等


### [11、渐进式框架的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#11渐进式框架的理解)  

### [12、对于作为元素实现的注释框，我们希望使用户能够按下键盘上的Enter键，来将内容提交给名为 “storeComment” 的方法。在代码中对此进行演示。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#12对于作为元素实现的注释框我们希望使用户能够按下键盘上的enter键来将内容提交给名为-“storecomment-的方法。在代码中对此进行演示。)  

### [13、什么是组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#13什么是组件)  

### [14、绑定 HTML 类时，该如何连接类？假设存在一个元素：Process。我们只希望使用名为 “isActive” 的数据属性动态地切换 btnActive 类。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#14绑定-html-类时该如何连接类假设存在一个元素：process。我们只希望使用名为-“isactive-的数据属性动态地切换-btnactive-类。)  

### [15、undefined，null 和 undeclared 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#15undefinednull-和-undeclared-有什么区别)  

### [16、vue首屏白屏如何解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#16vue首屏白屏如何解决)  

### [17、vue中的v-cloak的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#17vue中的v-cloak的理解)  

### [18、vue常用的修饰符？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#18vue常用的修饰符)  

### [19、created和mounted的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#19created和mounted的区别)  

### [20、v-if和v-for的优先级](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#20v-if和v-for的优先级)  

### [21、VUE的生命周期及理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#21vue的生命周期及理解)  

### [22、cancas和SVG的是什么以及区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#22cancas和svg的是什么以及区别)  

### [23、vue获取数据在哪个周期函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#23vue获取数据在哪个周期函数)  

### [24、如何确保在单文件组件中定义的 CSS 样式仅应用于该组件，而不被用于其他组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#24如何确保在单文件组件中定义的-css-样式仅应用于该组件而不被用于其他组件)  

### [25、JS中let和const有什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#25js中let和const有什么用)  

### [26、子组件像父组件传递事件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#26子组件像父组件传递事件)  

### [27、JS中的匿名函数是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue高级面试题附答案汇总（2021年Vue面试题及答案大全）.md#27js中的匿名函数是什么)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
