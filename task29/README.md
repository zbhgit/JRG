题目1： jQuery 中， $(document).ready()是什么意思？

    能够在DOM元素加载完成后执行JS代码，不必等CSS样式图片等加载完毕再执行

题目2： $node.html()和$node.text()的区别?
* $node.html()返回该节点下的HTML（包括HTML标签）
* $node.text()返回该节点下的文本内容（不包括HTML标签）

题目3： $.extend 的作用和用法? 
    
  作用：合并对象，接受对象作为参数。他会将第二个及其以后的参数对象的属性复制到第一个参数对象中，如果同名的属性在第一个参数对象中已经存在，则会覆盖他。如果仅传入了一个对象，则该对象的属性会复制到Jquery对象自身中；

    用法
    ```
        var obj={};
        var obj1={
            name:"战三"，
            sex: "man"
        };
        var obj2={
            name: "王五"，
            age: 28
        };

        $.extend(obj,obj1);
        $.extend(obj,obj1,obj2);
        $.extend(obj1);
        var opts = $.extend({},defalut,obj);
        // 上面几种是浅拷贝  

        // 下面是深拷贝 
        $.extend(true,obj,obj1);
   
    ```   

题目4： jQuery 的链式调用是什么？

链式调用：使用jQuery方法时，对象方法返回的是对象本身，可以调用对此对象的其他jQuery方法，实现连续调用多个方法

`$(this).siblings().removeClass('active');`

题目5： jQuery 中 data 函数的作用

作用：实际上是对js对象或DOM对象的额外属性做一个集中管理，来避免内存泄漏
```
    $.data(ele, name, data)是对ele元素附加数据
    $().data(key, value), $().data(obj)是为jQuery对象中的所有DOM对象分别附加数据
    $().data(key), $().data()从jQuery对象上读数据
```
题目6： 写出以下功能对应的 jQuery 方法：

> 给元素 $node 添加 class active，给元素 $noed 删除 class active
```
    $node.addClass('active');
    $node.removeClass('active);
```

>展示元素$node, 隐藏元素$node
```
    $node.show()
    $node.hide()
```

>获取元素$node 的 属性: id、src、title， 修改以上属性
```
    $node.attr('id')
    $node.attr('src')
    $node.attr('title')

    $node.attr('id','myId')
    $node.attr('src','mySrc')
    $node.attr('title','myTitle')
```
>给$node 添加自定义属性data-src

`$node.attr('data-src','hello')`

>在$ct 内部最开头添加元素$node

`$ct.prepend($node)`

>在$ct 内部最末尾添加元素$node

`$ct.append($node)`

>删除$node

`$node.remove()`

>把$ct里内容清空

`$ct.empty()`

>在$ct 里设置 html <div class="btn"></div>

`$ct.html('<div class="btn"></div>')`

>获取、设置$node 的宽度、高度(分别不包括内边距、包括内边距、包括边框、包括外边距)

```
    $node.width();                // width
    $node.height();               // height
    $node.innerWidth();       // width+ padding
    $node.innerHeight();      // height+ padding
    $node.outerWidth();       // width+ padding + border
    $node.outerHeight();      // height + padding + border
    $node.outWidth(true);    // width ＋ padding + border + margin
    $node.outHeight(true);   // height + padding + border + margin
```

>获取窗口滚动条垂直滚动距离

`$(window).scrollTop()`

>获取$node 到根节点水平、垂直偏移距离

`$node.offset()`

>修改$node 的样式，字体颜色设置红色，字体大小设置14px

`$node.css({'color': 'red','font-size': '14px'})`

>遍历节点，把每个节点里面的文本内容重复一遍

```
$.each(function(){
    console.log($(this).text());
})；
```
>从$ct 里查找 class 为 .item的子元素

`$ct.find('.tem')`
>获取$ct 里面的所有孩子

`$ct.children()`;

>对于$node，向上找到 class 为'.ct'的父亲，在从该父亲找到'.panel'的孩子

`$node.parent('.ct').find('.panel')`

>获取选择元素的数量

`$node.length`

>获取当前元素在兄弟中的排行

`$(this).index()
`
题目7：

用jQuery实现以下操作

    当点击$btn 时，让 $btn 的背景色变为红色再变为蓝色
    当窗口滚动时，获取垂直滚动距离
    当鼠标放置到$div 上，把$div 背景色改为红色，移出鼠标背景色变为白色
    当鼠标激活 input 输入框时让输入框边框变为蓝色，当输入框内容改变时把输入框里的文字小写变为大写，当输入框失去焦点时去掉边框蓝色，控制台展示输入框里的文字
    当选择 select 后，获取用户选择的内容
