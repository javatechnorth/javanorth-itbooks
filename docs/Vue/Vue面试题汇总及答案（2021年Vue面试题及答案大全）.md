# Vue面试题汇总及答案（2021年Vue面试题及答案大全）

Vue面试题及答案【最新版】Vue高级面试题大全(2021版)，发现网上很多Vue面试题及答案整理都没有答案，所以花了很长时间搜集，本套Vue面试题大全，Vue面试题大汇总，有大量经典的Vue面试题以及答案，包含Vue语言常见面试题、Vue工程师高级面试题及一些大厂Vue开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Vue面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Vue面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、再说一下Computed和Watch](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#1再说一下computed和watch)  


`Computed`本质是一个具备缓存的watcher，依赖的属性发生变化就会更新视图。 适用于计算比较消耗性能的计算场景。当表达式过于复杂时，在模板中放入过多逻辑会让模板难以维护，可以将复杂的逻辑放入计算属性中处理。

`Watch`没有缓存性，更多的是观察的作用，可以监听某些数据执行回调。当我们需要深度监听对象中的属性时，可以打开`deep：true`选项，这样便会对对象中的每一项进行监听。这样会带来性能问题，优化的话可以使用`字符串形式`监听，如果没有写到组件中，不要忘记使用`unWatch手动注销`哦。


### [2、v-for中的key的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#2v-for中的key的理解)  


需要使用key来给每个节点做一个唯一标识，Diff算法就可以正确的识别此节点。主要是为了高效的更新虚拟DOM。


### [3、v-model的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#3v-model的理解)  


v-model用于表单数据的双向绑定，其实它就是一个语法糖，这个背后就做了两个操作：

**1、** v-bind绑定一个value属性；

**2、** v-on指令给当前元素绑定input事件


### [4、vuex是什么？怎么使用？哪种功能场景使用它？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#4vuex是什么怎么使用哪种功能场景使用它)  


vue框架中状态管理。在main.js引入store，注入。新建了一个目录store，….、export 。场景有：单页应用中，组件之间的状态。音乐播放、登录状态、加入购物车


### [5、为什么Vue被称为“渐进框架”？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#5为什么vue被称为“渐进框架)  


使用渐进式框架的代价很小，从而使现有项目（使用其他技术构建的项目）更容易采用并迁移到新框架。 Vue.js 是一个渐进式框架，因为你可以逐步将其引入现有应用，而不必从头开始重写整个程序。

Vue 的最基本和核心的部分涉及“视图”层，因此可以通过逐步将 Vue 引入程序并替换“视图”实现来开始你的旅程。

由于其不断发展的性质，Vue 与其他库配合使用非常好，并且非常容易上手。这与 Angular.js 之类的框架相反，后者要求将现有程序完全重构并在该框架中实现。


### [6、DOM 渲染在 哪个周期中就已经完成？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#6dom-渲染在-哪个周期中就已经完成)  


DOM 渲染在 mounted 中就已经完成了


### [7、使用 Vue 时调用 event.preventDefault() 的最佳方式是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#7使用-vue-时调用-eventpreventdefault-的最佳方式是什么)  


在事件侦听器上调用 `event.preventDefault()` 的最佳方式是将 `.prevent` 修饰符与 `v-on` 指令一起使用。这是一个例子：

```
<a @click.prevent=”doSomethingWhenClicked”>Do Something</a>
```


### [8、第一次页面加载会触发哪几个钩子？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#8第一次页面加载会触发哪几个钩子)  


第一次页面加载时会触发 beforeCreate, created, beforeMount, mounted 这几个钩子


### [9、Vue-router跳转和location.href有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#9vue-router跳转和locationhref有什么区别)  


**1、** 使用location.href='/url'来跳转，简单方便，但是刷新了页面；

**2、** 使用history.pushState('/url')，无刷新页面，静态跳转；

**3、** 引进router，然后使用router.push('/url')来跳转，使用了diff算法，实现了按需加载，减少了dom的消耗。

**4、** 其实使用router跳转和使用history.pushState()没什么差别的，因为vue-router就是用了history.pushState()，尤其是在history模式下。


### [10、什么是过滤器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#10什么是过滤器)  


过滤器是在 Vue 程序中实现自定义文本格式的一种非常简单的方法。它们就像可以在表达式中通过管道传递（使用管道字符）以取得结果的运算符。下面是一个可以反转文本字符串的过滤器示例：

**模板**

```
<div id="app">{{ title | reverseText }}</div>
App
new Vue({
    el: '#app',
    data: {
      title: 'This is a title'
    },
    filters: {
      reverseText(text) {
        return text.split('').reverse().join('');
      }
    }
});
```

**输出**

eltit a si sihT

在上面的例子中，我们创建了一个名为 reverseText 的过滤器，该过滤器反转文本字符串并返回。这是一个简单的函数，接受输入并返回处理后的输出。通过在过滤器下声明，它就可以成为可以在模板中使用的过滤器。

在模板中，我们只是将 reverseText 过滤器通过管道传递到了想要在 mustache 标签中显示的数据变量。这样可以将多个过滤器管道连接在一起。因此过滤器提供了一种非常优雅的方式来处理文本。


### [11、如何在输入框和数据属性之间实现双向数据绑定？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#11如何在输入框和数据属性之间实现双向数据绑定)  

### [12、vue常用的UI组件库](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#12vue常用的ui组件库)  

### [13、请详细说下你对vue生命周期的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#13请详细说下你对vue生命周期的理解)  

### [14、vue修改打包后静态资源路径的修改](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#14vue修改打包后静态资源路径的修改)  

### [15、简述每个周期具体适合哪些场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#15简述每个周期具体适合哪些场景)  

### [16、JS中有哪些不同类型的弹出框可用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#16js中有哪些不同类型的弹出框可用)  

### [17、解释JS中的事件冒泡和事件捕获](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#17解释js中的事件冒泡和事件捕获)  

### [18、的作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#18的作用是什么)  

### [19、vue更新数组时触发视图更新的方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#19vue更新数组时触发视图更新的方法)  

### [20、Vue2.x组件通信有哪些方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#20vue2x组件通信有哪些方式)  

### [21、v-show 指令的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#21v-show-指令的用途是什么)  

### [22、vuex有哪几种属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#22vuex有哪几种属性)  

### [23、说一下v-model的原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#23说一下v-model的原理)  

### [24、再说一下vue2.x中如何监测数组变化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#24再说一下vue2x中如何监测数组变化)  

### [25、mvvm 框架是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#25mvvm-框架是什么)  

### [26、请说下封装 vue 组件的过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#26请说下封装-vue-组件的过程)  

### [27、解释 JS 事件委托模型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#27解释-js-事件委托模型)  

### [28、vue.cli中怎样使用自定义的组件？有遇到过哪些问题吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题汇总及答案（2021年Vue面试题及答案大全）.md#28vuecli中怎样使用自定义的组件有遇到过哪些问题吗)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
