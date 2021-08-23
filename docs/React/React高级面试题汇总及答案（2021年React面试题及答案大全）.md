# React高级面试题汇总及答案（2021年React面试题及答案大全）

React面试题及答案【最新版】React高级面试题大全(2021版)，发现网上很多React面试题及答案整理都没有答案，所以花了很长时间搜集，本套React面试题大全，React面试题大汇总，有大量经典的React面试题以及答案，包含React语言常见面试题、React工程师高级面试题及一些大厂React开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套React面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个React面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、你对 Time Slice的理解?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#1你对-time-slice的理解)  


**时间分片**

**1、** React 在渲染render的时候不会阻塞现在的线程

**2、** 如果你的设备足够快你会感觉渲染是同步的

**3、** 如果你设备非常慢你会感觉还算是灵敏的

**4、** 虽然是异步渲染但是你将会看到完整的渲染而不是一个组件一行行的渲染出来

**5、** 同样书写组件的方式

**6、** 也就是说这是React背后在做的事情对于我们开发者来说是透明的具体是什么样的效果呢


### [2、React 中 keys的作用是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#2react-中-keys的作用是什么)  


`Keys`是 `React` 用于追踪哪些列表中元素被修改、被添加或者被移除的辅助标识

在开发过程中我们需要保证某个元素的 `key` 在其同级元素中具有唯一性。在 `React Diff` 算法中`React` 会借助元素的 `Key` 值来判断该元素是新近创建的还是被移动而来的元素从而减少不必要的元素重渲染。此外React 还需要借助 `Key` 值来判断元素与本地状态的关联关系因此我们绝不可忽视转换函数中 `Key` 的重要性


### [3、keep-alive了解吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#3keep-alive了解吗)  


**1、** `keep-alive`可以实现组件缓存，当组件切换时不会对当前组件进行卸载。

**2、** 常用的两个属性`include/exclude`，允许组件有条件的进行缓存。

**3、** 两个生命周期`activated/deactivated`，用来得知当前组件是否处于活跃状态。

**4、** keep-alive的中还运用了`LRU(Least Recently Used)`算法。

**5、** （又是数据结构与算法，原来算法在前端也有这么多的应用）


### [4、setState到底是异步还是同步?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#4setstate到底是异步还是同步)  


先给出答案: 有时表现出异步,有时表现出同步

**1、** `setState`只在合成事件和钩子函数中是“异步”的在原生事件和`setTimeout` 中都是同步的

**2、** `setState` 的“异步”并不是说内部由异步代码实现其实本身执行的过程和代码都是同步的只是合成事件和钩子函数的调用顺序在更新之前导致在合成事件和钩子函数中没法立马拿到更新后的值形成了所谓的“异步”当然可以通过第二个参数`setState(partialState, callback)`中的`callback`拿到更新后的结果

**3、** `setState` 的批量更新优化也是建立在“异步”合成事件、钩子函数之上的在原生事件和`setTimeout` 中不会批量更新在“异步”中如果对同一个值进行多次`setState`的批量更新策略会对其进行覆盖取最后一次的执行如果是同时`setState`多个不同的值在更新时会对其进行合并批量更新


### [5、react-router里的标签和`<a>`标签有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#5react-router里的标签和<a>标签有什么区别)  


对比`<a>`,`Link`组件避免了不必要的重渲染


### [6、组件中的data为什么是一个函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#6组件中的data为什么是一个函数)  


一个组件被复用多次的话，也就会创建多个实例。本质上，`这些实例用的都是同一个构造函数`。如果data是对象的话，对象属于引用类型，会影响到所有的实例。所以为了保证组件不同的实例之间data不冲突，data必须是一个函数。


### [7、SSR了解吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#7ssr了解吗)  


SSR也就是服务端渲染，`也就是将Vue在客户端把标签渲染成HTML的工作放在服务端完成，然后再把html直接返回给客户端`。

SSR有着更好的SEO、并且首屏加载速度更快等优点。不过它也有一些缺点，比如我们的开发条件会受到限制，服务器端渲染只支持`beforeCreate`和`created`两个钩子，当我们需要一些外部扩展库时需要特殊处理，服务端渲染应用程序也需要处于Node.js的运行环境。还有就是服务器会有更大的负载需求。


### [8、React 中 key 的重要性是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#8react-中-key-的重要性是什么)  


key 用于识别唯一的 Virtual DOM 元素及其驱动 UI 的相应数据。它们通过回收 DOM 中当前所有的元素来帮助 React 优化渲染。这些 key 必须是唯一的数字或字符串，React 只是重新排序元素而不是重新渲染它们。这可以提高应用程序的性能。


### [9、再说一下虚拟Dom以及key属性的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#9再说一下虚拟dom以及key属性的作用)  


由于在浏览器中操作DOM是很昂贵的。频繁的操作DOM，会产生一定的性能问题。这就是虚拟Dom的`产生原因`。

Vue2的Virtual DOM借鉴了开源库`snabbdom`的实现。

`Virtual DOM本质就是用一个原生的JS对象去描述一个DOM节点。是对真实DOM的一层抽象。`(也就是源码中的VNode类，它定义在src/core/vdom/vnode.js中。)

VirtualDOM映射到真实DOM要经历VNode的create、diff、patch等阶段。

**「key的作用是尽可能的复用 DOM 元素。」**

新旧 children 中的节点只有顺序是不同的时候，最佳的操作应该是通过移动元素的位置来达到更新的目的。

需要在新旧 children 的节点中保存映射关系，以便能够在旧 children 的节点中找到可复用的节点。key也就是children中节点的唯一标识。


### [10、HOC(高阶组件)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#10hoc高阶组件)  


`HOC(Higher Order Componennt)` 是在 `React` 机制下社区形成的一种组件模式在很多第三方开源库中表现强大。

简述:

**1、** 高阶组件不是组件是 增强函数可以输入一个元组件返回出一个新的增强组件

**2、** 高阶组件的主要作用是 代码复用操作 状态和参数用法:

属性代理 (Props Proxy): 返回出一个组件它基于被包裹组件进行 功能增强默认参数: 可以为组件包裹一层默认参数

```
function proxyHoc(Comp) {
 return class extends React.Component {
  render() {
   const newProps = {
    name: 'tayde',
    age: 1,
   }
   return <Comp {...this.props} {...newProps} />
  }
 }
}
```

提取状态: 可以通过 `props` 将被包裹组件中的 `state` 依赖外层例如用于转换受控组件:

```
function withOnChange(Comp) {
 return class extends React.Component {
  constructor(props) {
   super(props)
   this.state = {
    name: '',
   }
  }
  onChangeName = () => {
   this.setState({
    name: 'dongdong',
   })
  }
  render() {
   const newProps = {
    value: this.state.name,
    onChange: this.onChangeName,
   }
   return <Comp {...this.props} {...newProps} />
  }
 }
}
```

使用姿势如下这样就能非常快速的将一个 `Input` 组件转化成受控组件。

```
const NameInput = props => (<input name="name" {...props} />)
export default withOnChange(NameInput)
```

包裹组件: 可以为被包裹元素进行一层包装

```
function withMask(Comp) {
  return class extends React.Component {
   render() {
   return (
     <div>
     <Comp {...this.props}/>
     <div style={{
       width: '100%',
       height: '100%',
       backgroundColor: 'rgba(0, 0, 0, .6)',
     }} 
    </div>
   )
   }
  }
}
```

反向继承 (`Inheritance Inversion`): 返回出一个组件继承于被包裹组件常用于以下操作

```
function IIHoc(Comp) {
    return class extends Comp {
        render() {
            return super.render();
        }
    };
}
```

渲染劫持 (Render Highjacking)

条件渲染: 根据条件渲染不同的组件

```
function withLoading(Comp) {
  return class extends Comp {
    render() {
      if(this.props.isLoading) {
          return <Loading />
      } else {
          return super.render()
      }
    }
  };
}
```

可以直接修改被包裹组件渲染出的 React 元素树

操作状态 (`Operate State`): 可以直接通过 `this.state` 获取到被包裹组件的状态并进行操作。但这样的操作容易使 `state` 变得难以追踪不易维护谨慎使用。

应用场景:

权限控制通过抽象逻辑统一对页面进行权限判断按不同的条件进行页面渲染:

```
function withAdminAuth(WrappedComponent) {
  return class extends React.Component {
   constructor(props){
    super(props)
    this.state = {
        isAdmin: false,
    }
   } 
   async componentWillMount() {
     const currentRole = await getCurrentUserRole();
     this.setState({
         isAdmin: currentRole === 'Admin',
     });
   }
   render() {
     if (this.state.isAdmin) {
       return <Comp {...this.props} />;
     } else {
       return (<div>您没有权限查看该页面请联系管理员</div>);
     }
   }
  };
}
```

性能监控包裹组件的生命周期进行统一埋点:

```
function withTiming(Comp) {
    return class extends Comp {
        constructor(props) {
            super(props);
            this.start = Date.now();
            this.end = 0;
        }
        componentDidMount() {
            super.componentDidMount && super.componentDidMount();
            this.end = Date.now();
            console.log(`${WrappedComponent.name} 组件渲染时间为 ${this.end - this.start} ms`);
        }
        render() {
            return super.render();
        }
    };
}
```

代码复用可以将重复的逻辑进行抽象。

**使用注意:**

**1、** 纯函数: 增强函数应为纯函数避免侵入修改元组件

**2、** 避免用法污染: 理想状态下应透传元组件的无关参数与事件尽量保证用法不变

**3、** 命名空间: 为 `HOC`增加特异性的组件名称这样能便于开发调试和查找问题

**4、** 引用传递: 如果需要传递元组件的 `refs` 引用可以使用 `React.forwardRef`

**5、** 静态方法: 元组件上的静态方法并无法被自动传出会导致业务层无法调用解决:

**6、** 函数导出

**7、** 静态方法赋值

**8、** 重新渲染: 由于增强函数每次调用是返回一个新组件因此如果在 `Render`中使用增强函数就会导致每次都重新渲染整个 `HOC`而且之前的状态会丢失


### [11、Redux设计理念](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#11redux设计理念)  

### [12、React组件通信如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#12react组件通信如何实现)  

### [13、react hooks它带来了那些便利](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#13react-hooks它带来了那些便利)  

### [14、Vue2.x和Vue3.x渲染器的diff算法分别说一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#14vue2x和vue3x渲染器的diff算法分别说一下)  

### [15、react组件的划分业务组件技术组件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#15react组件的划分业务组件技术组件)  

### [16、什么是高阶组件(HOC)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#16什么是高阶组件hoc)  

### [17、如何更新组件的状态？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#17如何更新组件的状态)  

### [18、为什么虚拟dom会提高性能](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#18为什么虚拟dom会提高性能)  

### [19、解释 Reducer 的作用。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#19解释-reducer-的作用。)  

### [20、如何将两个或多个组件嵌入到一个组件中？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#20如何将两个或多个组件嵌入到一个组件中)  

### [21、列出一些应该使用 Refs 的情况。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#21列出一些应该使用-refs-的情况。)  

### [22、Vue中组件生命周期调用顺序说一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#22vue中组件生命周期调用顺序说一下)  

### [23、redux中如何进行异步操作?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#23redux中如何进行异步操作)  

### [24、列出React的一些主要优点。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#24列出react的一些主要优点。)  

### [25、React有哪些优化性能是手段?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#25react有哪些优化性能是手段)  

### [26、React实现的移动应用中如果出现卡顿有哪些可以考虑的优化方案](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#26react实现的移动应用中如果出现卡顿有哪些可以考虑的优化方案)  

### [27、详细解释 React 组件的生命周期方法。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/React/React高级面试题汇总及答案（2021年React面试题及答案大全）.md#27详细解释-react-组件的生命周期方法。)  





