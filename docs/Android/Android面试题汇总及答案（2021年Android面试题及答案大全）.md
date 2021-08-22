# Android面试题汇总及答案（2021年Android面试题及答案大全）

Android面试题及答案【最新版】Android高级面试题大全(2021版)，发现网上很多Android面试题及答案整理都没有答案，所以花了很长时间搜集，本套Android面试题大全，Android面试题大汇总，有大量经典的Android面试题以及答案，包含Android语言常见面试题、Android工程师高级面试题及一些大厂Android开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Android面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Android面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、怎样对 android 进行优化？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#1怎样对-android-进行优化)  


**1、** 对 listview 的优化。

**2、** 对图片的优化。

**3、** 对内存的优化。

**4、** 具体一些措施

**5、** 尽量不要使用过多的静态类 static

**6、** 数据库使用完成后要记得关闭 cursor

**7、** 广播使用完之后要注销


### [2、Android中4大组件](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#2android中4大组件)  


**1、** Activity：Activity是Android程序与用户交互的窗口，是Android构造块中最基本的一种，它需要为保持各界面的状态，做很多持久化的事情，妥善管理生命周期以及一些跳转逻辑。

**2、** BroadCast Receiver：接受一种或者多种Intent作触发事件，接受相关消息，做一些简单处理，转换成一条Notification，统一了Android的事件广播模型。

**3、** Content Provider：是Android提供的第三方应用数据的访问方案，可以派生Content Provider类，对外提供数据，可以像数据库一样进行选择排序，屏蔽内部数据的存储细节，向外提供统一的接口模型，大大简化上层应用，对数据的整合提 供了更方便的途径。

**4、** service：后台服务于Activity，封装有一个完整的功能逻辑实现，接受上层指令，完成相关的事务，定义好需要接受的Intent提供同步和异步的接口。


### [3、SQLite支持事务吗? 添加删除如何提高性能?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#3sqlite支持事务吗-添加删除如何提高性能)  


在sqlite插入数据的时候默认一条语句就是一个事务，有多少条数据就有多少次磁盘操作 比如5000条记录也就是要5000次读写磁盘操作。

添加事务处理，把多条记录的插入或者删除作为一个事务


### [4、推送到达率如何提高](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#4推送到达率如何提高)  


判手机系统，小米使用小米推送，华为使用华为推送，其他手机使用友盟推送


### [5、Android本身的api并未声明会抛出异常，则其在运行时有无可能抛出runtime异常，你遇到过吗？诺有的话会导致什么问题？如何解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#5android本身的api并未声明会抛出异常则其在运行时有无可能抛出runtime异常你遇到过吗诺有的话会导致什么问题如何解决)  


会，比如nullpointerException。我遇到过，比如textview.setText()时，textview没有初始化。会导致程序无法正常运行出现forceclose。打开控制台查看logcat信息找出异常信息并修改程序。


### [6、如果有个100M大的文件，需要上传至服务器中，而服务器form表单最大只能上传2M，可以用什么方法。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#6如果有个100m大的文件需要上传至服务器中而服务器form表单最大只能上传2m可以用什么方法。)  


首先来说使用http协议上传数据，特别在android下，跟form没什么关系。

传统的在web中，在form中写文件上传，其实浏览器所做的就是将我们的数据进行解析组拼成字符串，以流的方式发送到服务器，且上传文件用的都是POST方式，POST方式对大小没什么限制。

回到题目，可以说假设每次真的只能上传2M，那么可能我们只能把文件截断，然后分别上传了，断点上传。



### [7、补间动画](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#7补间动画)  


补间动画又可以分为四种形式，分别是 alpha（淡入淡出），translate（位移），scale（缩放大小），rotate（旋转）。

补间动画的实现，一般会采用xml 文件的形式；代码会更容易书写和阅读，同时也更容易复用。Interpolator 主要作用是可以控制动画的变化速率 ，就是动画进行的快慢节奏。pivot 决定了当前动画执行的参考位置

```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@[package:]anim/interpolator_resource"
    android:shareInterpolator=["true" | "false"] >
    <alpha
        android:fromAlpha="float"
        android:toAlpha="float" />
    <scale
        android:fromXScale="float"
        android:toXScale="float"
        android:fromYScale="float"
        android:toYScale="float"
        android:pivotX="float"
        android:pivotY="float" />
    <translate
        android:fromXDelta="float"
        android:toXDelta="float"
        android:fromYDelta="float"
        android:toYDelta="float" />
    <rotate
        android:fromDegrees="float"
        android:toDegrees="float"
        android:pivotX="float"
        android:pivotY="float" />
    <set>
        ...
    </set>
</set>
```


### [8、什么是嵌入式实时操作系统, Android 操作系统属于实时操作系统吗?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#8什么是嵌入式实时操作系统,-android-操作系统属于实时操作系统吗)  


嵌入式实时操作系统是指当外界事件或数据产生时，能够接受并以足够快的速度予以处理，其处理的结果又能在规定的时间之内来控制生产过程或对处理系统作出快速响应，并控制所有实时任务协调一致运行的嵌入式操作系统。主要用于工业控制、 军事设备、 航空航天等领域对系统的响应时间有苛刻的要求，这就需要使用实时系统。又可分为软实时和硬实时两种，而android是基于linux内核的，因此属于软实时。


### [9、Service 和 Activity 在同一个线程吗](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#9service-和-activity-在同一个线程吗)  


默认情况下service与activity在同一个线程，都在main Thread，或者ui线程中。

如果在清单文件中指定service的process属性，那么service就在另一个进程中运行。


### [10、跨进程通信的几种方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#10跨进程通信的几种方式)  


Intent,比如拨打电话

ContentProvider数据库存储数据

Broadcast广播通信

AIDL通信，通过接口共享数据


### [11、系统上安装了多种浏览器，能否指定某浏览器访问指定页面？请说明原由。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#11系统上安装了多种浏览器能否指定某浏览器访问指定页面请说明原由。)  

### [12、如何将打开res aw目录中的数据库文件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#12如何将打开res-aw目录中的数据库文件)  

### [13、Serializable 和 Parcelable 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#13serializable-和-parcelable-的区别)  

### [14、Framework 工作方式及原理，Activity 是如何生成一个 view 的，机制是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#14framework-工作方式及原理activity-是如何生成一个-view-的机制是什么)  

### [15、描述下Handler 机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#15描述下handler-机制)  

### [16、Adapter是什么？你所接触过的adapter有那些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#16adapter是什么你所接触过的adapter有那些)  

### [17、谈谈对Android NDK的理解](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#17谈谈对android-ndk的理解)  

### [18、定位项目中，如何选取定位方案，如何平衡耗电与实时位置的精度？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#18定位项目中如何选取定位方案如何平衡耗电与实时位置的精度)  

### [19、音视频相关类](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#19音视频相关类)  

### [20、activity的生命周期](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#20activity的生命周期)  

### [21、dagger2](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#21dagger2)  

### [22、什么是aar?aar是jar有什么区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#22什么是aaraar是jar有什么区别)  

### [23、Android 判断SD卡是否存在](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#23android-判断sd卡是否存在)  

### [24、属性动画](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#24属性动画)  

### [25、Fragment与activity如何传值和交互？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#25fragment与activity如何传值和交互)  

### [26、ListView的优化方案](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#26listview的优化方案)  

### [27、activity之间传递参数，除了intent，广播接收器，contentProvider之外，还有那些方法？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#27activity之间传递参数除了intent广播接收器contentprovider之外还有那些方法)  

### [28、android系统的优势和不足](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#28android系统的优势和不足)  

### [29、Fragment中add与replace的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题汇总及答案（2021年Android面试题及答案大全）.md#29fragment中add与replace的区别)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
