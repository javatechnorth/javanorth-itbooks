# JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）

JavaScript面试题及答案【最新版】JavaScript高级面试题大全(2021版)，发现网上很多JavaScript面试题及答案整理都没有答案，所以花了很长时间搜集，本套JavaScript面试题大全，JavaScript面试题大汇总，有大量经典的JavaScript面试题以及答案，包含JavaScript语言常见面试题、JavaScript工程师高级面试题及一些大厂JavaScript开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套JavaScript面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个JavaScript面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、什么是缓存及它有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#1什么是缓存及它有什么作用)  


缓存是建立一个函数的过程，这个函数能够记住之前计算的结果或值。使用缓存函数是为了避免在最后一次使用相同参数的计算中已经执行的函数的计算。这节省了时间，但也有不利的一面，即我们将消耗更多的内存来保存以前的结果。


### [2、说说你对作用域链的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#2说说你对作用域链的理解)  


**1、** 作用域链的作用是保证执行环境里有权访问的变量和函数是有序的，作用域链的变量只能向上访问，变量访问到`window`对象即被终止，作用域链向下访问变量是不被允许的

**2、** 简单的说，作用域就是变量与函数的可访问范围，即作用域控制着变量与函数的可见性和生命周期


### [3、如何通过原生js 判断一个元素当前是显示还是隐藏状态?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#3如何通过原生js-判断一个元素当前是显示还是隐藏状态)  


```
if( document.getElementById("div").css("display")==='none')
if( document.getElementById("div").css("display")==='block')
$("#div").is(":hidden"); // 判断是否隐藏
$("#div").is(":visible")
```


### [4、window.onload ==? DOMContentLoaded ?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#4windowonload--domcontentloaded-)  


一般情况下，DOMContentLoaded事件要在window.onload之前执行，当DOM树构建完成的时候就会执行DOMContentLoaded事件，而window.onload是在页面载入完成的时候，才执行，这其中包括图片等元素。大多数时候我们只是想在DOM树构建完成后，绑定事件到元素，我们并不需要图片元素，加上有时候加载外域图片的速度非常缓慢。


### [5、sessionStorage和localstroage与cookie之间有什么关联, cookie最大存放多少字节](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#5sessionstorage和localstroage与cookie之间有什么关联,-cookie最大存放多少字节)  


**三者共同点：**

都是保存在浏览器端，且同源的。

区别:

**1、** cookie在浏览器和服务器间来回传递。而sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存

**2、** 存储大小限制也不同，cookie数据不能超过4k，sessionStorage和localStorage 但比cookie大得多，可以达到5M

**3、** 数据有效期不同，sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持；localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭

**4、** 作用域不同，sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面(即数据不共享)；localStorage 在所有同源窗口中都是共享的；cookie也是在所有同源窗口中都是共享的( 即数据共享 )。


### [6、介绍js有哪些内置对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#6介绍js有哪些内置对象)  


**1、** `Object` 是 `JavaScript` 中所有对象的父对象

**2、** 数据封装类对象：`Object`、`Array`、`Boolean`、`Number` 和 `String`

**3、** 其他对象：`Function`、`Arguments`、`Math`、`Date`、`RegExp`、`Error`


### [7、事件委托？有什么好处?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#7事件委托有什么好处)  


利用冒泡的原理，把事件加到父级上，触发执行效果

好处：新添加的元素还会有之前的事件；提高性能。


### [8、`require`/`import`之间的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#8require/import之间的区别)  


**1、** `require`是CommonJS语法，`import`是ES6语法；

**2、** `require`只在后端服务器支持，`import`在高版本浏览器及Node中都可以支持；

**3、** `require`引入的是原始导出值的复制，`import`则是导出值的引用；

**4、** `require`时运行时动态加载，`import`是静态编译；

**5、** `require`调用时默认不是严格模式，`import`则默认调用严格模式.

### [9、使用 + 或一元加运算符是将字符串转换为数字的最快方法吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#9使用-+-或一元加运算符是将字符串转换为数字的最快方法吗)  


根据MDN文档，`+`是将字符串转换为数字的最快方法，因为如果值已经是数字，它不会执行任何操作。


### [10、git 和 svn的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#10git-和-svn的区别)  


SVN是集中式版本控制系统，版本库是集中放在中央服务器的，而干活的时候，用的都是自己的电脑，所以首先要从中央服务器哪里得到最新的版本，然后干活，干完后，需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作，如果在局域网还可以，带宽够大，速度够快，如果在互联网下，如果网速慢的话，就纳闷了。

Git是分布式版本控制系统，那么它就没有中央服务器的，每个人的电脑就是一个完整的版本库，这样，工作的时候就不需要联网了，因为版本都是在自己的电脑上。既然每个人的电脑都有一个完整的版本库，那多个人如何协作呢？比如说自己在电脑上改了文件A，其他人也在电脑上改了文件A，这时，你们两之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。


### [11、谈谈你对AMD、CMD的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#11谈谈你对的理解)  

### [12、什么是提升？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#12什么是提升)  

### [13、谈谈This对象的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#13谈谈this对象的理解)  

### [14、声明函数作用提升?声明变量和声明函数的提升有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#14声明函数作用提升声明变量和声明函数的提升有什么区别)  

### [15、Node的应用场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#15node的应用场景)  

### [16、event.preventDefault() 和 event.stopPropagation()方法之间有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#16eventpreventdefault-和-eventstoppropagation方法之间有什么区别)  

### [17、说说严格模式的限制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#17说说严格模式的限制)  

### [18、Javascript如何实现继承？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#18javascript如何实现继承)  

### [19、如何在一行中计算多个表达式的值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#19如何在一行中计算多个表达式的值)  

### [20、事件流?事件捕获？事件冒泡？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#20事件流事件捕获事件冒泡)  

### [21、什么是类？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#21什么是类)  

### [22、DOM 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#22dom-是什么)  

### [23、JavaScript原型，原型链 ? 有什么特点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#23javascript原型原型链--有什么特点)  

### [24、null，undefined 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#24nullundefined-的区别)  

### [25、什么是默认参数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#25什么是默认参数)  

### [26、如何使用storage 对js文件进行缓存](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#26如何使用storage-对js文件进行缓存)  

### [27、什么是预编译语音|预编译处理器?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#27什么是预编译语音|预编译处理器)  

### [28、null，undefined 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#28nullundefined-的区别)  

### [29、回调函数?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#29回调函数)  

### [30、ECMAScript 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案（2021年JavaScript面试题及答案大汇总）.md#30ecmascript-是什么)  





