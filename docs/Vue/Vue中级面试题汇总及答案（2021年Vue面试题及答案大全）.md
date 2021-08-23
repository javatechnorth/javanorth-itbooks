# Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）

Vue面试题及答案【最新版】Vue高级面试题大全(2021版)，发现网上很多Vue面试题及答案整理都没有答案，所以花了很长时间搜集，本套Vue面试题大全，Vue面试题大汇总，有大量经典的Vue面试题以及答案，包含Vue语言常见面试题、Vue工程师高级面试题及一些大厂Vue开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Vue面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Vue面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、vue的filter的理解与用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#1vue的filter的理解与用法)  


**全局过滤器必须写在vue实例创建之前**

```
Vue.filter('testfilter', function (value,text) { // 返回处理后的值
   return value+text
   })
```

**局部写法：在组件实例对象里挂载**

```
filters: {
        changemsg:(val,text)\=>{ return val + text
        }
    }
```

3）使用方式：只能使用在{{}}和：v-bind中，定义时第一个参数固定为预处理的数，后面的数为调用时传入的参数，调用时参数第一个对应定义时第二个参数，依次往后类推

```
<h3 :title="test|changemsg(1234)">{{test|changemsg(4567)}}</h3>
//多个过滤器也可以串行使用
<h2>{{name|filter1|filter2|filter3}}</h2>
```

**vue-cli项目中注册多个全局过滤器写法：**

```
//1.创建一个单独的文件定义并暴露函数对象
const filter1 = function (val) {
  return val + '--1'
}
const filter2 = function (val) {
  return val + '--2'
}
const filter3 = function (val) {
  return val + '--3'
}

export default {
  filter1,
  filter2,
  filter3
}

//2.导入main.js(在vue实例之前)
import filters from './filter/filter.js'

//3.循环注册过滤器
Object.keys(filters).forEach(key=>{
  Vue.filter(key,filters[key])
})
```


### [2、vue的路由模式及区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#2vue的路由模式及区别)  


hash模式在浏览器中符号“#”，#以及#后面的字符称之为hash，用window.location.hash读取；

特点：hash虽然在URL中，但不被包括在HTTP请求中；用来指导浏览器动作，对服务端安全无用，hash不会重加载页面。

history模式：history采用HTML5的新特性；

提供了两个新方法：pushState（），replaceState（）可以对浏览器历史记录栈进行修改，以及popState事件的监听到状态变更。history 模式下，前端的 URL必须和实际向后端发起请求的URL一致，否则会报404错误


### [3、你们vue项目是打包了一个js文件，一个css文件，还是有多个文件？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#3你们vue项目是打包了一个js文件一个css文件还是有多个文件)  


根据vue-cli脚手架规范，一个js文件，一个CSS文件。


### [4、怎么定义 vue-router 的动态路由? 怎么获取传过来的值？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#4怎么定义-vue-router-的动态路由-怎么获取传过来的值)  


在router目录下的index.js文件中，对path属性加上/:id。 使用router对象的params.id。


### [5、vuejs与angularjs以及react的区别，与AngularJS的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#5vuejs与angularjs以及react的区别与angularjs的区别)  


**相同点：**

**1、** 都支持指令：内置指令和自定义指令。

**2、** 都支持过滤器：内置过滤器和自定义过滤器。

**3、** 都支持双向数据绑定。

**4、** 都不支持低端浏览器。

**不同点：**

**1、** AngularJS的学习成本高，比如增加了Dependency Injection特性，而Vue.js本身提供的API都比较简单、直观。

**2、** 在性能上，AngularJS依赖对数据做脏检查，所以Watcher越多越慢。

**3、** Vue.js使用基于依赖追踪的观察并且使用异步队列更新。所有的数据都是独立触发的。

**4、** 对于庞大的应用来说，这个优化差异还是比较明显的。


### [6、数组去重复的方法有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#6数组去重复的方法有哪些)  


1.使用 set

```
function uniquearray(array) {
 let unique_array= Array.from(set(array))
 return unique_array;
}
```

2.使用 filter

```
function unque_array (arr) {
  let unique_array = arr.filter(function(elem, index, self) {
    return index == self.indexOf(elem);
  })
  return unique_array;
}

 console.log(unique_array(array_with_duplicates));
```

3.使用 for 循环

```
Array dups_names = ['Ron', 'Pal', 'Fred', 'Rongo', 'Ron'];
function dups_array(dups_names) {
 let unique = {};
 names.forEach(function(i) {
    If (!unique[i]) {
      unique[i] = true;    }
  });
return Object.keys(unique);}   // Ron, Pal, Fred, Rongo
Dups_array(names);
```


### [7、什么是vue生命周期？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#7什么是vue生命周期)  


Vue 实例从创建到销毁的过程，就是生命周期。也就是从开始创建、初始化数据、编译模板、挂载Dom→渲染、更新→渲染、卸载等一系列过程，我们称这是 Vue 的生命周期。


### [8、父组件更新过程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#8父组件更新过程)  


`父 beforeUpdate -> 父 updated`


### [9、什么是生命周期hook？列出一些生命周期hook。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#9什么是生命周期hook列出一些生命周期hook。)  


Vue 实例（组件）从其初始化到销毁和删除都经历生命周期。在整个过程中，Vue 允许开发人员运行自定义函数的几个阶段。这些函数称为生命周期 hook。以下是一些生命周期 hook 的列表：

- created
- mounted
- updated
- destroyed


### [10、import 和 exports 是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#10import-和-exports-是什么)  


import和exports 帮助咱们编写模块化的JS代码。使用import和exports，咱们可以将代码分割成多个文件。import只允许获取文件的某些特定变量或方法。可以导入模块导出的方法或变量。

```
 //index.js

 import name,age from './person';

 console.log(name);
 console.log(age);

 //person.js

 let name ='Sharad', occupation='developer', age =26;

 export { name, age};
```


### [11、给出模板，描述 Vue 程序的输出。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#11给出模板描述-vue-程序的输出。)  

### [12、hash路由和history路由实现原理说一下](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#12hash路由和history路由实现原理说一下)  

### [13、什么是 vue 生命周期？有什么作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#13什么是-vue-生命周期有什么作用)  

### [14、RouterLink在IE和Firefox中不起作用（路由不跳转）的问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#14routerlink在ie和firefox中不起作用路由不跳转的问题)  

### [15、v-modal的使用。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#15v-modal的使用。)  

### [16、v-if和v-for同时使用在同一个标签上的表现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#16v-if和v-for同时使用在同一个标签上的表现)  

### [17、如何在单页 Vue 应用（SPA）中实现路由？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#17如何在单页-vue-应用spa中实现路由)  

### [18、Vue的双向数据绑定原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#18vue的双向数据绑定原理是什么)  

### [19、params和query的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#19params和query的区别)  

### [20、BOM 和 DOM 的关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#20bom-和-dom-的关系)  

### [21、请说出vue.cli项目中src目录每个文件夹和文件的用法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#21请说出vuecli项目中src目录每个文件夹和文件的用法)  

### [22、如何通过类别名获取 dom 元素](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#22如何通过类别名获取-dom-元素)  

### [23、如何在JavaScript中每x秒调用一个函数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#23如何在javascript中每x秒调用一个函数)  

### [24、vue的两个核心点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#24vue的两个核心点)  

### [25、Vue2中注册在router-link上事件无效解决方法](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#25vue2中注册在router-link上事件无效解决方法)  

### [26、Vue.js中ajax请求代码应该写在组件的methods中还是vuex的actions中？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#26vuejs中ajax请求代码应该写在组件的methods中还是vuex的actions中)  

### [27、是否可以在JS中执行301重定向？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#27是否可以在js中执行301重定向)  

### [28、vue组件的通信（父子组件和非父子组件）？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Vue/Vue中级面试题汇总及答案（2021年Vue面试题及答案大全）.md#28vue组件的通信父子组件和非父子组件)  





