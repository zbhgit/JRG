# DOM1 高程3第十章 十一章 十二章学习笔记

### 1. 10.1 节点层次

文档元素，是文档的最外层元素，在HTML页面中，文档元素始终都是<html>元素。XML没有预定义，任何元素都可能成为文档元素。
> 每一段标记都可以通过树种的一个节点表示：HTML 元素通过元素节点表示，特性（attribute）通过特性节点表示，文档类型通过文档类型节点表示，而注释则听过注释节点表示。总共有12中节点类型。

  ####  1.1 Node类型

* nodeType属性，用于表明节点类型，又12个数值常量表示，任何节点类型必居其一
    * Node.ELEMENT_NODE (1)；//元素节点
    * Node.ATTRIBUTE_NODE (2)； //属性节点
    * Node.TEXT_NODE (3)；     // 文本节点
    * Node.CDATA_SECTION_NODE (4)； 
    * Node.ENTITY_REFERENCE_NODE (5)；
    * Node.ENTITY_NODE (6)；
    * Node.PROCESSING_INSTRUCTION_NODE (7)；
    * Node.COMMENT_NODE (8)
    * Node.DOCUMENT_NODE (9)；    // 文档节点
    * Node.DOCUMENT_TYPE_NODE (10)；
    * Node.DOCUMENT_FRAGMENT_NODE (11)；
    * Node.NOTATION_NODE (12)
> nodeName和nodeValue属性

对于元素节点，nodeName中保存的始终都是元素的标签名，而nodeValue的值始终为 null
```
   if (someNode.nodeType === 1) {
          value = someNode。nodeName；
   }
```

> 节点关系。每个节点都有一个parentNode属性，该属性指向文档树种的父节点，每个节点的previousSibling和nextSibling属性，可以访问同一列表中的其他节点

此外，父节点的firstChild和lastChild属性分别指向childNodes列表中的第一个和最后一个节点

> 操作节点  
  * appendChild();用于向childNodes列表的末尾添加一个节点。添加后childNodes列表将自动更新
  
  * insertBefore():在特定的位置插入节点。这个方法接收两个参数，要插入的节点和作为参照的节点。如果参照节点是null，则与appendChild（）执行相同的操作
  
  * replaceChild（）方法接收两个参数，要插入的节点和要替换的节点，该节点的所有关系指针都会被它替换的节点复制过来。
  
  * removeChild（）：接收一个参数，即要移除的节点，被移除的节点将成为方法的返回值
  
  * cloneNode（），用于创建调用这个方法的节点的一个完全相同的副本，接收一个布尔参数，表示是否执行深复制，在参数为true的情况下，执行深复制，也就是这个子节点树，在false情况下，执行浅复制，只复制节点本身
  
  
  #### 1.2 Document类型
  
  nodeType的值为9
    
    
   * documentElement属性始终指向HTML页面中的html元素
   * document.body:指向body元素
   * document.doctype： 指向<!DOCTYPE>标签。
   * document.title： 包含着title元素中的文本，这个属性也可以修改其值
   `document.title = "New Page Title" `
   
   * document.url :包含页面完整的URL
   * document.domain ： 只包含页面的域名，非只读属性，可设置
   * document.referrer ：保存着链接到当前页面的那个URL
   
 > 查找元素
   
   * getElementById（）:接收一个参数，要取得的元素的ID，如果同名id有多个，只能取得页面上同名id的第一个
   
   * getElementsByTagName()：这个方法接受一个参数，即要取得元素的标签名，而返回的是包含零或多个元素的 NodeList 
    
    取得页面所有元素              
   `var allElements = document.getElementsByTagName("*")`
   
   * getElementsByName(): 这个方法返回带有给定name特性的所有元素
   
    此外还有特殊集合
    

   * document.anchors ，包含文档中所有带 name 特性的 \<a> 元素；
   * document.applets ，包含文档中所有的 \<applet> 元素，因为不再推荐使用 \<applet> 元素，所以这个集合已经不建议使用了；
   * document.forms ，包含文档中所有的 \<form> 元素，与 document.getElementsByTagName("form")得到的结果相同；
   * document.images ，包含文档中所有的 <img> 元素，与 document.getElementsByTagName("img") 得到的结果相同；
   * document.links ，包含文档中所有带 href 特性的\<a> 元素。
   
   ------------
 
> 文档写入 

  * document.write():接收一个字符串参数，原样写入
  * document.writeln()：接收一个字符串参数，在在字符串末尾添加一个换行符
  * document.open() 打开网页输出流
  * document.close() 关闭网页的输出流
  
   
  #### 1.2 Element类型
  
  nodeType的值为1


  每个HTML元素中都存在一下标准的特性
    
     id ，元素在文档中的唯一标识符。
     title ，有关元素的附加说明信息，一般通过工具提示条显示出来。
     lang ，元素内容的语言代码，很少使用。
     dir ，语言的方向，值为 "ltr" （left-to-right，从左至右）或 "rtl" （right-to-left，从右至左），
    也很少使用。
     className ，与元素的 class 特性对应，即为元素指定的CSS类。没有将这个属性命名为 class ，
    是因为 class 是 ECMAScript 的保留字（有关保留字的信息，请参见第 1 章）。
    
  获取取特性
    
  * getAttribute（）：获取特性属性
  * setAttribute（）：设置特性属性
  * removeAttribute（）：彻底删除元素的特性
  
  
  创建元素 
  
      使用document.createElement（）方法可以创建新元素，这个方法只接受一个参数，即要创建元素的标签名
      
      创建div标签
      `var div = document.createElement('div')`
      
      写入内容
      
      `div.innetHTML =  '我是内容'`
      
      插入文档中
      ` document.body.appendChild(div)`
      
  
  元素的子节点：元素可以有任意数目的子节点和后代节点，因为元素可以是其他元素的子节点。
  childNodes属性包含了它的所有子节点，这些子节点有可能是元素、文本节点、注释、或处理指令。
  ```
    <ul id="myList">
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ul>
  ```
  > 经测试IE8及以下ul元素会包含三个子节点，分别是三个li元素
  在其他浏览器中，ul会有7个元素，包含三个li和4个文本节点


  ```
    for (var i=0, len=element.childNodes.length; i < len; i++){
      if (element.childNodes[i].nodeType == 1){
      //执行某些操作
      }
    }
  ```
  
---------
  
 文本节点
 
 nodeType值是 3。
 
 document.createTextNode（）创建新的文本节点，接收一个参数，要插入节点中的文本
 
 ---------
 Comment类型，注释类型
 
 nodeType值是 8。
 
 ----------------
 
 CDATAsection类型，只针对于基于XML的文档，表示的是CDATA区域。
 
 nodeType值为4
 
 其他节点不多介绍了。
 
 
 ### 10.2 DOM操作技术
 
 -------------
 
 #### 2.1 动态脚本
 
 使用script元素可以向页面中插入JavaScript代码，一种方式通过其src属性包含外部文件，另一种方式就是用这个元素本身包含代码。
 动态脚本：指的是在页面加载时不存在，但将来的某一时刻通修改DOM动态添加的脚本。
 
 > 代码展示

```
    var script = document.createElement("script");
    script.type = "text/javascript";
    script.src = "client.js";
    document.body.appendChild(script);
```
代码优化，便于服用

```
    function loadScript(url) {
        var script = document.createElement("script");
        script.type = "text/javascript";
        script.src = url;
        document.body.appendChild(script);
    }
    
    loadScript(client.js)
```
#### 2.2  动态样式
原理同动态脚本
代码

```
    function loadStyles(url){
        var link = document.createElement("link");
        link.rel = "stylesheet";
        link.type = "text/css";
        link.href = url;
        var head = document.getElementsByTagName("head")[0];
        head.appendChild(link);
    }
    loadStyles('style.css')
```



## 十一章 DOM扩展

--------

###  选择符API

* querySelector（）：接收一个CSS选择符，返回与该模式匹配的第一个元素，如果没有匹配发哦，返回null

```
    //取得 body 元素
    var body = document.querySelector("body");
    //取得 ID 为"myDiv"的元素
    var myDiv = document.querySelector("#myDiv");
    //取得类为"selected"的第一个元素
    var selected = document.querySelector(".selected");
    //取得类为"button"的第一个图像元素
    var img = document.body.querySelector("img.button");
```
* querySelectorAll():接收一个CSS选择符，返回的是所有匹配的元素而不仅仅是一个元素

-------

#### 元素遍历

对于元素间的空格，IE9及之前版本不会返回文本节点，而其他所有浏览器都会返回文本节点。这样，
就导致了在使用 childNodes 和 firstChild 等属性时的行为不一致。为了弥补这一差异，而同时又保
持 DOM规范不变，Element Traversal规范（www.w3.org/TR/ElementTraversal/）新定义了一组属性。

    
    Element Traversal API 为 DOM 元素添加了以下 5 个属性。
     childElementCount ：返回子元素（不包括文本节点和注释）的个数。
     firstElementChild ：指向第一个子元素； firstChild 的元素版。
     lastElementChild ：指向最后一个子元素； lastChild 的元素版。
     previousElementSibling ：指向前一个同辈元素； previousSibling 的元素版。
     nextElementSibling ：指向后一个同辈元素； nextSibling 的元素版。


------

#### HTML5 

* getElementsByClassName（）；通过document对象及所有HTML元素调用该方法。接收一个参数，即一个包含一或多个类名的字符串，返回带有指定类的哟有元素的NodeList。传入多个类名时，类名的先后顺序不重要

> 支持 getElementsByClassName() 方法的浏览器有 IE 9+、Firefox 3+、Safari 3.1+、Chrome 和
  Opera 9.5+。
  
  
* classList属性
  
  删除其中一个类名的方法
  
 ```
    <div class="bd user disabled">.....</div>
    // 删除 user类名
    
    var classNames =  div.className.split(/\s+/);
    
    var pos = -1;
    
    var len = classNames.length;
    
    for (var i = 0; i <len;i++){
      if(classNames[i] === 'user') {
          pos = i;
      }
    }
    classNames.splice(i,1);
    
    div.className = classNames.join(' ')
  
 ```
 
 新增加的classList有如下属性
 
   *  add（value） 将给定的字符串添加到列表中。如果值已经存在，就不添加了 
    
   * contains(value) 表示列表中是否存在给定的值。如果存在返回true。否则返回false。
   * remove（value） 从列表中删除给定的字符串
   * toggle（value）如果列表已经存在给定值，删除它；如果列表中没有给定值，添加他
   
   如今删除 user 类
   `div.classList.remove('user')`
   
   
   -------------
   
   #### 自定义数据属性
   
   HTML5规定可以为元素添加非标准属性，但要添加前缀 data-，目的是为元素提供与渲染无关的信息，或者提供语义信息
   
   `<div id="myDiv" data-appId="12345" data-myname="Nicholas"></div>`
  
  添加了自定义属性之后，可以通过元素的 dataset属性来访问自定义属性的值。 dataset 属性的值是 DOMStringMap的一个实例，也就一个名值对儿的映射。在这个映射中，每个 data-name 形式的属性都会有一个对应的属性，只不过属性名没有 data- 前缀（比如，自定义属性是 data-myname ，那映射中对应的属性就是 myname ）
  
  
  -----------------
  
  ####  插入标记
  
  * innerHTML属性

    在读模式下， innerHTML 属性返回与调用元素的所有子节点（包括元素、注释和文本节点）对应的 HTML 标记。在写模式下， innerHTML 会根据指定的值创建新的 DOM树，然后用这个 DOM 树完全替换调用元素原先的所有子节点。

  * outerHTML属性 
    
    在读模式下， outerHTML 返回调用它的元素及所有子节点的HTML标签。在写模式下， outerHTML会根据指定的HTML字符串创建新的DOM子树，然后用这个 DOM子树完全替换调用元素。

> 避免下面的操作

```

  for (var i=0, len=values.length; i < len; i++){
      ul.innerHTML += "<li>" + values[i] + "</li>";//要避免这种频繁操作！！
  }
```


----------

#### 文档模式 

页面的文档模式决定了可以用什么功能，可以使用哪个级别的CSS，可以在JavaScript中使用哪个级别的CSS
到了IE9，总共有以下4种文档模式

```
  IE5：以混杂模式渲染页面（IE5 的默认模式就是混杂模式）。IE8 及更高版本中的新功能都无法
使用。
  IE7：以 IE7 标准模式渲染页面。IE8 及更高版本中的新功能都无法使用。
  IE8：以 IE8 标准模式渲染页面。IE8 中的新功能都可以使用，因此可以使用 Selectors API、更多
CSS2 级选择符和某些 CSS3 功能，还有一些 HTML5 的功能。不过 IE9 中的新功能无法使用。
  IE9：以 IE9 标准模式渲染页面。IE9 中的新功能都可以使用，比如 ECMAScript 5、完整的 CSS3
以及更多 HTML5 功能。这个文档模式是最高级的模式。
```
----------------

#### children属性
由于 IE9 之前的版本与其他浏览器在处理文本节点中的空白符时有差异，因此就出现了 children
属性。这个属性是 HTMLCollection 的实例，只包含元素中同样还是元素的子节点。除此之外，
children 属性与 childNodes 没有什么区别，即在元素只包含元素子节点时，这两个属性的值相同

contains（）方法，不多介绍，测试是否包含某节点

-------------------

#### 插入文本 innerText
通过 innertText 属性可以操作元素中包含的所有文本内容，包括子文档树中的文本。在通过
innerText 读取值时，它会按照由浅入深的顺序，将子文档树中的所有文本拼接起来。在通过
innerText 写入值时，结果会删除元素的所有子节点，插入包含相应文本值的文本节点。



-----------------------


## 第十二章 

难度系数大，暂未理解透
