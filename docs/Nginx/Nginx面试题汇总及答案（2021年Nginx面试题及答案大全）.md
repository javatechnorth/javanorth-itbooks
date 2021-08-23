# Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）

Nginx面试题及答案【最新版】Nginx高级面试题大全(2021版)，发现网上很多Nginx面试题及答案整理都没有答案，所以花了很长时间搜集，本套Nginx面试题大全，Nginx面试题大汇总，有大量经典的Nginx面试题以及答案，包含Nginx语言常见面试题、Nginx工程师高级面试题及一些大厂Nginx开发面试宝典，面试经验技巧等，应届生，实习生，企业工作过的，都可参考学习!

## 这套Nginx面试题汇总大全，希望对大家有帮助哈~ 

## 博主已将以下这些面试题整理成了一个Nginx面试手册，是PDF版的

### 下载链接：[高清172份，累计 7701 页大厂面试题  PDF](https://github.com/javatechnorth/javanorth-itbooks/blob/master/docs/index.md)


### [1、解释如何在`Nginx`服务器上添加模块?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#1解释如何在nginx服务器上添加模块)  


在编译过程中，必须选择`Nginx`模块，因为`Nginx`不支持模块的运行时间选择。


### [2、使用“反向代理服务器”的优点是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#2使用“反向代理服务器的优点是什么)  


反向代理服务器可以隐藏源服务器的存在和特征。它充当互联网云和 web 服务

器之间的中间层。这对于安全方面来说是很好的，特别是当您使用 web 托管服

务时。


### [3、请列举 Nginx 服务器的最佳用途。Nginx 服务器的最佳用法是在网络上部署动态 HTTP 内容，使用 SCGI、WSGI 应](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#3请列举-nginx-服务器的最佳用途。nginx-服务器的最佳用法是在网络上部署动态-http-内容使用-scgiwsgi-应)  


用程序服务器、用于脚本的 FastCGI 处理程序。它还可以作为负载均衡器。


### [4、用Nginx服务器解释-s的目的是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#4用nginx服务器解释-s的目的是什么)  


用于运行Nginx -s参数的可执行文件。


### [5、使用“反向代理服务器”的优点是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#5使用“反向代理服务器的优点是什么)  


反向代理服务器可以隐藏源服务器的存在和特征。它充当互联网云和 Web 服务器之间的中间层。这对于安全方面来说是很好的，特别是当我们使用 Web 托管服务时。

**这里，先不考虑负载均衡。**

**什么是正向代理？**

一个位于客户端和原始服务器(origin server)之间的服务器，为了从原始服务器取得内容，客户端向代理发送一个请求并指定目标(原始服务器)，然后代理向原始服务器转交请求并将获得的内容返回给客户端。

**1、** 客户端才能使用正向代理。

**2、** 正向代理总结就一句话：代理端代理的是客户端。例如说：? 我们使用的翻墙软件，OpenVPN 等等。

**什么是反向代理？**

反向代理（Reverse Proxy）方式，是指以代理服务器来接受 Internet上的连接请求，然后将请求，发给内部网络上的服务器并将从服务器上得到的结果返回给 Internet 上请求连接的客户端，此时代理服务器对外就表现为一个反向代理服务器。

**反向代理总结就一句话：代理端代理的是服务端。**

**请列举 Nginx 和 Apache 之间的不同点？**

**1、** 轻量级，同样起 web 服务，Nginx 比 Apache 占用更少的内存及资源。

**2、** 抗并发，Nginx 处理请求是异步非阻塞的，而 Apache 则是阻塞型的，在高并发下 Nginx 能保持低资源低消耗高性能。

**3、** 最核心的区别在于 Apache 是同步多进程模型，一个连接对应一个进程；Nginx 是异步的，多个连接（万级别）可以对应一个进程。

**4、** Nginx 高度模块化的设计，编写模块相对简单。

**LVS、Nginx、HAproxy 有什么区别？**

**1、** LVS ：是基于四层的转发。

**2、** HAproxy ： 是基于四层和七层的转发，是专业的代理服务器。

**3、** Nginx ：是 WEB 服务器，缓存服务器，又是反向代理服务器，可以做七层的转发。

Nginx 引入 [TCP 插件][TCP]之后，也可以支持四层的转发。

**区别**

LVS 由于是基于四层的转发所以只能做端口的转发，而基于 URL 的、基于目录的这种转发 LVS 就做不了。

**工作选择：**

HAproxy 和 Nginx 由于可以做七层的转发，所以 URL 和目录的转发都可以做，在很大并发量的时候我们就要选择 LVS ，像中小型公司的话并发量没那么大选择 HAproxy 或者 Nginx 足已。

由于 HAproxy 由是专业的代理服务器配置简单，所以中小型企业推荐使用HAproxy 。

**1、** 有些使用，使用 HAproxy 还是 Nginx ，也和公司运维对哪个技术栈的掌控程度。掌控 OK ，选择 Nginx 会更加不错。

**2、** 另外，LVS + Nginx 和 LVS + HAProxy 也是比较常见的选型组合。

**Squid、Varinsh、Nginx 有什么区别？**

三者都实现缓存服务器的作用。所以，本问题所有的视角，都是在作为缓存服务器下来聊。

**1、** Nginx本来是反向代理/web服务器，用了插件可以做做这个副业(缓存服务器)。

**2、** 但是本身不支持特性挺多，只能缓存静态文件。

**3、** 从这些功能上，Varinsh 和 Squid 是专业的 Cache 服务，而Nginx 这些是第三方模块完成。

**4、** Varnish 本身的技术上优势要高于 Squid ，它采用了可视化页面缓存技术。

**5、** 在内存的利用上，Varnis h比 Squid 具有优势，性能要比 Squid 高。

**6、** 还有强大的通过 Varnish 管理端口，可以使用正则表达式快速、批量地清除部分缓存

**7、** Varnish 是内存缓存，速度一流，但是内存缓存也限制了其容量，缓存页面和图片一般是挺好的。

**8、** Squid 的优势在于完整的庞大的 cache 技术资料，和很多的应用生产环境。

**工作选择：**

要做 cache 服务的话，我们肯定是要选择专业的 cache 服务，优先选择Squid 或者 Varnish 。


### [6、什么是正向代理和反向代理？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#6什么是正向代理和反向代理)  


**1、** 正向代理就是一个人发送一个请求直接就到达了目标的服务器

**2、** 反方代理就是请求统一被Nginx接收，nginx反向代理服务器接收到之后，按照一定的规 则分发给了后端的业务处理服务器进行处理了


### [7、Nginx怎么处理请求的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#7nginx怎么处理请求的)  


nginx接收一个请求后，首先由listen和server_name指令匹配server模块，再匹配server模块里的location，location就是实际地址

```
server {#第一个
    Server区块开始，表示一个独立的虚拟主机站点
    listen 80；#提供服务的端口，默认 80
    server_name localhost；#提供服务的域名主机名
    location / {#第一个
        location区块开始
        root html；#站点的根目录，相当于 Nginx的安装目录
        index index.html index.htm；#默认的首页文件，多个用空格分开
    }#第一个
location区块结果
```


### [8、权重 weight](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#8权重-weight)  


weight的值越大分配

到的访问概率越高，主要用于后端每台服务器性能不均衡的情况下。其次是为在主从的情况下设置不同的权值，达到合理有效的地利用主机资源。

```
upstream backserver {
 server 192.168.0.12 weight=2;
 server 192.168.0.13 weight=8;
}
```

权重越高，在被访问的概率越大，如上例，分别是20%，80%。


### [9、限流怎么做的？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#9限流怎么做的)  


Nginx限流就是限制用户请求速度，防止服务器受不了

**限流有3种**

**1、**  正常限制访问频率（正常流量）

**2、**  突发限制访问频率（突发流量）

**3、**  限制并发连接数

**Nginx的限流都是基于漏桶流算法，底下会说道什么是桶铜流**

**实现三种限流算法**


### [10、解释如何在Nginx中获得当前的时间?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#10解释如何在nginx中获得当前的时间)  


要获得Nginx的当前时间，必须使用SSI模块、$$date_gmt和$$date_local的变量。Proxy_set_header THE-TIME $date_gmt;


### [11、使用“反向代理服务器”的优点是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#11使用“反向代理服务器的优点是什么)  

### [12、解释 Nginx 是否支持将请求压缩到上游?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#12解释-nginx-是否支持将请求压缩到上游)  

### [13、正常限制访问频率（正常流量）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#13正常限制访问频率正常流量)  

### [14、Nginx 有哪些优点？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#14nginx-有哪些优点)  

### [15、请列举Nginx的一些特性？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#15请列举nginx的一些特性)  

### [16、为什么 Nginx 不使用多线程？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#16为什么-nginx-不使用多线程)  

### [17、fastcgi 与 cgi 的区别？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#17fastcgi-与-cgi-的区别)  

### [18、请解释 Nginx 服务器上的 Master 和 Worker 进程分别是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#18请解释-nginx-服务器上的-master-和-worker-进程分别是什么)  

### [19、Nginx 如何开启压缩？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#19nginx-如何开启压缩)  

### [20、location的作用是什么？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#20location的作用是什么)  

### [21、Nginx如何处理HTTP请求？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#21nginx如何处理http请求)  

### [22、Nginx配置高可用性怎么配置？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#22nginx配置高可用性怎么配置)  

### [23、解释如何在Nginx服务器上添加模块?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#23解释如何在nginx服务器上添加模块)  

### [24、为什么要做动、静分离？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#24为什么要做动静分离)  

### [25、请解释是否有可能将 Nginx 的错误替换为 502 错误、503?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#25请解释是否有可能将-nginx-的错误替换为-502-错误503)  

### [26、在 Nginx 中，如何使用未定义的服务器名称来阻止处理请求?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#26在-nginx-中如何使用未定义的服务器名称来阻止处理请求)  

### [27、Nginx服务器上的Master和Worker进程分别是什么?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#27nginx服务器上的master和worker进程分别是什么)  

### [28、突发限制访问频率（突发流量）](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#28突发限制访问频率突发流量)  

### [29、Nginx怎么做的动静分离？](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#29nginx怎么做的动静分离)  

### [30、请解释一下什么是 Nginx?](https://gitee.com/souyunku/NewDevBooks/blob/master/docs/Nginx/Nginx面试题汇总及答案（2021年Nginx面试题及答案大全）.md#30请解释一下什么是-nginx)  





