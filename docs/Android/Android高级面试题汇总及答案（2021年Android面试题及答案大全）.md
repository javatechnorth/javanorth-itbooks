# Android高级面试题汇总及答案（2021年Android面试题及答案大全）

Android面试题及答案【最新版】Android高级面试题大全(2021版)，发现网上很多Android面试题及答案整理都没有答案，所以花了很长时间搜集，本套Android面试题大全，Android面试题大汇总，有大量经典的Android面试题以及答案，包含Android语言常见面试题、Android工程师高级面试题及一些大厂Android开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Android面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Android面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、SQLite支持事务吗?添加删除如何提高性能?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#1sqlite支持事务吗添加删除如何提高性能)  


SQLite作为轻量级的数据库，比MySQL还小，但支持SQL语句查询，提高性能可以考虑通过原始经过优化的SQL查询语句方式处理


### [2、内存溢出和内存泄漏有什么区别？何时会产生内存泄漏？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#2内存溢出和内存泄漏有什么区别何时会产生内存泄漏)  


内存溢出：当程序运行时所需的内存大于程序允许的最高内存，这时会出现内存溢出；

内存泄漏：在一些比较消耗资源的操作中，如果操作中内存一直未被释放，就会出现内存泄漏。比如未关闭io,cursor。


### [3、如何退出Activity](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#3如何退出activity)  


结束当前activity

```
Finish()
killProgress()
System.exit(0)
```

关闭应用程序时，结束所有的activity

可以创建一个List集合，每新创建一个activity，将该activity的实例放进list中，程序结束时，从集合中取出循环取出activity实例，调用finish()方法结束


### [4、Android中touch事件的传递机制是怎样的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#4android中touch事件的传递机制是怎样的)  


**1、** Touch事件传递的相关API有dispatchTouchEvent、onTouchEvent、onInterceptTouchEvent

**2、** Touch事件相关的类有View、ViewGroup、Activity

**3、** Touch事件会被封装成MotionEvent对象，该对象封装了手势按下、移动、松开等动作

**4、** Touch事件通常从Activity#dispatchTouchEvent发出，只要没有被消费，会一直往下传递，到最底层的View。

**5、** 如果Touch事件传递到的每个View都不消费事件，那么Touch事件会反向向上传递,最终交由Activity#onTouchEvent处理、

**6、** onInterceptTouchEvent为ViewGroup特有，可以拦截事件、

**7、** Down事件到来时，如果一个View没有消费该事件，那么后续的MOVE/UP事件都不会再给它


### [5、FragmentPagerAdapter 与 与 FragmentStatePagerAdapter 的区别与使用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#5fragmentpageradapter-与-与-fragmentstatepageradapter-的区别与使用场景)  


FragmentPagerAdapter 的每个 Fragment 会持久的保存在 FragmentManager 中，只要用户可以返回到页面中，它都不会被销毁。因此适用于那些数据 相对静态的页，Fragment 数量也比较少的那种;FragmentStatePagerAdapter 只保留当前页面，当页面不可见时，该 Fragment 就会被消除，释放其资源。因此适用于那些 数据动态性较大、 占用内存较多，多 Fragment 的情况；


### [6、View的绘制原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#6view的绘制原理)  


View为所有图形控件的基类，View的绘制由3个函数完成

measure,计算视图的大小

layout,提供视图要显示的位置

draw,绘制


### [7、Android root机制](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#7android-root机制)  


root指的是你有权限可以再系统上对所有档案有 "读" "写" "执行"的权力。root机器不是真正能让你的应用程序具有root权限。它原理就跟linux下的像sudo这样的命令。在系统的bin目录下放个su程序并属主是root并有suid权限。则通过su执行的命令都具有Android root权限。当然使用临时用户权限想把su拷贝的/system/bin目录并改属性并不是一件容易的事情。这里用到2个工具跟2个命令。把busybox拷贝到你有权限访问的目录然后给他赋予4755权限，你就可以用它做很多事了。


### [8、ListView 如何定位到指定位置](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#8listview-如何定位到指定位置)  


可以通过 ListView 提供的 lv.setSelection(listView.getPosition())方法。



### [9、activity，service，intent之间的关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#9activityserviceintent之间的关系)  


这三个都是android应用频率非常的组件。Activity与service是四大核心组件。Activity用来加载布局，显示窗口界面，service运行后台，没有界面显示，intent是activity与service的通信使者。


### [10、View和SurfaceView的区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#10view和surfaceview的区别)  


View基于主线程刷新UI，SurfaceView子线程又可以刷新UI


### [11、Fragment 如何实现类似 Activity 栈的压栈和出栈效果的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#11fragment-如何实现类似-activity-栈的压栈和出栈效果的)  

### [12、DDMS和TraceView的区别?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#12ddms和traceview的区别)  

### [13、子线程中能不能 new handler？为什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#13子线程中能不能-new-handler为什么)  

### [14、Hander原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#14hander原理)  

### [15、Android中任务栈的分配](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#15android中任务栈的分配)  

### [16、NDK是什么](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#16ndk是什么)  

### [17、即时通讯是是怎么做的?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#17即时通讯是是怎么做的)  

### [18、SurfaceView](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#18surfaceview)  

### [19、activity与fragment区别](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#19activity与fragment区别)  

### [20、说下Activity 的四种启动模式、应用场景 ？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#20说下activity-的四种启动模式应用场景-)  

### [21、如果Listview中的数据源发生改变，如何更新listview中的数据](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#21如果listview中的数据源发生改变如何更新listview中的数据)  

### [22、说说 LruCache 底层原理](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#22说说-lrucache-底层原理)  

### [23、在 service 的生命周期方法 onstartConmand()可不可以执行网络操作？如何在 service 中执行网络操作？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#23在-service-的生命周期方法-onstartconmand可不可以执行网络操作如何在-service-中执行网络操作)  

### [24、请描述一下 Intent 和 IntentFilter](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#24请描述一下-intent-和-intentfilter)  

### [25、View的分发机制，滑动冲突](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#25view的分发机制滑动冲突)  

### [26、请介绍下Android的数据存储方式。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#26请介绍下android的数据存储方式。)  

### [27、内存泄露如何查看和解决](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#27内存泄露如何查看和解决)  

### [28、说说 ContentProvider、ContentResolver、ContentObserver 之间的关系](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#28说说-contentprovidercontentresolvercontentobserver-之间的关系)  

### [29、如何将打开res aw目录中的数据库文件?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Android/Android高级面试题汇总及答案（2021年Android面试题及答案大全）.md#29如何将打开res-aw目录中的数据库文件)  





