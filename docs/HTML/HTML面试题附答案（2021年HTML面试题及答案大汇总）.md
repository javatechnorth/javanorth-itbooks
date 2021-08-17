# HTML面试题附答案（2021年HTML面试题及答案大汇总）

HTML面试题及答案【最新版】HTML高级面试题大全(2021版)，发现网上很多HTML面试题及答案整理都没有答案，所以花了很长时间搜集，本套HTML面试题大全，HTML面试题大汇总，有大量经典的HTML面试题以及答案，包含HTML语言常见面试题、HTML工程师高级面试题及一些大厂HTML开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套HTML面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个HTML面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、常用的 meta 标签](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#1常用的-meta-标签)  


```
<meta> 元素可提供有关页面的元信息（meta-information），比如针对搜索引擎和更新频度的描述和关键词。
<meta> 标签位于文档的头部，不包含任何内容。<meta> 标签的属性定义了与文档相关联的名称/值对。

<!DOCTYPE html>  H5标准声明，使用 HTML5 doctype，不区分大小写
<head lang=”en”> 标准的 lang 属性写法
<meta charset=’utf-8′>    声明文档使用的字符编码
<meta http-equiv=”X-UA-Compatible” content=”IE=edge,chrome=1″/>   优先使用 IE 最新版本和 Chrome
<meta name=”description” content=”不超过150个字符”/>       页面描述
<meta name=”keywords” content=””/>      页面关键词者
<meta name=”author” content=”name, email@gmail.com”/>    网页作
<meta name=”robots” content=”index,follow”/>      搜索引擎抓取
<meta name=”viewport” content=”initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no”> 为移动设备添加 viewport
<meta name=”apple-mobile-web-app-title” content=”标题”> iOS 设备 begin
<meta name=”apple-mobile-web-app-capable” content=”yes”/>  添加到主屏后的标题（iOS 6 新增）
是否启用 WebApp 全屏模式，删除苹果默认的工具栏和菜单栏
<meta name=”apple-itunes-app” content=”app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL”>
添加智能 App 广告条 Smart App Banner（iOS 6+ Safari）
<meta name=”apple-mobile-web-app-status-bar-style” content=”black”/>
<meta name=”format-detection” content=”telphone=no, email=no”/>  设置苹果工具栏颜色
<meta name=”renderer” content=”webkit”>  启用360浏览器的极速模式(webkit)
<meta http-equiv=”X-UA-Compatible” content=”IE=edge”>     避免IE使用兼容模式
<meta http-equiv=”Cache-Control” content=”no-siteapp” />    不让百度转码
<meta name=”HandheldFriendly” content=”true”>     针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓
<meta name=”MobileOptimized” content=”320″>   微软的老式浏览器
<meta name=”screen-orientation” content=”portrait”>   uc强制竖屏
<meta name=”x5-orientation” content=”portrait”>    QQ强制竖屏
<meta name=”full-screen” content=”yes”>              UC强制全屏
<meta name=”x5-fullscreen” content=”true”>       QQ强制全屏
<meta name=”browsermode” content=”application”>   UC应用模式
<meta name=”x5-page-mode” content=”app”>    QQ应用模式
<meta name=”msapplication-tap-highlight” content=”no”>    windows phone 点击无高光
设置页面不缓存
<meta http-equiv=”pragma” content=”no-cache”>
<meta http-equiv=”cache-control” content=”no-cache”>
<meta http-equiv=”expires” content=”0″>
```


### [2、浏览器是怎么对`HTML5`的离线储存资源进行管理和加载的呢](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#2浏览器是怎么对html5的离线储存资源进行管理和加载的呢)  


**1、** 在线的情况下，浏览器发现`html`头部有`manifest`属性，它会请求`manifest`文件，如果是第一次访问`app`，那么浏览器就会根据manifest文件的内容下载相应的资源并且进行离线存储。如果已经访问过`app`并且资源已经离线存储了，那么浏览器就会使用离线的资源加载页面，然后浏览器会对比新的`manifest`文件与旧的`manifes`t文件，如果文件没有发生改变，就不做任何操作，如果文件改变了，那么就会重新下载文件中的资源并进行离线存储。

**2、** 离线的情况下，浏览器就直接使用离线存储的资源。


### [3、知道的网页制作会用到的图片格式有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#3知道的网页制作会用到的图片格式有哪些)  


png-8，png-24，jpeg，gif，svg。

但是上面的那些都不是面试官想要的最后答案。面试官希望听到是Webp。（是否有关注新技术，新鲜事物）

科普一下Webp：WebP格式，谷歌（google）开发的一种旨在加快图片加载速度的图片格式。图片压缩体积大约只有JPEG的2/3，并能节省大量的服务器带宽资源和数据空间。FacebookEbay等知名网站已经开始测试并使用WebP格式。

在质量相同的情况下，WebP格式图像的体积要比JPEG格式图像小40%


### [4、浏览器架构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#4浏览器架构)  


```
* 用户界面
  * 主进程
  * 内核
      * 渲染引擎
      * JS 引擎
          * 执行栈
      * 事件触发线程
          * 消息队列
              * 微任务
              * 宏任务
      * 网络异步线程
      * 定时器线程
```


### [5、怎么重构页面？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#5怎么重构页面)  


**1、** 编写 CSS

**2、** 让页面结构更合理化，提升用户体验

**3、** 实现良好的页面效果和提升性能


### [6、HTTP状态码及其含义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#6http状态码及其含义)  


**`1XX`：信息状态码**

**1、** `100 Continue` 继续，一般在发送`post`请求时，已发送了`http header`之后服务端将返回此信息，表示确认，之后发送具体参数信息

**`2XX`：成功状态码**

**1、** `200 OK` 正常返回信息

**2、** `201 Created` 请求成功并且服务器创建了新的资源

**3、** `202 Accepted` 服务器已接受请求，但尚未处理

**`3XX`：重定向**

**1、** `301 Moved Permanently` 请求的网页已永久移动到新位置。

**2、** `302 Found` 临时性重定向。

**3、** `303 See Other` 临时性重定向，且总是使用 `GET` 请求新的 `URI`。

**4、** `304 Not Modified` 自从上次请求后，请求的网页未修改过。

**`4XX`：客户端错误**

**1、** `400 Bad Request` 服务器无法理解请求的格式，客户端不应当尝试再次使用相同的内容发起请求。

**2、** `401 Unauthorized` 请求未授权。

**3、** `403 Forbidden` 禁止访问。

**4、** `404 Not Found` 找不到如何与 `URI` 相匹配的资源。

**`5XX:` 服务器错误**

**1、** `500 Internal Server Error` 最常见的服务器端错误。

**2、** `503 Service Unavailable` 服务器端暂时无法处理请求（可能是过载或维护）。


### [7、HTML元素的显示优先级？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#7html元素的显示优先级)  


帧元素（frame）>HTML元素优先，表单元素总>非表单元素优先

常见的非表单元素包括：链接标记（A），DIV标记，SPAN标记，TABLE标记等等。表单元素覆盖样式元素的根本原因在于HTML元素默认的显示优先级规则。

所有这样HTML元素又可以根据其显示要求分成两类，即有窗口的HTML元素(Windowed Element),无窗口的HTML元素（Windowless Element)。

有窗口的元素包括：SELECT元素，OBJECT元素，插件，IE5.01以主更早版本中的IFRAME元素。

无窗口的元素包括：大多数的普通HTML元素，如链接和TABLE标记，除了SELECT元素之外的大多数表单元素。


### [8、网页验证码是干嘛的，是为了解决什么安全问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#8网页验证码是干嘛的是为了解决什么安全问题)  


**1、** 区分用户是计算机还是人的程序;

**2、** 可以防止恶意破解密码、刷票、论坛灌水；


### [9、简述对Web 语义化的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#9简述对web-语义化的理解)  


就是让浏览器更好的读懂你写的代码，在进行 HTML 结构、表现、行为设计时，尽量使用语义化的标签，使程序代码简介明了，易于进行Web 操作和网站 SEO，方便团队协作的一种标准，以图实现一种“无障碍”的  Web 开发。


### [10、标签上title 与 alt 属性的区别是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#10标签上title-与-alt-属性的区别是什么)  


Alt 当图片不显示时，用文字代表。Title为该属性提供信息。


### [11、为什么操作 DOM 慢？（浏览器绘制过程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#11为什么操作-dom-慢浏览器绘制过程)  

### [12、渲染过程中遇到 JS 文件怎么处理？（浏览器解析过程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#12渲染过程中遇到-js-文件怎么处理浏览器解析过程)  

### [13、简述一下你对 HTML 语义化的理解？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#13简述一下你对-html-语义化的理解)  

### [14、title与h1的区别、b与strong的区别、i与em的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#14title与h1的区别b与strong的区别i与em的区别)  

### [15、xhtml和html有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#15xhtml和html有什么区别)  

### [16、页面导入样式时，使用link和@import有什么区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#16页面导入样式时使用link和@import有什么区别)  

### [17、如何处理 HTML5 新标签的浏览器兼容问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#17如何处理-html5-新标签的浏览器兼容问题)  

### [18、xhtml和 html 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#18xhtml和-html-有什么区别)  

### [19、在新窗口打开链接的方法是？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#19在新窗口打开链接的方法是)  

### [20、HTML标签：](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#20html标签：)  

### [21、如何在页面上实现一个圆形的可点击区域？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#21如何在页面上实现一个圆形的可点击区域)  

### [22、行内元素有哪些?块级元素有哪些?CSS的盒模型?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#22行内元素有哪些块级元素有哪些css的盒模型)  

### [23、页面可见性（Page Visibility API） 可以有哪些用途？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#23页面可见性page-visibility-api-可以有哪些用途)  

### [24、行内元素有哪些？块级元素有哪些？ 空(void)元素有那些](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#24行内元素有哪些块级元素有哪些-空void元素有那些)  

### [25、你做的页面在哪些流览器测试过？这些浏览器的内核分别是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#25你做的页面在哪些流览器测试过这些浏览器的内核分别是什么)  

### [26、css reset 和 normalize.css 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#26css-reset-和-normalizecss-有什么区别)  

### [27、`<img>` 的 title 和 alt 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#27<img>-的-title-和-alt-有什么区别)  

### [28、b 与 strong 的区别和 i 与 em 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#28b-与-strong-的区别和-i-与-em-的区别)  

### [29、请描述一下 `cookies`，`sessionStorage` 和 `localStorage` 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#29请描述一下-cookiessessionstorage-和-localstorage-的区别)  

### [30、iframe 有那些缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#30iframe-有那些缺点)  

### [31、页面导入样式时，使用 link 和 [@import ](/import ) 有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#31页面导入样式时使用-link-和-[@import-]/import--有什么区别)  

### [32、什么是重绘和回流？（浏览器绘制过程）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/HTML/HTML面试题附答案（2021年HTML面试题及答案大汇总）.md#32什么是重绘和回流浏览器绘制过程)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
