# Vue面试题带答案（2021年Vue面试题及答案大汇总）

Vue面试题及答案【最新版】Vue高级面试题大全(2021版)，发现网上很多Vue面试题及答案整理都没有答案，所以花了很长时间搜集，本套Vue面试题大全，Vue面试题大汇总，有大量经典的Vue面试题以及答案，包含Vue语言常见面试题、Vue工程师高级面试题及一些大厂Vue开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Vue面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Vue面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、vue中transition的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#1vue中transition的理解)  


定义transition时需要设置对应的name，具体语法为：需要动画的内容或者组件或者页面

过渡动画主要包含6个class，分别为：

**1、** v-enter：定义元素进入过渡的初始状态，在元素插入前生效，插入后一帧删除，

**2、** v-enter-active：在元素插入前生效，在动画完成后删除，

**3、** v-enter-to：在元素插入后一帧生效，在动画完成后删除，

**4、** v-leave：离开过渡的初始状态，在元素离开时生效，下一帧删除

**5、** v-leave-active：在离开过渡时生效，在动画完成后删除

**6、** v-leave-to：离开过渡结束状态，在离开过渡下一帧生效，在动画完成后删除

v会转化为对应的transition的name值

**1、** 当然我们也可以自定义这六个class 可以直接在transition中设置对应的属性为对应的class名称，属性有：enter-class，enter-active-class，enter-to-class，leave-class，leave-active-class，leave-to-class

**2、** 在同时使用过渡和css动画的时候 可以设置type属性来制定vue内部机制监听transitioned或者animationed事件来完成过渡还是动画的监听

**3、** 如果需要设置对应的过渡时间，可以直接设置属性duration，可以直接接收一个数字（单位为毫秒），也可以接收一个对象{enter:1000,leave:300}

**4、** 也可以设置过渡的钩子函数，具体有：before-enter，enter，after-enter，enter-cancelled，before-leave，leave，after-leave，leave-cancelled


### [2、JS中如何将页面重定向到另一个页面？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#2js中如何将页面重定向到另一个页面)  


使用 location.href：window.location.href

=“https://www.onlineinterviewquestions.com/” 使用 location.replace： window.location.replace(" [https://www.onlineinterviewquestions.com/;](https://www.onlineinterviewquestions.com/;)");


### [3、vue的自定义指令？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#3vue的自定义指令)  


自定义指令分为全局指令和组件指令，其中全局指令需要使用directive来进行定义，组件指令需要使用directives来进行定义，具体定义方法同过滤器filter或者其他生命周期，具体使用方法如下：

全局自定义指令 directive(name,{})，其中name表示定义的指令名称（定义指令的时候不需要带v-，但是在调用的时候需要哦带v-），第二个参数是一个对象，对象中包括五个自定义组件的钩子函数，具体包括：

**bind函数：**只调用一次，指令第一次绑定在元素上调用，即初始化调用一次，

**inserted函数：**并绑定元素插入父级元素（即new vue中el绑定的元素）时调用（此时父级元素不一定转化为了dom）

**update函数：**在元素发生更新时就会调用，可以通过比较新旧的值来进行逻辑处理

**componentUpdated函数：**元素更新完成后触发一次

**unbind函数：**在元素所在的模板删除的时候就触发一次

钩子函数对应的参数el,binding,vnode,oldnode,具体参数讲解如下：

**a、el指令所绑定的元素 可以直接操组dom元素**

**b、binding一个对象，具体包括以下属性：**

**1、** name：定义的指令名称 不包括v-

**2、** value：指令的绑定值，如果绑定的是一个计算式，value为对应计算结果

**3、** oldvalue：指令绑定元素的前一个值，只对update和componentUpdated钩子函数有值

**4、** expression：指令绑定的原始值 不对值进行任何加工

**5、** arg：传递给指令的参数

**6、** modifiers：指令修饰符，如：v-focus.show.async 则接收的modifiers为｛show：true，async：true｝

**c、vnode：vue编译生成的虚拟dom**

**d、oldVnode：上一个vnode，只在update和componentUpdated钩子函数中有效**

如果不需要其他钩子函数，可以直接简写为：directive(“focus”,function(el,binding){})


### [4、axios+tp5进阶中，调用axios.post(‘api/user’)是进行的什么操作？axios.put(‘api/user/8′)呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#4axios+tp5进阶中调用axiospost‘api/user’是进行的什么操作axiosput‘api/user/8′呢)  


跨域，添加用户操作，更新操作。


### [5、Vue里面router-link在电脑上有用，在安卓上没反应怎么解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#5vue里面router-link在电脑上有用在安卓上没反应怎么解决)  


Vue路由在Android机上有问题，babel问题，安装babel polypill插件解决。


### [6、简单描述每个周期具体适合哪些场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#6简单描述每个周期具体适合哪些场景)  


**1、** 生命周期钩子的一些使用方法： beforecreate : 可以在这加个loading事件，在加载实例时触发 created : 初始化完成时的事件写在这里，如在这结束loading事件，异步请求也适宜在这里调用 mounted : 挂载元素，获取到DOM节点 updated : 如果对数据统一处理，在这里写上相应函数 beforeDestroy : 可以做一个确认停止事件的确认框 nextTick : 更新数据后立即操作dom

**2、** arguments是一个伪数组，没有遍历接口，不能遍历


### [7、vue与angular的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#7vue与angular的区别)  


**1、** vue仅仅是mvvm中的view层，只是一个如jquery般的工具库，而不是框架，而angular而是mvvm框架。

**2、** vue的双向邦定是基于ES5 中的 3.getter/setter来实现的，而angular而是由自己实现一套模版编译规则，需要进行所谓的“脏”检查，vue则不需要。因此，vue在性能上更高效，但是代价是对于ie9以下的浏览器无法支持。

**4、** vue需要提供一个el对象进行实例化，后续的所有作用范围也是在el对象之下，而angular而是整个html页面。一个页面，可以有多个vue实例，而angular好像不是这么玩的。

**5、** vue真的很容易上手，学习成本相对低，不过可以参考的资料不是很丰富，官方文档比较简单，缺少全面的使用案例。高级的用法，需要自己去研究源码，至少目前是这样。


### [8、vuex的使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#8vuex的使用)  


Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化，具体包括：

**1、** state：Vuex 使用单一状态树,即每个应用将仅仅包含一个store 实例，但单一状态树和模块化并不冲突。存放的数据状态，不可以直接修改里面的数据。

**2、** getter：state的计算属性，类似vue的计算属性，主要用来过滤一些数据。

**3、** action：actions可以理解为通过将mutations里面处里数据的方法变成可异步的处理数据的方法，简单的说就是异步操作数据。view 层通过 store.dispath 来分发 action。可以异步函数调用

**4、** mutation：mutations定义的方法动态修改Vuex 的 store 中的状态或数据

**5、** modules：项目特别复杂的时候，可以让每一个模块拥有自己的state、mutation、action、getters,使得结构非常清晰，方便管理。


### [9、JS中的Array.splice()和Array.slice()方法有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#9js中的arraysplice和arrayslice方法有什么区别)  


话不多说，来看第一个例子：

```
var arr=[0,1,2,3,4,5,6,7,8,9];//设置一个数组
console.log(arr.slice(2,7));//2,3,4,5,6
console.log(arr.splice(2,7));//2,3,4,5,6,7,8
//由此我们简单推测数量两个函数参数的意义,
slice(start,end)第一个参数表示开始位置,第二个表示截取到的位置(不包含该位置)
splice(start,length)第一个参数开始位置,第二个参数截取长度
```

接着看第二个：

```
var x=y=[0,1,2,3,4,5,6,7,8,9]
console.log(x.slice(2,5));//2,3,4
console.log(x);[0,1,2,3,4,5,6,7,8,9]原数组并未改变
//接下来用同样方式测试splice
console.log(y.splice(2,5));//2,3,4,5,6
console.log(y);//[0,1,7,8,9]显示原数组中的数值被剔除掉了
```

slice和splice虽然都是对于数组对象进行截取,但是二者还是存在明显区别,函数参数上slice和splice第一个参数都是截取开始位置,slice第二个参数是截取的结束位置(不包含),而splice第二个参数(表示这个从开始位置截取的长度),slice不会对原数组产生变化,而splice会直接剔除原数组中的截取数据!


### [10、请说下封装 vue 组件的过程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#10请说下封装-vue-组件的过程)  


首先，组件可以提升整个项目的开发效率。能够把页面抽象成多个相对独立的模块，解决了我们传统项目开发：效率低、难维护、复用性等问题。

然后，使用Vue.extend方法创建一个组件，然后使用Vue.component方法注册组件。子组件需要数据，可以在props中接受定义。而子组件修改好数据后，想把数据传递给父组件。可以采用emit方法。


### [11、vue-router 有哪几种导航钩子?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#11vue-router-有哪几种导航钩子)  

### [12、computed和watch的用法和区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#12computed和watch的用法和区别)  

### [13、vue父组件向子组件传递数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#13vue父组件向子组件传递数据)  

### [14、SSR了解吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#14ssr了解吗)  

### [15、Vue中组件生命周期调用顺序说一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#15vue中组件生命周期调用顺序说一下)  

### [16、如何获取dom?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#16如何获取dom)  

### [17、嵌套路由怎么定义？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#17嵌套路由怎么定义)  

### [18、active-class是哪个组件的属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#18active-class是哪个组件的属性)  

### [19、v-show和v-if指令的共同点和不同点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#19v-show和v-if指令的共同点和不同点)  

### [20、mvvm框架是什么？它和其它框架（jquery）的区别是什么？哪些场景适合？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#20mvvm框架是什么它和其它框架jquery的区别是什么哪些场景适合)  

### [21、什么是计算属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#21什么是计算属性)  

### [22、解释JS中的MUL函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#22解释js中的mul函数)  

### [23、vue-router是什么？它有哪些组件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#23vue-router是什么它有哪些组件)  

### [24、vue的diff算法理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#24vue的diff算法理解)  

### [25、axios是什么？怎么使用？描述使用它实现登录功能的流程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#25axios是什么怎么使用描述使用它实现登录功能的流程)  

### [26、什么是观察者？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#26什么是观察者)  

### [27、列出JS中的一些设计模式:](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#27列出js中的一些设计模式:)  

### [28、你用哪个指令遍历对象的属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题带答案（2021年Vue面试题及答案大汇总）.md#28你用哪个指令遍历对象的属性)  





