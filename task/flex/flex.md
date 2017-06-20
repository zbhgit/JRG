## Flexbox

1. 使用Flexbox，首先就是声明一个Flex容器

> 只需要在父元素中显示的设置 `display: flex` 或者 `display； inline-flex`


此时设置为flex的元素 为Flex容器，其子元素成为 Flex项目

2. Flex容器的属性

|属性|属性值|说明|
|:----|:----|:----|
|flex-direction|row,column,row-reverse, column-reverse|该属性控制Flex项目沿着主轴的排列方向|
|flex-wrap|wrap, nowrap, wrap-reverse|设定flex项目是否换行，如果设置为wrap，则flex项目为自身宽度，设置为nowrap，则flex项目可能会被改变宽度以适应整行宽度|
|flex-flow|`flex-flow: row wrap`|这是两个flex-direction和flex-wrap两个属性的简写|
|justify-content|flex-start, flex-end, ceenter, space-between,space-around|定义Flex项目在主轴（main-Axis）上的对其方式|
|align-items|flex-start, flex-end, center, stretch, baseline|主要定义flex项目在Cross-Axis（Y轴）方向的对其方式|
|align-content|flex-start, flex-end, center, stretch, baseline|用来控制Flex项目在flex容器里的排列方式|


3. Flex项目的属性

|属性|属性值|说明|
|:---|:---|:---|
|order|接收一个数字，可以正值，可以负值|允许flex项目在一个flex容器中重新排序|
|flex-grow|0或大于0的整数|控制Flex项目在容器有多余空间如何放大扩展|
|flex-shrink|0或大于0的整数|控制flex项目在没有空间又如何缩小|
|flex-basis|默认值auto，可以取任何width属性的值，必须带单位|指定flex项目的初始大小|
|flex|三个属性的简写，取值如上|简写属性，顺序为flex-grow，flex-shrink，flex-basis|
|align-self|auto,flex-start,flex-end,center,baseline,stretch|定义flex项目侧轴的位置|



4. 此外有一点应该格外注意  主轴 mai-Axis  不是一成不变的。他随这flex-direction的属性改变.

>  以上是新语法，还有一种旧语法，使用flex要注意兼容性问题。




参考链接 [w3cPlus大漠](http://www.w3cplus.com/css3/understanding-flexbox-everything-you-need-to-know.html)
