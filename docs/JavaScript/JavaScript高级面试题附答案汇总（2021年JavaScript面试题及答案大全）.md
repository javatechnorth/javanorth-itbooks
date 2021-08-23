# JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）

JavaScript面试题及答案【最新版】JavaScript高级面试题大全(2021版)，发现网上很多JavaScript面试题及答案整理都没有答案，所以花了很长时间搜集，本套JavaScript面试题大全，JavaScript面试题大汇总，有大量经典的JavaScript面试题以及答案，包含JavaScript语言常见面试题、JavaScript工程师高级面试题及一些大厂JavaScript开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套JavaScript面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个JavaScript面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、ajax中 get 和 post 有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#1ajax中-get-和-post-有什么区别)  


get和post都是数据提交的方式。

get的数据是通过网址问号后边拼接的字符串进行传递的。post是通过一个HTTP包体进行传递数据的。

get的传输量是有限制的，post是没有限制的。

get的安全性可能没有post高，所以我们一般用get来获取数据，post一般用来修改数据。


### [2、Function.prototype.bind 的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#2functionprototypebind-的用途是什么)  


`bind()` 方法创建一个新的函数，在 `bind()` 被调用时，这个新函数的 `this` 被指定为 `bind()` 的第一个参数，而其余参数将作为新函数的参数，供调用时使用。

```
import React from 'react';
class MyComponent extends React.Component {
   constructor(props){
      super(props); 
      this.state = {
         value : ""
      }  
      this.handleChange = this.handleChange.bind(this); 
      // 将 “handleChange” 方法绑定到 “MyComponent” 组件
   }

   handleChange(e){
     //do something amazing here
   }

   render(){
    return (
      <>
        <input type={this.props.type}
                value={this.state.value}
             onChange={this.handleChange}                      
          />
      </>
    )
   }
}
```


### [3、一个页面从输入 URL 到页面加载显示完成，这个过程中都发生了什么？（流程说的越详细越好）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#3一个页面从输入-url-到页面加载显示完成这个过程中都发生了什么流程说的越详细越好)  


**1、** 查找浏览器缓存

**2、** DNS解析、查找该域名对应的IP地址、重定向（301）、发出第二个GET请求

**3、** 进行HTTP协议会话

**4、** 客户端发送报头(请求报头)

**5、** 服务器回馈报头(响应报头)

**6、** html文档开始下载

**7、** 文档树建立，根据标记请求所需指定MIME类型的文件

**8、** 文件显示

**浏览器这边做的工作大致分为以下几步：**

**1、** 加载：根据请求的URL进行域名解析，向服务器发起请求，接收文件（HTML、JS、CSS、图象等）。

**2、** 解析：对加载到的资源（HTML、JS、CSS等）进行语法解析，建议相应的内部数据结构（比如HTML的DOM树，JS的（对象）属性表，CSS的样式规则等等）


### [4、DOM事件模型和事件流？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#4dom事件模型和事件流)  


DOM事件模型包括事件捕获(自上而下触发)与事件冒泡(自下而上触发，ie用的就是冒泡)机制。基于事件冒泡机制可以完成事件代理。

> 事件捕获


![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/b3d7c68a2b2740e7b784f25c2db3d14d~tplv-k3u1fbpfcp-zoom-1.image#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

> 事件冒泡


![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f354c39ed3e9462b9b735297fd031c0b~tplv-k3u1fbpfcp-zoom-1.image#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

DOM事件流包括三个阶段事件捕获阶段、处于目标阶段、事件冒泡阶段。


### [5、什么是 ES6 模块？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#5什么是-es6-模块)  


**模块**使我们能够将代码基础分割成多个文件，以获得更高的可维护性，并且避免将所有代码放在一个大文件中。在 ES6 支持模块之前，有两个流行的模块。

-
**CommonJS-Node.js**

-
AMD（异步模块定义）-**浏览器**


基本上，使用模块的方式很简单，`import`用于从另一个文件中获取功能或几个功能或值，同时`export`用于从文件中公开功能或几个功能或值。

**导出**

使用 ES5 (CommonJS)

```
// 使用 ES5 CommonJS - helpers.js
exports.isNull = function (val) {
  return val === null;
}

exports.isUndefined = function (val) {
  return val === undefined;
}

exports.isNullOrUndefined = function (val) {
  return exports.isNull(val) || exports.isUndefined(val);
}
```

使用 ES6 模块

```
使用 ES6 Modules - helpers.js
export function isNull(val){
  return val === null;
}

export function isUndefined(val) {
  return val === undefined;
}

export function isNullOrUndefined(val) {
  return isNull(val) || isUndefined(val);
}
```

在另一个文件中导入函数

```
// 使用 ES5 (CommonJS) - index.js
const helpers = require('./helpers.js'); // helpers is an object
const isNull = helpers.isNull;
const isUndefined = helpers.isUndefined;
const isNullOrUndefined = helpers.isNullOrUndefined;

// or if your environment supports Destructuring
const { isNull, isUndefined, isNullOrUndefined } = require('./helpers.js');
-------------------------------------------------------

// ES6 Modules - index.js
import * as helpers from './helpers.js'; // helpers is an object

// or 

import { isNull, isUndefined, isNullOrUndefined as isValid } from './helpers.js';

// using "as" for renaming named exports
```

**在文件中导出单个功能或默认导出**

使用 ES5 (CommonJS)

```
// 使用 ES5 (CommonJS) - index.js
class Helpers {
  static isNull(val) {
    return val === null;
  }

  static isUndefined(val) {
    return val === undefined;
  }

  static isNullOrUndefined(val) {
    return this.isNull(val) || this.isUndefined(val);
  }
}

module.exports = Helpers;
```

使用ES6 Modules

```
// 使用 ES6 Modules - helpers.js
class Helpers {
  static isNull(val) {
    return val === null;
  }

  static isUndefined(val) {
    return val === undefined;
  }

  static isNullOrUndefined(val) {
    return this.isNull(val) || this.isUndefined(val);
  }
}

export default Helpers
```

从另一个文件导入单个功能

使用ES5 (CommonJS)

`// 使用 ES5 (CommonJS) - index.js const Helpers = require('./helpers.js'); console.log(Helpers.isNull(null));`

使用 ES6 Modules

`import Helpers from '.helpers.js' console.log(Helpers.isNull(null));`


### [6、基本数据类型和引用数据类型有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#6基本数据类型和引用数据类型有什么区别)  


**两者作为函数的参数进行传递时：**

**1、** 基本数据类型传入的是数据的副本，原数据的更改不会影响传入后的数据。

**2、** 引用数据类型传入的是数据的引用地址，原数据的更改会影响传入后的数据。

**两者在内存中的存储位置：**

**1、** 基本数据类型存储在栈中。

**2、** 引用数据类型在栈中存储了指针，该指针指向的数据实体存储在堆中。


### [7、什么是闭包? 堆栈溢出有什么区别？ 内存泄漏? 那些操作会造成内存泄漏？怎么样防止内存泄漏？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#7什么是闭包-堆栈溢出有什么区别-内存泄漏-那些操作会造成内存泄漏怎么样防止内存泄漏)  


**闭包：**

**1、** 就是能够读取其他函数内部变量的函数。

**2、** 堆栈溢出：就是不顾堆栈中分配的局部数据块大小，向该数据块写入了过多的数据，导致数据越界，结果覆盖了别的数据。经常会在递归中发生。

**3、** 内存泄露是指：用动态存储分配函数内存空间，在使用完毕后未释放，导致一直占据该内存单元。直到程序结束。指任何对象在您不再拥有或需要它之后仍然存在。

**造成内存泄漏：**

setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。

闭包、控制台日志、循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）

防止内存泄露：

**1、** 不要动态绑定事件；

**2、** 不要在动态添加，或者会被动态移除的dom上绑事件，用事件冒泡在父容器监听事件；

**3、** 如果要违反上面的原则，必须提供destroy方法，保证移除dom后事件也被移除，这点可以参考Backbone的源代码，做的比较好；

**4、** 单例化，少创建dom，少绑事件。


### [8、有哪些数据类型？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#8有哪些数据类型)  


根据 JavaScript 中的变量类型传递方式，分为基本数据类型和引用数据类型两大类七种。

基本数据类型包括Undefined、Null、Boolean、Number、String、Symbol (ES6新增)六种。 引用数据类型只有Object一种，主要包括对象、数组和函数。

**判断数据类型采用`typeof`操作符，有两种语法：**

```
typeof 123;//语法一

const FG = 123;
typeof FG;//语法二

typeof(null) //返回 object;
null == undefined //返回true，因为undefined派生自null;
null === undefined //返回false。
```


### [9、什么是构造函数？与普通函数有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#9什么是构造函数与普通函数有什么区别)  


构造函数：是一种特殊的方法、主要用来创建对象时初始化对象，总与new运算符一起使用，创建对象的语句中构造函数的函数名必须与类名完全相同。

与普通函数相比只能由new关键字调用，构造函数是类的标示


### [10、同步和异步的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#10同步和异步的区别)  


javascript同步表示sync，指：代码依次执行 javascript异步表示async，指：代码执行不按顺序，‘跳过’执行，待其他某些代码执行完后再来执行，成为异步。


### [11、用过哪些设计模式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#11用过哪些设计模式)  

### [12、说说你对AMD和Commonjs的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#12说说你对和commonjs的理解)  

### [13、与深拷贝有何区别？如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#13与深拷贝有何区别如何实现)  

### [14、commonjs?requirejs?AMD|CMD|UMD?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#14commonjsrequirejs||)  

### [15、JavaScript 中的虚值是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#15javascript-中的虚值是什么)  

### [16、如何对登录的账号密码进行加密?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#16如何对登录的账号密码进行加密)  

### [17、JavaScript有几种类型的值？，你能画一下他们的内存图吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#17javascript有几种类型的值你能画一下他们的内存图吗)  

### [18、简述一下你理解的面向对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#18简述一下你理解的面向对象)  

### [19、为什么在调用这个函数时，代码中的`b`会变成一个全局变量?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#19为什么在调用这个函数时代码中的b会变成一个全局变量)  

### [20、JavaScript 中 `this` 值是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#20javascript-中-this-值是什么)  

### [21、有哪些方法可以处理 JS 中的异步代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#21有哪些方法可以处理-js-中的异步代码)  

### [22、什么是高阶函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#22什么是高阶函数)  

### [23、JavaScript原型，原型链 ? 有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#23javascript原型原型链--有什么特点)  

### [24、jQuery与jQuery UI 有啥区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#24jquery与jquery-ui-有啥区别)  

### [25、js的几种继承方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#25js的几种继承方式)  

### [26、常见web安全及防护原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#26常见web安全及防护原理)  

### [27、vue、react、angular](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#27vuereactangular)  

### [28、异步编程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#28异步编程)  

### [29、如何知道是否在元素中使用了`event.preventDefault()`方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#29如何知道是否在元素中使用了eventpreventdefault方法)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
