1. 块级元素和行内元素分别有哪些？动手测试并列出4条以上的特性区别

> 常见块级元素
 
 
 div h1~h6 p hr ul ol li dl dt dd pre table tr td  form 

> 常见行内元素

em strong span a img input br select textarea label button code script

两者区别

* 块级元素会占据一整行，行内元素占据自身大小，一行可以放很多行内元素

* 块级元素能嵌套块级元素，行内元素等，行内元素只能包含文本和行内元素

* width和height属性只对块级元素有效，对行内元素无效

* 行内元素对齐设定margin，padding时，上下设置是无效的




2. 什么是 CSS 继承? 哪些属性能继承，哪些不能？

css继承： 当元素的一个继承属性没有指定值时，则取父元素的同属性的计算值；
    当一个非继承属性没有指定值时，则取属性的初始值

> 常用继承属性

   |属性|定义|
    |:---|:---|
    |border-collapse|定表格的边框是分开的还是合并的，collapse，separate|
    |border-spacing|相邻单元格之间的距离，只适用于边框分离模式|
    |color|字体颜色|
    |cursor|鼠标悬浮在元素上显示的鼠标光标|
    |direction|规定文本的方向、书写方向|
    |font-family|选择什么字体|
    |font-size|字体大小|
    |font-style|字体样式|
    |font-weight|字体粗细|
    |font|合并写法|
    |letter-spacing|字母或字符间的间隔|
    |line-height|行高|
    |list-style-image|列表每项前的图片|
    |list-style-position|列表图片前的位置|
    |list-style-type|类型|
    |list-style|合并方式写法|
    |text-align|文本对齐方式left center right justify|
    |text-indent| 文本第一行缩进|
    |text-transform|改变文字大小写none，uppercase lowercase capitalize|
    |visibility|设定元素显示隐藏，取值hidden，collapse，visible|
    |word-spacing|可以改变字和单词之间的间隔|
    
    
> 常用非继承属性 
    
    display,margin,padding,border,background,position,left,top,right, width,height ,overflow,float,vertical-align
    
    
    
3. 如何让块级元素水平居中？如何让行内元素水平居中?

> 块级元素水平居中

```
    /* 使用此方法时必须要有宽度值非100% */
    div {
        width: 100px;
        margin: 0 auton;
    }
```

> 行内元素水平居中

```
    /* 在其父元素上添加下列属性 */
    
    text-align: center
```

4. 用 CSS 实现一个三角形

改变对应边框值，就可以写出不同方向的三角形
```
 div {
            width: 0;
            height:0;
            border-right:100px solid transparent;
            border-left:100px solid transparent;
            border-top:100px solid transparent;
            border-bottom:100px solid pink;
  }
```

5. 单行文本溢出加 ...如何实现?

```
    .title {
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
    }
```

6. px, em, rem 有什么区别

* px表示固定的像素值

* em表示相对单位，相对于父元素字体大小

* rem表示相对单位，相对于根元素（html）字体大小
* vw vh 也是相对单位，1vw为屏幕款多的1%

7. 解释下面代码的作用?为什么要加引号? 字体里\5b8b\4f53代表什么?

```
body{
  font: 12px/1.5 tahoma,arial,'Hiragino Sans GB','\5b8b\4f53',sans-serif;
}

```
作用：设定字体大小12px，行高为字体大小的1.5倍，首先使用 tahoma字体，没有的情况下使用Arial字体，后面的同样的选择方式。

由于Hiragino Sans GB单词之间有空格，加引号使他们成为一个整体

'\5b8b\4f53' 代表'黑体'，这种事Unicode编码表示方式
