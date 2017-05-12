### Form表单笔记
1. form表单有什么作用？有哪些常用的input 标签，分别有什么作用？

   form表单作用：用来向web服务器提交信息
   
   > 常用属性
   
   |属性名|属性值|说明|
   |---|---|---|
   |method|post和get|用那种方式提交信息|
   |name|---|这个表单的名字|
   |action|一个URL|一个处理form信息的程序所在URL|
   |enctype|1.application/x-www-form-urlencoded,2.multipart/form-data,3.text/plain|第一个为默认值，第二个当上传文件时使用|
   
   
   >常用input标签
   
   |type类型|说明|
   |---|---|
   |text|单行文本框|
   |password|密码框|
   |button|普通按钮|
   |checkbox|多选框|
   |file|上传文件|
   |radio|单选框组件|
   |hidden|隐藏域|
   |submit|提交数据按钮|
   |reset|重置按钮|

   
2. GET和POST方式的区别
   
   > 区别 
   
   * GET：常用与获取信息，并不会修改web服务器上的资源
    POST：常用发送请求信息，有可能修改服务器上的资源
   
   * GET请求的数据会附在URL之后，以？分割URL和传输数据，参数之间以&项链
     POST把提交的数据放置在HTTP包的包体中
     
   * GET方式因URL长度的限制，所发送的数据量就有了一定限制，但这个限制和浏览器和服务器有关。POST方式理论上讲没有大小的限制，
 
3. input中name的作用

  > name 给该input元素添加标识，用来是服务器识别所受到的数据
  
4. 单选框radio分组
  
  > 使相同分组的内容的name属性相同
  
  ```
       <input type="radio" name="sex">男
       <input type="radio" name="sex">女
       <input type="radio" name="family">父亲
       <input type="radio" name="family">母亲
  ```
  
5.  placeholder的作用

> 当文本框有该属性时，文本框内会显示placeholder的值，当文本框开始输入内容时，文本框显示placeholder的内容自动消失，当文本框的内容为空时，placeholder的值又重新显示

6. type=hidden的作用

> 隐藏不想让用户看到的信息，但是这些信息对于Web应用又是非常必要的。
    
   *  暂存信息：后端在构造web页面的过程中，通过hidden隐藏域在页面中添加了相关数据信息(用户对网页进行操作时可能会用到这些数据信息),服务器可能会通过隐藏域的信息进行信息验证，可以有效防止请求数据带来的安全隐患
   
   
7.   [form表单简单介绍](http://www.jianshu.com/p/a870ba51dfb8)
  

8. [表单效果链接](https://zbhgit.github.io/learn-task/task5/)