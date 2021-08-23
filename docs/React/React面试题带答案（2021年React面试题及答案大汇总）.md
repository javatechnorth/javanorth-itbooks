# React面试题带答案（2021年React面试题及答案大汇总）

React面试题及答案【最新版】React高级面试题大全(2021版)，发现网上很多React面试题及答案整理都没有答案，所以花了很长时间搜集，本套React面试题大全，React面试题大汇总，有大量经典的React面试题以及答案，包含React语言常见面试题、React工程师高级面试题及一些大厂React开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套React面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个React面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、与 ES5 相比，React 的 ES6 语法有何不同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#1与-es5-相比react-的-es6-语法有何不同)  


以下语法是 ES5 与 ES6 中的区别：

**1、**  require 与 import

```
// ES5
var React = require('react');

// ES6
import React from 'react';
```

**1、**  export 与 exports

```
// ES5
module.exports = Component;

// ES6
export default Component;
```

**1、**  component 和 function

```
// ES5
var MyComponent = React.createClass({
    render: function() {
        return
            <h3>Hello Edureka!</h3>;
    }
});

// ES6
class MyComponent extends React.Component {
    render() {
        return
            <h3>Hello Edureka!</h3>;
    }
}
```

**1、**  props

```
// ES5
var App = React.createClass({
    propTypes: { name: React.PropTypes.string },
    render: function() {
        return
            <h3>Hello, {this.props.name}!</h3>;
    }
});

// ES6
class App extends React.Component {
    render() {
        return
            <h3>Hello, {this.props.name}!</h3>;
    }
}
```

**1、**  state

```
// ES5
var App = React.createClass({
    getInitialState: function() {
        return { name: 'world' };
    },
    render: function() {
        return
            <h3>Hello, {this.state.name}!</h3>;
    }
});

// ES6
class App extends React.Component {
    constructor() {
        super();
        this.state = { name: 'world' };
    }
    render() {
        return
            <h3>Hello, {this.state.name}!</h3>;
    }
}
```


### [2、React最新的生命周期是怎样的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#2react最新的生命周期是怎样的)  


React 16之后有三个生命周期被废弃(但并未删除)

**1、** componentWillMount

**2、** componentWillReceiveProps

**3、** componentWillUpdate

官方计划在17版本完全删除这三个函数，只保留UNSAVE_前缀的三个函数，目的是为了向下兼容，但是对于开发者而言应该尽量避免使用他们，而是使用新增的生命周期函数替代它们

目前React 16.8 +的生命周期分为三个阶段,分别是挂载阶段、更新阶段、卸载阶段

**挂载阶段:**

**1、** constructor: 构造函数，最先被执行,我们通常在构造函数里初始化state对象或者给自定义方法绑定this

**2、** getDerivedStateFromProps: `static getDerivedStateFromProps(nextProps, prevState)`,这是个静态方法,当我们接收到新的属性想去修改我们state，可以使用getDerivedStateFromProps

**3、** render: render函数是纯函数，只返回需要渲染的东西，不应该包含其它的业务逻辑,可以返回原生的DOM、React组件、Fragment、Portals、字符串和数字、Boolean和null等内容

**4、** componentDidMount: 组件装载之后调用，此时我们可以获取到DOM节点并操作，比如对canvas，svg的操作，服务器请求，订阅都可以写在这个里面，但是记得在componentWillUnmount中取消订阅

**更新阶段:**

**1、** getDerivedStateFromProps: 此方法在更新个挂载阶段都可能会调用

**2、** shouldComponentUpdate: `shouldComponentUpdate(nextProps, nextState)`,有两个参数nextProps和nextState，表示新的属性和变化之后的state，返回一个布尔值，true表示会触发重新渲染，false表示不会触发重新渲染，默认返回true,我们通常利用此生命周期来优化React程序性能

**3、** render: 更新阶段也会触发此生命周期

**4、** getSnapshotBeforeUpdate: `getSnapshotBeforeUpdate(prevProps, prevState)`,这个方法在render之后，componentDidUpdate之前调用，有两个参数prevProps和prevState，表示之前的属性和之前的state，这个函数有一个返回值，会作为第三个参数传给componentDidUpdate，如果你不想要返回值，可以返回null，此生命周期必须与componentDidUpdate搭配使用

**5、** componentDidUpdate: `componentDidUpdate(prevProps, prevState, snapshot)`,该方法在getSnapshotBeforeUpdate方法之后被调用，有三个参数prevProps，prevState，snapshot，表示之前的props，之前的state，和snapshot。第三个参数是getSnapshotBeforeUpdate返回的,如果触发某些回调函数时需要用到 DOM 元素的状态，则将对比或计算的过程迁移至 getSnapshotBeforeUpdate，然后在 componentDidUpdate 中统一触发回调或更新状态。

**卸载阶段:**

componentWillUnmount: 当我们的组件被卸载或者销毁了就会调用，我们可以在这个函数里去清除一些定时器，取消网络请求，清理无效的DOM元素等垃圾清理工作

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/4/30/1939/39/97_1.png#alt=97%5C_1.png)


### [3、什么是控制组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#3什么是控制组件)  


在 HTML 中，表单元素通常维护自己的状态，并根据用户输入进行更新。当用户提交表单时，来自上述元素的值将随表单一起发送。 而 React 的工作方式则不同。包含表单的组件将跟踪其状态中的输入值，并在每次回调函数(例如onChange)触发时重新渲染组件，因为状态被更新。以这种方式由 React 控制其值的输入表单元素称为受控组件。


### [4、说一下Vue的生命周期](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#4说一下vue的生命周期)  


`beforeCreate`是new Vue()之后触发的第一个钩子，在当前阶段data、methods、computed以及watch上的数据和方法都不能被访问。

`created`在实例创建完成后发生，当前阶段已经完成了数据观测，也就是可以使用数据，更改数据，在这里更改数据不会触发updated函数。可以做一些初始数据的获取，在当前阶段无法与Dom进行交互，如果非要想，可以通过vm.$nextTick来访问Dom。

`beforeMount`发生在挂载之前，在这之前template模板已导入渲染函数编译。而当前阶段虚拟Dom已经创建完成，即将开始渲染。在此时也可以对数据进行更改，不会触发updated。

`mounted`在挂载完成后发生，在当前阶段，真实的Dom挂载完毕，数据完成双向绑定，可以访问到Dom节点，使用$refs属性对Dom进行操作。

`beforeUpdate`发生在更新之前，也就是响应式数据发生更新，虚拟dom重新渲染之前被触发，你可以在当前阶段进行更改数据，不会造成重渲染。

`updated`发生在更新完成之后，当前阶段组件Dom已完成更新。要注意的是避免在此期间更改数据，因为这可能会导致无限循环的更新。

`beforeDestroy`发生在实例销毁之前，在当前阶段实例完全可以被使用，我们可以在这时进行善后收尾工作，比如清除计时器。

`destroyed`发生在实例销毁之后，这个时候只剩下了dom空壳。组件已被拆解，数据绑定被卸除，监听被移出，子实例也统统被销毁。


### [5、再说一下Computed和Watch](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#5再说一下computed和watch)  


`Computed`本质是一个具备缓存的watcher，依赖的属性发生变化就会更新视图。 适用于计算比较消耗性能的计算场景。当表达式过于复杂时，在模板中放入过多逻辑会让模板难以维护，可以将复杂的逻辑放入计算属性中处理。

`Watch`没有缓存性，更多的是观察的作用，可以监听某些数据执行回调。当我们需要深度监听对象中的属性时，可以打开`deep：true`选项，这样便会对对象中的每一项进行监听。这样会带来性能问题，优化的话可以使用`字符串形式`监听，如果没有写到组件中，不要忘记使用`unWatch手动注销`哦。


### [6、传入 setState 函数的第二个参数的作用是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#6传入-setstate-函数的第二个参数的作用是什么)  


该函数会在 setState 函数调用完成并且组件开始重渲染的时候被调用我们可以用该函数来监听渲染是否完成

```
this.setState(
  { username: 'tylermcginnis33' },
  () => console.log('setState has finished and the component has re-rendered.')
)
this.setState((prevState, props) => {
  return {
    streak: prevState.streak + props.count
  }
})
```


### [7、redux异步中间件之间的优劣?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#7redux异步中间件之间的优劣)  


**redux-thunk优点:**

**1、** 体积小: redux-thunk的实现方式很简单,只有不到20行代码

**2、** 使用简单: redux-thunk没有引入像redux-saga或者redux-observable额外的范式,上手简单

**redux-thunk缺陷:**

**1、** 样板代码过多: 与redux本身一样,通常一个请求需要大量的代码,而且很多都是重复性质的

**2、** 耦合严重: 异步操作与redux的action偶合在一起,不方便管理

**3、** 功能孱弱: 有一些实际开发中常用的功能需要自己进行封装

**redux-saga优点:**

**1、** 异步解耦: 异步操作被被转移到单独 saga.js 中，不再是掺杂在 action.js 或 component.js 中

**2、** action摆脱thunk function: dispatch 的参数依然是一个纯粹的 action (FSA)，而不是充满 “黑魔法” thunk function

**3、** 异常处理: 受益于 generator function 的 saga 实现，代码异常/请求失败 都可以直接通过 try/catch 语法直接捕获处理

**4、** 功能强大: redux-saga提供了大量的Saga 辅助函数和Effect 创建器供开发者使用,开发者无须封装或者简单封装即可使用

**5、** 灵活: redux-saga可以将多个Saga可以串行/并行组合起来,形成一个非常实用的异步flow

**6、** 易测试，提供了各种case的测试方案，包括mock task，分支覆盖等等

**redux-saga缺陷:**

**1、** 额外的学习成本: redux-saga不仅在使用难以理解的 generator function,而且有数十个API,学习成本远超redux-thunk,最重要的是你的额外学习成本是只服务于这个库的,与redux-observable不同,redux-observable虽然也有额外学习成本但是背后是rxjs和一整套思想

**2、** 体积庞大: 体积略大,代码近2000行，min版25KB左右

**3、** 功能过剩: 实际上并发控制等功能很难用到,但是我们依然需要引入这些代码

**4、** ts支持不友好: yield无法返回TS类型

**redux-observable优点:**

**1、** 功能最强: 由于背靠rxjs这个强大的响应式编程的库,借助rxjs的操作符,你可以几乎做任何你能想到的异步处理

**2、** 背靠rxjs: 由于有rxjs的加持,如果你已经学习了rxjs,redux-observable的学习成本并不高,而且随着rxjs的升级redux-observable也会变得更强大

**redux-observable缺陷:**

学习成本奇高: 如果你不会rxjs,则需要额外学习两个复杂的库

社区一般: redux-observable的下载量只有redux-saga的1/5,社区也不够活跃,在复杂异步流中间件这个层面redux-saga仍处于领导地位



### [8、如何在 Redux 中定义 Action？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#8如何在-redux-中定义-action)  


React 中的 Action 必须具有 type 属性，该属性指示正在执行的 ACTION 的类型。必须将它们定义为字符串常量，并且还可以向其添加更多的属性。在 Redux 中，action 被名为 Action Creators 的函数所创建。以下是 Action 和Action Creator 的示例：

```
function addTodo(text) {
       return {
                type: ADD_TODO,
                 text
    }
}
```


### [9、react 的渲染过程中兄弟节点之间是怎么处理的也就是key值不一样的时候](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#9react-的渲染过程中兄弟节点之间是怎么处理的也就是key值不一样的时候)  


通常我们输出节点的时候都是`map`一个数组然后返回一个`ReactNode`为了方便`react`内部进行优化我们必须给每一个`reactNode`添加`key`这个`key prop`在设计值处不是给开发者用的而是给react用的大概的作用就是给每一个reactNode添加一个身份标识方便react进行识别在重渲染过程中如果key一样若组件属性有所变化则`react`只更新组件对应的属性没有变化则不更新如果`key`不一样则`react`先销毁该组件然后重新创建该组件


### [10、react-redux是如何工作的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#10react-redux是如何工作的)  


**1、** Provider: Provider的作用是从最外部封装了整个应用，并向connect模块传递store

**2、** connect: 负责连接React和Redux

**1、** 获取state: connect通过context获取Provider中的store，通过store.getState()获取整个store tree 上所有state

**2、** 包装原组件: 将state和action通过props的方式传入到原组件内部wrapWithConnect返回一个ReactComponent对象Connect，Connect重新render外部传入的原组件WrappedComponent，并把connect中传入的mapStateToProps, mapDispatchToProps与组件上原有的props合并后，通过属性的方式传给WrappedComponent

**3、** 监听store tree变化: connect缓存了store tree中state的状态,通过当前state状态和变更前state状态进行比较,从而确定是否调用`this.setState()`方法触发Connect及其子组件的重新渲染

![](https://gitee.com/souyunkutech/souyunku-home/raw/master/images/souyunku-web/2020/4/30/1939/39/97_12.png#alt=97%5C_12.png)


### [11、React的请求应该放在哪个生命周期中?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#11react的请求应该放在哪个生命周期中)  

### [12、为什么React Router v4中使用 switch 关键字 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#12为什么react-router-v4中使用-switch-关键字-)  

### [13、你能用HOC做什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#13你能用hoc做什么)  

### [14、Store 在 Redux 中的意义是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#14store-在-redux-中的意义是什么)  

### [15、那你能讲一讲MVVM吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#15那你能讲一讲mvvm吗)  

### [16、react性能优化是哪个周期函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#16react性能优化是哪个周期函数)  

### [17、那你知道Vue3.x响应式数据原理吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#17那你知道vue3x响应式数据原理吗)  

### [18、React的请求应该放在哪个生命周期中?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#18react的请求应该放在哪个生命周期中)  

### [19、nextTick知道吗，实现原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#19nexttick知道吗实现原理是什么)  

### [20、React组件通信如何实现?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#20react组件通信如何实现)  

### [21、react 的虚拟dom是怎么实现的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#21react-的虚拟dom是怎么实现的)  

### [22、你的接口请求一般放在哪个生命周期中？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#22你的接口请求一般放在哪个生命周期中)  

### [23、什么是Redux？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#23什么是redux)  

### [24、如何告诉 React 它应该编译生产环境版](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#24如何告诉-react-它应该编译生产环境版)  

### [25、diff算法?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#25diff算法)  

### [26、虚拟DOM的优劣如何?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#26虚拟dom的优劣如何)  

### [27、redux中间件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#27redux中间件)  

### [28、你对“单一事实来源”有什么理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题带答案（2021年React面试题及答案大汇总）.md#28你对“单一事实来源有什么理解)  





