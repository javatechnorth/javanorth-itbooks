# HTML面试题汇总及答案（2021年HTML面试题及答案大全）

HTML面试题及答案【最新版】HTML高级面试题大全(2021版)，发现网上很多HTML面试题及答案整理都没有答案，所以花了很长时间搜集，本套HTML面试题大全，HTML面试题大汇总，有大量经典的HTML面试题以及答案，包含HTML语言常见面试题、HTML工程师高级面试题及一些大厂HTML开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套HTML面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个HTML面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Iframe的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#1iframe的作用)  


**用法：**

Iframe是用来在网页中插入第三方页面，早期的页面使用 iframe 主要是用于导航栏这种很多页面都相同的部分，这样可以在切换页面的时候避免重复下载。

优点：便于修改，模块分离，像一些信息管理系统会用到。但现在基本上不推荐使用。除非特殊需要，一般不推荐使用。

**缺点 :**

**1、** iframe 的创建比一般的 DOM 元素慢了 1-2 个数量级

**2、** iframe 标签会阻塞页面的加载，如果页面的onload 事件不能及时触发，会让用户觉得网页加载很慢，用户体验不好.在 Safari 和 Chrome 中可以通过 js 动态设置 iframe 的 src 属性来避免阻塞.

**3、** iframe 对于 SEO 不友好，替代方案一般就是动态语言的 Incude 机制和 ajax 动态填充内容等.


### [2、常见的浏览器端的存储技术有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#2常见的浏览器端的存储技术有哪些)  


浏览器常见的存储技术有 cookie、localStorage 和 sessionStorage。

还有两种存储技术用于大规模数据存储，webSQL（已被废除）和 indexDB。

IE 支持 userData 存储数据，但是基本很少使用到，除非有很强的浏览器兼容需求。


### [3、HTML5有哪些新特性,移除了那些元素？如何处理HTML5新标签的浏览器兼容问题？如何区分HTML和HTML5**](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#3html5有哪些新特性,移除了那些元素如何处理html5新标签的浏览器兼容问题如何区分html和html5**)  


新增加了图像、位置、存储、多任务等功能。

**新增元素：**

**1、** canvas

**2、** 用于媒介回放的video和audio元素

**3、** 本地离线存储。localStorage长期存储数据，浏览器关闭后数据不丢失;sessionStorage的数据在浏览器关闭后自动删除

**4、** 语意化更好的内容元素，比如 article footer header nav section

**5、** 位置API：Geolocation

**6、** 表单控件，calendar date time email url search

**7、** 新的技术：web worker(web worker是运行在后台的 JavaScript，独立于其他脚本，不会影响页面的性能。您可以继续做任何愿意做的事情：点击、选取内容等等，而此时 web worker 在后台运行) web socket


### [4、简述一下src与href的区别。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#4简述一下src与href的区别。)  


src用于替换当前元素，href用于在当前文档和引用资源之间确立联系。

src是source的缩写，指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在请求src资源时会将其指向的资源下载并应用到文档内，例如js脚本，img图片和frame等元素。
当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也如此，类似于将所指向资源嵌入当前标签内。这也是为什么将js脚本放在底部而不是头部。

href是Hypertext Reference的缩写，指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接，如果我们在文档中添加


那么浏览器会识别该文档为css文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议使用link方式来加载css，而不是使用@import方式。


### [5、常见浏览器所用内核](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#5常见浏览器所用内核)  


IE 浏览器内核：Trident 内核，也是俗称的 IE 内核；

Chrome 浏览器内核：统称为 Chromium 内核或 Chrome 内核，以前是 Webkit 内核，现在是 Blink内核；

Firefox 浏览器内核：Gecko 内核，俗称 Firefox 内核；

Safari 浏览器内核：Webkit 内核；

Opera 浏览器内核：最初是自己的 Presto 内核，后来加入谷歌大军，从 Webkit 又到了 Blink 内核；

360浏览器、猎豹浏览器内核：IE + Chrome 双内核；

搜狗、遨游、QQ 浏览器内核：Trident（兼容模式）+ Webkit（高速模式）；

百度浏览器、世界之窗内核：IE 内核；

2345浏览器内核：好像以前是 IE 内核，现在也是 IE + Chrome 双内核了；

UC 浏览器内核：这个众口不一，UC 说是他们自己研发的 U3 内核，但好像还是基于 Webkit 和 Trident ，还有说是基于火狐内核。


### [6、DOCTYPE 的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#6doctype-的作用是什么)  


**相关知识点：**

IE5.5 引入了文档模式的概念，而这个概念是通过使用文档类型（DOCTYPE）切换实现的。
DOCTYPE 不存在或格式不正确会导致文档以兼容模式呈现。
在 html5 之后不再需要指定 DTD 文档，因为 html5 以前的 html 文档都是基于 SGML 的，所以需要通过指定 DTD 来定义文档中允许的属性以及一些规则。而 html5 不再基于 SGML 了，所以不再需要使用 DTD。


### [7、如何减少回流？（浏览器绘制过程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#7如何减少回流浏览器绘制过程)  


**1、** 使用 transform 替代 top

**2、** 不要把节点的属性值放在一个循环里当成循环里的变量

**3、** 不要使用 table 布局，可能很小的一个小改动会造成整个 table 的重新布局

**4、** 把 DOM 离线后修改。如：使用 documentFragment 对象在内存里操作 DOM

**5、** 不要一条一条地修改 DOM 的样式。与其这样，还不如预先定义好 css 的 class，然后修改 DOM 的 className。


### [8、Label 的作用是什么？是怎么用的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#8label-的作用是什么是怎么用的)  


label 标签来定义表单控制间的关系，当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。

Number:




### [9、label的作用是什么? 是怎么用的?**](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#9label的作用是什么-是怎么用的**)  


label标签用来定义表单控件间的关系,当用户选择该标签时，浏览器会自动将焦点转到和标签相关的表单控件上。label 中有两个属性是非常有用的, FOR和ACCESSKEY。

FOR属性功能：表示label标签要绑定的HTML元素，你点击这个标签的时候，所绑定的元素将获取焦点。例如，

```
<Label FOR="InputBox">姓名</Label><input ID="InputBox" type="text">
```

ACCESSKEY属性功能：表示访问label标签所绑定的元素的热键，当您按下热键，所绑定的元素将获取焦点。例如，

```
<Label FOR="InputBox" ACCESSKEY＝"N">姓名</Label><input ID="InputBox" type="text">
```


### [10、常见的浏览器内核比较](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#10常见的浏览器内核比较)  


Trident：这种浏览器内核是 IE 浏览器用的内核，因为在早期 IE 占有大量的市场份额，所以这种内核比较流行，以前有很多网页也是根据这个内核的标准来编写的，但是实际上这个内核对真正的网页标准支持不是很好。但是由于 IE 的高市场占有率，微软也很长时间没有更新 Trident 内核，就导致了 Trident 内核和 W3C 标准脱节。还有就是 Trident 内核的大量 Bug 等安全问题没有得到解决，加上一些专家学者公开自己认为 IE 浏览器不安全的观点，使很多用户开始转向其他浏览器。

Gecko：这是 Firefox 和 Flock 所采用的内核，这个内核的优点就是功能强大、丰富，可以支持很多复杂网页效果和浏览器扩展接口，但是代价是也显而易见就是要消耗很多的资源，比如内存。

Presto：Opera 曾经采用的就是 Presto 内核，Presto 内核被称为公认的浏览网页速度最快的内核，这得益于它在开发时的天生优势，在处理 JS 脚本等脚本语言时，会比其他的内核快3倍左右，缺点就是为了达到很快的速度而丢掉了一部分网页兼容性。

Webkit：Webkit 是 Safari 采用的内核，它的优点就是网页浏览速度较快，虽然不及 Presto 但是也胜于 Gecko 和 Trident，缺点是对于网页代码的容错性不高，也就是说对网页代码的兼容性较低，会使一些编写不标准的网页无法正确显示。WebKit 前身是 KDE 小组的 KHTML 引擎，可以说 WebKit 是 KHTML 的一个开源的分支。

Blink：谷歌在 Chromium Blog 上发表博客，称将与苹果的开源浏览器核心 Webkit 分道扬镳，在 Chromium 项目中研发 Blink 渲染引擎（即浏览器核心），内置于 Chrome 浏览器之中。其实 Blink 引擎就是 Webkit 的一个分支，就像 webkit 是KHTML 的分支一样。Blink 引擎现在是谷歌公司与 Opera Software 共同研发，上面提到过的，Opera 弃用了自己的 Presto 内核，加入 Google 阵营，跟随谷歌一起研发 Blink。


### [11、Doctype作用? 严格模式与混杂模式如何区分？它们有何意义?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#11doctype作用-严格模式与混杂模式如何区分它们有何意义)  

### [12、标准模式与兼容模式各有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#12标准模式与兼容模式各有什么区别)  

### [13、浏览器是怎么对 HTML5 的离线储存资源进行管理和加载的呢？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#13浏览器是怎么对-html5-的离线储存资源进行管理和加载的呢)  

### [14、HTML5的文件离线储存怎么使用，工作原理是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#14html5的文件离线储存怎么使用工作原理是什么)  

### [15、CSS 如何阻塞文档解析？（浏览器解析过程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#15css-如何阻塞文档解析浏览器解析过程)  

### [16、box-sizing、transition、translate分别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#16box-sizingtransitiontranslate分别是什么)  

### [17、HTML5 元素的分类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#17html5-元素的分类)  

### [18、Flash、Ajax 各自的优缺点，在使用中如何取舍？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#18flashajax-各自的优缺点在使用中如何取舍)  

### [19、html5有哪些新特性、移除了那些元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#19html5有哪些新特性移除了那些元素)  

### [20、DOCTYPE有什么作用？标准模式与混杂模式如何区分？它们有何意义?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#20doctype有什么作用标准模式与混杂模式如何区分它们有何意义)  

### [21、拖放API：drag、drop](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#21拖放api：dragdrop)  

### [22、display：none；与 visibility： hidden 的区别是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#22display：none；与-visibility：-hidden-的区别是什么)  

### [23、DTD 介绍](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#23dtd-介绍)  

### [24、Canvas 和 SVG 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#24canvas-和-svg-有什么区别)  

### [25、块级元素定义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#25块级元素定义)  

### [26、IE 各版本和 Chrome 可以并行下载多少个资源？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#26ie-各版本和-chrome-可以并行下载多少个资源)  

### [27、前端页面有哪三层构成，分别是什么?作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#27前端页面有哪三层构成分别是什么作用是什么)  

### [28、position几个属性的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#28position几个属性的作用)  

### [29、对 web 标准、可用性、可访问性的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#29对-web-标准可用性可访问性的理解)  

### [30、常见的浏览器内核有哪些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#30常见的浏览器内核有哪些)  

### [31、渐进增强和优雅降级的定义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题汇总及答案（2021年HTML面试题及答案大全）.md#31渐进增强和优雅降级的定义)  





