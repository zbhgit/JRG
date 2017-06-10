## 第21章  Ajax与Comet

本章内容 
* 使用XMLHttpRequest对象
* 使用XMLHttpRequest事件
* 跨域Ajax通信的限制

1.XMLHttpRequest对象

IE7 及以上创建XHR对象 

`var xhr = new XMLHttpRquest()`

1.1 用法

在使用XHR对象时，要调用的第一个方法是open(),它接受三个参数：要发送请求的类型、请求的URL和表示是否异步发送请求的布尔值
`xhr.send('get','example.php',false)`

注意：一，url相对于执行代码当前页面的路径；二，调用open（）方法并不会真正发送请求，而是启动一个请求以备发送。
> 只能向同一个域中使用相同端口和协议的url发送请求

--------------

要发送特定的请求，必须调用send（）方法。
`xhr.send(null)`

send()接收一个参数，即要作为请求主体发送的数据。如果不需要通过请求主题发送数据，则必须传入null。因为这个参数对有修浏览器来说是必需的。

------------------
收到响应后，响应的数据会自动填充XHR对象属性

* responseText：作为响应主体被返回的文本
* responseXML：如果响应的内容类型是‘text/xml’或 'application/xml'，这个属性将保存着包含响应数据的XML DOM文档

* status： 响应的HTTP状态
* statusText：HTTP状态说明

在接收到响应后，第一步是检查status属性，已确定响应已经成功返回。
一般来说，可以将http状态码为200作为成功的标志。吃屎responseText属性的内容已经就绪，
此外，状态码为304表示请求的资源并没有被修改，可以直接使用浏览器中缓存的版本。

```
  xhr.open("get", "example.txt", false);
  xhr.send(null);
  if ((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){
      alert(xhr.responseText);
  } else {
      alert("Request was unsuccessful: " + xhr.status);
  }
```

---------------


多数情况下，我们还要发送异步请求，才能让JavaScript继续执行而不必等待响应。此时，可以检测XHR对象的readyState属性，该属性表示请求/响应过程中当前活动阶段：
* 0： 未初始化。尚未调用open（）方法
* 1： 启动。已经调用open（）方法，但尚未调用send（）方法。
* 2： 发送。已经调用send方法，但尚未接收到响应。
* 3： 接收。 已经接收到部分响应数据
* 4： 完成。已经接收到全部响应数据，而且已经可以在客户端使用了。

只要readyState的属性值由一个值变为另一个值，就会触发一次readystatechange事件。可以利用这个事件检测每次状态变化后 readyState的值。
```
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = function(){
    if (xhr.readyState == 4){
       if ((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){
          alert(xhr.responseText);
       } else {
          alert("Request was unsuccessful: " + xhr.status);
       }
    }
};
xhr.open("get", "example.txt", true);
xhr.send(null);

```

> 这个例子在 onreadystatechange 事件处理程序中使用了 xhr 对象，没有使用this 对象，原因是 onreadystatechange 事件处理程序的作用域问题。如果使用this 对象，在有的浏览器中会导致函数执行失败，或者导致错误发生。因此，使用实际的 XHR 对象实例变量是较为可靠的一种方式。

另外，在接收到响应之前还可以调用abort（）方法来取消异步请求：
`xhr.abort()`
调用这个方法后，XHR对象会停止触发事件，而且也不在允许访问任何和响应有关的对象属性

1.2  HTTP头部信息

每个HTTP请求和响应都会带有响应的头部信息。
默认情况下，在发送XHR请求的同事，还会发送下列头部信息

   * Accept：浏览器能够处理的内容类型
   * Accept-Charset：浏览器能够显示的字符集
   * Accept-Encoding：浏览器能够处理的压缩编码
   * Accept-Language：浏览器当前设置的语言
   * Connection：浏览器与服务器之间连接的类型
   * Cookie：当前页面设置的任何Cookie
   * Host： 发出请求的页面所在的域
   * Referer：发出请求的页面的URL（规范中单词错误）
   * User-Agent：浏览器用户代理字符串
   
使用 setRequestHeader（）可以设置自定义的请求头部信息，可以接受两个参数：头部字段的名称和头部字段的值，必须在调用open方法之后且在调用send方法之前。
   ```
     xhr.open("get", "example.php", true);
     xhr.setRequestHeader("MyHeader", "MyValue");
     xhr.send(null);
   ```
   
调用 XHR 对象的 getResponseHeader() 方法并传入头部字段名称，可以取得相应的响应头部信息。而调用 getAllResponseHeaders() 方法则可以取得一个包含所有头部信息的长字符串   
   
1.3 GET请求

GET请求是最常见的请求类型，最常用与想服务器查询某些信息。必要时，可以将查询字符串参数追加到URL的末尾，以便将信息发送给服务器。
```
  function addURLParam(url, name, value) {
      url += (url.indexOf("?") == -1 ? "?" : "&");
      url += encodeURIComponent(name) + "=" + encodeURIComponent(value);
      return url;
  }
  var url = "example.php";
  //添加参数
  url = addURLParam(url, "name", "Nicholas");
  url = addURLParam(url, "book", "Professional JavaScript");
  //初始化请求
  xhr.open("get", url, false);

```

1.4 POST请求

使用频率仅次于GET的请求是POST请求，通常用于向服务器发送应该被保存的数据。
```
  xhr.open("post", "postexample.php", true);
  xhr.setRequestHeader("Content-Type","application/x-www-form-urlencoded");
  var form = document.getElementById("user-info");
  xhr.send(serialize(form));
```
--------------------------------------


2. XMLHttpRequest 2 级


2.1  FormData

现代Web应用中频繁使用的意向功能就是表单数据的序列化。FormData为序列化表单以及创建于表单相同数据提供了便利。

```
  var data = new FormData();
  data.append('name','zhangsan');
```
append()方法接收两个参数：键和值、分别对应表单字段的名字和字段中包含的值。

使用FormData的方便之处体现在不必明确地在XHR对象上设置请求头部。
```
  var xhr = createXHR();
  xhr.onreadystatechange = function(){
    if (xhr.readyState == 4){
      if ((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){
          alert(xhr.responseText);
      } else {
          alert("Request was unsuccessful: " + xhr.status);
      }
    }
  };
  xhr.open("post","postexample.php", true);
  // 省去了设置请求头部
  var form = document.getElementById("user-info");
  xhr.send(new FormData(form));

```

----------------------
2.2  超时设定

timeout属性：表示请求在等待响应多少毫秒之后就终止。
在给timeout 设置一个数值后，如果在规定的时间内浏览器还没有接收到响应，那么就会触发 timeout 事件，进而会调用 ontimeout 事件处理程序。

> IE8+ 以上支持，其他浏览器需要测试

-------------------

2.3  overrideMimeType（）方法。

用于重写XHR响应的MIME类型。
```
    xhr.open("get", "text.php", true);
    xhr.overrideMimeType("text/xml");
    xhr.send(null);

```
这个例子强迫XHR对象将响应当做XML而非纯文本来处理。


---------------------

3. 进度事件
Progress Events 规范是 W3C 的一个工作草案，定义了与客户端服务器通信有关的事件。这些事件最
早其实只针对 XHR 操作，但目前也被其他 API 借鉴。有以下 6 个进度事件。
* loadstart ：在接收到响应数据的第一个字节时触发。
* progress ：在接收响应期间持续不断地触发。
* error ：在请求发生错误时触发。
* abort ：在因为调用 abort() 方法而终止连接时触发。
* load ：在接收到完整的响应数据时触发。
* loadend ：在通信完成或者触发 error 、 abort 或 load 事件后触发。

每个请求都从触发 loadstart 事件开始，接下来是一或多个 progress 事件，然后触发 error 、
abort 或 load 事件中的一个，最后以触发 loadend 事件结束。

3.1 load事件

```
    xhr.onload = function(){
        if ((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304){
            alert(xhr.responseText);
        } else {
            alert("Request was unsuccessful: " + xhr.status);
        }
    };
```

3.2 progress事件

Mozilla 对 XHR 的另一个革新是添加了 progress 事件，这个事件会在浏览器接收新数据期间周期
性地触发。而 onprogress 事件处理程序会接收到一个 event 对象，其 target 属性是 XHR 对象，但
包含着三个额外的属性： lengthComputable 、 position 和 totalSize 。其中， lengthComputable
是一个表示进度信息是否可用的布尔值， position 表示已经接收的字节数， totalSize 表示根据
Content-Length 响应头部确定的预期字节数。有了这些信息，我们就可以为用户创建一个进度指示器
了


```
xhr.onprogress = function(event){
    var divStatus = document.getElementById("status");
    if (event.lengthComputable){
        divStatus.innerHTML = "Received " + event.position + " of " +
        event.totalSize +" bytes";
    }
};

```

4. 跨源资源共享

4.1  cros 

4.2 jsonp



