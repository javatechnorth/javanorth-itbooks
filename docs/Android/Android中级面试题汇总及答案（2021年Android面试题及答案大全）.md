# Android中级面试题汇总及答案（2021年Android面试题及答案大全）

Android面试题及答案【最新版】Android高级面试题大全(2021版)，发现网上很多Android面试题及答案整理都没有答案，所以花了很长时间搜集，本套Android面试题大全，Android面试题大汇总，有大量经典的Android面试题以及答案，包含Android语言常见面试题、Android工程师高级面试题及一些大厂Android开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Android面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Android面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、说说mvc模式的原理，它在android中的运用,android的官方建议应用程序的开发采用mvc模式。何谓mvc？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#1说说mvc模式的原理它在android中的运用,android的官方建议应用程序的开发采用mvc模式。何谓mvc)  


mvc是model,view,controller的缩写，mvc包含三个部分：

**1、** 模型（model）对象：是应用程序的主体部分，所有的业务逻辑都应该写在该层。

**2、** 视图（view）对象：是应用程序中负责生成用户界面的部分。也是在整个mvc架构中用户唯一可以看到的一层，接收用户的输入，显示处理结果。

**3、** 控制器（control）对象：是根据用户的输入，控制用户界面数据显示及更新model对象状态的部分，控制器更重要的一种导航功能，响应用户出发的相关事件，交给m层处理。

**android鼓励弱耦合和组件的重用，在android中mvc的具体体现如下：**

**1、** 视图层（view）：一般采用xml文件进行界面的描述，使用的时候可以非常方便的引入，当然，如果你对android了解的比较的多了话，就一定可以想到在android中也可以使用JavaScript+html等的方式作为view层，当然这里需要进行java和javascript之间的通信，幸运的是，android提供了它们之间非常方便的通信实现。

**2、** 控制层（controller）：android的控制层的重任通常落在了众多的acitvity的肩上，这句话也就暗含了不要在acitivity中写代码，要通过activity交割model业务逻辑层处理，这样做的另外一个原因是android中的acitivity的响应时间是5s，如果耗时的操作放在这里，程序就很容易被回收掉。

**3、** 模型层（model）：对数据库的操作、对网络等的操作都应该在model里面处理，当然对业务计算等操作也是必须放在的该层的。


### [2、wait和 sleep 的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#2wait和-sleep-的区别)  


wait是Object的方法，wait是对象锁，锁定方法不让继续执行，当执行notify方法后就会继续执行，sleep 是Thread的方法，sleep 是使线程睡眠，让出cpu，结束后自动继续执行


### [3、java中如何引用本地语言](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#3java中如何引用本地语言)  


可以用JNI（java native interface  java 本地接口）接口 。


### [4、如何将SQLite数据库(dictionary.db文件)与apk文件一起发布](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#4如何将sqlite数据库dictionarydb文件与apk文件一起发布)  


解可以将dictionary.db文件复制到Eclipse Android工程中的res aw目录中。所有在res aw目录中的文件不会被压缩，这样可以直接提取该目录中的文件。可以将dictionary.db文件复制到res aw目录中


### [5、自定义view的基本流程](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#5自定义view的基本流程)  


**1、** 自定义View的属性 编写attr.xml文件

**2、** 在layout布局文件中引用，同时引用命名空间

**3、** 在View的构造方法中获得我们自定义的属性 ，在自定义控件中进行读取（构造方法拿到attr.xml文件值）

**4、** 重写onMesure

**5、** 重写onDraw


### [6、说下 Activity 跟 跟 window ， view 之间的关系？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#6说下-activity-跟-跟-window--view-之间的关系)  


Activity 创建时通过 attach()初始化了一个 Window 也就是PhoneWindow，一个 PhoneWindow 持有一个DecorView 的实例，DecorView 本身是一个 FrameLayout，继承于 View，Activty 通过setContentView 将xml 布局控件不断 addView()添加到 View 中，最终显示到 Window 于我们交互；


### [7、Android中，帧动画](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#7android中帧动画)  


帧动画是最容易实现的一种动画，这种动画更多的依赖于完善的UI资源，他的原理就是将一张张单独的图片连贯的进行播放，从而在视觉上产生一种动画的效果；有点类似于某些软件制作gif动画的方式。在有些代码中，我们还会看到android：oneshot="false" ，这个oneshot 的含义就是动画执行一次（true）还是循环执行多次。

```
<?xml version="1.0" encoding="utf-8"?>
<animation-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:drawable="@drawable/a_0"
        android:duration="100" />
    <item
        android:drawable="@drawable/a_1"
        android:duration="100" />
    <item
        android:drawable="@drawable/a_2"
        android:duration="100" />
</animation-list>
```


### [8、注册广播有几种方式，这些方式有何优缺点？请谈谈Android引入广播机制的用意。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#8注册广播有几种方式这些方式有何优缺点请谈谈android引入广播机制的用意。)  


首先写一个类要继承BroadcastReceiver

第一种:在清单文件中声明

第二种使用代码进行注册如:‍‍

```
IntentFilter filter =  new IntentFilter("android.provider.Telephony.SMS_RECEIVED");
IncomingSMSReceiver receiver = new IncomgSMSReceiver();
registerReceiver(receiver.filter);
```

两种注册类型的区别是：

1)第一种不是常驻型广播，也就是说广播跟随程序的生命周期。

2)第二种是常驻型，也就是说当应用程序关闭后，如果有信息广播来，程序也会被系统调用自动运行。


### [9、如何保存activity的状态？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#9如何保存activity的状态)  


默认情况下activity的状态系统会自动保存，有些时候需要我们手动调用保存。

当activity处于onPause，onStop之后，activity处于未活动状态，但是activity对象却仍然存在。当内存不足，onPause，onStop之后的activity可能会被系统摧毁。

当通过返回退出activity时，activity状态并不会保存。

保存activity状态需要重写onSavedInstanceState()方法，在执行onPause,onStop之前调用onSavedInstanceState方法，onSavedInstanceState需要一个Bundle类型的参数，我们可以将数据保存到bundle中，通过实参传递给onSavedInstanceState方法。

Activity被销毁后，重新启动时，在onCreate方法中，接受保存的bundle参数，并将之前的数据取出。


### [10、Service生命周期](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#10service生命周期)  


在Service的生命周期里，常用的有：

4个手动调用的方法

```
startService()    启动服务
stopService()    关闭服务
bindService()    绑定服务
unbindService()    解绑服务
```

5个内部自动调用的方法

```
onCreat()            创建服务
onStartCommand()    开始服务
onDestroy()            销毁服务
onBind()            绑定服务
onUnbind()            解绑服务
```

**1、** 手动调用startService()启动服务，自动调用内部方法：onCreate()、onStartCommand()，如果一个Service被startService()多次启动，那么onCreate()也只会调用一次。

**2、** 手动调用stopService()关闭服务，自动调用内部方法：onDestory()，如果一个Service被启动且被绑定，如果在没有解绑的前提下使用stopService()关闭服务是无法停止服务的。

**3、** 手动调用bindService()后，自动调用内部方法：onCreate()、onBind()。

**4、** 手动调用unbindService()后，自动调用内部方法：onUnbind()、onDestory()。

**5、** startService()和stopService()只能开启和关闭Service，无法操作Service，调用者退出后Service仍然存在；bindService()和unbindService()可以操作Service，调用者退出后，Service随着调用者销毁。


### [11、什么是ANR 如何避免它？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#11什么是anr-如何避免它)  

### [12、Fragment 在你们项目中的使用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#12fragment-在你们项目中的使用)  

### [13、Android 应用中验证码登陆都有哪些实现方案](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#13android-应用中验证码登陆都有哪些实现方案)  

### [14、activity在屏幕旋转时的生命周期](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#14activity在屏幕旋转时的生命周期)  

### [15、子线程发消息到主线程进行更新 UI，除了 handler 和 AsyncTask，还有什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#15子线程发消息到主线程进行更新-ui除了-handler-和-asynctask还有什么)  

### [16、Activity的状态有几种？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#16activity的状态有几种)  

### [17、什么是 AIDL？如何使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#17什么是-aidl如何使用)  

### [18、Android的四大组件是哪些，它们的作用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#18android的四大组件是哪些它们的作用)  

### [19、Service 是否在 main thread 中执行, service 里面是否能执行耗时的操作?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#19service-是否在-main-thread-中执行,-service-里面是否能执行耗时的操作)  

### [20、IntentService有何优点?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#20intentservice有何优点)  

### [21、请介绍下Android中常用的五种布局。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#21请介绍下android中常用的五种布局。)  

### [22、android 中有哪几种解析xml的类？官方推荐哪种？以及它们的原理和区别。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#22android-中有哪几种解析xml的类官方推荐哪种以及它们的原理和区别。)  

### [23、请解释下Android程序运行时权限与文件系统权限的区别。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#23请解释下android程序运行时权限与文件系统权限的区别。)  

### [24、事件分发中的 onTouch 和 onTouchEvent 有什么区别，又该如何使用？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#24事件分发中的-ontouch-和-ontouchevent-有什么区别又该如何使用)  

### [25、谈谈你在工作中是怎样解决一个 bug](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#25谈谈你在工作中是怎样解决一个-bug)  

### [26、AIDL 的全称是什么?如何工作?能处理哪些类型的数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#26aidl-的全称是什么如何工作能处理哪些类型的数据)  

### [27、9.进程和线程的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#279进程和线程的区别)  

### [28、属性动画，例如一个 button 从 A 移动到 B 点，B 点还是可以响应点击事件，这个原理是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#28属性动画例如一个-button-从-a-移动到-b-点b-点还是可以响应点击事件这个原理是什么)  

### [29、AsyncTask使用在哪些场景？它的缺陷是什么？如何解决？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android中级面试题汇总及答案（2021年Android面试题及答案大全）.md#29asynctask使用在哪些场景它的缺陷是什么如何解决)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
