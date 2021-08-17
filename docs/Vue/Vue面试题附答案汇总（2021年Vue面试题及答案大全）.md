# Vue面试题附答案汇总（2021年Vue面试题及答案大全）

Vue面试题及答案【最新版】Vue高级面试题大全(2021版)，发现网上很多Vue面试题及答案整理都没有答案，所以花了很长时间搜集，本套Vue面试题大全，Vue面试题大汇总，有大量经典的Vue面试题以及答案，包含Vue语言常见面试题、Vue工程师高级面试题及一些大厂Vue开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Vue面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Vue面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、如何让CSS只在当前组件中起作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#1如何让css只在当前组件中起作用)  


在组件中的style前面加上scoped


### [2、$$emit 、$$on 、$$once 、$$off理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#2$$emit-$$on-$$once-$$off理解)  


**$emit**

触发当前实例上的自定义事件（并将附加参数都传给监听器回调）

**$on**

监听实例上自定义事件并调用回调函数，监听emit触发的事件

**$once**

监听一个自定义事件，但是只触发一次，在第一次触发之后移除监听器。

**$off**

用来移除自定义事件监听器。如果没有提供参数，则移除所有的事件监听器；如果只提供了事件，则移除该事件所有的监听器；如果同时提供了事件与回调，则只移除这个回调的监听器。

这四个方法的实现原理是：通过对vue实例挂载，然后分别使用对象存储数组对应的函数事件，其中emit通过循环查找存储的数组中对应的函数进行调用，once只匹配一次就就结束，on是将对应的函数存储到数组中，off是删除数组中指定的元素或者所有的元素事件。具体可以参考文章：VUEemit实现


### [3、路由跳转和location.href的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#3路由跳转和locationhref的区别)  


使用location.href='/url'来跳转，简单方便，但是刷新了页面；

使用路由方式跳转，无刷新页面，静态跳转；


### [4、如何封装一个vue组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#4如何封装一个vue组件)  


根据业务需求，建立组件的模板，先把架子搭起来，写写样式，考虑好组件的基本逻辑。

**1、** 准备好组件的数据输入。即分析好逻辑，定好 props 里面的数据、类型。

**2、** 准备好组件的数据输出。即根据组件逻辑，做好要暴露出来的方法。

**3、** 封装完毕了，直接调用即可


### [5、vue常用的修饰符](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#5vue常用的修饰符)  


**1、** .stop：等同于JavaScript中的event.stopPropagation()，防止事件冒泡；

**2、** .prevent：等同于JavaScript中的event.preventDefault()，防止执行预设的行为（如果事件可取消，则取消该事件，而不停止事件的进一步传播）；

**3、** .capture：与事件冒泡的方向相反，事件捕获由外到内；

**4、** .self：只会触发自己范围内的事件，不包含子元素；

**5、** .once：只会触发一次。


### [6、Vue2.x和Vue3.x渲染器的diff算法分别说一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#6vue2x和vue3x渲染器的diff算法分别说一下)  


简单来说，diff算法有以下过程

**1、** 同级比较，再比较子节点

**2、** 先判断一方有子节点一方没有子节点的情况(如果新的children没有子节点，将旧的子节点移除)

**3、** 比较都有子节点的情况(核心diff)

**4、** 递归比较子节点

正常Diff两个树的时间复杂度是`O(n^3)`，但实际情况下我们很少会进行`跨层级的移动DOM`，所以Vue将Diff进行了优化，从`O(n^3) -> O(n)`，只有当新旧children都为多个子节点时才需要用核心的Diff算法进行同层级比较。

Vue2的核心Diff算法采用了`双端比较`的算法，同时从新旧children的两端开始进行比较，借助key值找到可复用的节点，再进行相关操作。相比React的Diff算法，同样情况下可以减少移动节点次数，减少不必要的性能损耗，更加的优雅。

Vue3.x借鉴了 [ivi](https://github.com/localvoid/ivi)算法和 [inferno](https://github.com/infernojs/inferno)算法

在创建VNode时就确定其类型，以及在`mount/patch`的过程中采用`位运算`来判断一个VNode的类型，在这个基础之上再配合核心的Diff算法，使得性能上较Vue2.x有了提升。(实际的实现可以结合Vue3.x源码看。)

该算法中还运用了`动态规划`的思想求解最长递归子序列。

(看到这你还会发现，框架内无处不蕴藏着数据结构和算法的魅力)


### [7、vue生命周期的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#7vue生命周期的作用是什么)  


它的生命周期中有多个事件钩子，让我们在控制整个Vue实例的过程时更容易形成好的逻辑。


### [8、说出几种vue当中的指令和它的用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#8说出几种vue当中的指令和它的用法)  


v-model双向数据绑定；

v-for循环；

v-if v-show 显示与隐藏；

v-on事件；v-once: 只绑定一次。


### [9、JS中的深拷贝与浅拷贝的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#9js中的深拷贝与浅拷贝的区别)  


**1、** 深拷贝递归地复制新对象中的所有值或属性，而拷贝只复制引用。

**2、** 在深拷贝中，新对象中的更改不会影响原始对象，而在浅拷贝中，新对象中的更改，原始对象中也会跟着改。

**3、** 在深拷贝中，原始对象不与新对象共享相同的属性，而在浅拷贝中，它们具有相同的属性。


### [10、vue单页面和传统的多页面区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#10vue单页面和传统的多页面区别)  


**单页面应用（SPA）**

通俗一点说就是指只有一个主页面的应用，浏览器一开始要加载所有必须的 html, js, css。所有的页面内容都包含在这个所谓的主页面中。但在写的时候，还是会分开写（页面片段），然后在交互的时候由路由程序动态载入，单页面的页面跳转，仅刷新局部资源。多应用于pc端。

**多页面（MPA）**

指一个应用中有多个页面，页面跳转时是整页刷新

**单页面的优点：**

用户体验好，快，内容的改变不需要重新加载整个页面，基于这一点spa对服务器压力较小；前后端分离；页面效果会比较炫酷（比如切换页面内容时的专场动画）。

**单页面缺点：**

不利于seo；导航不可用，如果一定要导航需要自行实现前进、后退。（由于是单页面不能用浏览器的前进后退功能，所以需要自己建立堆栈管理）；初次加载时耗时多；页面复杂度提高很多。


### [11、如何在JS中动态添加/删除对象的属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#11如何在js中动态添加/删除对象的属性)  

### [12、如何将数据从父组件传递到子组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#12如何将数据从父组件传递到子组件)  

### [13、用纯JS编写一个程序来反转字符串](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#13用纯js编写一个程序来反转字符串)  

### [14、简单说一下Vue2.x响应式数据原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#14简单说一下vue2x响应式数据原理)  

### [15、说说你对angular脏检查理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#15说说你对angular脏检查理解)  

### [16、axios及安装?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#16axios及安装)  

### [17、如何在JS中编码和解码](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#17如何在js中编码和解码)  

### [18、你都做过哪些Vue的性能优化，编码阶段](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#18你都做过哪些vue的性能优化编码阶段)  

### [19、销毁过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#19销毁过程)  

### [20、解释一下什么是 promise ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#20解释一下什么是-promise-)  

### [21、mint-ui是什么？怎么使用？说出至少三个组件使用方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#21mint-ui是什么怎么使用说出至少三个组件使用方法)  

### [22、vue和jQuery的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#22vue和jquery的区别)  

### [23、如何动态地在元素上切换 CSS 类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#23如何动态地在元素上切换-css-类)  

### [24、你的接口请求一般放在哪个生命周期中？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#24你的接口请求一般放在哪个生命周期中)  

### [25、用户体验](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#25用户体验)  

### [26、v-show 与 v-if 指令有何不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#26v-show-与-v-if-指令有何不同)  

### [27、scss是什么？在vue.cli中的安装使用步骤是？有哪几大特性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#27scss是什么在vuecli中的安装使用步骤是有哪几大特性)  

### [28、vuex是什么？怎么使用？哪种功能场景使用它？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案汇总（2021年Vue面试题及答案大全）.md#28vuex是什么怎么使用哪种功能场景使用它)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
