# React中级面试题汇总及答案（2021年React面试题及答案大全）

React面试题及答案【最新版】React高级面试题大全(2021版)，发现网上很多React面试题及答案整理都没有答案，所以花了很长时间搜集，本套React面试题大全，React面试题大汇总，有大量经典的React面试题以及答案，包含React语言常见面试题、React工程师高级面试题及一些大厂React开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套React面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个React面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、简单说一下Vue2.x响应式数据原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#1简单说一下vue2x响应式数据原理)  


Vue在初始化数据时，会使用`Object.defineProperty`重新定义data中的所有属性，当页面使用对应属性时，首先会进行依赖收集(收集当前组件的`watcher`)如果属性发生变化会通知相关依赖进行更新操作(`发布订阅`)。


### [2、如何在 React 中创建表单](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#2如何在-react-中创建表单)  


React 表单类似于 HTML 表单。但是在 React 中，状态包含在组件的 state 属性中，并且只能通过 `setState()` 更新。因此元素不能直接更新它们的状态，它们的提交是由 JavaScript 函数处理的。此函数可以完全访问用户输入到表单的数据。

```
handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
}

render() {
    return (
        <form onSubmit={this.handleSubmit}>
            <label>
                Name:
                <input type="text" value={this.state.value} onChange={this.handleSubmit} />
            </label>
            <input type="submit" value="Submit" />
        </form>
    );
}
```


### [3、Redux遵循的三个原则是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#3redux遵循的三个原则是什么)  


**1、**  单一事实来源：整个应用的状态存储在单个 store 中的对象/状态树里。单一状态树可以更容易地跟踪随时间的变化，并调试或检查应用程序。

**2、**  状态是只读的：改变状态的唯一方法是去触发一个动作。动作是描述变化的普通 JS 对象。就像 state 是数据的最小表示一样，该操作是对数据更改的最小表示。

**3、**  使用纯函数进行更改：为了指定状态树如何通过操作进行转换，你需要纯函数。纯函数是那些返回值仅取决于其参数值的函数。


### [4、redux与mobx的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#4redux与mobx的区别)  


**两者对比:**

**1、** redux将数据保存在单一的store中，mobx将数据保存在分散的多个store中

**2、** redux使用plain object保存数据，需要手动处理变化后的操作；mobx适用observable保存数据，数据变化后自动处理响应的操作

**3、** redux使用不可变状态，这意味着状态是只读的，不能直接去修改它，而是应该返回一个新的状态，同时使用纯函数；mobx中的状态是可变的，可以直接对其进行修改

**4、** mobx相对来说比较简单，在其中有很多的抽象，mobx更多的使用面向对象的编程思维；redux会比较复杂，因为其中的函数式编程思想掌握起来不是那么容易，同时需要借助一系列的中间件来处理异步和副作用

**5、** mobx中有更多的抽象和封装，调试会比较困难，同时结果也难以预测；而redux提供能够进行时间回溯的开发工具，同时其纯函数以及更少的抽象，让调试变得更加的容易

**场景辨析:**

基于以上区别,我们可以简单得分析一下两者的不同使用场景.

mobx更适合数据不复杂的应用: mobx难以调试,很多状态无法回溯,面对复杂度高的应用时,往往力不从心.

redux适合有回溯需求的应用: 比如一个画板应用、一个表格应用，很多时候需要撤销、重做等操作，由于redux不可变的特性，天然支持这些操作.

mobx适合短平快的项目: mobx上手简单,样板代码少,可以很大程度上提高开发效率.

当然mobx和redux也并不一定是非此即彼的关系,你也可以在项目中用redux作为全局状态管理,用mobx作为组件局部状态管理器来用.


### [5、为什么选择使用框架而不是原生?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#5为什么选择使用框架而不是原生)  


**框架的好处:**

**1、** 组件化: 其中以 React 的组件化最为彻底,甚至可以到函数级别的原子组件,高度的组件化可以是我们的工程易于维护、易于组合拓展

**2、** 天然分层: JQuery 时代的代码大部分情况下是面条代码,耦合严重,现代框架不管是 MVC、MVP还是MVVM 模式都能帮助我们进行分层，代码解耦更易于读写。

**3、** 生态: 现在主流前端框架都自带生态,不管是数据流管理架构还是 UI 库都有成熟的解决方案。

**4、** 开发效率: 现代前端框架都默认自动更新DOM,而非我们手动操作,解放了开发者的手动DOM成本,提高开发效率,从根本上解决了UI 与状态同步问题.


### [6、说一下v-if和v-show的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#6说一下v-if和v-show的区别)  


当条件不成立时，`v-if`不会渲染DOM元素，`v-show`操作的是样式(display)，切换当前DOM的显示和隐藏。


### [7、React与Angular有何不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#7react与angular有何不同)  

| 主题 | React | Angular |
| --- | --- | --- |
| _1、体系结构_ | 只有 MVC 中的 View | 完整的 MVC |
| _2、渲染_ | 可以在服务器端渲染 | 客户端渲染 |
| _3、DOM_ | 使用 virtual DOM | 使用 real DOM |
| _4、数据绑定_ | 单向数据绑定 | 双向数据绑定 |
| _5、调试_ | 编译时调试 | 运行时调试 |
| _6、作者_ | Facebook | Google |



### [8、你对 React 的 refs 有什么了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#8你对-react-的-refs-有什么了解)  


Refs 是 React 中引用的简写。它是一个有助于存储对特定的 React 元素或组件的引用的属性，它将由组件渲染配置函数返回。用于对 render() 返回的特定元素或组件的引用。当需要进行 DOM 测量或向组件添加方法时，它们会派上用场。

```
class ReferenceDemo extends React.Component{
     display() {
         const name = this.inputDemo.value;
         document.getElementById('disp').innerHTML = name;
     }
render() {
    return(
          <div>
            Name: <input type="text" ref={input => this.inputDemo = input} />
            <button name="Click" onClick={this.display}>Click</button>
            <h2>Hello <span id="disp"></span> !!!</h2>
          </div>
    );
   }
 }
```


### [9、react和vue的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#9react和vue的区别)  


**相同点**

**1、** 数据驱动页面提供响应式的试图组件

**2、** 都有 `virtual DOM`,组件化的开发通过 `props`参数进行父子之间组件传递数据都实现了 `webComponents`规范

**3、** 数据流动单向都支持服务器的渲染SSR

**4、** 都有支持 `native`的方法 `react`有 `React native vue`有 `wexx`

**不同点**

**1、** 数据绑定 `Vue`实现了双向的数据绑定 `react`数据流动是单向的

**2、** 数据渲染大规模的数据渲染 `react`更快

**3、** 使用场景 `React`配合 `Redux`架构适合大规模多人协作复杂项目Vue适合小快的项目

**4、** 开发风格 `react`推荐做法 `jsx` + `inline style`把 `html`和 `css`都写在 `js`了

**5、** `vue`是采用 `webpack` + `vue-loader`单文件组件格式 `html`, `js`, `css`同一个文件


### [10、你对受控组件和非受控组件了解多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#10你对受控组件和非受控组件了解多少)  

| 受控组件 | 非受控组件 |
| --- | --- |
| 1、没有维持自己的状态 | 1、保持着自己的状态 |
| 2.数据由父组件控制 | 2.数据由 DOM 控制 |
| 3、通过 props 获取当前值，然后通过回调通知更改 | 3、Refs 用于获取其当前值 |



### [11、为什么需要 React 中的路由？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#11为什么需要-react-中的路由)  

### [12、你了解 Virtual DOM 吗？解释一下它的工作原理。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#12你了解-virtual-dom-吗解释一下它的工作原理。)  

### [13、redux中间件有哪些，做什么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#13redux中间件有哪些做什么用)  

### [14、setState](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#14setstate)  

### [15、区分Real DOM和Virtual DOM](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#15区分real-dom和virtual-dom)  

### [16、什么是React 路由？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#16什么是react-路由)  

### [17、setState到底是异步还是同步?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#17setstate到底是异步还是同步)  

### [18、React中的状态是什么？它是如何使用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#18react中的状态是什么它是如何使用的)  

### [19、React中的事件是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#19react中的事件是什么)  

### [20、react性能优化方案](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#20react性能优化方案)  

### [21、Redux 有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#21redux-有哪些优点)  

### [22、什么是React？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#22什么是react)  

### [23、React有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#23react有什么特点)  

### [24、React如何进行组件/逻辑复用?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#24react如何进行组件/逻辑复用)  

### [25、简述flux 思想](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#25简述flux-思想)  

### [26、setState: React 中用于修改状态更新视图。它具有以下特点:](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#26setstate:-react-中用于修改状态更新视图。它具有以下特点:)  

### [27、生命周期钩子 (useEffect):](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React中级面试题汇总及答案（2021年React面试题及答案大全）.md#27生命周期钩子-useeffect:)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
