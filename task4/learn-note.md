## HTML学习笔记

1. HTML、XML、XHTML有什么区别

简单介绍（内容来自维基百科）

> HTML:超文本标记语言（英语：HyperText Markup Language，简称：HTML）是一种用于创建网页的标准标记语言。 HTML是一种基础技术，常与CSS、JavaScript一起被众多网站用于设计令人赏心悦目的网页、网页应用程序以及移动应用程序的用户界面。

> XML:可扩展标记语言（英语：Extensible Markup Language，简称：XML），是一种标记语言。标记指计算机所能理解的信息符号，通过此种标记，计算机之间可以处理包含各种信息的文章等

> XHTML可扩展超文本标记语言（英语：Extensible HyperText Markup Language，XHTML），是一种标记语言，表现方式与超文本标记语言（HTML）类似，不过语法上更加严格

区别

* XML的设计宗旨是传输数据，而非显示数据，如下一段代码
    
```
<?xml version="1.0">
<小纸条>
<收件人>大元</收件人>
<發件人>小張</發件人>
<主題>問候</主題>
<具體內容>早啊，飯吃了沒？ </具體內容>
```
    
* HTML被设计用来显示数据，其焦点是数据的外观。如下代码

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>Hello World</h1>
<h2>Hello HTML</h2>
</body>
</html>
```

* XHTML与HTML对比
    1. 文档的结构良好，元素都必须有结束标签，而且必须合理嵌套
    ```
        正确嵌套
        <p><em>这是一个强调的段落。</em></p>
        错误嵌套
        <em><p>这是一个强调的段落。</em></p>

    ```
    
    2. XHTML文件要求元素名称和属性必须小写，因为XML本身大小写意义不同，比如\<LI>和\<li>是完全不同的
    
    3. XHTML要有结束标签
    ```
        正确结束
        <p>这是一个段落。</p><p>这是一个段落。</p>
        错误结束
        <p>这是一个段落。<p>这是一个段落。</p>
    
    ```
    
    4. XHTML属性值必须总是使用引号包裹
    
    ```
         正确
         <td rowspan="3">
         错误
         <td rowspan=3>
        
     ```
     
    5. XHTML禁止属性简化，属性值必须书写完整
    
    ```
         正确
         <dl compact="compact">
         错误
         <dl compact>
             
    ```
    6. XHTML中空元素必须有一个结束标签，或者用 "/>"来结束开始标签
    
    ```
        正确的：结束空标签
        <br /><hr />
        错误的：没有结束空标签
        <br><hr>
    ```
    
2. 如何理解HTML语义化

> 语义化HTML是一种编写HTML的方式，选择合适的标签，使用合理的代码结构，便于开发者阅读，同时让浏览器的爬虫和及其很好地解析。利于SEO


3. 如何理解内容与样式的分离原则

> 写HTMl的时候先不管样式，重点放在HTML的结构和语义化上，让HTML能体现页面结构或者内容，之后再去写样式
> 写JS的时候，尽量不要用JS直接操作样式，而是通过给元素添加删除class来控制样式变化
>HTML内不允许出现属性样式，尽量不要出现行内样式

实现结构与样式，行为的分离主要是为了

* 提高代码的重用性，减少冗余代码，提高开发速度
* 提高代码的结构性，组织好代码结构更利于维护和应变特殊情况。
* 尽量减小文件的大小，提高页面的加载速度

代码展示1,四个相同样式的DIV
```
<div style="width:100px;height: 100px;background-color: red;margin: 10px;">
    我是div1
</div>
<div style="width:100px;height: 100px;background-color: red;margin: 10px;">
    我是div2
</div>
<div style="width:100px;height: 100px;background-color: red;margin: 10px;">
    我是div3
</div>
<div style="width:100px;height: 100px;background-color: red;margin: 10px;">
    我是div4
</div>
```

代码展示2，同样四个相同样式的DIV
```
<style>
    div {
        width:100px;
        height: 100px;
        background-color: 
        red;margin: 10px;
    }
</style>

<div >
    我是div1
</div>
<div >
    我是div2
</div>
<div >
    我是div3
</div>
<div>
    我是div4
</div>


```


4. 常见的meta标签

> meta 元素表示那些不能由其他HTML元相关元素（base，link script style title）之一表示的任何元数据信息
 
 *全局属性name在meta元素中具有特殊的语义；另外，在同一个meta标签中，name，http-equiv或者charset三者中任何一个属性存在时，itemprop属性不能被使用*
 
* charset 声明当前文档所使用的字符编马，但该属性可以被任何一个元素的lang特性的值覆盖
 > 鼓励使用 UTF-8；
 不应该使用不兼容的ASCLL编码规范
 
       <meta charset="UTF-8">

* content 基于内容，这个属性为http-equiv或name属性提供了相关值的定义

* http-equiv 这个枚举属性定义了能改变服务器和用引擎行为的编译，这个编译值使用content来定义

* name具有如下属性值

    |属性值|含义|
    |----|----|
    |application-name|定义正在运行在该网页上的网络应用名称|
    |author| 这个网络应用的作者|
    |description|关于页面内容的缩略而精简的描述|
    |keywords|网页内容的关键词|
    |viewport|视口设置|

还有其他属性，更多请参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/meta)

> 常用代码设置如下

```
    <!--设置字符编码-->
    <meta charset="UTF-8">
    <!--设置页面关键词-->
    <meta name="keyword" content="meta-keyword">
    <!--设置页面描述-->
    <meta name="description" content="learn-meta">
    <!--设置页面作者-->
    <meta name="author" content="author-name">
    <!--移动端视口设置-->
    <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no">
    <!--优先使用IE最新版本和Chrome-->
    <meta http-equiv="x-ua-compatible" content="IE=edge,chrome=1">
```

5. 文档声明的作用?严格模式和混杂模式指什么?<!doctype html> 的作用

> \<!DOCTYPE>文档声明作用：

告知浏览器当前的HTML（或XML）文档是哪一个版本，触发不同的渲染模式。

> 严格模式：浏览器根据规范呈现页面，行为即由 HTML 与 CSS 的规范描述的行为

> 混杂模式：页面以一种比较宽松的向后兼容的方式呈现页面

*两者差异*

 * 对CSS IE盒模型处理方式不同
 
 * 某些行内元素的垂直对齐方式不同
 
还有一种模式：接近标准模式，在此模式下，只有少数的怪异行为被实现
 
 > <!doctype html> 是所有可用的DOCTYPE中最简单的，是被HTML5推荐的。该声明的作用为：启用严格模式呈现页面
 
 6. 浏览器出现乱码的原因
 
 > 因为编写页面时所用的字符编码格式与浏览器解析时的编码格式不相同，所以建议字符编码设置为UTF-8
 
 7. |常见浏览器|内核|代码|
     |---|---|:---|
     |chrome|WebKi| Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/57.0.2987.133 Safari/537.36 |
     |IE11| Trident| Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; rv:11.0) like Gecko |
     |Firefox|Gecko|Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:52.0) Gecko/20100101 Firefox/52.0|
     |Microsoft Edge|Edge||
     |uc浏览器|webkit||
     |Safari|webkit||


 8. HTML常用标签

    |标签|含义|
    |:----|:----|
    |h1~h6|标题，h1代表页面最大的标题，h2二级标题……|
    |p|段落标签，表示一个段落|
    |a|链接标签，当需要打开网页跳转或使用锚点时使用|
    |img|展示一张图片，当需要插如图片时使用|
    |div| 语义为“一大块”，用于给页面划分区块，让结构更清晰|
    |ul li|ul是无序列表，用于展示并列的内容，li是他的子元素|
    |ol li|ol是有序列表|，用于表示带步骤或者编号的并列内容，li同样是他的子元素
    |dl dt dd|用于展示一系列“标题，内容……”的场景|
    |button|按钮，需要点击时使用|
    |strong|很重要，强调性更强|
    |em|需要强调下|
    |iframe|用于嵌入一个页面，注意跨域操作问题|
    |table|用于展示表格，不能用来做布局，thead tbody tfoot可省略|

 


