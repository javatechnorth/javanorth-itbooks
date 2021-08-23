# JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）

JavaScript面试题及答案【最新版】JavaScript高级面试题大全(2021版)，发现网上很多JavaScript面试题及答案整理都没有答案，所以花了很长时间搜集，本套JavaScript面试题大全，JavaScript面试题大汇总，有大量经典的JavaScript面试题以及答案，包含JavaScript语言常见面试题、JavaScript工程师高级面试题及一些大厂JavaScript开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套JavaScript面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个JavaScript面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、数组的排序方法（sort）？排序？汉字排序？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#1数组的排序方法sort排序汉字排序)  


数组的排序方法：reverse()和sort()。reverse()方法会对反转数组项的顺序。

Eg:var values = [0, 1, 5, 10, 15]; values.sort();//0,1,10,15,5

var values = [1, 2, 3, 4, 5]; values.reverse();//5,4,3,2,1

js中的排序（详情参考： [http://www.tuicool.com/articles/IjInMbU](http://link.zhihu.com/?target=http%3A//www.tuicool.com/articles/IjInMbU)）

利用sort排序, 冒泡排序, 快速排序, 插入排序, 希尔排序, 选择排序

归并排序

localeCompare() 方法用于字符串编码的排序

localeCompare 方法：返回一个值，指出在当前的区域设置中两个字符串是否相同。


### [2、简述ajax执行流程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#2简述ajax执行流程)  


```
基本步骤：
var xhr =null;//创建对象 
if(window.XMLHttpRequest){
       xhr = new XMLHttpRequest();
}else{
       xhr = new ActiveXObject("Microsoft.XMLHTTP");
}
xhr.open(“方式”,”地址”,”标志位”);//初始化请求 
   xhr.setRequestHeader(“”,””);//设置http头信息 
xhr.onreadystatechange =function(){}//指定回调函数 
xhr.send();//发送请求
```


### [3、上一个项目是什么？主要负责哪些？购物车流程?支付功能?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#3上一个项目是什么主要负责哪些购物车流程支付功能)  


**主要负责哪些就讲主要做哪些功能模块：**

1）商品模块:

**1、** 商品列表：商品排序 商品筛选 商品过滤 商品查询 商品推荐

**2、** 商品详情:类型推荐 商品简介 商品详情 商品评价 售后维护

2)购物车模块：商品编号、数量、价格、总额、运费、运输选项、运费总计、从购物车删除选项、更新数量、结账、继续购物、商品描述、库存信息


### [4、异步加载的方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#4异步加载的方式有哪些)  


(1) defer，只支持IE

(2) async：true

(3) 创建script，插入到DOM中，加载完毕后callBack


### [5、什么是包装对象（wrapper object）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#5什么是包装对象wrapper-object)  


我们现在复习一下JS的数据类型，JS数据类型被分为两大类，**基本类型**和**引用类型**。

基本类型：`Undefined`,`Null`,`Boolean`,`Number`,`String`,`Symbol`,`BigInt`

引用类型：`Object`,`Array`,`Date`,`RegExp`等，说白了就是对象。

其中引用类型有方法和属性，但是基本类型是没有的，但我们经常会看到下面的代码：

```
let name = "marko";

console.log(typeof name); // "string"
console.log(name.toUpperCase()); // "MARKO"
```

`name`类型是 `string`，属于基本类型，所以它没有属性和方法，但是在这个例子中，我们调用了一个`toUpperCase()`方法，它不会抛出错误，还返回了对象的变量值。

原因是基本类型的值被临时转换或强制转换为**对象**，因此`name`变量的行为类似于**对象**。除`null`和`undefined`之外的每个基本类型都有自己**包装对象**。也就是：`String`，`Number`，`Boolean`，`Symbol`和`BigInt`。在这种情况下，`name.toUpperCase()`在幕后看起来如下：

`console.log(new String(name).toUpperCase()); // "MARKO"`

在完成访问属性或调用方法之后，新创建的对象将立即被丢弃。


### [6、谁是c的构造函数?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#6谁是c的构造函数)  


```
function ab() {
         this.say = ""; } 
ab.constructor = {} ab.name = ''; 
var c = new ab(); 
//构造函数默认指向函数本身,ab是一个类,它的构造函数是它本身，
//然后ab.constructor={};ab的构造函数就指向{}了，c是ab的实例化对象，c的构造函数就是{}
//通过使用new的时候,创建对象发生了那些改变? 当使用new操作时，会马上开辟一个块内存，
//创建一个空对象，并将this指向这个对象。接着，执行构造函数ab()，对这个空对象进行构造
//（构造函数里有什么属性和方法都一一给这个空白对象装配上去，这就是为何它叫构造函数了）。
```


### [7、!! 运算符能做什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#7-运算符能做什么)  


`!!`运算符可以将右侧的值强制转换为布尔值，这也是将值转换为布尔值的一种简单方法。

```
console.log(!!null); // false
console.log(!!undefined); // false
console.log(!!''); // false
console.log(!!0); // false
console.log(!!NaN); // false
console.log(!!' '); // true
console.log(!!{}); // true
console.log(!![]); // true
console.log(!!1); // true
console.log(!![].length); // false
```


### [8、为什么在 JS 中比较两个相似的对象时返回 false？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#8为什么在-js-中比较两个相似的对象时返回-false)  


先看下面的例子：

```
let a = { a: 1 };
let b = { a: 1 };
let c = a;
console.log(a === b); // 打印 false，即使它们有相同的属性
console.log(a === c); // true
```

JS 以不同的方式比较对象和基本类型。在基本类型中，JS 通过值对它们进行比较，而在对象中，JS 通过引用或存储变量的内存中的地址对它们进行比较。这就是为什么第一个`console.log`语句返回`false`，而第二个`console.log`语句返回`true`。`a`和`c`有相同的引用地址，而`a`和`b`没有。


### [9、什么是原型、原型链？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#9什么是原型原型链)  


原型：JS声明构造函数(用来实例化对象的函数)时，会在内存中创建一个对应的对象，这个对象就是原函数的原型。构造函数默认有一个prototype属性，`prototype`的值指向函数的原型。同时原型中也有一个`constructor`属性，`constructor`的值指向原函数。

通过构造函数实例化出来的对象，并不具有`prototype`属性，其默认有一个`__proto__`属性，`__proto__`的值指向构造函数的原型对象。在原型对象上添加或修改的属性，在所有实例化出的对象上都可共享。

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/49bad3cc378b4232a4b768bfe0ea67d7~tplv-k3u1fbpfcp-zoom-1.image#alt=%E5%9C%A8%E8%BF%99%E9%87%8C%E6%8F%92%E5%85%A5%E5%9B%BE%E7%89%87%E6%8F%8F%E8%BF%B0)

当在实例化的对象中访问一个属性时，首先会在该对象内部寻找，如找不到，则会向其`__proto__`指向的原型中寻找，如仍找不到，则继续向原型中`__proto__`指向的上级原型中寻找，直至找到或`Object.prototype`为止，这种链状过程即为原型链。


### [10、数据持久化技术(ajax)?简述ajax流程###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#10数据持久化技术ajax简述ajax流程###)  


**1、** 客户端产生js的事件

**2、** 创建XMLHttpRequest对象

**3、** 对XMLHttpRequest进行配置

**4、** 通过AJAX引擎发送异步请求

**5、** 服务器端接收请求并且处理请求，返回html或者xml内容

**6、** XML调用一个callback()处理响应回来的内容

**7、** 页面局部刷新


### [11、判断数据类型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#11判断数据类型)  

### [12、如何确保ajax或连接不走缓存路径](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#12如何确保ajax或连接不走缓存路径)  

### [13、Jq中get和eq有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#13jq中get和eq有什么区别)  

### [14、怎么理解宏任务，微任务？？？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#14怎么理解宏任务微任务)  

### [15、如何解决跨域问题?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#15如何解决跨域问题)  

### [16、ajax 和 jsonp ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#16ajax-和-jsonp-)  

### [17、split() join()?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#17split-join)  

### [18、什么是 event.target ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#18什么是-eventtarget-)  

### [19、什么是 `async/await` 及其如何工作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#19什么是-async/await-及其如何工作)  

### [20、Gc机制是什么？为什么闭包不会被回收变量和函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#20gc机制是什么为什么闭包不会被回收变量和函数)  

### [21、为什么typeof null 返回 object？如何检查一个值是否为 null？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#21为什么typeof-null-返回-object如何检查一个值是否为-null)  

### [22、bootstrap好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#22bootstrap好处)  

### [23、异步加载JS的方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#23异步加载js的方式有哪些)  

### [24、如何创建一个没有 prototype(原型)的对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#24如何创建一个没有-prototype原型的对象)  

### [25、判断数据类型的方法有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#25判断数据类型的方法有哪些)  

### [26、Jq绑定事件的几种方式？on bind ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#26jq绑定事件的几种方式on-bind-)  

### [27、什么是事件捕获？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#27什么是事件捕获)  

### [28、同步异步?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#28同步异步)  

### [29、sass和less有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript中级面试题汇总及答案（2021年JavaScript面试题及答案大全）.md#29sass和less有什么区别)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
