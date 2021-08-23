# Nginx面试题附答案（2021年Nginx面试题及答案大汇总）

Nginx面试题及答案【最新版】Nginx高级面试题大全(2021版)，发现网上很多Nginx面试题及答案整理都没有答案，所以花了很长时间搜集，本套Nginx面试题大全，Nginx面试题大汇总，有大量经典的Nginx面试题以及答案，包含Nginx语言常见面试题、Nginx工程师高级面试题及一些大厂Nginx开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Nginx面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Nginx面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、Nginx配置文件nginx.conf有哪些属性模块?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#1nginx配置文件nginxconf有哪些属性模块)  


```
worker_processes 1；# worker进程的数量
events {#事件区块开始
    worker_connections 1024；#每个 worker进程支持的最大连接数
}

#事件区块结束

http {#
    HTTP区块开始
    include mime.types；# Nginx支持的媒体类型库文件
    default_type application / octet - stream；#默认的媒体类型
    sendfile on；#开启高效传输模式
    keepalive_timeout 65；#连接超时
    server {

        #第一个
        Server区块开始，表示一个独立的虚拟主机站点
        listen 80；#提供服务的端口，默认 80
        server_name localhost；#提供服务的域名主机名
        location / {
             #第一个
            location区块开始
            root html；#站点的根目录，相当于 Nginx的安装目录
            index index.html index.htm；#默认的首页文件，多个用空格分开
        }

        #第一个
        location区块结果
        error_page 500502503504 / 50x.html；#出现对应的 http状态码时，使用 50x.html回应客户
        location = /50x.html {
              # location区块开始，访问50x.html
            root   html；                                  # 指定对应的站点目录为html
        }
    }
......
```


### [2、Nginx 是如何实现高并发的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#2nginx-是如何实现高并发的)  


如果一个 server 采用一个进程(或者线程)负责一个request的方式，那么进程数就是并发数。那么显而易见的，就是会有很多进程在等待中。等什么？最多的应该是等待网络传输。其缺点胖友应该也感觉到了，此处不述。

**思考下，Java 的 NIO 和 BIO 的对比哟。**

而 Nginx 的异步非阻塞工作方式正是利用了这点等待的时间。在需要等待的时候，这些进程就空闲出来待命了。因此表现为少数几个进程就解决了大量的并发问题。

Nginx是如何利用的呢，简单来说：同样的 4 个进程，如果采用一个进程负责一个 request 的方式，那么，同时进来 4 个 request 之后，每个进程就负责其中一个，直至会话关闭。期间，如果有第 5 个request进来了。就无法及时反应了，因为 4 个进程都没干完活呢，因此，一般有个调度进程，每当新进来了一个 request ，就新开个进程来处理。

**回想下，BIO 是不是存在酱紫的问题？嘻嘻。**

Nginx 不这样，每进来一个 request ，会有一个 worker 进程去处理。但不是全程的处理，处理到什么程度呢？处理到可能发生阻塞的地方，比如向上游（后端）服务器转发 request ，并等待请求返回。那么，这个处理的 worker 不会这么傻等着，他会在发送完请求后，注册一个事件：“如果 upstream 返回了，告诉我一声，我再接着干”。于是他就休息去了。此时，如果再有 request 进来，他就可以很快再按这种方式处理。而一旦上游服务器返回了，就会触发这个事件，worker 才会来接手，这个 request 才会接着往下走。

**这就是为什么说，Nginx 基于事件模型。**

由于 web server 的工作性质决定了每个 request 的大部份生命都是在网络传输中，实际上花费在 server 机器上的时间片不多。这是几个进程就解决高并发的秘密所在。即：

**webserver 刚好属于网络 IO 密集型应用，不算是计算密集型。**

而正如叔度所说的

**异步，非阻塞，使用 epoll ，和大量细节处的优化**

也正是 Nginx 之所以然的技术基石。


### [3、请解释 Nginx 如何处理 HTTP 请求？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#3请解释-nginx-如何处理-http-请求)  


**1、** 首先，Nginx 在启动时，会解析配置文件，得到需要监听的端口与 IP 地址，然后在 Nginx 的 Master 进程里面先初始化好这个监控的Socket(创建 S ocket，设置 addr、reuse 等选项，绑定到指定的 ip 地址端口，再 listen 监听)。

**2、** 然后，再 fork(一个现有进程可以调用 fork 函数创建一个新进程。由 fork 创建的新进程被称为子进程 )出多个子进程出来。

**3、** 之后，子进程会竞争 accept 新的连接。此时，客户端就可以向 nginx 发起连接了。当客户端与nginx进行三次握手，与 nginx 建立好一个连接后。此时，某一个子进程会 accept 成功，得到这个建立好的连接的 Socket ，然后创建 nginx 对连接的封装，即 ngx_connection_t 结构体。

**4、** 接着，设置读写事件处理函数，并添加读写事件来与客户端进行数据的交换。


### [4、Nginx是否支持将请求压缩到上游?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#4nginx是否支持将请求压缩到上游)  


可以使用Nginx模块gunzip将请求压缩到上游。gunzip模块是一个过滤器，它可以对不支持“gzip”编码方法的客户机或服务器使用“内容编码:gzip”来解压缩响应。


### [5、nginx和apache的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#5nginx和apache的区别)  


 轻量级，同样起web 服务，比apache 占用更少的内存及资源；抗并发，nginx处理请求是异步非阻塞的，而apache 则是阻塞型的，在高并发下nginx 能保持低资源低消耗高性能；高度模块化的设计，编写模块相对简单；最核心的区别在于apache是同步多进程模型，一个连接对应一个进程；nginx是异步的，多个连接（万级别）可以对应一个进程。


### [6、解释如何在 Nginx 中获得当前的时间?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#6解释如何在-nginx-中获得当前的时间)  


要获得 Nginx 的当前时间，必须使用 SSI 模块、$$date_gmt 和$$date_local 的变

量。

Proxy_set_header THE-TIME $date_gmt;


### [7、为什么要做动静分离？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#7为什么要做动静分离)  


**1、** Nginx是当下最热的Web容器，网站优化的重要点在于静态化网站，网站静态化的关键点则是是动静分离，动静分离是让动态网站里的动态网页根据一定规则把不变的资源和经常变的资源区分开来，动静资源做好了拆分以后，我们则根据静态资源的特点将其做缓存操作。

**2、** 让静态的资源只走静态资源服务器，动态的走动态的服务器

**3、** Nginx的静态处理能力很强，但是动态处理能力不足，因此，在企业中常用动静分离技术。

**4、** 对于静态资源比如图片，js，css等文件，我们则在反向代理服务器nginx中进行缓存。这样浏览器在请求一个静态资源时，代理服务器nginx就可以直接处理，无需将请求转发给后端服务器tomcat。

**5、** 若用户请求的动态文件，比如servlet,jsp则转发给Tomcat服务器处理，从而实现动静分离。这也是反向代理服务器的一个重要的作用。


### [8、请陈述 stub_status 和 sub_filter 指令的作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#8请陈述-stub_status-和-sub_filter-指令的作用是什么)  


Stub_status 指令：该指令用于了解 Nginx 当前状态的当前状态，如当前的活

动连接，接受和处理当前读/写/等待连接的总数

Sub_filter 指令：它用于搜索和替换响应中的内容，并快速修复陈旧的数据


### [9、如何通过不同于80的端口开启Nginx?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#9如何通过不同于80的端口开启nginx)  


为了通过一个不同的端口开启Nginx，你必须进/etc/Nginx/sites-enabled/，如果这是默认文件，那么必须打开名为“default”的文件。编辑文件，并放置在你想要的端口：

![](https://www.wkcto.com/static/uploads/index/article/20200610/1591779001@f3c2283e33bd1f26deab4c50144691af.png#alt=)


### [10、nginx是如何实现高并发的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#10nginx是如何实现高并发的)  


一个主进程，多个工作进程，每个工作进程可以处理多个请求，每进来一个request，会有一个worker进程去处理。但不是全程的处理，处理到可能发生阻塞的地方，比如向上游（后端）服务器转发request，并等待请求返回。那么，这个处理的worker继续处理其他请求，而一旦上游服务器返回了，就会触发这个事件，worker才会来接手，这个request才会接着往下走。由于web server的工作性质决定了每个request的大部份生命都是在网络传输中，实际上花费在server机器上的时间片不多。这是几个进程就解决高并发的秘密所在。即@skoo所说的webserver刚好属于网络io密集型应用，不算是计算密集型。


### [11、Nginx 如何实现后端服务的健康检查？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#11nginx-如何实现后端服务的健康检查)  

### [12、502错误可能原因](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#12502错误可能原因)  

### [13、nginx状态码](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#13nginx状态码)  

### [14、什么是C10K问题?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#14什么是c10k问题)  

### [15、Nginx应用场景？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#15nginx应用场景)  

### [16、Nginx目录结构有哪些？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#16nginx目录结构有哪些)  

### [17、为什么不使用多线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#17为什么不使用多线程)  

### [18、轮询(默认)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#18轮询默认)  

### [19、Nginx 常用命令？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#19nginx-常用命令)  

### [20、Nginx虚拟主机怎么配置?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#20nginx虚拟主机怎么配置)  

### [21、解释`Nginx`是否支持将请求压缩到上游?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#21解释nginx是否支持将请求压缩到上游)  

### [22、Location正则案例](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#22location正则案例)  

### [23、什么是动态资源、静态资源分离？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#23什么是动态资源静态资源分离)  

### [24、请解释`ngx_http_upstream_module`的作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#24请解释ngx_http_upstream_module的作用是什么)  

### [25、限制并发连接数](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#25限制并发连接数)  

### [26、Nginx怎么判断别IP不可访问？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#26nginx怎么判断别ip不可访问)  

### [27、用 Nginx 服务器解释-s 的目的是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#27用-nginx-服务器解释-s-的目的是什么)  

### [28、Nginx负载均衡的算法怎么实现的?策略有哪些?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#28nginx负载均衡的算法怎么实现的策略有哪些)  

### [29、Nginx的优缺点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#29nginx的优缺点)  

### [30、在Nginx中，如何使用未定义的服务器名称来阻止处理请求?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题附答案（2021年Nginx面试题及答案大汇总）.md#30在nginx中如何使用未定义的服务器名称来阻止处理请求)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")

[![大厂面试题](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")](https://github.com/javatechnorth/javanorth-itbooks/blob/master/image/面试题.png "架构师专栏")
