## 从输入URL到页面展示发生了什么？

1. 在浏览器中输入一个URL

>例如 facebook.com 

2. 浏览器开始查找IP地址（域名解析）

> DNS解析过程如下

 * Browser cache(浏览器缓存)：浏览器缓存DNS会保存一段时间。有趣的是，系统不会告诉浏览器每个DNS记录生成的时间，因此浏览器会以固定的时间缓存他们(不同浏览器缓存时间不等2-30分钟)

 * OS cache(系统缓存)：系统存在自己的缓存，会查找hosts文件中的内容

 * Router cache(路由器缓存)：路由器也会缓存DNS

 * ISP DNS cache(服务器缓存，Internet Service Provider)

 * Recursive search(递归查询)：递归搜索从根域名服务器开始，在通过.COM顶级域名服务器，然后到Facebook的域名服务器搜索


 3. 浏览器发送一个HTTP请求到服务器
浏览器发送请求到Facebook服务器

例如
```
    GET http://www.facebook.com/ HTTP/1.1  // 请求方式和地址
    Accept: application/x-ms-application, image/jpeg,  application/xaml+xml, [...]  // 接受那种类型的响应
    User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; [...]  // 浏览器识别
    Accept-Encoding: gzip, deflate // 接受那种类型的响应
    Connection: Keep-Alive
    Host: facebook.com
    Cookie: datr=1265876274-[...]; locale=en_US; lsd=WW[...]; c_user=2101[...] // 储存着登录用户名称，由服务器分配给用户的密码和用户的一些设置。Cookie将存储在客户端上的文件中，

```


4. 服务器返回响应

> 下面是服务器返回的响应

```
  HTTP/1.1 200 OK
  Cache-Control: private, no-store, no-cache, must-revalidate, post-check=0,
      pre-check=0
  Expires: Sat, 01 Jan 2000 00:00:00 GMT
  P3P: CP="DSP LAW"
  Pragma: no-cache
  Content-Encoding: gzip  // 采用的gzip算法
  Content-Type: text/html; charset=utf-8 // 响应内容格式
  X-Cnection: close
  Transfer-Encoding: chunked
  Date: Fri, 12 Feb 2010 09:05:55 GMT

```


5. 浏览器开始渲染网页

  浏览器收到HTML、CSS、JS文件后，开始 渲染网页

  Webkit内核浏览器渲染过程

  * 解析HTML构建DOM树

  * 解析CSS文件构建渲染树

  * 浏览器布局渲染树并将其绘制到屏幕上

6. 链接结束



参考:

  [http://igoro.com/archive/what-really-happens-when-you-navigate-to-a-url/](http://igoro.com/archive/what-really-happens-when-you-navigate-to-a-url/)

  [https://segmentfault.com/a/1190000006879700](https://segmentfault.com/a/1190000006879700)


     