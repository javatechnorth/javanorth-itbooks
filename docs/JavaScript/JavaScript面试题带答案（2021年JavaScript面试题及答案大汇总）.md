# JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）

JavaScript面试题及答案【最新版】JavaScript高级面试题大全(2021版)，发现网上很多JavaScript面试题及答案整理都没有答案，所以花了很长时间搜集，本套JavaScript面试题大全，JavaScript面试题大汇总，有大量经典的JavaScript面试题以及答案，包含JavaScript语言常见面试题、JavaScript工程师高级面试题及一些大厂JavaScript开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套JavaScript面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个JavaScript面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、实现继承的方法有哪些？？？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#1实现继承的方法有哪些)  


实现继承的方法有：

**class+extends继承（ES6）**

```
//类模板
class Animal {
    constructor(name) {
        this.name = name
    }
}
//继承类
class Cat extends Animal { //重点。extends方法，内部用constructor+super
    constructor(name) {
        super(name);
        //super作为函数调用时，代表父类的构造函数
    } //constructor可省略
    eat() {
        console.log("eating")
    }
}
```

**原型继承**

```
//类模板
function Animal(name) {
    this.name = name;
}
//添加原型方法
Animal.prototype.eat = function() {
    console.log("eating")
}

function Cat(furColor) {
    this.color = color;
};
//继承类
Cat.prototype = new Animal() //重点：子实例的原型等于父类的实例
```

**借用构造函数继承**

```
function Animal(name){
    this.name = name
}
function Cat(){
    Animal.call(this,"CatName")//重点，调用父类的call方法
}
```

**寄生组合式继承（重点）**


### [2、25.Jq如何判断元素显示隐藏？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#225jq如何判断元素显示隐藏)  


```
//第一种：使用CSS属性 
var display =$('#id').css('display'); 
if(display == 'none'){    alert("我是隐藏的！"); }
//第二种：使用jquery内置选择器 
<div id="test"<p>仅仅是测试所用</p</div>
if($("#test").is(":hidden")){        $("#test").show();    //如果元素为隐藏,则将它显现 }else{       $("#test").hide();     //如果元素为显现,则将其隐藏 }
//第三种：jQuery判断元素是否显示 是否隐藏
var node=$('#id');
if(node.is(':hidden')){　　//如果node是隐藏的则显示node元素，否则隐藏
　　node.show();　
}else{
　　node.hide();
}
```


### [3、ajax请求方式有几种（8种）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#3ajax请求方式有几种8种)  


1）$$.get(url,\[data\],\[callback\])  
2）$$.getJSON(url,[data],[callback])

3）$$.post(url,\[data\],\[callback\],\[type\])  
4）$$.ajax(opiton)

5）$.getScript( url, [callback] )

6）jquery对象.load( url, [data], [callback] )

7）serialize() 与 serializeArray()


### [4、26.移动端上什么是点击穿透?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#426移动端上什么是点击穿透)  


**点击穿透现象有3种：**

**点击穿透问题：**

点击蒙层（mask）上的关闭按钮，蒙层消失后发现触发了按钮下面元素的click事件跨页面点击穿透问题：如果按钮下面恰好是一个有href属性的a标签，那么页面就会发生跳转另一种跨页面点击穿透问题：这次没有mask了，直接点击页内按钮跳转至新页，然后发现新页面中对应位置元素的click事件被触发了

**解决方案：**

**1、** 只用touch

最简单的解决方案，完美解决点击穿透问题

把页面内所有click全部换成touch事件（ touchstart 、’touchend’、’tap’）

**2、** 只用click

下下策，因为会带来300ms延迟，页面内任何一个自定义交互都将增加300毫秒延迟

**3、** tap后延迟350ms再隐藏mask

改动最小，缺点是隐藏mask变慢了，350ms还是能感觉到慢的

**4、** pointer-events

比较麻烦且有缺陷， 不建议使用mask隐藏后，给按钮下面元素添上 pointer-events: none; 样式，让click穿过去，350ms后去掉这个样式，恢复响应缺陷是mask消失后的的350ms内，用户可以看到按钮下面的元素点着没反应，如果用户手速很快的话一定会发现


### [5、如何检查对象中是否存在某个属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#5如何检查对象中是否存在某个属性)  


检查对象中是否存在属性有三种方法。

第一种使用 `in` 操作符号：

```
const o = { 
  "prop" : "bwahahah",
  "prop2" : "hweasa"
};

console.log("prop" in o); // true
console.log("prop1" in o); // false
```

第二种使用 `hasOwnProperty` 方法，`hasOwnProperty()` 方法会返回一个布尔值，指示对象自身属性中是否具有指定的属性（也就是，是否有指定的键）。

```
console.log(o.hasOwnProperty("prop2")); // true
console.log(o.hasOwnProperty("prop1")); // false
```

第三种使用括号符号`obj["prop"]`。如果属性存在，它将返回该属性的值，否则将返回`undefined`。

`console.log(o["prop"]); // "bwahahah" console.log(o["prop1"]); // undefined`


### [6、强制转换 显式转换 隐式转换?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#6强制转换-显式转换-隐式转换)  


```
//强制类型转换：
Boolean(0)   // =false - 零
Boolean(new object())   // =true - 对象
Number(undefined)       // =  NaN
Number(null)              // =0
String(null)              // ="null"
parseInt( )
parseFloat( )
JSON.parse( )
JSON.stringify ( )
```

隐式类型转换：

在使用算术运算符时，运算符两边的数据类型可以是任意的，比如，一个字符串可以和数字相加。之所以不同的数据类型之间可以做运算，是因为JavaScript引擎在运算之前会悄悄的把他们进行了隐式类型转换的

```
（例如：x+"" //等价于String(x)  
\+x //等价于Number(x)  
x-0 //同上  
!!x //等价于Boolean(x),是双叹号）
```

**显式转换：**

如果程序要求一定要将某一类型的数据转换为另一种类型，则可以利用强制类型转换运算符进行转换，这种强制转换过程称为显示转换。

显示转换是你定义让这个值类型转换成你要用的值类型，是底到高的转换。例 int 到float就可以直接转，int i=5,想把他转换成char类型，就用显式转换（char）i


### [7、编写一个 getElementsByClassName 封装函数?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#7编写一个-getelementsbyclassname-封装函数)  


```
<body  
<input type="submit" id = "sub" class="ss confirm btn" value="提交"/  
<scriptwindow.onload = function(){ 
//方法一         
    var Opt = document.getElementById('sub');
    var getClass = function(className,tagName){
        if(document.getElementsByTagName){
            var Inp = document.getElementsByTagName(tagName);
            for(var i=0; i<Inp.length; i++){
                if((new RegExp('(\\s|^)' +className +'(\\s|$)')).test(Inp[i].className)){
                      return Inp[i];
                    }
                }
            }else if(document.getElementsByClassName){
                return document.getElementsByClassName(className);
        }
    }                 
//方法二
    var aa = getClass("confirm", "input");
        function getClass(className, targetName){
            var ele = [];
            var all = document.getElementsByTagName(targetName || "*");
            for(var i=0; i<all.length; i++){
                if(all[i].className.match(new RegExp('(\\s|^)'+confirm+'(\\s|$)'))){    
                    ele[ele.length] = all[i];
                }
            }
            return ele;
        }
//方法三
    function getObjsByClass(tagName, className){
           if(document.getElementsByClassName){
               alert("document.getElementsByClassName");
               return document.getElementsByClassName(className);
           }else{
               var el = [];
               var _el = document.getElementsByTagName(tagName);
               for(var i=0; i<_el.length; i++){
                   if(_el[i].className.indexOf(className) -1){
                       alert(_el[i]);
                       el[_el.length] = _el[i];
                   }
               }
               alert(el);
               return el;
           }
       }
   }
 </script>
</body>
```


### [8、什么是对象解构？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#8什么是对象解构)  


**对象析构**是从对象或数组中获取或提取值的一种新的、更简洁的方法。假设有如下的对象：

```
const employee = {
  firstName: "Marko",
  lastName: "Polo",
  position: "Software Developer",
  yearHired: 2017
};
```

从对象获取属性，早期方法是创建一个与对象属性同名的变量。这种方法很麻烦，因为我们要为每个属性创建一个新变量。假设我们有一个大对象，它有很多属性和方法，用这种方法提取属性会很麻烦。

`var firstName = employee.firstName; var lastName = employee.lastName; var position = employee.position; var yearHired = employee.yearHired;`

使用解构方式语法就变得简洁多了：

`{ firstName, lastName, position, yearHired } = employee;`

我们还可以为属性取别名：

`let { firstName: fName, lastName: lName, position, yearHired } = employee;`

当然如果属性值为 `undefined` 时，我们还可以指定默认值：

`let { firstName = "Mark", lastName: lName, position, yearHired } = employee;`


### [9、什么是作用域？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#9什么是作用域)  


JavaScript 中的作用域是我们可以有效访问变量或函数的区域。JS 有三种类型的作用域：**全局作用域**、**函数作用域**和**块作用域(ES6)**。

**全局作用域**——在全局命名空间中声明的变量或函数位于全局作用域中，因此在代码中的任何地方都可以访问它们。

```
//global namespace
var g = "global";

function globalFunc(){
  function innerFunc(){
    console.log(g); // can access "g" because "g" is a global variable
  }
 innerFunc();
}
```

**函数作用域**——在函数中声明的变量、函数和参数可以在函数内部访问，但不能在函数外部访问。

```
function myFavoriteFunc(a) {
  if (true) {
    var b = "Hello " + a;
  }
  return b;
}

myFavoriteFunc("World");

console.log(a); // Throws a ReferenceError "a" is not defined
console.log(b); // does not continue here
```

- **块作用域**-在块`{}`中声明的变量（`let，const`）只能在其中访问。

```
function testBlock(){
   if(true){
     let z = 5;
   }
   return z; 
 }

 testBlock(); // Throws a ReferenceError "z" is not defined
```

作用域也是一组用于查找变量的规则。如果变量在当前作用域中不存在，它将向外部作用域中查找并搜索，如果该变量不存在，它将再次查找直到到达全局作用域，如果找到，则可以使用它，否则引发错误，这种查找过程也称为**作用域链**。

```
/* 作用域链

 内部作用域->外部作用域-> 全局作用域
*/

// 全局作用域
var variable1 = "Comrades";   
var variable2 = "Sayonara";

function outer(){
// 外部作用域
var variable1 = "World";
function inner(){
// 内部作用域
  var variable2 = "Hello";
  console.log(variable2 + " " + variable1);
}
inner();
}  
outer(); // Hello World
```


### [10、ajax的缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#10ajax的缺点)  


**1、** ajax不支持浏览器back按钮。

**2、** 安全问题 AJAX暴露了与服务器交互的细节。

**3、** 对搜索引擎的支持比较弱。

**4、** 破坏了程序的异常机制。

**5、** 不容易调试



### [11、什么是事件冒泡？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#11什么是事件冒泡)  

### [12、什么是`Set`对象，它是如何工作的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#12什么是set对象它是如何工作的)  

### [13、实现异步的方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#13实现异步的方式有哪些)  

### [14、new操作符具体干了什么呢?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#14new操作符具体干了什么呢)  

### [15、ajax 是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#15ajax-是什么)  

### [16、简述下你理解的面向对象？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#16简述下你理解的面向对象)  

### [17、new 关键字有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#17new-关键字有什么作用)  

### [18、|| 运算符能做什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#18||-运算符能做什么)  

### [19、AJAX 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#19ajax-是什么)  

### [20、typeof？typeof [ ]返回数据类型是？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#20typeoftypeof-[-]返回数据类型是)  

### [21、JSON 的了解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#21json-的了解)  

### [22、调用函数，可以使用哪些方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#22调用函数可以使用哪些方法)  

### [23、函数表达式和函数声明之间有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#23函数表达式和函数声明之间有什么区别)  

### [24、js延迟加载的方式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#24js延迟加载的方式有哪些)  

### [25、如何检查值是否虚值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#25如何检查值是否虚值)  

### [26、手动实现`Array.prototype.reduce`方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#26手动实现arrayprototypereduce方法)  

### [27、一般使用什么版本控制工具?svn如何对文件加锁###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#27一般使用什么版本控制工具svn如何对文件加锁###)  

### [28、jsonp原理？ 缺点?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#28jsonp原理-缺点)  

### [29、javascript创建对象的几种方式？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#29javascript创建对象的几种方式)  

### [30、call & apply 两者之间的区别###](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/JavaScript/JavaScript面试题带答案（2021年JavaScript面试题及答案大汇总）.md#30call-&-apply-两者之间的区别###)  





