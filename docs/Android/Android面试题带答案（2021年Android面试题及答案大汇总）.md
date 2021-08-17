# Android面试题带答案（2021年Android面试题及答案大汇总）

Android面试题及答案【最新版】Android高级面试题大全(2021版)，发现网上很多Android面试题及答案整理都没有答案，所以花了很长时间搜集，本套Android面试题大全，Android面试题大汇总，有大量经典的Android面试题以及答案，包含Android语言常见面试题、Android工程师高级面试题及一些大厂Android开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Android面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Android面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、Android中的ANR](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#1android中的anr)  


ANR的全称application not responding 应用程序未响应。

```
在android中Activity的最长执行时间是5秒。
BroadcastReceiver的最长执行时间则是10秒。
Service的最长执行时间则是20秒。
```

超出执行时间就会产生ANR。注意：ANR是系统抛出的异常，程序是捕捉不了这个异常的。

解决方法:

**1、** 运行在主线程里的任何方法都尽可能少做事情。特别是，Activity应该在它的关键生命周期方法 （如onCreate()和onResume()）里尽可能少的去做创建操作。（可以采用重新开启子线程的方式，然后使用Handler+Message 的方式做一些操作，比如更新主线程中的ui等）

**2、** 应用程序应该避免在BroadcastReceiver里做耗时的操作或计算。但不再是在子线程里做这些任务（因为 BroadcastReceiver的生命周期短），替代的是，如果响应Intent广播需要执行一个耗时的动作的话，应用程序应该启动一个 Service。


### [2、了解IntentServices吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#2了解intentservices吗)  


**1、** IntentService是Service的子类，是一个异步的，会自动停止的服务，很好解决了传统的Service中处理完耗时操作忘记停止并销毁Service的问题

**2、** 生成一个默认的且与线程相互独立的工作线程执行所有发送到onStartCommand()方法的Intent,可以在onHandleIntent()中处理.

**3、** 串行队列,每次只运行一个任务,不存在线程安全问题,所有任务执行完后自动停止服务,不需要自己手动调用stopSelf()来停止.


### [3、让Activity变成一个窗口](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#3让activity变成一个窗口)  


设置activity的style属性=”@android:style/Theme.Dialog”


### [4、android中的动画有哪几类，它们的特点和区别是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#4android中的动画有哪几类它们的特点和区别是什么)  


两种，一种是Tween动画、还有一种是Frame动画。Tween动画，这种实现方式可以使视图组件移动、放大、缩小以及产生透明度的变化;另一种Frame动画，传统的动画方法，通过顺序的播放排列好的图片来实现，类似电影。


### [5、Fragment的生命周期](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#5fragment的生命周期)  


Fragment的生命周期

![92_2.png][92_2.png]

Fragment与Activity生命周期对比

![92_3.png][92_3.png]

Fragment的生命周期方法主要有onAttach()、onCreate()、onCreateView()、onActivityCreated()、onstart()、onResume()、onPause()、onStop()、onDestroyView()、onDestroy()、onDetach()等11个方法。

**1、** 切换到该Fragment，分别执行onAttach()、onCreate()、onCreateView()、onActivityCreated()、onstart()、onResume()方法。

**2、** 锁屏，分别执行onPause()、onStop()方法。

**3、** 亮屏，分别执行onstart()、onResume()方法。

**4、** 覆盖，切换到其他Fragment，分别执行onPause()、onStop()、onDestroyView()方法。

**5、** 从其他Fragment回到之前Fragment，分别执行onCreateView()、onActivityCreated()、onstart()、onResume()方法。


### [6、为什么Android引入广播机制?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#6为什么android引入广播机制)  


**1、** 从MVC的角度考虑(应用程序内) 其实回答这个问题的时候还可以这样问，android为什么要有那4大组件，现在的移动开发模型基本上也是照搬的web那一套MVC架构，只不过是改了点嫁妆而已。

**2、** android的四大组件本质上就是为了实现移动或者说嵌入式设备上的MVC架构

**3、** 它们之间有时候是一种相互依存的关系，有时候又是一种补充关系，引入广播机制可以方便几大组件的信息和数据交互。

**4、** 程序间互通消息(例如在自己的应用程序内监听系统来电)

**5、** 效率上(参考UDP的广播协议在局域网的方便性)

**6、** 设计模式上(反转控制的一种应用，类似监听者模式)


### [7、都使用过哪些自定义控件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#7都使用过哪些自定义控件)  


**1、** pull2RefreshListView

**2、** LazyViewPager

**3、** SlidingMenu

**4、** SmoothProgressBar

**5、** 自定义组合控件

**6、** ToggleButton

**7、** 自定义Toast


### [8、Android中常用布局](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#8android中常用布局)  


常用的布局：

```
FrameLayout(帧布局):所有东西依次都放在左上角，会重叠
LinearLayout(线性布局):按照水平和垂直进行数据展示
RelativeLayout(相对布局):以某一个元素为参照物，来定位的布局方式
```

不常用的布局：

```
TableLayout(表格布局): 每一个TableLayout里面有表格行TableRow，TableRow里面可以具体定义每一个元素（Android TV上使用）
AbsoluteLayout(绝对布局):用X,Y坐标来指定元素的位置，元素多就不适用。（机顶盒上使用）
```

新增布局：

```
PercentRelativeLayout（百分比相对布局）可以通过百分比控制控件的大小。
PercentFrameLayout（百分比帧布局）可以通过百分比控制控件的大小。
```


### [9、android的数据存储](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#9android的数据存储)  


**1、** 使用SharedPreferences存储数据；它是Android提供的用来存储一些简单配置信息的一种机制，采用了XML格式将数据存储到设备中。只能在同一个包内使用，不能在不同的包之间使用。

**2、** 文件存储数据；文件存储方式是一种较常用的方法，在Android中读取/写入文件的方法，与Java中实现I/O的程序是完全一样的，提供了openFileInput()和openFileOutput()方法来读取设备上的文件。

**3、** SQLite数据库存储数据；SQLite是Android所带的一个标准的数据库，它支持SQL语句，它是一个轻量级的嵌入式数据库。

**4、** 使用ContentProvider存储数据；主要用于应用程序之间进行数据交换，从而能够让其他的应用保存或读取此Content Provider的各种数据类型。

**5、** 网络存储数据；通过网络上提供给我们的存储空间来上传(存储)和下载(获取)我们存储在网络空间中的数据信息。


### [10、RecyclerView和ListView的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#10recyclerview和listview的区别)  


缓存上:前者缓存的是View+ViewHolder+flag，不用每次调用findViewById,后者则只是缓存View

刷新数据方面，前者提供了局部刷新，后者则全部刷新


### [11、如何退出Activity？如何安全退出已调用多个Activity的Application？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#11如何退出activity如何安全退出已调用多个activity的application)  

### [12、请描述下Activity的生命周期。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#12请描述下activity的生命周期。)  

### [13、GLSurfaceView](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#13glsurfaceview)  

### [14、ListView 可以显示多种类型的条目吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#14listview-可以显示多种类型的条目吗)  

### [15、Android dvm的进程和Linux的进程, 应用程序的进程是否为同一个概念](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#15android-dvm的进程和linux的进程,-应用程序的进程是否为同一个概念)  

### [16、如何提升Service进程优先级](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#16如何提升service进程优先级)  

### [17、请解释下 Android 程序运行时权限与文件系统权限的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#17请解释下-android-程序运行时权限与文件系统权限的区别)  

### [18、开发中都使用过哪些框架、平台](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#18开发中都使用过哪些框架平台)  

### [19、如何将SQLite数据库(dictionary.db文件)与apk文件一起发布](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#19如何将sqlite数据库dictionarydb文件与apk文件一起发布)  

### [20、Android 中的动画有哪几类，它们的特点和区别是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#20android-中的动画有哪几类它们的特点和区别是什么)  

### [21、简述JNI](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#21简述jni)  

### [22、Android 中如何捕获未捕获的异常](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#22android-中如何捕获未捕获的异常)  

### [23、String,StringBuffer,StringBuilder的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#23string,stringbuffer,stringbuilder的区别)  

### [24、如何将SQLite数据库(dictionary.db文件)与apk文件一起发布?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#24如何将sqlite数据库dictionarydb文件与apk文件一起发布)  

### [25、什么是 IntentService？有何优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#25什么是-intentservice有何优点)  

### [26、简述TCP，UDP，Socket](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#26简述tcpudpsocket)  

### [27、注册广播的几种方法?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#27注册广播的几种方法)  

### [28、andorid 应用第二次登录实现自动登录](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#28andorid-应用第二次登录实现自动登录)  

### [29、请介绍下ContentProvider是如何实现数据共享的。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#29请介绍下contentprovider是如何实现数据共享的。)  

### [30、Android 引入广播机制的用意](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题带答案（2021年Android面试题及答案大汇总）.md#30android-引入广播机制的用意)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
