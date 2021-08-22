# HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）

HTML面试题及答案【最新版】HTML高级面试题大全(2021版)，发现网上很多HTML面试题及答案整理都没有答案，所以花了很长时间搜集，本套HTML面试题大全，HTML面试题大汇总，有大量经典的HTML面试题以及答案，包含HTML语言常见面试题、HTML工程师高级面试题及一些大厂HTML开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套HTML面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个HTML面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、无样式内容闪烁（FOUC）Flash of Unstyle Content**](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#1无样式内容闪烁foucflash-of-unstyle-content**)  


@import导入CSS文件会等到文档加载完后再加载CSS样式表。因此，在页面DOM加载完成到CSS导入完成之间会有一段时间页面上的内容是没有样式的。

解决方法：使用link标签加载CSS样式文件。因为link是顺序加载的，这样页面会等到CSS下载完之后再下载HTML文件，这样先布局好，就不会出现FOUC问题。


### [2、HTML5 的离线储存怎么使用，工作原理能不能解释一下？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#2html5-的离线储存怎么使用工作原理能不能解释一下)  


在用户没有与因特网连接时，可以正常访问站点或应用，在用户与因特网连接时，更新用户机器上的缓存文件。

原理：HTML5 的离线存储是基于一个新建的 .appcache 文件的缓存机制（不是存储技术），通过这个文件上的解析清单离线存储资源，这些资源就会像 cookie 一样被存储了下来。之后当网络在处于离线状态下时，浏览器会通过被离线存储的数据进行页面展示。

**如何使用：**

创建一个和 html 同名的 manifest 文件，然后在页面头部像下面一样加入一个 manifest 的属性。

`<html lang="en" manifest="index.manifest">`

在如下 cache.manifest 文件的编写离线存储的资源。

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

CACHE: 表示需要离线存储的资源列表，由于包含 manifest 文件的页面将被自动离线存储，所以不需要把页面自身也列出 来。

NETWORK: 表示在它下面列出来的资源只有在在线的情况下才能访问，他们不会被离线存储，所以在离线情况下无法使用这些资源。不过，如果在 CACHE 和 NETWORK 中有一个相同的资源，那么这个资源还是会被离线存储，也就是说 CACHE 的优先级更高。

FALLBACK: 表示如果访问第一个资源失败，那么就使用第二个资源来替换他，比如上面这个文件表示的就是如果访问根目录下任何一个资源失败了，那么就去访问 offline.html 。
```

（3）在离线状态时，操作 window.applicationCache 进行离线缓存的操作。

**如何更新缓存：**

**1、** 更新 manifest 文件

**2、** 通过 javascript 操作

**3、** 清除浏览器缓存

**注意事项：**

**1、** 浏览器对缓存数据的容量限制可能不太一样（某些浏览器设置的限制是每个站点 5MB）。

**2、** 如果 manifest 文件，或者内部列举的某一个文件不能正常下载，整个更新过程都将失败，浏览器继续全部使用老的缓存。

**3、** 引用 manifest 的 html 必须与 manifest 文件同源，在同一个域下。

**4、** FALLBACK 中的资源必须和 manifest 文件同源。

**5、** 当一个资源被缓存后，该浏览器直接请求这个绝对路径也会访问缓存中的资源。

**6、** 站点中的其他页面即使没有设置 manifest 属性，请求的资源如果在缓存中也从缓存中访问。

**7、** 当 manifest 文件发生改变时，资源请求本身也会触发更新。


### [3、title 与 h1 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#3title-与-h1-的区别)  


title 属性没有明确意义只表示是个标题，h1 则表示层次明确的标题，对页面信息的抓取也有很大的影响。


### [4、请描述一下 cookies，sessionStorage 和 localStorage 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#4请描述一下-cookiessessionstorage-和-localstorage-的区别)  


**相关资料：**

SessionStorage， LocalStorage， Cookie 这三者都可以被用来在浏览器端存储数据，而且都是字符串类型的键值对。区别在于前两者属于 HTML5 WebStorage，创建它们的目的便于客户端存储数据。而 cookie 是网站为了标示用户身份而储存在用户本地终端上的数据（通常经过加密）。cookie 数据始终在同源（协议、主机、端口相同）的 http 请求中携带（即使不需要），会在浏览器和服务器间来回传递。

**存储大小：**

**1、** cookie 数据大小不能超过4 k 。

**2、** sessionStorage 和 localStorage 虽然也有存储大小的限制，但比 cookie 大得多，可以达到 5M 或更大。

**有期时间：**

**1、** localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据。

**2、** sessionStorage  数据在页面会话结束时会被清除。页面会话在浏览器打开期间一直保持，并且重新加载或恢复页面仍会保持原来的页面会话。在新标签或窗口打开一个页面时会在顶级浏览上下文中初始化一个新的会话。

**3、** cookie          设置的 cookie 过期时间之前一直有效，即使窗口或浏览器关闭。

**作用域：**

**1、** sessionStorage  只在同源的同窗口（或标签页）中共享数据，也就是只在当前会话中共享。

**2、** localStorage    在所有同源窗口中都是共享的。

**3、** cookie          在所有同源窗口中都是共享的。

**回**

浏览器端常用的存储技术是 cookie 、localStorage 和 sessionStorage。

cookie 其实最开始是服务器端用于记录用户状态的一种方式，由服务器设置，在客户端存储，然后每次发起同源请求时，发送给服务器端。cookie 最多能存储 4 k 数据，它的生存时间由 expires 属性指定，并且 cookie 只能被同源的页面访问共享。

sessionStorage 是 html5 提供的一种浏览器本地存储的方法，它借鉴了服务器端 session 的概念，代表的是一次会话中所保存的数据。它一般能够存储 5M 或者更大的数据，它在当前窗口关闭后就失效了，并且 sessionStorage 只能被同一个窗口的同源页面所访问共享。

localStorage 也是 html5 提供的一种浏览器本地存储的方法，它一般也能够存储 5M 或者更大的数据。它和 sessionStorage 不同的是，除非手动删除它，否则它不会失效，并且 localStorage 也只能被同源页面所访问共享。

上面几种方式都是存储少量数据的时候的存储方式，当我们需要在本地存储大量数据的时候，我们可以使用浏览器的 indexDB 这是浏览器提供的一种本地的数据库存储机制。它不是关系型数据库，它内部采用对象仓库的形式存储数据，它更接近 NoSQL 数据库。


### [5、`<img>`的`title`和`alt`有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#5<img>的title和alt有什么区别)  


通常当鼠标滑动到元素上的时候显示

`alt`是`<img>`的特有属性，是图片内容的等价描述，用于图片无法加载时显示、读屏器阅读图片。可提图片高可访问性，除了纯装饰图片外都必须设置有意义的值，搜索引擎会重点分析。


### [6、什么是文档的预解析？（浏览器解析过程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#6什么是文档的预解析浏览器解析过程)  


Webkit 和 Firefox 都做了这个优化，当执行 JavaScript 脚本时，另一个线程解析剩下的文档，并加载后面需要通过网络加载的资源。这种方式可以使资源并行加载从而使整体速度更快。需要注意的是，预解析并不改变 DOM 树，它将这个工作留给主解析过程，自己只解析外部资源的引用，比如外部脚本、样式表及图片。


### [7、如何在页面上实现一个圆形的可点击区域](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#7如何在页面上实现一个圆形的可点击区域)  


**1、** map+area或者svg

**2、** border-radius

**3、** 纯js实现，一个点不在圆上的算法


### [8、选择器优先级是怎样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#8选择器优先级是怎样的)  


！important>行内样式>id 选择器>类选择器>标签选择器>通配符>继承

权重[算法](/jump/super-jump/word?word=%E7%AE%97%E6%B3%95)：

（0，0，0，0）==》第一个 0 对应的是 important 的个数，第二个 0 对应的是 id 选择器的个数，第三个 0 对

应的类选择器的个数，第四个 0 对应的是标签选择器的个数，就是当前选择器的权重。

比较：

先从第一个 0 开始比较，如果第一个 0 大，那么说明这个选择器的权重高，如果第一个相同，比较第二个，依次类推


### [9、页面可见性（Page Visibility）API 可以有哪些用途](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#9页面可见性page-visibilityapi-可以有哪些用途)  


**1、** 通过visibility state的值得检测页面当前是否可见，以及打开网页的时间。

**2、** 在页面被切换到其他后台进程时，自动暂停音乐或视频的播放。


### [10、如何进行网站性能优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#10如何进行网站性能优化)  


`content`方面

**1、** 减少`HTTP`请求：合并文件、`CSS`精灵、`inline Image`

**2、** 减少`DNS`查询：`DNS`缓存、将资源分布到恰当数量的主机名

**3、** 减少`DOM`元素数量

`Server`方面

**1、** 使用`CDN`

**2、** 配置`ETag`

**3、** 对组件使用`Gzip`压缩

`Cookie`方面

**1、** 减小`cookie`大小

`css`方面

**1、** 将样式表放到页面顶部

**2、** 不使用`CSS`表达式

**3、** 使用`<link>`不使用`@import`

`Javascript`方面

**1、** 将脚本放到页面底部

**2、** 将`javascript`和`css`从外部引入

**3、** 压缩`javascript`和`css`

**4、** 删除不需要的脚本

**5、** 减少`DOM`访问

图片方面

**1、** 优化图片：根据实际颜色需要选择色深、压缩

**2、** 优化`css`精灵

**3、** 不要在`HTML`中拉伸图片


### [11、WEB标准以及W3C标准是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#11web标准以及w3c标准是什么)  

### [12、用于预格式化文本的标签是？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#12用于预格式化文本的标签是)  

### [13、webSocket如何兼容低浏览器](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#13websocket如何兼容低浏览器)  

### [14、每个HTML 文件里开头都有个很重要的东西，Doctype，知道这是干什么的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#14每个html-文件里开头都有个很重要的东西doctype知道这是干什么的吗)  

### [15、改变元素的外边距用什么属性？改变元素的内填充用什么属性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#15改变元素的外边距用什么属性改变元素的内填充用什么属性)  

### [16、如何实现浏览器内多个标签页之间的通信?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#16如何实现浏览器内多个标签页之间的通信)  

### [17、合理的页面布局中常听过结构与表现分离，那么结构是什么？表现是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#17合理的页面布局中常听过结构与表现分离那么结构是什么表现是什么)  

### [18、cookies，sessionStorage和localStorage的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#18cookiessessionstorage和localstorage的区别)  

### [19、表格自动换行怎么实现？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#19表格自动换行怎么实现)  

### [20、如何实现浏览器内多个标签页之间的通信?**](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#20如何实现浏览器内多个标签页之间的通信**)  

### [21、img的alt与title有何异同？ strong与em的异同？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#21img的alt与title有何异同-strong与em的异同)  

### [22、空元素定义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#22空元素定义)  

### [23、SGML 、 HTML 、XML 和 XHTML 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#23sgml--html-xml-和-xhtml-的区别)  

### [24、HTML5为什么只需要写](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#24html5为什么只需要写)  

### [25、每个HTML文件里开头都有个很重要的东西，Doctype，知道这是干什么的吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#25每个html文件里开头都有个很重要的东西doctype知道这是干什么的吗)  

### [26、HTML5 的 form 的自动完成功能是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#26html5-的-form-的自动完成功能是什么)  

### [27、DOMContentLoaded 事件和 Load 事件的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#27domcontentloaded-事件和-load-事件的区别)  

### [28、行内元素定义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#28行内元素定义)  

### [29、行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？行内元素和块级元素有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#29行内元素有哪些块级元素有哪些-空void元素有那些行内元素和块级元素有什么区别)  

### [30、HTML5 有哪些新特性、移除了那些元素？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#30html5-有哪些新特性移除了那些元素)  

### [31、前端需要注意哪些SEO](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML中级面试题汇总及答案（2021年HTML面试题及答案大全）.md#31前端需要注意哪些seo)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
