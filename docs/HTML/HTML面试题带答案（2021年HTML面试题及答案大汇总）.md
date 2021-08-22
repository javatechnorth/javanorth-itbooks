# HTML面试题带答案（2021年HTML面试题及答案大汇总）

HTML面试题及答案【最新版】HTML高级面试题大全(2021版)，发现网上很多HTML面试题及答案整理都没有答案，所以花了很长时间搜集，本套HTML面试题大全，HTML面试题大汇总，有大量经典的HTML面试题以及答案，包含HTML语言常见面试题、HTML工程师高级面试题及一些大厂HTML开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套HTML面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个HTML面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、从浏览器地址栏输入url到显示页面的步骤](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#1从浏览器地址栏输入url到显示页面的步骤)  


浏览器根据请求的`URL`交给`DNS`域名解析，找到真实`IP`，向服务器发起请求；

服务器交给后台处理完成后返回数据，浏览器接收文件（`HTML、JS、CSS`、图象等）；

浏览器对加载到的资源（`HTML、JS、CSS`等）进行语法解析，建立相应的内部数据结构（如`HTML`的`DOM`）；

载入解析到的资源文件，渲染页面，完成。


### [2、px，em，rem的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#2pxemrem的区别)  


**1、** px 像素（Pixel）。绝对单位。像素 px 是相对于显示器屏幕分辨率而言的，是一个虚拟长度单位，是计算机系统的数字化图像长度单位，如果 px 要换算成物理长度，需要指定精度 DPI。

**2、** em 是相对长度单位，相对于当前对象内文本的字体尺寸。如当前对行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸。它会继承父级元素的字体大小，因此并不是一个固定的值。

**3、** rem是[CSS3](https://links.jianshu.com/go?to=http%3A%2F%2Fwww.html5cn.org%2Fportal.php%3Fmod%3Dlist%26catid%3D16)新增的一个相对单位（rootem，根 em），使用 rem 为元素设定字体大小时，仍然是相对大小，但相对的只是 HTML 根元素。

**4、** 区别：IE 无法调整那些使用 px 作为单位的字体大小，而 em 和 rem 可以缩放，rem 相对的只是 HTML 根元素。这个单位可谓集相对大小和绝对大小的优点于一身，通过它既可以做到只修改根元素就成比例地调整所有字体大小，又可以避免字体大小逐层复合的连锁反应。目前，除了 IE8 及更早版本外，所有浏览器均已支持 rem。


### [3、webSocket 如何兼容低版本浏览器？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#3websocket-如何兼容低版本浏览器)  


**1、** Adobe Flash Socket 、

**2、** ActiveX HTMLFile (IE) 、

**3、** 基于 multipart 编码发送 XHR 、

**4、** 基于长轮询的 XHR


### [4、介绍一下你对浏览器内核的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#4介绍一下你对浏览器内核的理解)  


主要分成两部分：渲染引擎(Layout Engine或Rendering Engine)和JS引擎。

渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。

JS引擎：解析和执行javascript来实现网页的动态效果。

最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。


### [5、网页验证码是干嘛的，是为了解决什么安全问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#5网页验证码是干嘛的是为了解决什么安全问题)  


区分用户是计算机还是人的公共全自动程序。可以防止恶意破解密码、刷票、论坛灌水

有效防止黑客对某一个特定注册用户用特定程序暴力破解方式进行不断的登陆尝试


### [6、浏览器的渲染原理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#6浏览器的渲染原理)  


首先解析收到的文档，根据文档定义构建一棵 DOM 树，DOM 树是由 DOM 元素及属性节点组成的。

然后对 CSS 进行解析，生成 CSSOM 规则树。

根据 DOM 树和 CSSOM 规则树构建渲染树。渲染树的节点被称为渲染对象，渲染对象是一个包含有颜色和大小等属性的矩形，渲染对象和 DOM 元素相对应，但这种对应关系不是一对一的，不可见的 DOM 元素不会被插入渲染树。还有一些 DOM 元素对应几个可见对象，它们一般是一些具有复杂结构的元素，无法用一个矩形来描述。

当渲染对象被创建并添加到树中，它们并没有位置和大小，所以当浏览器生成渲染树以后，就会根据渲染树来进行布局（也可以叫做回流）。这一阶段浏览器要做的事情是要弄清楚各个节点在页面中的确切位置和大小。通常这一行为也被称为“自动重排”。

布局阶段结束后是绘制阶段，遍历渲染树并调用渲染对象的 paint 方法将它们的内容显示在屏幕上，绘制使用 UI 基础组

件。

值得注意的是，这个过程是逐步完成的，为了更好的用户体验，渲染引擎将会尽可能早的将内容呈现到屏幕上，并不会等到所有的html 都解析完成之后再去构建和布局 render 树。它是解析完一部分内容就显示一部分内容，同时，可能还在通过网络下载其余内容。


### [7、HTML5 为什么只需要写 `<!DOCTYPE HTML>`，而不需要引入 DTD？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#7html5-为什么只需要写-<doctype-html>而不需要引入-dtd)  


HTML5 不基于 SGML，因此不需要对 DTD 进行引用，但是需要 DOCTYPE 来规范浏览器的行为（让浏览器按照它们应该的方式来运行）。

而 HTML4.01 基于 SGML ，所以需要对 DTD 进行引用，才能告知浏览器文档所使用的文档类型。


### [8、实现不使用 border 画出 1 px 高的线，在不同浏览器的标准模式与怪异模式下都能保持一致的效果。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#8实现不使用-border-画出-1-px-高的线在不同浏览器的标准模式与怪异模式下都能保持一致的效果。)  


```
html
<div style="height:1px;overflow:hidden;background:red"></div>
```


### [9、有一个导航栏在chrome 里面样式完好？在 IE 里文字都聚到一起了，是哪个兼容性问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#9有一个导航栏在chrome-里面样式完好在-ie-里文字都聚到一起了是哪个兼容性问题)  


用了 display：flex 属性，在 ie10 以下都是无效的。


### [10、`HTML5`的离线储存怎么使用，工作原理能不能解释一下？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#10html5的离线储存怎么使用工作原理能不能解释一下)  


**1、** 在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件

**2、** 原理：`HTML5`的离线存储是基于一个新建的`.appcache`文件的缓存机制(不是存储技术)，通过这个文件上的解析清单离线存储资源，这些资源就会像`cookie`一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示

**如何使用：**

**1、** 页面头部像下面一样加入一个`manifest`的属性；

**2、** 在`cache.manifest`文件的编写离线存储的资源

**3、** 在离线状态时，操作`window.applicationCache`进行需求实现

```
CACHE MANIFEST
#v0.11
CACHE:
js/app.js
css/style.css
NETWORK:
resourse/logo.png
FALLBACK:
/ /offline.html
```


### [11、介绍一下你对浏览器内核的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#11介绍一下你对浏览器内核的理解)  

### [12、介绍一下你对浏览器内核的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#12介绍一下你对浏览器内核的理解)  

### [13、你对浏览器的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#13你对浏览器的理解)  

### [14、语义化的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#14语义化的理解)  

### [15、link 标签定义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#15link-标签定义)  

### [16、什么是语义化的HTML?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#16什么是语义化的html)  

### [17、元素的alt和title有什么异同](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#17元素的alt和title有什么异同)  

### [18、简述一下你对HTML语义化的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#18简述一下你对html语义化的理解)  

### [19、iframe框架有那些优缺点](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#19iframe框架有那些优缺点)  

### [20、渲染页面时常见哪些不良现象？（浏览器渲染过程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#20渲染页面时常见哪些不良现象浏览器渲染过程)  

### [21、HTML部分常见问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#21html部分常见问题)  

### [22、HTML全局属性(global attribute)有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#22html全局属性global-attribute有哪些)  

### [23、attribute 和 property 的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#23attribute-和-property-的区别是什么)  

### [24、如何优化关键渲染路径？（浏览器渲染过程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#24如何优化关键渲染路径浏览器渲染过程)  

### [25、iframe有那些缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#25iframe有那些缺点)  

### [26、行内元素与块级元素的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#26行内元素与块级元素的区别)  

### [27、async 和 defer 的作用是什么？有什么区别？（浏览器解析过程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#27async-和-defer-的作用是什么有什么区别浏览器解析过程)  

### [28、实现不使用 border 画出1px高的线，在不同浏览器的Quirks mode和CSS Compat模式下都能保持同一效果**](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#28实现不使用-border-画出1px高的线在不同浏览器的quirks-mode和css-compat模式下都能保持同一效果**)  

### [29、HTTP的几种请求方法用途](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#29http的几种请求方法用途)  

### [30、HTML5的form如何关闭自动完成功能](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#30html5的form如何关闭自动完成功能)  

### [31、什么是BFC？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#31什么是bfc)  

### [32、前端需要注意哪些 SEO ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题带答案（2021年HTML面试题及答案大汇总）.md#32前端需要注意哪些-seo-)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
