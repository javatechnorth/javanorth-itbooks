# JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）

JavaScript面试题及答案【最新版】JavaScript高级面试题大全(2021版)，发现网上很多JavaScript面试题及答案整理都没有答案，所以花了很长时间搜集，本套JavaScript面试题大全，JavaScript面试题大汇总，有大量经典的JavaScript面试题以及答案，包含JavaScript语言常见面试题、JavaScript工程师高级面试题及一些大厂JavaScript开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套JavaScript面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个JavaScript面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、如何添加一个dom对象到body中?innerHTML和innerText区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#1如何添加一个dom对象到body中innerhtml和innertext区别)  


body.appendChild(dom元素)；

innerHTML:从对象的起始位置到终止位置的全部内容,包括Html标签。

innerText:从起始位置到终止位置的内容, 但它去除Html标签

分别简述五个window对象、属性

**成员对象**

**1、** window.event window.document window.history

**2、** window.screen window.navigator window.external

**3、** Window对象的属性如下：

**4、** window //窗户自身

**5、** window.self [//引用本窗户window=window.self](//%E5%BC%95%E7%94%A8%E6%9C%AC%E7%AA%97%E6%88%B7window=window.self)

**6、** window.name //为窗户命名

**7、** window.defaultStatus //设定窗户状态栏信息

**8、** window.location //URL地址,配备布置这个属性可以打开新的页面


### [2、this是什么 在不同场景中分别代表什么###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#2this是什么-在不同场景中分别代表什么###)  


（1）function a(){ this ?} //This:指向windows

（2）function b(){ return function(){ this ?}}b()(); //This:指向windows

（3）function c(){ return {s:function(){this}}}c().s(); //This:指向object

由于其运行期绑定的特性，JavaScript 中的 this 含义要丰富得多，它可以是全局对象、当前对象或者任意对象，这完全取决于函数的调用方式。


### [3、offsetWidth/offsetHeight,clientWidth/clientHeight与scrollWidth/scrollHeight的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#3offsetwidth/offsetheight,clientwidth/clientheight与scrollwidth/scrollheight的区别)  


**1、** `offsetWidth/offsetHeight`返回值包含**content + padding + border**，效果与e.getBoundingClientRect()相同

**2、** `clientWidth/clientHeight`返回值只包含**content + padding**，如果有滚动条，也**不包含滚动条**

**3、** `scrollWidth/scrollHeight`返回值包含**content + padding + 溢出内容的尺寸**


### [4、call和apply 有什么好处？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#4call和apply-有什么好处)  


用call和apply:实现更好的继承和扩展，更安全。


### [5、为什么此代码 `obj.someprop.x` 会引发错误?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#5为什么此代码-objsomepropx-会引发错误)  


```
const obj = {};console.log(obj.someprop.x);
```

显然，由于我们尝试访问`someprop`属性中的`x`属性，而 someprop 并没有在对象中，所以值为 `undefined`。记住对象本身不存在的属性，并且其原型的默认值为`undefined`。因为`undefined`没有属性`x`，所以试图访问将会报错。


### [6、如何判断值是否为数组？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#6如何判断值是否为数组)  


我们可以使用`Array.isArray`方法来检查值是否为**数组**。当传递给它的参数是数组时，它返回`true`，否则返回`false`。

```
console.log(Array.isArray(5));  // false
console.log(Array.isArray("")); // false
console.log(Array.isArray()); // false
console.log(Array.isArray(null)); // false
console.log(Array.isArray({ length: 5 })); // false

console.log(Array.isArray([])); // true
```

如果环境不支持此方法，则可以使用`polyfill`实现。

`function isArray(value){ return Object.prototype.toString.call(value) === "[object Array]" }`

当然还可以使用传统的方法：

`let a = [] if (a instanceof Array) { console.log('是数组') } else { console.log('非数组') }`


### [7、&& 运算符能做什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#7&&-运算符能做什么)  


`&&` 也可以叫**逻辑与**，在其操作数中找到第一个虚值表达式并返回它，如果没有找到任何虚值表达式，则返回最后一个真值表达式。它采用短路来防止不必要的工作。

```
console.log(false && 1 && []); // false
console.log(" " && true && 5); // 5
```

**使用`if`语句**

```
const router: Router = Router();
router.get('/endpoint', (req: Request, res: Response) => {
   let conMobile: PoolConnection;
   try {
      //do some db operations
   } catch (e) {
   if (conMobile) {
    conMobile.release();
   }
  }
});
```

**使用`&&`操作符**

```
const router: Router = Router();

router.get('/endpoint', (req: Request, res: Response) => {
  let conMobile: PoolConnection;
  try {
     //do some db operations
  } catch (e) {
    conMobile && conMobile.release()
  }
});
```


### [8、defer和async](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#8defer和async)  


**1、** `defer`并行加载`js`文件，会按照页面上`script`标签的顺序执行

**2、** `async`并行加载`js`文件，下载完成立即执行，不会按照页面上`script`标签的顺序执行


### [9、如何在不使用`%`模运算符的情况下检查一个数字是否是偶数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#9如何在不使用%模运算符的情况下检查一个数字是否是偶数)  


我们可以对这个问题使用按位`&`运算符，`&`对其操作数进行运算，并将其视为二进制值，然后执行与运算。

`function isEven(num) { if (num & 1) { return false } else { return true } }`

`0` 二进制数是 `000` `1` 二进制数是 `001` `2` 二进制数是 `010` `3` 二进制数是 `011` `4` 二进制数是 `100` `5` 二进制数是 `101` `6` 二进制数是 `110` `7` 二进制数是 `111`

以此类推...

因此，当我们执行`console.log(5&1)`这个表达式时，结果为`1`。首先，`&`运算符将两个数字都转换为二进制，因此`5`变为`101`，`1`变为`001`。

然后，它使用按位怀运算符比较每个位（`0`和`1`）。`101&001`，从表中可以看出，如果`a & b`为`1`，所以`5&1`结果为`1`。

101 & 001

101

001

001

**1、** 首先我们比较最左边的`1&0`，结果是`0`。

**2、** 然后我们比较中间的`0&0`，结果是`0`。

**3、** 然后我们比较最后`1&1`，结果是`1`。

**4、** 最后，得到一个二进制数`001`，对应的十进制数，即`1`。

由此我们也可以算出`console.log(4 & 1)` 结果为`0`。知道`4`的最后一位是`0`，而`0 & 1` 将是`0`。如果你很难理解这一点，我们可以使用递归函数来解决此问题。

```
function isEven(num) {
  if (num < 0 || num === 1) return false;
  if (num == 0) return true;
  return isEven(num - 2);
}
```


### [10、什么是作用域和作用域链？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#10什么是作用域和作用域链)  


作用域可以理解为一个独立的地盘，可以理解为标识符所能生效的范围。作用域最大的用处就是隔离变量，不同作用域下同名变量不会有冲突。ES6中有全局作用域、函数作用域和块级作用域三层概念。

当一个变量在当前块级作用域中未被定义时，会向父级作用域(创建该函数的那个父级作用域)寻找。如果父级仍未找到，就会再一层一层向上寻找，直到找到全局作用域为止。这种一层一层的关系，就是作用域链 。


### [11、什么是闭包？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#11什么是闭包)  

### [12、什么是AJAX？如何实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#12什么是ajax如何实现)  

### [13、通过new创建一个对象的时候，函数内部有哪些改变###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#13通过new创建一个对象的时候函数内部有哪些改变###)  

### [14、什么是NaN？以及如何检查值是否为NaN？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#14什么是nan以及如何检查值是否为nan)  

### [15、`var`,`let`和`const`的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#15var,let和const的区别是什么)  

### [16、什么是箭头函数？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#16什么是箭头函数)  

### [17、变量作用域?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#17变量作用域)  

### [18、web开发中会话跟踪的方法有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#18web开发中会话跟踪的方法有哪些)  

### [19、html和xhtml有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#19html和xhtml有什么区别)  

### [20、事件模型](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#20事件模型)  

### [21、为什么要有同源限制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#21为什么要有同源限制)  

### 22、闭包
### [23、JavaScript提供了哪几种“异步模式”？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#23javascript提供了哪几种“异步模式)  

### [24、ES6或ECMAScript 2015有哪些新特性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#24es6或ecmascript-2015有哪些新特性)  

### [25、["1", "2", "3"].map(parseInt) 答案是多少？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#25["1",-"2",-"3"]mapparseint-答案是多少)  

### [26、Ajax原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#26ajax原理)  

### [27、promise###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#27promise###)  

### [28、this指向的各种情况都有什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#28this指向的各种情况都有什么)  

### [29、渐进增强和优雅降级](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题附答案汇总（2021年JavaScript面试题及答案大全）.md#29渐进增强和优雅降级)  





