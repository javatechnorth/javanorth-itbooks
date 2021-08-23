# Vue面试题附答案（2021年Vue面试题及答案大汇总）

Vue面试题及答案【最新版】Vue高级面试题大全(2021版)，发现网上很多Vue面试题及答案整理都没有答案，所以花了很长时间搜集，本套Vue面试题大全，Vue面试题大汇总，有大量经典的Vue面试题以及答案，包含Vue语言常见面试题、Vue工程师高级面试题及一些大厂Vue开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Vue面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Vue面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何将文件的所有导出作为一个对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#1如何将文件的所有导出作为一个对象)  


import * as objectname from ‘./file.js’用于将所有导出的成员导入为对象。 可以使用对象的点（.）运算符来访问导出的变量或方法，如：

```
objectname.member1;
objectname.member2;
objectname.memberfunc();
```


### [2、Vue.js 中的声明式渲染是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#2vuejs-中的声明式渲染是什么)  


Vue.js 使渲染数据变得容易，并隐藏了内部实现。例如下面的代码：

**HTML**

```
<div id=”app”></div>
```

**JavaScript**

```
const greeting = “Hello there!”;
const appDiv = document.getElementById(“app”);
appDiv.innerText = greeting;
```

上面的代码段将在 ID 为 “app” 的 div 中显示短语 “Hello there！”。代码包含实现结果所需的所有步骤。首先选择 ID 为 “app” 的 DOM 元素，然后用 innerText 属性手动设置 div 的内容。

现在，让我们看看在 Vue 中是怎么做的。

**Template**

```
<div id=”app”>{{ greeting }}</div>
```

**App**

```
new Vue({
    data: {
       greeting: ‘Hello There!’
    },
   el: ‘#app’
});
```

我们在 Vue 程序中创建了一个名为 “greeting” 的数据属性，但是只需要在 div 中用 mustache 语法输入 “greeting” 即可，而不必关心内部实现。我们声明了 “greeting” 变量，其余的由 Vue 完成。这就是声明式渲染的样子。 Vue 隐藏并管理内部信息。


### [3、vue的keep-alive的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#3vue的keep-alive的理解)  


keep-alive 是Vue内置的一个组件，可以使被包含的组件保留状态，或避免重新渲染，页面第一次进入，钩子的触发顺序:created-> mounted-> activated，退出时触发 deactivated ,当再次进入（前进或者后退）时，只触发activated事件挂载的方法等，只执行一次的放在 mounted 中；组件每次进去执行的方法放在 activated 中；其有几个属性如下：

**1、** include - 字符串或正则表达式，只有名称匹配的组件会被缓存

**2、** exclude - 字符串或正则表达式，任何名称匹配的组件都不会被缓存

**3、** include 和 exclude 的属性允许组件有条件地缓存。二者都可以用“，”分隔字符串、正则表达式、数组。当使用正则或者是数组时，要记得使用v-bind 。

```
<!-- 逗号分隔字符串，只有组件a与b被缓存。-->
<keep-alive include="a,b">
  <component></component>
</keep-alive>

<!-- 正则表达式 (需要使用 v-bind，符合匹配规则的都会被缓存) -->
<keep-alive :include="/a|b/">
  <component></component>
</keep-alive>

<!-- Array (需要使用 v-bind，被包含的都会被缓存) -->
<keep-alive :include="['a', 'b']">
  <component></component>
</keep-alive>
```


### [4、你是怎么认识vuex的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#4你是怎么认识vuex的)  


vuex可以理解为一种开发模式或框架。比如PHP有thinkphp，java有spring等。

通过状态（数据源）集中管理驱动组件的变化（好比spring的IOC容器对bean进行集中管理）。

应用级的状态集中放在store中； 改变状态的方式是提交mutations，这是个同步的事物； 异步逻辑应该封装在action中。


### [5、聊聊你对Vue.js的template编译的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#5聊聊你对vuejs的template编译的理解)  


简而言之，就是先转化成AST树，再得到的render函数返回VNode（Vue的虚拟DOM节点）

**详情步骤：**

**1、** 首先，通过compile编译器把template编译成AST语法树（abstract syntax tree 即 源代码的抽象语法结构的树状表现形式），compile是createCompiler的返回值，createCompiler是用以创建编译器的。另外compile还负责合并option。

**2、** 然后，AST会经过generate（将AST语法树转化成render funtion字符串的过程）得到render函数，render的返回值是VNode，VNode是Vue的虚拟DOM节点，里面有（标签名、子节点、文本等等）


### [6、引进组件的步骤](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#6引进组件的步骤)  


在template中引入组件；

在script的第一行用import引入路径；

用component中写上组件名称。


### [7、SPA首屏加载慢如何解决](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#7spa首屏加载慢如何解决)  


安装动态懒加载所需插件；使用CDN资源。


### [8、解释 JS 中的函数提升](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#8解释-js-中的函数提升)  


JS允许将声明移动到顶部的默认行为称为提升。JS中创建函数的两种方法是函数声明和函数表达式。

**函数声明**

具有特定参数的函数称为函数声明，在JS中创建变量称为声明。如：

```
hoisted(); // logs "foo"

function hoisted() {
  console.log('foo');
}
```

**函数表达式**

当使用表达式创建函数时，称为函数表达式。如：

```
notHoisted(); // TypeError: notHoisted is not a function

var notHoisted = function() {
   console.log('bar');
};
```


### [9、keep-alive了解吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#9keep-alive了解吗)  


`keep-alive`可以实现组件缓存，当组件切换时不会对当前组件进行卸载。

常用的两个属性`include/exclude`，允许组件有条件的进行缓存。

两个生命周期`activated/deactivated`，用来得知当前组件是否处于活跃状态。

keep-alive的中还运用了`LRU(Least Recently Used)`算法。

（又是数据结构与算法，原来算法在前端也有这么多的应用）


### [10、Vue模版编译原理知道吗，能简单说一下吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#10vue模版编译原理知道吗能简单说一下吗)  


简单说，Vue的编译过程就是将`template`转化为`render`函数的过程。会经历以下阶段：

**1、** 生成AST树

2、优化

**3、** codegen

首先解析模版，生成`AST语法树`(一种用JavaScript对象的形式来描述整个模板)。 使用大量的正则表达式对模板进行解析，遇到标签、文本的时候都会执行对应的钩子进行相关处理。

Vue的数据是响应式的，但其实模板中并不是所有的数据都是响应式的。有一些数据首次渲染后就不会再变化，对应的DOM也不会变化。那么优化过程就是深度遍历AST树，按照相关条件对树节点进行标记。这些被标记的节点(静态节点)我们就可以`跳过对它们的比对`，对运行时的模板起到很大的优化作用。

编译的最后一步是`将优化后的AST树转换为可执行的代码`。


### [11、Vue中双向数据绑定是如何实现的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#11vue中双向数据绑定是如何实现的)  

### [12、JS中的substr()和substring()函数有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#12js中的substr和substring函数有什么区别)  

### [13、如何在现有函数中添加新属性](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#13如何在现有函数中添加新属性)  

### [14、$$root、$$refs、$parent的使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#14$$root$$refs$parent的使用)  

### [15、$nextTick的使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#15$nexttick的使用)  

### [16、assets和static的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#16assets和static的区别)  

### [17、导航钩子有哪些？它们有哪些参数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#17导航钩子有哪些它们有哪些参数)  

### [18、单页面应用和多页面应用区别及优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#18单页面应用和多页面应用区别及优缺点)  

### [19、如何将 JS 日期转换为ISO标准](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#19如何将-js-日期转换为iso标准)  

### [20、再说一下虚拟Dom以及key属性的作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#20再说一下虚拟dom以及key属性的作用)  

### [21、JS 中的主要有哪几类错误](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#21js-中的主要有哪几类错误)  

### [22、SEO优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#22seo优化)  

### [23、分别简述computed和watch的使用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#23分别简述computed和watch的使用场景)  

### [24、列出一些单元测试框架](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#24列出一些单元测试框架)  

### [25、vue-loader是什么？使用它的用途有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#25vue-loader是什么使用它的用途有哪些)  

### [26、子组件更新过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#26子组件更新过程)  

### [27、data为什么是一个函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#27data为什么是一个函数)  

### [28、$nextTick的使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue面试题附答案（2021年Vue面试题及答案大汇总）.md#28$nexttick的使用)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
