# React面试题附答案（2021年React面试题及答案大汇总）

React面试题及答案【最新版】React高级面试题大全(2021版)，发现网上很多React面试题及答案整理都没有答案，所以花了很长时间搜集，本套React面试题大全，React面试题大汇总，有大量经典的React面试题以及答案，包含React语言常见面试题、React工程师高级面试题及一些大厂React开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套React面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个React面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、你都做过哪些Vue的性能优化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#1你都做过哪些vue的性能优化)  


**编码阶段**

**1、** 尽量减少data中的数据，data中的数据都会增加getter和setter，会收集对应的watcher

**2、** v-if和v-for不能连用

**3、** 如果需要使用v-for给每项元素绑定事件时使用事件代理

**4、** SPA 页面采用keep-alive缓存组件

**5、** 在更多的情况下，使用v-if替代v-show

**6、** key保证唯一

**7、** 使用路由懒加载、异步组件

**8、** 防抖、节流

**9、** 第三方模块按需导入

**10、** 长列表滚动到可视区域动态加载

**11、** 图片懒加载

**SEO优化**

**1、** 预渲染

**2、** 服务端渲染SSR

**打包优化**

**1、** 压缩代码

**2、** Tree Shaking/Scope Hoisting

**3、** 使用cdn加载第三方模块

**4、** 多线程打包happypack

**5、** splitChunks抽离公共文件

**6、** sourceMap优化

**用户体验**

**1、** 骨架屏

**2、** PWA

还可以使用缓存(客户端缓存、服务端缓存)优化、服务端开启gzip压缩等。

(优化是个大工程，会涉及很多方面，这里申请另开一个专栏)


### [2、redux的工作流程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#2redux的工作流程)  


首先，我们看下几个核心概念：

Store：保存数据的地方，你可以把它看成一个容器，整个应用只能有一个Store。

State：Store对象包含所有数据，如果想得到某个时点的数据，就要对Store生成快照，这种时点的数据集合，就叫做State。

Action：State的变化，会导致View的变化。但是，用户接触不到State，只能接触到View。所以，State的变化必须是View导致的。Action就是View发出的通知，表示State应该要发生变化了。

Action Creator：View要发送多少种消息，就会有多少种Action。如果都手写，会很麻烦，所以我们定义一个函数来生成Action，这个函数就叫Action Creator。

Reducer：Store收到Action以后，必须给出一个新的State，这样View才会发生变化。这种State的计算过程就叫做Reducer。Reducer是一个函数，它接受Action和当前State作为参数，返回一个新的State。

dispatch：是View发出Action的唯一方法。 然后我们过下整个工作流程：

首先，用户（通过View）发出Action，发出方式就用到了dispatch方法。

然后，Store自动调用Reducer，并且传入两个参数：当前State和收到的Action，Reducer会返回新的State

State一旦有变化，Store就会调用监听函数，来更新View。 到这儿为止，一次用户交互流程结束。可以看到，在整个流程中数据都是单向流动的，这种方式保证了流程的清晰。


### [3、为什么浏览器无法读取JSX？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#3为什么浏览器无法读取jsx)  


浏览器只能处理 JavaScript 对象，而不能读取常规 JavaScript 对象中的 JSX。所以为了使浏览器能够读取 JSX，首先，需要用像 Babel 这样的 JSX 转换器将 JSX 文件转换为 JavaScript 对象，然后再将其传给浏览器。


### [4、react旧版生命周期函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#4react旧版生命周期函数)  


初始化阶段

**1、** `getDefaultProps`:获取实例的默认属性

**2、** `getInitialState`:获取每个实例的初始化状态

**3、** `componentWillMount`组件即将被装载、渲染到页面上

**4、** `render`:组件在这里生成虚拟的DOM节点

**5、** `componentDidMount`:组件真正在被装载之后

运行中状态

**1、** `componentWillReceiveProps`:组件将要接收到属性的时候调用

**2、** `shouldComponentUpdate`:组件接受到新属性或者新状态的时候可以返回 `false`接收数据后不更新阻止 `render`调用后面的函数不会被继续执行了

**3、** `componentWillUpdate`:组件即将更新不能修改属性和状态

**4、** `render`:组件重新描绘

**5、** `componentDidUpdate`:组件已经更新


### [5、说说你用react有什么坑点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#5说说你用react有什么坑点)  


**1、** JSX做表达式判断时候需要强转为boolean类型

如果不使用 !!b 进行强转数据类型会在页面里面输出 0。

```
render() {
  const b = 0;
  return <div>
    {
      !!b && <div>这是一段文本</div>
    }
  </div>
}
```

**1、** 尽量不要在 `componentWillReviceProps` 里使用 `setState`如果一定要使用那么需要判断结束条件不然会出现无限重渲染导致页面崩溃

**2、** 给组件添加ref时候尽量不要使用匿名函数因为当组件更新的时候匿名函数会被当做新的`prop`处理让`ref`属性接受到新函数的时候`react`内部会先清空`ref`也就是会以`null`为回调参数先执行一次`ref`这个`props`然后在以该组件的实例执行一次`ref`所以用匿名函数做ref的时候有的时候去`ref`赋值后的属性会取到`null`

**3、** 遍历子节点的时候不要用 index 作为组件的 key 进行传入


### [6、如何模块化 React 中的代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#6如何模块化-react-中的代码)  


可以使用 export 和 import 属性来模块化代码。它们有助于在不同的文件中单独编写组件。

```
//ChildComponent.jsx
export default class ChildComponent extends React.Component {
    render() {
        return(
              <div>
                  <h1>This is a child component</h1>
              </div>
        );
    }
}

//ParentComponent.jsx
import ChildComponent from './childcomponent.js';
class ParentComponent extends React.Component {
    render() {
        return(
             <div>
                <App />
             </div>
        );
    }
}
```


### [7、Vue模版编译原理知道吗，能简单说一下吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#7vue模版编译原理知道吗能简单说一下吗)  


简单说，Vue的编译过程就是将`template`转化为`render`函数的过程。会经历以下阶段：

**1、** 生成AST树

2、优化

**3、** codegen

首先解析模版，生成`AST语法树`(一种用JavaScript对象的形式来描述整个模板)。 使用大量的正则表达式对模板进行解析，遇到标签、文本的时候都会执行对应的钩子进行相关处理。

Vue的数据是响应式的，但其实模板中并不是所有的数据都是响应式的。有一些数据首次渲染后就不会再变化，对应的DOM也不会变化。那么优化过程就是深度遍历AST树，按照相关条件对树节点进行标记。这些被标记的节点(静态节点)我们就可以`跳过对它们的比对`，对运行时的模板起到很大的优化作用。

编译的最后一步是`将优化后的AST树转换为可执行的代码`。


### [8、说一下v-model的原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#8说一下v-model的原理)  


`v-model`本质就是一个语法糖，可以看成是`value + input`方法的语法糖。 可以通过model属性的`prop`和`event`属性来进行自定义。原生的v-model，会根据标签的不同生成不同的事件和属性。


### [9、销毁阶段](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#9销毁阶段)  


componentWillUnmount:组件即将销毁新版生命周期

在新版本中React 官方对生命周期有了新的 变动建议:

**1、** 使用getDerivedStateFromProps替换componentWillMount

**2、** 使用getSnapshotBeforeUpdate替换componentWillUpdate

**3、** 避免使用componentWillReceiveProps

其实该变动的原因正是由于上述提到的 `Fiber`。首先从上面我们知道 `React` 可以分成 `reconciliation` 与 `commit`两个阶段对应的生命周期如下:

**1、** reconciliation

**2、** componentWillMount

**3、** componentWillReceiveProps

**4、** shouldComponentUpdate

**5、** componentWillUpdate

**6、** commit

**7、** componentDidMoun

**8、** componentDidUpdate

**9、** componentWillUnmount

在 `Fiber` 中`reconciliation` 阶段进行了任务分割涉及到 暂停 和 重启因此可能会导致 `reconciliation` 中的生命周期函数在一次更新渲染循环中被 多次调用 的情况产生一些意外错误

新版的建议生命周期如下:

```
class Component extends React.Component {
  // 替换 `componentWillReceiveProps` 
  // 初始化和 update 时被调用
  // 静态函数无法使用 this
  static getDerivedStateFromProps(nextProps, prevState) {}
  
  // 判断是否需要更新组件
  // 可以用于组件性能优化
  shouldComponentUpdate(nextProps, nextState) {}
  
  // 组件被挂载后触发
  componentDidMount() {}
  
  // 替换 componentWillUpdate
  // 可以在更新之前获取最新 dom 数据
  getSnapshotBeforeUpdate() {}
  
  // 组件更新后调用
  componentDidUpdate() {}
  
  // 组件即将销毁
  componentWillUnmount() {}
  
  // 组件已销毁
  componentDidUnMount() {}
}
```

使用建议:

**1、** 在 `constructor`初始化 `state`

**2、** 在 `componentDidMount`中进行事件监听并在 `componentWillUnmount`中解绑事件

**3、** 在 `componentDidMount`中进行数据的请求而不是在 `componentWillMount`

**4、** 需要根据 `props` 更新 `state` 时使用 `getDerivedStateFromProps(nextProps, prevState)`

**5、** 旧 `props` 需要自己存储以便比较

```
public static getDerivedStateFromProps(nextProps, prevState) {
 // 当新 props 中的 data 发生变化时同步更新到 state 上
 if (nextProps.data !== prevState.data) {
  return {
   data: nextProps.data
  }
 } else {
  return null1
 }
}
```

可以在componentDidUpdate监听 props 或者 state 的变化例如:

```
componentDidUpdate(prevProps) {
 // 当 id 发生变化时重新获取数据
 if (this.props.id !== prevProps.id) {
  this.fetchData(this.props.id);
 }
}
```

在`componentDidUpdate使用`setState`时必须加条件否则将进入死循环

`shouldComponentUpdate`: 默认每次调用`setState`一定会最终走到 `diff` 阶段但可以通过`shouldComponentUpdate`的生命钩子返回false来直接阻止后面的逻辑执行通常是用于做条件渲染优化渲染的性能。


### [10、pureComponent和FunctionComponent区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#10purecomponent和functioncomponent区别)  


`PureComponent`和`Component`完全相同但是在`shouldComponentUpdate`实现中`PureComponent`使用了`props`和`state`的浅比较。主要作用是用来提高某些特定场景的性能


### [11、为什么要用redux](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#11为什么要用redux)  

### [12、Redux实现原理解析](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#12redux实现原理解析)  

### [13、在合成事件 和 生命周期钩子(除 componentDidUpdate) 中setState是"异步"的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#13在合成事件-和-生命周期钩子除-componentdidupdate-中setstate是"异步"的)  

### [14、connect原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#14connect原理)  

### [15、React中的合成事件是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#15react中的合成事件是什么)  

### [16、如何在React中创建一个事件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#16如何在react中创建一个事件)  

### [17、区分有状态和无状态组件。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#17区分有状态和无状态组件。)  

### [18、虚拟DOM实现原理?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#18虚拟dom实现原理)  

### [19、什么是纯组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#19什么是纯组件)  

### [20、我现在有一个button要用react在上面绑定点击事件要怎么做](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#20我现在有一个button要用react在上面绑定点击事件要怎么做)  

### [21、区分状态和 props](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#21区分状态和-props)  

### [22、具体实现步骤如下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#22具体实现步骤如下)  

### [23、列出 React Router 的优点。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#23列出-react-router-的优点。)  

### [24、MVC框架的主要问题是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#24mvc框架的主要问题是什么)  

### [25、你理解“在React中，一切都是组件”这句话。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#25你理解“在react中一切都是组件这句话。)  

### [26、什么是 Props?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#26什么是-props)  

### [27、解释一下 Flux](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#27解释一下-flux)  

### [28、diff算法?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React面试题附答案（2021年React面试题及答案大汇总）.md#28diff算法)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
