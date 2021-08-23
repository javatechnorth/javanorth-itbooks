# JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）

JavaScript面试题及答案【最新版】JavaScript高级面试题大全(2021版)，发现网上很多JavaScript面试题及答案整理都没有答案，所以花了很长时间搜集，本套JavaScript面试题大全，JavaScript面试题大汇总，有大量经典的JavaScript面试题以及答案，包含JavaScript语言常见面试题、JavaScript工程师高级面试题及一些大厂JavaScript开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套JavaScript面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个JavaScript面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、怎么理解Promise对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#1怎么理解promise对象)  


**`Promise`对象有如下两个特点：**

**1、** 对象的状态不受外界影响。`Promise`对象共有三种状态`pending`、`fulfilled`、`rejected`。状态值只会被异步结果决定，其他任何操作无法改变。

**2、** 状态一旦成型，就不会再变，且任何时候都可得到这个结果。状态值会由`pending`变为`fulfilled`或`rejected`，这时即为`resolved`。

**Promise的缺点有如下三个缺点：**

**1、** `Promise`一旦执行便无法被取消；

**2、** 不可设置回调函数，其内部发生的错误无法捕获；

**3、** 当处于`pending`状态时，无法得知其具体发展到了哪个阶段。

**`Pomise`中常用的方法有：**

**1、** `Promise.prototype.then()`：`Promise`实例的状态发生改变时，会调用`then`内部的回调函数。`then`方法接受两个参数（第一个为`resolved`状态时时执行的回调，第一个为`rejected`状态时时执行的回调）

**2、** `Promise.prototype.catch()`：`.then(null, rejection)`或`.then(undefined, rejection)`的别名，用于指定发生错误时的回调函数。


### [2、什么是事件传播?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#2什么是事件传播)  


当**事件**发生在**DOM**元素上时，该**事件**并不完全发生在那个元素上。在**“冒泡阶段”**中，事件冒泡或向上传播至父级，祖父母，祖父母或父级，直到到达`window`为止；而在**“捕获阶段”**中，事件从`window`开始向下触发元素 事件或`event.target`。

**事件传播有三个阶段：**

**1、** 捕获阶段 事件从 `window` 开始，然后向下到每个元素，直到到达目标元素。

**2、** 目标阶段 事件已达到目标元素。

**3、** 冒泡阶段 事件从目标元素冒泡，然后上升到每个元素，直到到达 `window`。


### [3、几种基本数据类型?复杂数据类型?值类型和引用数据类型?堆栈数据结构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#3几种基本数据类型复杂数据类型值类型和引用数据类型堆栈数据结构)  


**1、** 基本数据类型：Undefined、Null、Boolean、Number、String

**2、** 值类型：数值、布尔值、null、undefined。

**3、** 引用类型：对象、数组、函数。

**4、** 堆栈数据结构：是一种支持后进先出(LIFO)的集合,即后被插入的数据,先被取出!

**5、** js数组中提供了以下几个方法可以让我们很方便实现堆栈：

**6、** shift:从数组中把第一个元素删除，并返回这个元素的值。

**7、** unshift: 在数组的开头添加一个或更多元素，并返回新的长度

**8、** push:在数组的中末尾添加元素，并返回新的长度

**9、** pop:从数组中把最后一个元素删除，并返回这个元素的值。


### [4、说说你对promise的了解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#4说说你对promise的了解)  


依照 `Promise/A+` 的定义，`Promise` 有四种状态：

**1、** `pending:` 初始状态, 非 `fulfilled` 或 `rejected.`

**2、** `fulfilled:` 成功的操作.

**3、** `rejected:` 失败的操作.

**4、** `settled: Promise`已被`fulfilled`或`rejected`，且不是`pending`

另外， `fulfilled`与 `rejected`一起合称 `settled`

`Promise` 对象用来进行延迟(`deferred`) 和异步(`asynchronous`) 计算

**Promise 的构造函数**

构造一个 `Promise`，最基本的用法如下：

```
var promise = new Promise(function(resolve, reject) {

        if (...) {  // succeed

            resolve(result);

        } else {   // fails

            reject(Error(errMessage));

        }
    });
```

`Promise` 实例拥有 `then` 方法（具有 `then` 方法的对象，通常被称为`thenable`）。它的使用方法如下：

```
promise.then(onFulfilled, onRejected)
```

接收两个函数作为参数，一个在 `fulfilled` 的时候被调用，一个在`rejected`的时候被调用，接收参数就是 `future`，`onFulfilled` 对应`resolve`, `onRejected`对应 `reject`


### [5、Jq中如何实现多库并存?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#5jq中如何实现多库并存)  


Noconfict 多库共存就是“$ ”符号的冲突。

**方法一**：

利用jQuery的实用函数$$.noConflict();这个函数归还$$的名称控制权给另一个库，因此可以在页面上使用其他库。这时，我们可以用"jQuery "这个名称调用jQuery的功能。 $.noConflict();

```
jQuery('\#id').hide();
.....
//或者给jQuery一个别名
var $j=jQuery
$j('\#id').hide();
```

**方法二**： `(function($)\{\})(jQuery)`

**方法三**： `jQuery(function($)\{\})`

通过传递一个函数作为jQuery的参数，因此把这个函数声明为就绪函数。 我们声明$为就绪函数的参数，因为jQuery总是吧jQuery对象的引用作为第一个参数传递，所以就保证了函数的执行。


### [6、除了jsonp 还有什么跨域方式###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#6除了jsonp-还有什么跨域方式###)  


javascript跨域有两种情况：

**1、** 基于同一父域的子域之间，如： [http://a.c.com](http://link.zhihu.com/?target=http%3A//a.c.com)和 [http://b.c.com](http://link.zhihu.com/?target=http%3A//b.c.com)

**2、** 基于不同的父域之间，如： [http://www.a.com](http://link.zhihu.com/?target=http%3A//www.a.com)和 [http://www.b.com](http://link.zhihu.com/?target=http%3A//www.b.com)

**3、** 端口的不同，如： [http://www.a.com:8080](http://link.zhihu.com/?target=http%3A//www.a.com%3A8080)和 [http://www.a.com:8088](http://link.zhihu.com/?target=http%3A//www.a.com%3A8088)

**4、** 协议不同，如： [http://www.a.com](http://link.zhihu.com/?target=http%3A//www.a.com)和 [https://www.a.com](http://link.zhihu.com/?target=https%3A//www.a.com)

**对于情况3和4，需要通过后台proxy来解决，具体方式如下：**

a、在发起方的域下创建proxy程序

b、发起方的js调用本域下的proxy程序

c、proxy将请求发送给接收方并获取相应数据

d、proxy将获得的数据返回给发起方的js

代码和ajax调用一致，其实这种方式就是通过ajax进行调用的

而情况1和2除了通过后台proxy这种方式外，还可以有多种办法来解决：

**1、** document.domain+iframe（只能解决情况1）：

a、在发起方页面和接收方页面设置document.domain，并将值设为父域的主域名(window.location.hostname)

b、在发起方页面创建一个隐藏的iframe，iframe的源是接收方页面

c、根据浏览器的不同，通过iframe.contentDocument || iframe.contentWindow.document来获得接收方页面的内容

d、通过获得的接收方页面的内容来与接收方进行交互

这种方法有个缺点，就是当一个域被攻击时，另一个域会有安全漏洞出现。


### [7、`in` 运算符和 `Object.hasOwnProperty` 方法有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#7in-运算符和-objecthasownproperty-方法有什么区别)  


**hasOwnPropert方法**

`hasOwnPropert()`方法返回值是一个布尔值，指示对象自身属性中是否具有指定的属性，因此这个方法会忽略掉那些从原型链上继承到的属性。

看下面的例子：

```
Object.prototype.phone= '15345025546';

let obj = {
  name: 'kyle',
  age: '28'
}
console.log(obj.hasOwnProperty('phone')) // false
console.log(obj.hasOwnProperty('name')) // true
```

可以看到，如果在函数原型上定义一个变量`phone`，`hasOwnProperty`方法会直接忽略掉。

**in 运算符**

如果指定的属性在指定的对象或其原型链中，则`in` 运算符返回`true`。

还是用上面的例子来演示：

`console.log('phone' in obj) // true`

可以看到`in`运算符会检查它或者其原型链是否包含具有指定名称的属性。


### [8、手动实现`Array.prototype.filter`方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#8手动实现arrayprototypefilter方法)  


`filter()` 方法创建一个新数组, 其包含通过所提供函数实现的测试的所有元素。

```
function filter(arr, filterCallback) {
  // 首先，检查传递的参数是否正确。
  if (!Array.isArray(arr) || !arr.length || typeof filterCallback !== 'function') 
  {
    return [];
  } else {
    let result = [];
     // 每次调用此函数时，我们都会创建一个 result 数组
     // 因为我们不想改变原始数组。
    for (let i = 0, len = arr.length; i < len; i++) {
      // 检查 filterCallback 的返回值是否是真值
      if (filterCallback(arr[i], i, arr)) { 
      // 如果条件为真，则将数组元素 push 到 result 中
        result.push(arr[i]);
      }
    }
    return result; // return the result array
  }
}
```


### [9、压缩合并目的？http请求的优化方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#9压缩合并目的http请求的优化方式)  


1）Web性能优化最佳实践中最重要的一条是减少HTTP请求。而减少HTTP请求的最主要的方式就是，合并并压缩JavaScript和CSS文件。

CSS Sprites（CSS精灵）：把全站的图标都放在一个图像文件中，然后用CSS的background-image和background-position属性定位来显示其中的一小部分。

合并脚本和样式表; 图片地图：利用image map标签定义一个客户端图像映射，（图像映射指带有可点击区域的一幅图像）具体看： [http://club.topsage.com/thread-2527479-1-1.html](http://link.zhihu.com/?target=http%3A//club.topsage.com/thread-2527479-1-1.html)

图片js/css等静态资源放在静态服务器或CDN服时，尽量采用不用的域名，这样能防止cookie不会互相污染，减少每次请求的往返数据。

css替代图片, 缓存一些数据

少用location.reload()：使用location.reload() 会刷新页面，刷新页面时页面所有资源 (css，js，img等) 会重新请求服务器。建议使用location.href="当前页url" 代替location.reload() ，使用location.href 浏览器会读取本地缓存资源。


### [10、jquery和zepto有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#10jquery和zepto有什么区别)  


**1、** 针对移动端程序，Zepto有一些基本的触摸事件可以用来做触摸屏交互（tap事件、swipe事件），Zepto是不支持IE浏览器的，这不是Zepto的开发者Thomas Fucks在跨浏览器问题上犯了迷糊，而是经过了认真考虑后为了降低文件尺寸而做出的决定，就像jQuery的团队在2.0版中不再支持旧版的IE（6 7 8）一样。因为Zepto使用jQuery句法，所以它在文档中建议把jQuery作为IE上的后备库。那样程序仍能在IE中，而其他浏览器则能享受到Zepto在文件大小上的优势，然而它们两个的API不是完全兼容的，所以使用这种方法时一定要小心，并要做充分的测试。

**2、** Dom操作的区别：添加id时jQuery不会生效而Zepto会生效。

**3、** zepto主要用在移动设备上，只支持较新的浏览器，好处是代码量比较小，性能也较好。

jquery主要是兼容性好，可以跑在各种pc，移动上，好处是兼容各种浏览器，缺点是代码量大，同时考虑兼容，性能也不够好。


### [11、arguments 的对象是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#11arguments-的对象是什么)  

### [12、在jq中 mouseover mouseenter mouseout mouseleave 和 hover有什么关联?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#12在jq中-mouseover-mouseenter-mouseout-mouseleave-和-hover有什么关联)  

### [13、什么是闭包？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#13什么是闭包)  

### [14、什么是模板字符串？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#14什么是模板字符串)  

### [15、如何清除一个定时器?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#15如何清除一个定时器)  

### [16、作用域和执行上下文的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#16作用域和执行上下文的区别是什么)  

### [17、什么是跨域？怎么解决跨域问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#17什么是跨域怎么解决跨域问题)  

### [18、对象的 prototype(原型) 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#18对象的-prototype原型-是什么)  

### [19、隐式和显式转换有什么区别）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#19隐式和显式转换有什么区别)  

### [20、XML和JSON的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#20xml和json的区别)  

### [21、如何解决跨域问题?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#21如何解决跨域问题)  

### [22、如何理解同步和异步？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#22如何理解同步和异步)  

### [23、JS是如何实现异步的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#23js是如何实现异步的)  

### [24、什么是回调函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#24什么是回调函数)  

### [25、开发时如何对项目进行管理?gulp?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#25开发时如何对项目进行管理gulp)  

### [26、'use strict' 是干嘛用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#26'use-strict'-是干嘛用的)  

### [27、谈谈你对webpack的看法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#27谈谈你对webpack的看法)  

### [28、Function.prototype.apply 方法的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#28functionprototypeapply-方法的用途是什么)  

### [29、eval是做什么的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#29eval是做什么的)  





