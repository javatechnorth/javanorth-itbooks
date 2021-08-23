# Android面试题附答案汇总（2021年Android面试题及答案大全）

Android面试题及答案【最新版】Android高级面试题大全(2021版)，发现网上很多Android面试题及答案整理都没有答案，所以花了很长时间搜集，本套Android面试题大全，Android面试题大汇总，有大量经典的Android面试题以及答案，包含Android语言常见面试题、Android工程师高级面试题及一些大厂Android开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Android面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Android面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、描述一下android的系统架构](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#1描述一下android的系统架构)  


android系统架构分从下往上为linux 内核层、运行库、应用程序框架层、和应用程序层。

linuxkernel：负责硬件的驱动程序、网络、电源、系统安全以及内存管理等功能。

libraries和 android runtime：libraries：即c/c++函数库部分，大多数都是开放源代码的函数库，例如webkit（引擎），该函数库负责 android网页浏览器的运行，例如标准的c函数库libc、openssl、sqlite等，当然也包括支持游戏开发2dsgl和 3dopengles，在多媒体方面有mediaframework框架来支持各种影音和图形文件的播放与显示，例如mpeg4、h.264、mp3、 aac、amr、jpg和png等众多的多媒体文件格式。android的runtime负责解释和执行生成的dalvik格式的字节码。

applicationframework（应用软件架构），java应用程序开发人员主要是使用该层封装好的api进行快速开发。

applications:该层是java的应用程序层，android内置的googlemaps、e-mail、即时通信工具、浏览器、mp3播放器等处于该层，java开发人员开发的程序也处于该层，而且和内置的应用程序具有平等的位置，可以调用内置的应用程序，也可以替换内置的应用程序。

上面的四个层次，下层为上层服务，上层需要下层的支持，调用下层的服务，这种严格分层的方式带来的极大的稳定性、灵活性和可扩展性，使得不同层的开发人员可以按照规范专心特定层的开发。

android应用程序使用框架的api并在框架下运行，这就带来了程序开发的高度一致性，另一方面也告诉我们，要想写出优质高效的程序就必须对整个 applicationframework进行非常深入的理解。精通applicationframework，你就可以真正的理解android的设计和运行机制，也就更能够驾驭整个应用层的开发。


### [2、跟activity和Task 有关的 Intent启动方式有哪些？其含义？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#2跟activity和task-有关的-intent启动方式有哪些其含义)  


核心的Intent Flag有

**1、** FLAG_ACTIVITY_NEW_TAS

**2、** FLAG_ACTIVITY_CLEAR_TOP

**3、** FLAG_ACTIVITY_RESET_TASK_IF_NEEDED

**4、** FLAG_ACTIVITY_SINGLE_TO

**5、** FLAG_ACTIVITY_NEW_TAS

如果设置，这个Activity会成为历史stack中一个新Task的开始。一个Task（从启动它的Activity到下一个Task中的 Activity）定义了用户可以迁移的Activity原子组。Task可以移动到前台和后台；在某个特定Task中的所有Activity总是保持相同的次序

这个标志一般用于呈现“启动”类型的行为：它们提供用户一系列可以单独完成的事情，与启动它们的Activity完全无关。

使用这个标志，如果正在启动的Activity的Task已经在运行的话，那么，新的Activity将不会启动；代替的，当前Task会简单的移入前台。参考FLAG_ACTIVITY_MULTIPLE_TASK标志，可以禁用这一行为。

这个标志不能用于调用方对已经启动的Activity请求结果。

**FLAG_ACTIVITY_CLEAR_TOP**

如果设置，并且这个Activity已经在当前的Task中运行，因此，不再是重新启动一个这个Activity的实例，而是在这个Activity上方的所有Activity都将关闭，然后这个Intent会作为一个新的Intent投递到老的Activity（现在位于顶端）中。

例如，假设一个Task中包含这些Activity：A，B，C，D。如果D调用了startActivity()，并且包含一个指向Activity B的Intent，那么，C和D都将结束，然后B接收到这个Intent，因此，目前stack的状况是：A，B。

上例中正在运行的Activity B既可以在onNewIntent()中接收到这个新的Intent，也可以把自己关闭然后重新启动来接收这个Intent。如果它的启动模式声明为 “multiple”(默认值)，并且你没有在这个Intent中设置FLAG_ACTIVITY_SINGLE_TOP标志，那么它将关闭然后重新创建；对于其它的启动模式，或者在这个Intent中设置FLAG_ACTIVITY_SINGLE_TOP标志，都将把这个Intent投递到当前这个实例的onNewIntent()中。

这个启动模式还可以与FLAG_ACTIVITY_NEW_TASK结合起来使用：用于启动一个Task中的根Activity，它会把那个Task中任何运行的实例带入前台，然后清除它直到根Activity。这非常有用，例如，当从Notification Manager处启动一个Activity。

**FLAG_ACTIVITY_RESET_TASK_IF_NEEDED**

如果设置这个标志，这个activity不管是从一个新的栈启动还是从已有栈推到栈顶，它都将以the front door of the task的方式启动。这就讲导致任何与应用相关的栈都讲重置到正常状态（不管是正在讲activity移入还是移除），如果需要，或者直接重置该栈为初始状态。

**FLAG_ACTIVITY_SINGLE_TOP**

如果设置，当这个Activity位于历史stack的顶端运行时，不再启动一个新的

**FLAG_ACTIVITY_BROUGHT_TO_FRONT**

这个标志一般不是由程序代码设置的，如在launchMode中设置singleTask模式时系统帮你设定。

**FLAG_ACTIVITY_CLEAR_WHEN_TASK_RESET**

如果设置，这将在Task的Activity stack中设置一个还原点，当Task恢复时，需要清理Activity。也就是说，下一次Task带着 FLAG_ACTIVITY_RESET_TASK_IF_NEEDED标记进入前台时（典型的操作是用户在主画面重启它），这个Activity和它之上的都将关闭，以至于用户不能再返回到它们，但是可以回到之前的Activity。

这在你的程序有分割点的时候很有用。例如，一个e-mail应用程序可能有一个操作是查看一个附件，需要启动图片浏览Activity来显示。这个 Activity应该作为e-mail应用程序Task的一部分，因为这是用户在这个Task中触发的操作。然而，当用户离开这个Task，然后从主画面选择e-mail app，我们可能希望回到查看的会话中，但不是查看图片附件，因为这让人困惑。通过在启动图片浏览时设定这个标志，浏览及其它启动的Activity在下次用户返回到mail程序时都将全部清除。

**FLAG_ACTIVITY_EXCLUDE_FROM_RECENTS**

如果设置，新的Activity不会在最近启动的Activity的列表中保存。

**FLAG_ACTIVITY_FORWARD_RESULT**

如果设置，并且这个Intent用于从一个存在的Activity启动一个新的Activity，那么，这个作为答复目标的Activity将会传到这个新的Activity中。这种方式下，新的Activity可以调用setResult(int)，并且这个结果值将发送给那个作为答复目标的 Activity。

**FLAG_ACTIVITY_LAUNCHED_FROM_HISTORY**

这个标志一般不由应用程序代码设置，如果这个Activity是从历史记录里启动的（常按HOME键），那么，系统会帮你设定。

**FLAG_ACTIVITY_MULTIPLE_TASK**

不要使用这个标志，除非你自己实现了应用程序启动器。与FLAG_ACTIVITY_NEW_TASK结合起来使用，可以禁用把已存的Task送入前台的行为。当设置时，新的Task总是会启动来处理Intent，而不管这是是否已经有一个Task可以处理相同的事情。

由于默认的系统不包含图形Task管理功能，因此，你不应该使用这个标志，除非你提供给用户一种方式可以返回到已经启动的Task。

如果FLAG_ACTIVITY_NEW_TASK标志没有设置，这个标志被忽略。

**FLAG_ACTIVITY_NO_ANIMATION**

如果在Intent中设置，并传递给Context.startActivity()的话，这个标志将阻止系统进入下一个Activity时应用 Acitivity迁移动画。这并不意味着动画将永不运行——如果另一个Activity在启动显示之前，没有指定这个标志，那么，动画将被应用。这个标志可以很好的用于执行一连串的操作，而动画被看作是更高一级的事件的驱动。

**FLAG_ACTIVITY_NO_HISTORY**

如果设置，新的Activity将不再历史stack中保留。用户一离开它，这个Activity就关闭了。这也可以通过设置noHistory特性。

**FLAG_ACTIVITY_NO_USER_ACTION**

如果设置，作为新启动的Activity进入前台时，这个标志将在Activity暂停之前阻止从最前方的Activity回调的onUserLeaveHint()。

典型的，一个Activity可以依赖这个回调指明显式的用户动作引起的Activity移出后台。这个回调在Activity的生命周期中标记一个合适的点，并关闭一些Notification。

如果一个Activity通过非用户驱动的事件，如来电或闹钟，启动的，这个标志也应该传递给Context.startActivity，保证暂停的Activity不认为用户已经知晓其Notification。

**FLAG_ACTIVITY_PREVIOUS_IS_TOP**

If set and this intent is being used to launch a new activity from an existing one, the current activity will not be counted as the top activity for deciding whether the new intent should be delivered to the top instead of starting a new one、The previous activity will be used as the top, with the assumption being that the current activity will finish itself immediately.

**FLAG_ACTIVITY_REORDER_TO_FRONT**

如果在Intent中设置，并传递给Context.startActivity()，这个标志将引发已经运行的Activity移动到历史stack的顶端。

例如，假设一个Task由四个Activity组成：A,B,C,D。如果D调用startActivity()来启动Activity B，那么，B会移动到历史stack的顶端，现在的次序变成A,C,D,B。如果FLAG_ACTIVITY_CLEAR_TOP标志也设置的话，那么这个标志将被忽略。


### 3、NDK

**1、** NDK是一系列工具集合，NDK提供了一系列的工具，帮助开发者迅速的开发C/C++的动态库，并能自动将so和Java应用打成apk包。

**2、** NDK集成了交叉编译器，并提供了相应的mk文件和隔离cpu、平台等的差异，开发人员只需要简单的修改mk文件就可以创建出so文件。


### [4、请介绍下 ContentProvider 是如何实现数据共享的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#4请介绍下-contentprovider-是如何实现数据共享的)  


ContentProvider是一个对外提供数据的接口，首先需要实现ContentProvider这个接口，然后重写query，insert，getType，delete，update方法，最后在清单文件定义contentProvider的访问uri


### [5、Activity启动模式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#5activity启动模式)  


介绍 Android 启动模式之前，先介绍两个概念task和taskAffinity

**task：**

翻译过来就是“任务”，是一组相互有关联的 activity 集合，可以理解为 Activity 是在 task 里面活动的。 task 存在于一个称为 back stack 的数据结构中，也就是说， task 是以栈的形式去管理 activity 的，所以也叫可以称为“任务栈”。

**taskAffinity：**

官方文档解释是："The task that the activity has an affinity for."，可以翻译为 activity 相关或者亲和的任务，这个参数标识了一个 Activity 所需要的任务栈的名字。默认情况下，所有Activity所需的任务栈的名字为应用的包名。 taskAffinity 属性主要和 singleTask 启动模式或者 allowTaskReparenting 属性配对使用。

**4种启动模式**

**1、** standard：

标准模式，也是系统默认的启动模式。假如 activity A 启动了 activity B ， activity B 则会运行在 activity A 所在的任务栈中。而且每次启动一个 Activity ，都会重新创建新的实例，不管这个实例在任务中是否已经存在。非 Activity 类型的 context （如 ApplicationContext ）启动 standard 模式的 Activity 时会报错。非 Activity 类型的 context 并没有所谓的任务栈，由于上面第 1 点的原因所以系统会报错。此解决办法就是为待启动 Activity 指定 FLAG_ACTIVITY_NEW_TASK 标记位，这样启动的时候系统就会为它创建一个新的任务栈。这个时候待启动 Activity 其实是以 singleTask 模式启动的。

**2、** singleTop：

栈顶复用模式。假如 activity A 启动了 activity B ，就会判断 A 所在的任务栈栈顶是否是 B 的实例。如果是，则不创建新的 activity B 实例而是直接引用这个栈顶实例，同时 onNewIntent 方法会被回调，通过该方法的参数可以取得当前请求的信息；如果不是，则创建新的 activity B 实例。

**3、** singleTask：

栈内复用模式。在第一次启动这个 Activity 时，系统便会创建一个新的任务，并且初始化 Activity 的实例，放在新任务的底部。不过需要满足一定条件的。那就是需要设置 taskAffinity 属性。前面也说过了， taskAffinity 属性是和 singleTask 模式搭配使用的。

![92_4.png][92_4.png]

**1、** singleInstance：单实例模式。这个是 singleTask 模式的加强版，它除了具有 singleTask 模式的所有特性外，它还有一点独特的特性，那就是此模式的 Activity 只能单独地位于一个任务栈，不与其他 Activity 共存于同一个任务栈。


### [6、谈MVC ，MVP，MVVM](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#6谈mvc-mvpmvvm)  


MVC:View是可以直接访问Model的！从而，View里会包含Model信息，不可避免的还要包括一些 业务逻辑。 在MVC模型里，更关注的Model的不变，而同时有多个对Model的不同显示，及View。所以，在MVC模型里，Model不依赖于View，但是 View是依赖于Model的。不仅如此，因为有一些业务逻辑在View里实现了，导致要更改View也是比较困难的，至少那些业务逻辑是无法重用的。

MVP：MVP 是从经典的模式MVC演变而来，它们的基本思想有相通的地方：Controller/Presenter负责逻辑的处理，Model提供数据，View负 责显示。作为一种新的模式，MVP与MVC有着一个重大的区别：在MVP中View并不直接使用Model，它们之间的通信是通过Presenter (MVC中的Controller)来进行的，所有的交互都发生在Presenter内部，而在MVC中View会从直接Model中读取数据而不是通过 Controller。

MVVM：数据双向绑定，通过数据驱动UI，M提供数据，V视图，VM即数据驱动层


### [7、广播接受者的生命周期？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#7广播接受者的生命周期)  


```
广播接收者的生命周期非常短。当执行onRecieve方法之后，广播就会销毁
在广播接受者不能进行耗时较长的操作
在广播接收者不要创建子线程。广播接收者完成操作后，所在进程会变成空进程，很容易被系统回收
```


### [8、如果后台的Activity由于某原因被系统回收了，如何在被系统回收之前保存当前状态？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#8如果后台的activity由于某原因被系统回收了如何在被系统回收之前保存当前状态)  


重写onSaveInstanceState()方法，在此方法中保存需要保存的数据，该方法将会在activity被回收之前调用。通过重写onRestoreInstanceState()方法可以从中提取保存好的数据


### [9、ListView 中图片错位的问题是如何产生的](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#9listview-中图片错位的问题是如何产生的)  


图片错位问题的本质源于我们的 listview 使用了缓存 convertView， 假设一种场景， 一个 listview一屏显示九个 item，那么在拉出第十个 item 的时候，事实上该 item 是重复使用了第一个 item，也就是说在第一个 item 从网络中下载图片并最终要显示的时候，其实该 item 已经不在当前显示区域内了，此时显示的后果将可能在第十个 item 上输出图像，这就导致了图片错位的问题。所以解决办法就是可见则显示，不可见则不显示。


### [10、简要解释一下activity、 intent 、intent filter、service、Broadcase、BroadcaseReceiver](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#10简要解释一下activity-intent-intent-filterservicebroadcasebroadcasereceiver)  


一个activity呈现了一个用户可以操作的可视化用户界面；一个service不包含可见的用户界面，而是在后台运行，可以与一个activity绑定，通过绑定暴露出来接口并与其进行通信；一个broadcast receiver是一个接收广播消息并做出回应的component，broadcast receiver没有界面；一个intent是一个Intent对象，它保存了消息的内容。对于activity和service来说，它指定了请求的操作名称和待操作数据的URI，Intent对象可以显式的指定一个目标component。如果这样的话，android会找到这个component(基于manifest文件中的声明)并激活它。但如果一个目标不是显式指定的，android必须找到响应intent的最佳component。它是通过将Intent对象和目标的intent filter相比较来完成这一工作的；一个component的intent filter告诉android该component能处理的intent。intent filter也是在manifest文件中声明的。


### [11、ListView 如何提高其效率？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#11listview-如何提高其效率)  

### [12、什么是IntentService？有何优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#12什么是intentservice有何优点)  

### [13、Android数字签名](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#13android数字签名)  

### [14、请解释下在单线程模型中Message、Handler、Message Queue、Looper之间的关系。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#14请解释下在单线程模型中messagehandlermessage-queuelooper之间的关系。)  

### [15、Android中activity，context，application有什么不同。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#15android中activitycontextapplication有什么不同。)  

### [16、如何将一个Activity设置成窗口的样式。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#16如何将一个activity设置成窗口的样式。)  

### [17、消息推送的方式](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#17消息推送的方式)  

### [18、什么情况会导致Force Close ？如何避免？能否捕获导致其的异常？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#18什么情况会导致force-close-如何避免能否捕获导致其的异常)  

### [19、如何修改 Activity 进入和退出动画](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#19如何修改-activity-进入和退出动画)  

### [20、sim卡的EF 文件有何作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#20sim卡的ef-文件有何作用)  

### [21、sim卡的EF文件是什么？有何作用](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#21sim卡的ef文件是什么有何作用)  

### [22、AIDL的全称是什么？如何工作？能处理哪些类型的数据？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#22aidl的全称是什么如何工作能处理哪些类型的数据)  

### [23、Android 线程间通信有哪几种方式（重要）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#23android-线程间通信有哪几种方式重要)  

### [24、16Android性能优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#2416android性能优化)  

### [25、请介绍下 AsyncTask 的内部实现和适用的场景](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#25请介绍下-asynctask-的内部实现和适用的场景)  

### [26、你一般在开发项目中都使用什么设计模式？如何来重构，优化你的代码？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#26你一般在开发项目中都使用什么设计模式如何来重构优化你的代码)  

### [27、ContentProvider与sqlite有什么不一样的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#27contentprovider与sqlite有什么不一样的)  

### [28、ListView优化](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#28listview优化)  

### [29、谈谈Android的IPC（进程间通信）机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android面试题附答案汇总（2021年Android面试题及答案大全）.md#29谈谈android的ipc进程间通信机制)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
