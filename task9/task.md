1. text-align: center的作用是什么，作用在什么元素上？能让什么元素水平居中

> 作用：使文字或元素居中显示，能够使用inline和inline-block水平的元素

2. IE 盒模型和W3C盒模型有什么区别?

区别

> W3C标准中 padding、border所占的空间不再width、height范围内，大家俗称的IE盒模型的 width包括content，border，padding的值

有下面一个盒模型
 
 ```
        div {
             margin:10px;
             padding:10px;
             width: 100px;
             height: 100px;
             border: 10px solid blue;
         }
 ```
 
 按照标准盒模型计算 总宽度 W = 100 + 10 +10 +10+ 10 = 140
 
 按照IE盒模型计算 总宽度 w = 100



有下面一个盒模型


3. *{ box-sizing: border-box;}的作用是什么？

> box-sizing 是css3的新属性

* box-sizing: content-box  使用标准盒模型

*box-sizing：border-box  “使用IE盒模型”

```
* {
    box-sizing: border-box
}

所有盒模型 全部使用“IE盒模型”
```


4. line-height: 2和line-height: 200%有什么区别?

> line-height:2  是基于自身文字大小的两倍

> line-height: 200%,是基于父元素文字大小的两倍


此外 line-height具有垂直居中的功能

5. inline-block有什么特性？如何去除缝隙？高度不一样的inline-block元素如何顶端对齐?

> 特性：具有inline特性，不占据一整行，宽度由内容宽度决定，同时又具有block特性，可以设置宽高和内外编剧

两个inline-block之间会产生缝隙，

> 解决办法，去除html标签间的空格元素，但不推荐，代码可读性较低
> 也可以设置父元素的font-size：0；

更多方法参考[张鑫旭](http://www.zhangxinxu.com/wordpress/2012/04/inline-block-space-remove-%E5%8E%BB%E9%99%A4%E9%97%B4%E8%B7%9D/)

高度不一样事，元素以文字的底部基线对齐的方式对齐


6. CSS sprite 是什么?

> 指把不同的图片/图标合并到一张图片上
> 使用CSS Sprite 可以减少网络请求，提高网页加载性能


7. 让一个元素"看不见"有几种方式？有什么区别?

* display设置为 none，在页面中完全消失
* visibility 设置为hidden，隐藏，但是还占据元素的位置

* 设置透明度 opacity属性为0

* 背景色也可以设置为透明色

* 设置绝对定位，把元素定位到：可视区之外，如 left：-99999px，top：-99999px


8.ICON五种实现方式

* image
    > 注意事项
    
        1. img的大小设置
        2. img的vertical-align
        3. 请求数过多

* CSS Sprite

* Icon Font

* CSS icon

* SVG
