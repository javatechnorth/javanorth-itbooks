# React面试题汇总及答案（2021年React面试题及答案大全）

React面试题及答案【最新版】React高级面试题大全(2021版)，发现网上很多React面试题及答案整理都没有答案，所以花了很长时间搜集，本套React面试题大全，React面试题大汇总，有大量经典的React面试题以及答案，包含React语言常见面试题、React工程师高级面试题及一些大厂React开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套React面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个React面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是JSX？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#1什么是jsx)  


JSX 是J avaScript XML 的简写。是 React 使用的一种文件，它利用 JavaScript 的表现力和类似 HTML 的模板语法。这使得 HTML 文件非常容易理解。此文件能使应用非常可靠，并能够提高其性能。下面是JSX的一个例子：

```
render(){
    return(
        <div>
            <h1> Hello World from Edureka!!</h1>
        </div>
    );
}
```


### [2、React Portal 有哪些使用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#2react-portal-有哪些使用场景)  


在以前 `react` 中所有的组件都会位于 `#app` 下而使用 `Portals` 提供了一种脱离 `#app` 的组件因此 `Portals` 适合脱离文档流(`out of flow`) 的组件特别是 `position: absolute` 与 `position: fixed`的组件。比如模态框通知警告`goTop` 等。

以下是官方一个模态框的示例可以在以下地址中测试效果

```
<html>
  <body>
    <div id="app"></div>
    <div id="modal"></div>
    <div id="gotop"></div>
    <div id="alert"></div>
  </body>
</html>
```

```
const modalRoot = document.getElementById('modal');

class Modal extends React.Component {
  constructor(props) {
    super(props);
    this.el = document.createElement('div');
  }

  componentDidMount() {
    modalRoot.appendChild(this.el);
  }

  componentWillUnmount() {
    modalRoot.removeChild(this.el);
  }

  render() {
    return ReactDOM.createPortal(
      this.props.children,
      this.el,
    );
  }
}
```

`React Hooks`当中的`useEffect`是如何区分生命周期钩子的

`useEffect`可以看成是`componentDidMountcomponentDidUpdate`和`componentWillUnmount`三者的结合。`useEffect(callback, [source])`接收两个参数调用方式如下

```
 useEffect(() => {
   console.log('mounted');
   
   return () => {
       console.log('willUnmount');
   }
 }, [source]);
```

生命周期函数的调用主要是通过第二个参数[source]来进行控制有如下几种情况

**1、** [source]参数不传时则每次都会优先调用上次保存的函数中返回的那个函数然后再调用外部那个函数

**2、** [source]参数传[]时则外部的函数只会在初始化时调用一次返回的那个函数也只会最终在组件卸载时调用一次

**3、** [source]参数有值时则只会监听到数组中的值发生变化后才优先调用返回的那个函数再调用外部的函数。


### [3、再说一下vue2.x中如何监测数组变化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#3再说一下vue2x中如何监测数组变化)  


使用了函数劫持的方式，重写了数组的方法，Vue将data中的数组进行了原型链重写，指向了自己定义的数组原型方法。这样当调用数组api时，可以通知依赖更新。如果数组中包含着引用类型，会对数组中的引用类型再次递归遍历进行监控。这样就实现了监测数组变化。

（能问到这的面试官都比较注重深度，这些常规操作要记牢）


### [4、解释 React 中 render() 的目的。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#4解释-react-中-render-的目的。)  


每个React组件强制要求必须有一个 render()。它返回一个 React 元素，是原生 DOM 组件的表示。如果需要渲染多个 HTML 元素，则必须将它们组合在一个封闭标记内，例如 `<form>`、`<group>`、`<div>` 等。此函数必须保持纯净，即必须每次调用时都返回相同的结果。


### [5、什么是高阶组件（HOC）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#5什么是高阶组件hoc)  


高阶组件是重用组件逻辑的高级方法，是一种源于 React 的组件模式。 HOC 是自定义组件，在它之内包含另一个组件。它们可以接受子组件提供的任何动态，但不会修改或复制其输入组件中的任何行为。你可以认为 HOC 是“纯（Pure）”组件。


### [6、Vue2.x组件通信有哪些方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#6vue2x组件通信有哪些方式)  


**父子组件通信**

**1、** 父->子`props`，子->父 `$on、$emit`

**2、** 获取父子组件实例 `$parent、$children`

**3、** `Ref` 获取实例的方式调用组件的属性或者方法

**4、** `Provide、inject` 官方不推荐使用，但是写组件库时很常用

**兄弟组件通信**

**1、** `Event Bus` 实现跨组件通信 `Vue.prototype.$bus = new Vue`

**2、** `Vuex`

**跨级组件通信**

**1、** `Vuex`

**2、** `$attrs、$listeners`

**3、** `Provide、inject`


### [7、Redux与Flux有何不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#7redux与flux有何不同)  

| Flux | Redux |
| --- | --- |
| 1、Store 包含状态和更改逻辑 | 1、Store 和更改逻辑是分开的 |
| 2、有多个 Store | 2、只有一个 Store |
| 3、所有 Store 都互不影响且是平级的 | 3、带有分层 reducer 的单一 Store |
| 4、有单一调度器 | 4、没有调度器的概念 |
| 5、React 组件订阅 store | 5、容器组件是有联系的 |
| 6、状态是可变的 | 6、状态是不可改变的 |



### [8、React 中的箭头函数是什么？怎么用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#8react-中的箭头函数是什么怎么用)  


箭头函数（=>）是用于编写函数表达式的简短语法。这些函数允许正确绑定组件的上下文，因为在 ES6 中默认下不能使用自动绑定。使用高阶函数时，箭头函数非常有用。

```
//General way
render() {
    return(
        <MyInput onChange = {this.handleChange.bind(this) } />
    );
}
//With Arrow Function
render() {
    return(
        <MyInput onChange = { (e)=>this.handleOnChange(e) } />
    );
}
```


### [9、redux的工作流程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#9redux的工作流程)  


首先，我们看下几个核心概念：

**1、** Store：保存数据的地方，你可以把它看成一个容器，整个应用只能有一个Store。

**2、** State：Store对象包含所有数据，如果想得到某个时点的数据，就要对Store生成快照，这种时点的数据集合，就叫做State。

**3、** Action：State的变化，会导致View的变化。但是，用户接触不到State，只能接触到View。所以，State的变化必须是View导致的。Action就是View发出的通知，表示State应该要发生变化了。

**4、** Action Creator：View要发送多少种消息，就会有多少种Action。如果都手写，会很麻烦，所以我们定义一个函数来生成Action，这个函数就叫Action Creator。

**5、** Reducer：Store收到Action以后，必须给出一个新的State，这样View才会发生变化。这种State的计算过程就叫做Reducer。Reducer是一个函数，它接受Action和当前State作为参数，返回一个新的State。

**6、** dispatch：是View发出Action的唯一方法。

**然后我们过下整个工作流程：**

**1、** 首先，用户（通过View）发出Action，发出方式就用到了dispatch方法。

**2、** 然后，Store自动调用Reducer，并且传入两个参数：当前State和收到的Action，Reducer会返回新的State

**3、** State一旦有变化，Store就会调用监听函数，来更新View。

到这儿为止，一次用户交互流程结束。可以看到，在整个流程中数据都是单向流动的，这种方式保证了流程的清晰。

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/4/30/1939/39/97_11.png#alt=97%5C_11.png)


### [10、Vue事件绑定原理说一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#10vue事件绑定原理说一下)  


原生事件绑定是通过`addEventListener`绑定给真实元素的，组件事件绑定是通过Vue自定义的`$on`实现的。

**面试官：(这小子基础还可以，接下来我得上上难度了)**


### [11、React Router与常规路由有何不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#11react-router与常规路由有何不同)  

### [12、你对 Time Slice的理解?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#12你对-time-slice的理解)  

### [13、React有哪些限制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#13react有哪些限制)  

### [14、mixin、hoc、render props、react-hooks的优劣如何？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#14mixinhocrender-propsreact-hooks的优劣如何)  

### [15、setState到底是异步还是同步?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#15setstate到底是异步还是同步)  

### [16、概述下 React 中的事件处理逻辑](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#16概述下-react-中的事件处理逻辑)  

### [17、React与Vue的相似之处](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#17react与vue的相似之处)  

### [18、在生命周期中的哪一步你应该发起 AJAX 请求](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#18在生命周期中的哪一步你应该发起-ajax-请求)  

### [19、列出 Redux 的组件。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#19列出-redux-的组件。)  

### [20、React组件生命周期的阶段是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#20react组件生命周期的阶段是什么)  

### [21、redux有什么缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#21redux有什么缺点)  

### [22、React如何进行组件/逻辑复用?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#22react如何进行组件/逻辑复用)  

### [23、createElement 与 cloneElement 的区别是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#23createelement-与-cloneelement-的区别是什么)  

### [24、hash路由和history路由实现原理说一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#24hash路由和history路由实现原理说一下)  

### [25、Redux三大原则](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#25redux三大原则)  

### [26、React 中 refs 的作用是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#26react-中-refs-的作用是什么)  

### [27、shouldComponentUpdate 的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#27shouldcomponentupdate-的作用)  

### [28、你是如何理解fiber的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题汇总及答案（2021年React面试题及答案大全）.md#28你是如何理解fiber的)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
