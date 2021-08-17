# Nginx面试题带答案（2021年Nginx面试题及答案大汇总）

Nginx面试题及答案【最新版】Nginx高级面试题大全(2021版)，发现网上很多Nginx面试题及答案整理都没有答案，所以花了很长时间搜集，本套Nginx面试题大全，Nginx面试题大汇总，有大量经典的Nginx面试题以及答案，包含Nginx语言常见面试题、Nginx工程师高级面试题及一些大厂Nginx开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Nginx面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Nginx面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/index.md)


### [1、nignx配置](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#1nignx配置)  


```
worker_processes  8;     工作进程个数

worker_connections  65535;  每个工作进程能并发处理（发起）的最大连接数（包含所有连接数）

error_log         /data/logs/nginx/error.log;  错误日志打印地址

access_log      /data/logs/nginx/access.log  进入日志打印地址

log_format  main  'remote_addr"request" ''status upstream_addr "$request_time"'; 进入日志格式

fastcgi_connect_timeout=300; #连接到后端fastcgi超时时间

fastcgi_send_timeout=300; #向fastcgi请求超时时间(这个指定值已经完成两次握手后向fastcgi传送请求的超时时间)

fastcgi_rend_timeout=300; #接收fastcgi应答超时时间，同理也是2次握手后

fastcgi_buffer_size=64k; #读取fastcgi应答第一部分需要多大缓冲区，该值表示使用1个64kb的缓冲区读取应答第一部分(应答头),可以设置为fastcgi_buffers选项缓冲区大小

fastcgi_buffers 4 64k;#指定本地需要多少和多大的缓冲区来缓冲fastcgi应答请求，假设一个php或java脚本所产生页面大小为256kb,那么会为其分配4个64kb的缓冲来缓存

fastcgi_cache TEST;#开启fastcgi缓存并为其指定为TEST名称，降低cpu负载,防止502错误发生

listen       80;                                            监听端口

server_name  rrc.test.jiedaibao.com;       允许域名

root  /data/release/rrc/web;                    项目根目录

index  index.php index.html index.htm;  访问根文件
```


### [2、请解释你如何通过不同于 80 的端口开启 Nginx?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#2请解释你如何通过不同于-80-的端口开启-nginx)  


为了通过一个不同的端口开启 Nginx，你必须进入/etc/Nginx/sites

enabled/，如果这是默认文件，那么你必须打开名为“default”的文件。编辑

文件，并放置在你想要的端口：

Like server { listen 81; }


### [3、Nginx静态资源?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#3nginx静态资源)  


静态资源访问，就是存放在nginx的html页面，我们可以自己编写


### [4、漏桶流算法和令牌桶算法知道，漏桶算法#](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#4漏桶流算法和令牌桶算法知道漏桶算法#)  


漏桶算法是网络世界中流量整形或速率限制时经常使用的一种算法，它的主要目的是控制数据注入到网络的速率，平滑网络上的突发流量。漏桶算法提供了一种机制，通过它，突发流量可以被整形以便为网络提供一个稳定的流量。也就是我们刚才所讲的情况。漏桶算法提供的机制实际上就是刚才的案例：**突发流量会进入到一个漏桶，漏桶会按照我们定义的速率依次处理请求，如果水流过大也就是突发流量过大就会直接溢出，则多余的请求会被拒绝。所以漏桶算法能控制数据的传输速率。**

![56_1.png][56_1.png]


### [5、令牌桶算法#](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#5令牌桶算法#)  


令牌桶算法是网络流量整形和速率限制中最常使用的一种算法。典型情况下，令牌桶算法用来控制发送到网络上的数据的数目，并允许突发数据的发送。Google开源项目Guava中的RateLimiter使用的就是令牌桶控制算法。**令牌桶算法的机制如下：存在一个大小固定的令牌桶，会以恒定的速率源源不断产生令牌。如果令牌消耗速率小于生产令牌的速度，令牌就会一直产生直至装满整个令牌桶。**

![56_2.png][56_2.png]


### [6、解释如何在 Nginx 服务器上添加模块?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#6解释如何在-nginx-服务器上添加模块)  


在编译过程中，必须选择 Nginx 模块，因为 Nginx 不支持模块的运行时间选

择。



### [7、fair(第三方插件)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#7fair第三方插件)  


必须安装upstream_fair模块。

对比 weight、ip_hash更加智能的负载均衡算法，fair算法可以根据页面大小和加载时间长短智能地进行负载均衡，响应时间短的优先分配。

```
upstream backserver {
 server server1; 
 server server2; 
 fair; 
}
```

哪个服务器的响应速度快，就将请求分配到那个服务器上。


### [8、Nginx 常用配置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#8nginx-常用配置)  


```
worker_processes  8; # 工作进程个数
worker_connections  65535; # 每个工作进程能并发处理（发起）的最大连接数（包含所有连接数）
error_log         /data/logs/nginx/error.log; # 错误日志打印地址
access_log      /data/logs/nginx/access.log; # 进入日志打印地址
log_format  main  '$remote_addr"$request" ''$status $upstream_addr "$request_time"'; # 进入日志格式

## 如果未使用 fastcgi 功能的，可以无视
fastcgi_connect_timeout=300; # 连接到后端 fastcgi 超时时间
fastcgi_send_timeout=300; # 向 fastcgi 请求超时时间(这个指定值已经完成两次握手后向fastcgi传送请求的超时时间)
fastcgi_rend_timeout=300; # 接收 fastcgi 应答超时时间，同理也是2次握手后
fastcgi_buffer_size=64k; # 读取 fastcgi 应答第一部分需要多大缓冲区，该值表示使用1个64kb的缓冲区读取应答第一部分(应答头),可以设置为fastcgi_buffers选项缓冲区大小
fastcgi_buffers 4 64k; # 指定本地需要多少和多大的缓冲区来缓冲fastcgi应答请求，假设一个php或java脚本所产生页面大小为256kb,那么会为其分配4个64kb的缓冲来缓存
fastcgi_cache TEST; # 开启fastcgi缓存并为其指定为TEST名称，降低cpu负载,防止502错误发生

listen       80; # 监听端口
server_name  rrc.test.jiedaibao.com; # 允许域名
root  /data/release/rrc/web; # 项目根目录
index  index.php index.html index.htm; # 访问根文件
```

Nginx 日志格式中的 $time_local 表示的是什么时间？请求开始的时间？请求结束的时间？其次，当我们从前到后观察日志中的 $time_local 时间时，有时候会发现时间顺序前后错乱的现象，请说明原因？

`$time_local` ：在服务器里请求开始写入本地的时间。

因为请求发生时间有前有后，所以会时间顺序前后错乱。


### [9、Nginx 有哪些负载均衡策略？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#9nginx-有哪些负载均衡策略)  


负载均衡，即是代理服务器将接收的请求均衡的分发到各服务器中。

Nginx 默认提供了 3 种负载均衡策略：

**轮询（默认）round_robin**

每个请求按时间顺序逐一分配到不同的后端服务器，如果后端服务器 down 掉，能自动剔除。

**IP 哈希 ip_hash**

每个请求按访问 ip 的 hash 结果分配，这样每个访客固定访问一个后端服务器，可以解决 session 共享的问题。

当然，实际场景下，一般不考虑使用 ip_hash 解决 session 共享。

**最少连接 least_conn**

下一个请求将被分派到活动连接数量最少的服务器

通过 Nginx 插件，我们还可以引入 fair、url_hash 等负载均衡策略。

另外，我们还可以配置每一个后端节点在负载均衡时的其它配置：

```
weight=1; # (weight 默认为1.weight越大，负载的权重就越大)
down; # (down 表示单前的server暂时不参与负载)
backup; # (其它所有的非backup机器down或者忙的时候，请求backup机器)
max_fails=1; # 允许请求失败的次数默认为 1 。当超过最大次数时，返回 proxy_next_upstream 模块定义的错误
fail_timeout=30; # max_fails 次失败后，暂停的时间
```


### [10、基于端口的虚拟主机](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#10基于端口的虚拟主机)  


使用端口来区分，浏览器使用域名或ip地址:端口号 访问

```
#当客户端访问
www.lijie.com, 监听端口号为8080, 直接跳转到data / www目录下文件
server {
    listen 8080;
    server_name 8080.lijie.com;
    location / {
        root data / www;
        index index.html index.htm;
    }
}#当客户端访问
www.lijie.com, 监听端口号为80直接跳转到真实 ip服务器地址 127.0.0.1: 8080
server {
    listen 80;
    server_name www.lijie.com;
    location / {
        proxy_pass http: //127.0.0.1:8080;
        index index.html index.htm;
    }
}
```


### [11、列举Nginx服务器的最佳用途。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#11列举nginx服务器的最佳用途。)  

### [12、使用“反向代理服务器的优点是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#12使用“反向代理服务器的优点是什么)  

### [13、ngx_http_upstream_module的作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#13ngx_http_upstream_module的作用是什么)  

### [14、Rewrite全局变量是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#14rewrite全局变量是什么)  

### [15、请解释 ngx_http_upstream_module 的作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#15请解释-ngx_http_upstream_module-的作用是什么)  

### [16、在 Nginx 中，解释如何在 URL 中保留双斜线?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#16在-nginx-中解释如何在-url-中保留双斜线)  

### [17、url_hash(第三方插件)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#17url_hash第三方插件)  

### [18、请陈述stub_status和sub_filter指令的作用是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#18请陈述stub_status和sub_filter指令的作用是什么)  

### [19、如何用Nginx解决前端跨域问题？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#19如何用nginx解决前端跨域问题)  

### [20、在Nginx中如何在URL中保留双斜线?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#20在nginx中如何在url中保留双斜线)  

### [21、怎么限制浏览器访问？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#21怎么限制浏览器访问)  

### [22、为什么Nginx性能这么高？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#22为什么nginx性能这么高)  

### [23、请解释什么是`C10K`问题?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#23请解释什么是c10k问题)  

### [24、用`Nginx`服务器解释`-s`的目的是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#24用nginx服务器解释-s的目的是什么)  

### [25、请列举 Nginx 的一些特性。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#25请列举-nginx-的一些特性。)  

### [26、ip_hash( IP绑定)](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#26ip_hash-ip绑定)  

### [27、基于虚拟主机配置域名](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#27基于虚拟主机配置域名)  

### [28、为什么要用Nginx？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#28为什么要用nginx)  

### [29、location的语法能说出来吗？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#29location的语法能说出来吗)  

### [30、请解释 Nginx 如何处理 HTTP 请求。](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题带答案（2021年Nginx面试题及答案大汇总）.md#30请解释-nginx-如何处理-http-请求。)  





## [全部答案，整理好了，直接下载吧](https://gitee.com/souyunku/DevBooks/blob/master/docs/daan.md)

### 下载链接：[全部答案，整理好了](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/daan.md)




## 新增，高清PDF：172份，7701页，最新整理

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/mst.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")

[![大厂面试题](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")](https://www.souyunku.com/wp-content/uploads/weixin/githup-weixin.png "架构师专栏")
