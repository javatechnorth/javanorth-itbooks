# JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）

JavaScript面试题及答案【最新版】JavaScript高级面试题大全(2021版)，发现网上很多JavaScript面试题及答案整理都没有答案，所以花了很长时间搜集，本套JavaScript面试题大全，JavaScript面试题大汇总，有大量经典的JavaScript面试题以及答案，包含JavaScript语言常见面试题、JavaScript工程师高级面试题及一些大厂JavaScript开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套JavaScript面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个JavaScript面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、undefined 和 null 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#1undefined-和-null-有什么区别)  


在理解 `undefined` 和 `null` 的差异之前，我们先来看看它们的相似点。

**它们都属于 JavaScript 的 7 种基本类型。**

```
let primitiveTypes = ['string','number','null','undefined','boolean','symbol', 'bigint'];
```

它们是属于 falsy 值类型，可以使用 `Boolean(value)` 或 `!!value` 将其转换为布尔值时，值为`false`。

```
console.log(!!null); // false
console.log(!!undefined); // false

console.log(Boolean(null)); // false
console.log(Boolean(undefined)); // false
```

接着来看看它们的区别。

`undefined` 是未指定特定值的变量的默认值，或者没有显式返回值的函数，如：`console.log(1)`，还包括对象中不存在的属性，这些 JS 引擎都会为其分配 `undefined` 值。

```
let _thisIsUndefined;
const doNothing = () => {};
const someObj = {
  a : "ay",
  b : "bee",
  c : "si"
};

console.log(_thisIsUndefined); // undefined
console.log(doNothing()); // undefined
console.log(someObj["d"]); // undefined
```

`null` 是『不代表任何值的值』。`null`是已明确定义给变量的值。在此示例中，当`fs.readFile`方法未引发错误时，我们将获得`null`值。

```
fs.readFile('path/to/file', (e,data) => {
   console.log(e); // 当没有错误发生时，打印 null
   if(e){
     console.log(e);
   }
   console.log(data);
 });
```

在比较`null`和`undefined`时，我们使用`==`时得到`true`，使用`===`时得到`false`:

```
console.log(null == undefined); // true
console.log(null === undefined); // false
```


### [2、什么是执行上下文和执行栈？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#2什么是执行上下文和执行栈)  


变量或函数的执行上下文，决定了它们的行为以及可以访问哪些数据。每个上下文都有一个关联的变量对象，而这个上下文中定义的所有变量和函数都存在于这个对象上(如DOM中全局上下文关联的便是`window`对象)。

每个函数调用都有自己的上下文。当代码执行流进入函数时，函数的上下文被推到一个执行栈中。在函数执行完之后，执行栈会弹出该函数上下文，在其上的所有变量和函数都会被销毁，并将控制权返还给之前的执行上下文。 JS的执行流就是通过这个执行栈进行控制的。


### [3、你觉得jQuery源码有哪些写的好的地方](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#3你觉得jquery源码有哪些写的好的地方)  


**1、** `jquery`源码封装在一个匿名函数的自执行环境中，有助于防止变量的全局污染，然后通过传入`window`对象参数，可以使`window`对象作为局部变量使用，好处是当`jquery`中访问`window`对象的时候，就不用将作用域链退回到顶层作用域了，从而可以更快的访问window对象。同样，传入`undefined`参数，可以缩短查找`undefined`时的作用域链

**2、** `jquery`将一些原型属性和方法封装在了`jquery.prototype`中，为了缩短名称，又赋值给了`jquery.fn`，这是很形象的写法

**3、** 有一些数组或对象的方法经常能使用到，`jQuery`将其保存为局部变量以提高访问速度

**4、** `jquery`实现的链式调用可以节约代码，所返回的都是同一个对象，可以提高代码效率


### [4、30.Jq中怎么样编写插件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#430jq中怎么样编写插件)  


```
//第一种是类级别的插件开发：
//1.1 添加一个新的全局函数 添加一个全局函数，我们只需如下定义： 
jQuery.foo = function() {
     alert('This is a test、This is only a test.');  };   

//1.2 增加多个全局函数 添加多个全局函数，可采用如下定义： 
jQuery.foo = function() {
       alert('This is a test、This is only a test.');  };  
jQuery.bar = function(param) {
      alert('This function takes a parameter, which is "' + param + '".');  };   调用时和一个函数的一样的:jQuery.foo();jQuery.bar();或者$.foo();$.bar('bar');
//1.3 使用jQuery.extend(object);　 
jQuery.extend({
      foo: function() {
          alert('This is a test、This is only a test.');
        },
      bar: function(param) {
          alert('This function takes a parameter, which is "' + param +'".');
        }
     }); 
//1.4 使用命名空间
// 虽然在jQuery命名空间中，我们禁止使用了大量的javaScript函数名和变量名。
// 但是仍然不可避免某些函数或变量名将于其他jQuery插件冲突，因此我们习惯将一些方法
// 封装到另一个自定义的命名空间。
jQuery.myPlugin = {         
foo:function() {         
  alert('This is a test、This is only a test.');         
 },         
 bar:function(param) {         
  alert('This function takes a parameter, which is "' + param + '".');   
 }        
}; 
//采用命名空间的函数仍然是全局函数，调用时采用的方法： 
$.myPlugin.foo();        
$.myPlugin.bar('baz');
//通过这个技巧（使用独立的插件名），我们可以避免命名空间内函数的冲突。

//第二种是对象级别的插件开发
//形式1： 
(function($){    
  $.fn.extend({    
   pluginName:function(opt,callback){    
             // Our plugin implementation code goes here、     
   }    
  })    
})(jQuery);  

//形式2：
(function($) {      
   $.fn.pluginName = function() {    
        // Our plugin implementation code goes here、   
   };     
})(jQuery);
//形参是$，函数定义完成之后,把jQuery这个实参传递进去.立即调用执行。
//这样的好处是,我们在写jQuery插件时,也可以使用$这个别名,而不会与prototype引起冲突
```


### [5、Function.prototype.apply 和 Function.prototype.call 之间有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#5functionprototypeapply-和-functionprototypecall-之间有什么区别)  


`apply()`方法可以在使用一个指定的 `this` 值和一个参数数组（或类数组对象）的前提下调用某个函数或方法。`call()`方法类似于`apply()`，不同之处仅仅是`call()`接受的参数是参数列表。

```
const obj1 = {
result:0
};

const obj2 = {
result:0
};

function reduceAdd(){
  let result = 0;
  for(let i = 0, len = arguments.length; i < len; i++){
    result += arguments[i];
  }
  this.result = result;
}

reduceAdd.apply(obj1, [1, 2, 3, 4, 5]); // 15
reduceAdd.call(obj2, 1, 2, 3, 4, 5); // 15
```


### [6、自执行函数?用于什么场景？好处?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#6自执行函数用于什么场景好处)  


**自执行函数:**

**1、** 声明一个匿名函数

**2、** 马上调用这个匿名函数。

作用：创建一个独立的作用域。

**好处：**

防止变量弥散到全局，以免各种js库冲突。隔离作用域避免污染，或者截断作用域链，避免闭包造成引用变量无法释放。利用立即执行特性，返回需要的业务函数或对象，避免每次通过条件判断来处理

场景：一般用于框架、插件等场景


### [7、$$('div+.ab')和$$('.ab+div') 哪个效率高？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#7$$'div+ab'和$$'ab+div'-哪个效率高)  


$('div+.ab')效率高


### [8、Promise 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#8promise-是什么)  


**Promise** 是异步编程的一种解决方案：从语法上讲，`promise`是一个对象，从它可以获取异步操作的消息；从本意上讲，它是承诺，承诺它过一段时间会给你一个结果。`promise`有三种状态：`pending(等待态)`，`fulfiled(成功态)`，`rejected(失败态)`；状态一旦改变，就不会再变。创造`promise`实例后，它会立即执行。

```
fs.readFile('somefile.txt', function (e, data) {
  if (e) {
    console.log(e);
  }
  console.log(data);
});
```

如果我们在回调内部有另一个异步操作，则此方法存在问题。我们将有一个混乱且不可读的代码。此代码称为 **『回调地狱』**。

```
// 回调地狱
fs.readFile('somefile.txt', function (e, data) {
  //your code here
  fs.readdir('directory', function (e, files) {
    //your code here
    fs.mkdir('directory', function (e) {
      //your code here
    })
  })
})
```

如果我们在这段代码中使用`promise`，它将更易于阅读、理解和维护。

`promReadFile('file/path') .then(data => { return promReaddir('directory'); }) .then(data => { return promMkdir('directory'); }) .catch(e => { console.log(e); })`

`promise`有三种不同的状态：

**1、** pending：初始状态，完成或失败状态的前一个状态

**2、** fulfilled：操作成功完成

**3、** rejected：操作失败

`pending` 状态的 `Promise` 对象会触发 `fulfilled/rejected` 状态，在其状态处理方法中可以传入参数/失败信息。当操作成功完成时，**Promise** 对象的 `then` 方法就会被调用；否则就会触发 `catch`。如：

```
const myFirstPromise = new Promise((resolve, reject) => {
  setTimeout(function(){
      resolve("成功!"); 
  }, 250);
});

myFirstPromise.then((data) => {
  console.log("Yay! " + data);
}).catch((e) => {...});
```


### [9、手动实现缓存方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#9手动实现缓存方法)  


```
function memoize(fn) {
  const cache = {};
  return function (param) {
    if (cache[param]) {
      console.log('cached');
      return cache[param];
    } else {
      let result = fn(param);
      cache[param] = result;
      console.log(`not cached`);
      return result;
    }
  }
}

const toUpper = (str ="")=> str.toUpperCase();

const toUpperMemoized = memoize(toUpper);

toUpperMemoized("abcdef");
toUpperMemoized("abcdef");
```

这个缓存函数适用于接受一个参数。我们需要改变下，让它接受多个参数。

```
const slice = Array.prototype.slice;
function memoize(fn) {
  const cache = {};
  return (...args) => {
    const params = slice.call(args);
    console.log(params);
    if (cache[params]) {
      console.log('cached');
      return cache[params];
    } else {
      let result = fn(...args);
      cache[params] = result;
      console.log(`not cached`);
      return result;
    }
  }
}
const makeFullName = (fName, lName) => `${fName} ${lName}`;
const reduceAdd = (numbers, startingValue = 0) => numbers.reduce((total, cur) => total + cur, startingValue);

const memoizedMakeFullName = memoize(makeFullName);
const memoizedReduceAdd = memoize(reduceAdd);

memoizedMakeFullName("Marko", "Polo");
memoizedMakeFullName("Marko", "Polo");

memoizedReduceAdd([1, 2, 3, 4, 5], 5);
memoizedReduceAdd([1, 2, 3, 4, 5], 5);
```


### [10、请解释什么是事件代理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#10请解释什么是事件代理)  


**1、** 事件代理（`Event Delegation`），又称之为事件委托。是 `JavaScript` 中常用绑定事件的常用技巧。顾名思义，“事件代理”即是把原本需要绑定的事件委托给父元素，让父元素担当事件监听的职务。事件代理的原理是DOM元素的事件冒泡。使用事件代理的好处是可以提高性能

**2、** 可以大量节省内存占用，减少事件注册，比如在`table`上代理所有`td`的`click`事件就非常棒

**3、** 可以实现当新增子对象时无需再次对其绑定


### [11、手动实现 `Array.prototype.map 方法`](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#11手动实现-arrayprototypemap-方法)  

### [12、如何创建一个对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#12如何创建一个对象)  

### [13、== 和 === 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#13-和-=-有什么区别)  

### [14、展开(spread )运算符和 剩余(Rest) 运算符有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#14展开spread-运算符和-剩余rest-运算符有什么区别)  

### [15、简述下工作流程###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#15简述下工作流程###)  

### [16、javascript 代码中的"use strict";是什么意思 ? 使用它区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#16javascript-代码中的"use-strict";是什么意思--使用它区别是什么)  

### [17、如何copy一个dom元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#17如何copy一个dom元素)  

### [18、何为防抖和节流？如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#18何为防抖和节流如何实现)  

### [19、你有哪些性能优化的方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#19你有哪些性能优化的方法)  

### [20、平时工作中怎么样进行数据交互?如果后台没有提供数据怎么样进行开发?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#20平时工作中怎么样进行数据交互如果后台没有提供数据怎么样进行开发)  

### [21、什么是 event.currentTarget？？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#21什么是-eventcurrenttarget)  

### [22、如何在 JS 中创建对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#22如何在-js-中创建对象)  

### [23、你对数据校验是怎么样处理的？jquery.validate？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#23你对数据校验是怎么样处理的jqueryvalidate)  

### [24、同步和异步的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#24同步和异步的区别)  

### [25、谈谈你对ES6的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#25谈谈你对es6的理解)  

### [26、$(function(){})和window.onload 和 $(document).ready(function(){})](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#26$function{}和windowonload-和-$documentreadyfunction{})  

### [27、attribute和property的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#27attribute和property的区别是什么)  

### [28、简述下 this 和定义属性和方法的时候有什么区别?Prototype？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#28简述下-this-和定义属性和方法的时候有什么区别prototype)  

### [29、JSON 的了解？**](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#29json-的了解**)  





