# JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）

JavaScript面试题及答案【最新版】JavaScript高级面试题大全(2021版)，发现网上很多JavaScript面试题及答案整理都没有答案，所以花了很长时间搜集，本套JavaScript面试题大全，JavaScript面试题大汇总，有大量经典的JavaScript面试题以及答案，包含JavaScript语言常见面试题、JavaScript工程师高级面试题及一些大厂JavaScript开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套JavaScript面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个JavaScript面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、EventLoop事件循环是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#1eventloop事件循环是什么)  


js是一门单线程的需要，它的异步操作都是通过事件循环来完成的。整个事件循环大体由执行栈、消息队列和微任务队列三个部分组成。

同步代码会直接在执行栈中调用执行。

定时器中的回调会在执行栈被清空且定时达成时推入执行栈中执行。

`promise`、`async`异步函数的回调会被推入到微任务队列中，当执行栈被清空且异步操作完成时立即执行。


### [2、readystate 0~4](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#2readystate-0~4)  


0：未初始化状态：此时，已经创建了一个XMLHttpRequest对象

1： 准备发送状态：此时，已经调用了XMLHttpRequest对象的open方法，并且XMLHttpRequest对象已经准备好将一个请求发送到服务器端

2：已经发送状态：此时，已经通过send方法把一个请求发送到服务器端，但是还没有收到一个响应

3：正在接收状态：此时，已经接收到HTTP响应头部信息，但是消息体部分还没有完全接收到

4：完成响应状态：此时，已经完成了HTTP响应的接收


### [3、Jq中如何将一个jq对象转化为dom对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#3jq中如何将一个jq对象转化为dom对象)  


**方法一：**

jQuery对象是一个数据对象，可以通过[index]的方法，来得到相应的DOM对象。

如：var $$v =$$("#v") ; //jQuery对象

var v=$v[0]; //DOM对象

alert(v.checked) //检测这个checkbox是否被选中

**方法二：**

jQuery本身提供，通过.get(index)方法，得到相应的DOM对象

如：var $$v=$$("#v"); //jQuery对象

var v=$v.get(0); //DOM对象

alert(v.checked) //检测这个checkbox是否被选中


### [4、什么是 IIFE，它的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#4什么是-iife它的用途是什么)  


**IIFE**或立即调用的函数表达式是在创建或声明后将被调用或执行的函数。创建**IIFE的**语法是，将`function (){}`包裹在在括号`()`内，然后再用另一个括号`()`调用它，如：`(function(){})()`

```
(function(){
  ...
} ());

(function () {
  ...
})();

(function named(params) {
  ...
})();

(() => {

});

(function (global) {
  ...
})(window);

const utility = (function () {
  return {
    ...
  }
})
```

这些示例都是有效的**IIFE**。倒数第二个救命表明我们可以将参数传递给**IIFE**函数。最后一个示例表明，我们可以将`IIFE`的结果保存到变量中，以便稍后使用。

**IIFE**的一个主要作用是避免与全局作用域内的其他变量命名冲突或污染全局命名空间，来个例子。

`<script src="https://cdnurl.com/somelibrary.js"></script>`

假设我们引入了一个`omelibr.js`的链接，它提供了一些我们在代码中使用的全局函数，但是这个库有两个方法我们没有使用：`createGraph`和`drawGraph`，因为这些方法都有`bug`。我们想实现自己的`createGraph`和`drawGraph`方法。

解决此问题的一种方法是直接覆盖：

```
<script src="https://cdnurl.com/somelibrary.js"></script>
<script>
   function createGraph() {
      // createGraph logic here
   }
   function drawGraph() {
      // drawGraph logic here
   }
</script>
```

当我们使用这个解决方案时，我们覆盖了库提供给我们的那两个方法。

另一种方式是我们自己改名称：

```
<script src="https://cdnurl.com/somelibrary.js"></script>
<script>
   function myCreateGraph() {
      // createGraph logic here
   }
   function myDrawGraph() {
      // drawGraph logic here
   }
</script>
```

当我们使用这个解决方案时，我们把那些函数调用更改为新的函数名。

还有一种方法就是使用**IIFE**：

```
<script src="https://cdnurl.com/somelibrary.js"></script>
<script>
   const graphUtility = (function () {
      function createGraph() {
         // createGraph logic here
      }
      function drawGraph() {
         // drawGraph logic here
      }
      return {
         createGraph,
         drawGraph
      }
   })
</script>
```

在此解决方案中，我们要声明了`graphUtility` 变量，用来保存**IIFE**执行的结果，该函数返回一个包含两个方法`createGraph`和`drawGraph`的对象。

**IIFE** 还可以用来解决一个常见的面试题：

```
var li = document.querySelectorAll('.list-group > li');
for (var i = 0, len = li.length; i < len; i++) {
   li[i].addEventListener('click', function (e) {
      console.log(i);
   })
```

假设我们有一个带有`list-group`类的`ul`元素，它有`5`个`li`子元素。当我们单击单个`li`元素时，打印对应的下标值。但在此外上述代码不起作用，这里每次点击 `li` 打印 `i` 的值都是`5`，这是由于闭包的原因。

**闭包**只是函数记住其当前作用域，父函数作用域和全局作用域的变量引用的能力。当我们在全局作用域内使用`var`关键字声明变量时，就创建全局变量`i`。因此，当我们单击`li`元素时，它将打印`5`，因为这是稍后在回调函数中引用它时`i`的值。

使用 **IIFE** 可以解决此问题：

`var li = document.querySelectorAll('.list-group > li'); for (var i = 0, len = li.length; i < len; i++) { (function (currentIndex) { li[currentIndex].addEventListener('click', function (e) { console.log(currentIndex); }) })(i); }`

该解决方案之所以行的通，是因为**IIFE**会为每次迭代创建一个新的作用域，我们捕获`i`的值并将其传递给`currentIndex`参数，因此调用**IIFE**时，每次迭代的`currentIndex`值都是不同的。


### [5、js延迟加载的方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#5js延迟加载的方式有哪些)  


`defer`和`async`、动态创建`DOM`方式（用得最多）、按需异步载入`js`


### [6、那些操作会造成内存泄漏？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#6那些操作会造成内存泄漏)  


**1、** 内存泄漏指任何对象在您不再拥有或需要它之后仍然存在

**2、** `setTimeout` 的第一个参数使用字符串而非函数的话，会引发内存泄漏

**3、** 闭包、控制台日志、循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）


### [7、常见兼容性问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#7常见兼容性问题)  


**1、** `png24`位的图片在iE6浏览器上出现背景，解决方案是做成`PNG8`

**2、** 浏览器默认的`margin`和`padding`不同。解决方案是加一个全局的`*{margin:0;padding:0;}`来统一,，但是全局效率很低，一般是如下这样解决：

```
body,ul,li,ol,dl,dt,dd,form,input,h1,h2,h3,h4,h5,h6,p{
    margin:0;
    padding:0;
}
```

`IE`下,`event`对象有`x`,`y`属性,但是没有`pageX`,`pageY`属性

`Firefox`下,`event`对象有`pageX`,`pageY`属性,但是没有`x,y`属性.


### [8、什么是移动端的300ms延迟？什么是点击穿透？解决方案?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#8什么是移动端的300ms延迟什么是点击穿透解决方案)  


移动端300ms延迟：假定这么一个场景。用户在 浏览器里边点击了一个链接。由于用户可以进行双击缩放或者双击滚动的操作，当用户一次点击屏幕之后，浏览器并不能立刻判断用户是确实要打开这个链接，还是想要进行双击操作。因此，浏览器 就等待 300 毫秒，以判断用户是否再次点击了屏幕。也就是说，当我们点击页面的时候移动端浏览器并不是立即作出反应，而是会等上一小会儿才会出现点击的效果。

点击穿透：假如页面上有两个元素A和B。B元素在A元素之上。我们在B元素的touchstart事件上注册了一个回调函数，该回调函数的作用是隐藏B元素。我们发现，当我们点击B元素，B元素被隐藏了，随后，A元素触发了click事件。这是因为在移动端浏览器，事件执行的顺序是touchstart touchend click。而click事件有300ms的延迟，当touchstart事件把B元素隐藏之后，隔了300ms，浏览器触发了click事件，但是此时B元素不见了，所以该事件被派发到了A元素身上。如果A元素是一个链接，那此时页面就会意外地跳转。

300ms延迟解决方案：

(1) 禁用缩放，在html文档头部加meta标签如下：




(4) FastClick为解决移动端浏览器300毫秒延迟开发的一个轻量级的库

点击穿透解决方案：

（1）只用touch

（2）只用click

（3）tap后延迟350ms再隐藏mask

（4）pointer-events


### [9、如何合并两个数组？数组删除一个元素?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#9如何合并两个数组数组删除一个元素)  


```
//三种方法。

（1）var arr1=[1,2,3];
        var arr2=[4,5,6];
        arr1 = arr1.concat(arr2);
        console.log(arr1); 
        
（2）var arr1=[1,2,3];
        var arr2=[4,5,6];
        Array.prototype.push.apply(arr1,arr2);
        console.log(arr1);
        
（3）var arr1=[1,2,3];
    var arr2=[4,5,6];
    for (var i=0; i < arr2.length; i++) {
    arr1.push( arr2[i] );
    }
    console.log(arr1);
```


### [10、slice() splice()?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#10slice-splice)  


slice() 方法可从已有的数组中返回选定的元素。

splice() 方法向/从数组中添加/删除项目，然后返回被删除的项目。


### [11、模块化开发怎么做？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#11模块化开发怎么做)  

### [12、eval是做什么的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#12eval是做什么的)  

### [13、Object.seal 和 Object.freeze 方法之间有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#13objectseal-和-objectfreeze-方法之间有什么区别)  

### [14、如何改变this指针的指向？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#14如何改变this指针的指向)  

### [15、`Function.prototype.call` 方法的用途是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#15functionprototypecall-方法的用途是什么)  

### [16、什么是函数式编程? JavaScript 的哪些特性使其成为函数式语言的候选语言？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#16什么是函数式编程-javascript-的哪些特性使其成为函数式语言的候选语言)  

### 17、**
### [18、说几条写JavaScript的基本规范？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#18说几条写javascript的基本规范)  

### [19、介绍js的基本数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#19介绍js的基本数据类型)  

### [20、节点类型?判断当前节点类型?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#20节点类型判断当前节点类型)  

### [21、Jq中 attr 和 prop 有什么区别###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#21jq中-attr-和-prop-有什么区别###)  

### [22、那些操作会造成内存泄漏？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#22那些操作会造成内存泄漏)  

### [23、disabled readyonly?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#23disabled-readyonly)  

### [24、为什么函数被称为一等公民？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#24为什么函数被称为一等公民)  

### [25、函数fn1 函数fn2 函数fn3，如果想在三个函数都执行完成后执行某一个事件应该如何实现?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#25函数fn1-函数fn2-函数fn3如果想在三个函数都执行完成后执行某一个事件应该如何实现)  

### [26、$$.map和$$.each有什么区别###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#26$$map和$$each有什么区别###)  

### [27、javascript有哪些方法定义对象](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#27javascript有哪些方法定义对象)  

### [28、Jq中有几种选择器?分别是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#28jq中有几种选择器分别是什么)  

### [29、说出几个http协议状态码?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript高级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#29说出几个http协议状态码)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
