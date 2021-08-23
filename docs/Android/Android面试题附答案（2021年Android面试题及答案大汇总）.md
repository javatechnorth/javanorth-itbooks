# Android面试题附答案（2021年Android面试题及答案大汇总）

Android面试题及答案【最新版】Android高级面试题大全(2021版)，发现网上很多Android面试题及答案整理都没有答案，所以花了很长时间搜集，本套Android面试题大全，Android面试题大汇总，有大量经典的Android面试题以及答案，包含Android语言常见面试题、Android工程师高级面试题及一些大厂Android开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Android面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Android面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Android中的长度单位详解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#1android中的长度单位详解)  


```
Px：像素
Sp与dp也是长度单位，但是与屏幕的单位密度无关。
```


### [2、Android与服务器交互的方式中的对称加密和非对称加密是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#2android与服务器交互的方式中的对称加密和非对称加密是什么)  


对称加密，就是加密和解密数据都是使用同一个key，这方面的算法有DES。

非对称加密，加密和解密是使用不同的key。发送数据之前要先和服务端约定生成公钥和私钥，使用公钥加密的数据可以用私钥解密，反之。这方面的算法有RSA。ssh 和 ssl都是典型的非对称加密。


### [3、activity的启动模式有哪些？是什么含义](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#3activity的启动模式有哪些是什么含义)  


在android里，有4种activity的启动模式，分别为：

**1、** “standard” (默认)

**2、** “singleTop”

**3、** “singleTask”

**4、** “singleInstance”

它们主要有如下不同

**1、** 如何决定所属task

“standard”和”singleTop”的activity的目标task，和收到的Intent的发送者在同一个task内，除非intent包括参数FLAG_ACTIVITY_NEW_TASK

如果提供了FLAG_ACTIVITY_NEW_TASK参数，会启动到别的task里。

“singleTask”和”singleInstance”总是把activity作为一个task的根元素，他们不会被启动到一个其他task里

**2、** 是否允许多个实例

“standard”和”singleTop”可以被实例化多次，并且存在于不同的task中，且一个task可以包括一个activity的多个实例；

“singleTask”和”singleInstance”则限制只生成一个实例，并且是task的根元素。 singleTop要求如果创建intent的时候栈顶已经有要创建的Activity的实例，则将intent发送给该实例，而不发送给新的实例

**3、** 是否允许其它activity存在于本task内

“singleInstance”独占一个task，其它activity不能存在那个task里；如果它启动了一个新的activity，不管新的activity的launch mode 如何，新的activity都将会到别的task里运行（如同加了FLAG_ACTIVITY_NEW_TASK参数）。

而另外三种模式，则可以和其它activity共存

**4、** 是否每次都生成新实

“standard”对于没一个启动Intent都会生成一个activity的新实例；

“singleTop”的activity如果在task的栈顶的话，则不生成新的该activity的实例，直接使用栈顶的实例，否则，生成该activity的实例。

比如现在task栈元素为A-B-C-D（D在栈顶），这时候给D发一个启动intent，如果D是 “standard”的，则生成D的一个新实例，栈变为A－B－C－D－D

如果D是singleTop的话，则不会生产D的新实例，栈状态仍为A-B-C-D

如果这时候给B发Intent的话，不管B的launchmode是”standard” 还是 “singleTop” ，都会生成B的新实例，栈状态变为A-B-C-D-B

“singleInstance”是其所在栈的唯一activity，它会每次都被重用

“singleTask”如果在栈顶，则接受intent，否则，该intent会被丢弃，但是该task仍会回到前台

当已经存在的activity实例处理新的intent时候，会调用onNewIntent()方法 如果收到intent生成一个activity实例，那么用户可以通过back键回到上一个状态；如果是已经存在的一个activity来处理这个intent的话，用户不能通过按back键返回到这之前的状态


### [4、Android系统的架构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#4android系统的架构)  


**1、** Android系统架构之应用程序

Android会同一系列核心应用程序包一起发布，该应用程序包包括email客户端，SMS短消息程序，日历，地图，浏览器，联系人管理程序等。所有的应用程序都是使用JAVA语言编写的。

**2、** Android系统架构之应用程序框架

开发人员可以完全访问核心应用程序所使用的API框架（android.jar）。该应用程序的架构设计简化了组件的重用;任何一个应用程序都可以发布它的功能块并且任何其它的应用程序都可以使用其所发布的功能块。

**3、** Android系统架构之系统运行库

Android 包含一些C/C++库，这些库能被Android系统中不同的组件使用。它们通过 Android 应用程序框架为开发者提供服务。

**4、** Android系统架构之Linux 内核

Android 的核心系统服务依赖于 Linux 2.6 内核，如安全性，内存管理，进程管理， 网络协议栈和驱动模型。 Linux 内核也同时作为硬件和软件栈之间的抽象层。


### [5、启动一个程序，可以主界面点击图标进入，也可以从一个程序中跳转过去，二者有什么区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#5启动一个程序可以主界面点击图标进入也可以从一个程序中跳转过去二者有什么区别)  


通过主界面进入，就是设置默认启动的activity。在manifest.xml文件的activity标签中，写以下代码

```
<intent- filter>
<intent android:name=“android.intent.action.MAIN”>
<intent android:name=”android:intent.category.LAUNCHER”>
</intent-filter>
```

从另一个组件跳转到目标activity，需要通过intent进行跳转。具体

```
Intent intent=new Intent(this,activity.class),startActivity(intent)
```


### [6、一条最长的短信息约占多少byte?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#6一条最长的短信息约占多少byte)  


中文70(包括标点)，英文160，160个字节。


### [7、Service 里面可以弹吐司么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#7service-里面可以弹吐司么)  


可以。


### [8、activity，fragment传值问题](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#8activityfragment传值问题)  


通过Bundle传值，在activty定义变量传值，扩展fragment创建传值


### [9、jni 的调用过程?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#9jni-的调用过程)  


**1、** 安装和下载 Cygwin，下载 Android NDK。

**2、** ndk 项目中 JNI 接口的设计。

**3、** 使用 C/C++实现本地方法。

**4、** JNI 生成动态链接库.so 文件。

**5、** 将动态链接库复制到 java 工程，在 java 工程中调用，运行 java 工程即可。


### [10、Manifest.xml文件中主要包括哪些信息？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#10manifestxml文件中主要包括哪些信息)  


**1、** manifest：根节点，描述了package中所有的内容。

**2、** uses-permission：请求你的package正常运作所需赋予的安全许可。

**3、** permission： 声明了安全许可来限制哪些程序能你package中的组件和功能。

**4、** instrumentation：声明了用来测试此package或其他package指令组件的代码。

**5、** application：包含package中application级别组件声明的根节点。

**6、** activity：Activity是用来与用户交互的主要工具。

**7、** receiver：IntentReceiver能使的application获得数据的改变或者发生的操作，即使它当前不在运行。

**8、** service：Service是能在后台运行任意时间的组件。

**9、** provider：ContentProvider是用来管理持久化数据并发布给其他应用程序使用的组件。


### [11、Fragment 的 replace 和 add 方法的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#11fragment-的-replace-和-add-方法的区别)  

### [12、Service和Thread的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#12service和thread的区别)  

### [13、AsyncTask](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#13asynctask)  

### [14、嵌入式操作系统内存管理有哪几种， 各有何特性](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#14嵌入式操作系统内存管理有哪几种-各有何特性)  

### [15、Intent 传递数据时，可以传递哪些类型数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#15intent-传递数据时可以传递哪些类型数据)  

### [16、Android i18n](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#16android-i18n)  

### [17、android:gravity与android:layout_gravity的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#17android:gravity与android:layout_gravity的区别)  

### [18、如何在 ScrollView 中如何嵌入 ListView](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#18如何在-scrollview-中如何嵌入-listview)  

### [19、SharedPreference跨进程使用会怎么样？如何保证跨进程使用安全？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#19sharedpreference跨进程使用会怎么样如何保证跨进程使用安全)  

### [20、Activity间通过Intent传递数据大小有没有限制？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#20activity间通过intent传递数据大小有没有限制)  

### [21、ListView 如何实现分页加载](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#21listview-如何实现分页加载)  

### [22、广播注册](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#22广播注册)  

### [23、横竖屏切换的Activity 生命周期变化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#23横竖屏切换的activity-生命周期变化)  

### [24、谈谈你对 Bitmap 的理解, 什么时候应该手动调用 bitmap.recycle()](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#24谈谈你对-bitmap-的理解,-什么时候应该手动调用-bitmaprecycle)  

### [25、View](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#25view)  

### [26、如何切换 fragement,不重新实例化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#26如何切换-fragement,不重新实例化)  

### [27、如何启用Service，如何停用Service。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#27如何启用service如何停用service。)  

### [28、recyclerView嵌套卡顿解决如何解决](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#28recyclerview嵌套卡顿解决如何解决)  

### [29、如何对 Android 应用进行性能分析](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#29如何对-android-应用进行性能分析)  

### [30、如果后台的Activity由于某原因被系统回收了，如何在被系统回收之前保存当前状态？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案（2021年Android面试题及答案大汇总）.md#30如果后台的activity由于某原因被系统回收了如何在被系统回收之前保存当前状态)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
