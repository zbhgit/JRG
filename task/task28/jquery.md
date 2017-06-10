题目1： 说说库和框架的区别？
  
  库：将代码集合 成一个产品，提供给卡发着调用。面向对象的代码组织而成的叫类库，面向过程组织而成的叫函数库
  
  框架：为解决艺蕾文体而开发的产品，框架用户一般只需要使用框架提供的类或函数，即可实现全部功能

  区别：库提供更灵活的选择，需要自己组织，需要自己组织。框架更觉有针对性，提供一整套完整代码


题目2： jquery 能做什么？

  * 设置HTML属性、CSS样式和类、HTML表单得值和内容、位置宽高、以及数据
  * 改变文档结构：对元素记性插入、替换、包装盒删除操作
  * 能使用跨浏览器事件模型
  * 能够使用Ajax工具发起HTTP请求
  * 能够实现动画效果
  * 能够利用“CSS选择器”查询文档元素
  * 简介的语言用法--链式调用

题目3： jquery 对象和 DOM 原生对象有什么区别？如何转化？
  jQuery对象：是通过jquery包装的DOM对象后产生的对象。
  DOM原生对象：是通过W3C标准用于操作文档API获得的
  ```
    
    <div class='example'> 
    <div class='example'> 
    
    // jquery
    var $div = $('.example');
    // DOM
    var div = document.getElementsByClassName('example');

  ```
区别：Jquery对象可以使用jQuery里的方法，不能使用原生DOM对象的方法。同样DOM对象也不能使用jQuery对象的方法。

转换：jquery→DOM
```
  var $div = $('.example');
  var domDiv = $div[0];
  var domDiv2 = $div.get(1);
```
DOM→jQuery 只需要用$()把DOM对象包装起来
```
var div = document.getElementsByClassName
var $div = $(div);

```


题目4：jquery中如何绑定事件？bind、unbind、delegate、live、on、off都有什么作用？推荐使用哪种？使用on绑定事件使用事件代理的写法？

* 如何绑定时间，例子如下
```
  // 简单的事件绑定，为每个div添加一个点击事件
  // 还有更多的事件类型:mousedown mousemove keyup blur....等
  // 没有带参数，也没有返回值
  
  $('div').click(function(){alert(this)});

  // 高级绑定注册

  $('div').bind('clik',fun) // 新创建元素不会有绑定事件

  // '实时事件'依赖于事件冒泡
  $(document).delegate('a','mouseover',linkHandler);

  // live也可以注册实时事件.同样依赖于事件冒泡
  $('a').liv('mosueover',linkhandler);

  // 普通事件绑定，最简单的用法
  $('div').on('click', function(e){
      console.log(this);
      console.log(e);
  });

  // 事件委托或者事件代理，想让div 下面所有的span绑定事件，可以把事件绑定到div上
  $('div').on('click', 'span', function(e){
      console.log(this);
      console.log(e);
  });

  // 可以在绑定的时候给事件处理程序传递一些参数
  $('div').on('click', {name: 'Byron', age: 24}, function(e){
      console.log(e.data);
  });

  // 下面三种是对应的注销事件方法
  // 使用时一定要注意命名空间的问题
  $('div').unbind(''click)

  $(document).undelegate('a');
  
  $("body").off("click", "#theone", aClick) 

```

推荐使用.on 进行绑定事件。事件代理方法如上。
  
题目5：jquery 如何展示/隐藏元素？

主要利用hide()show()方法。还有就是fadeIn(),fadeOut(),slidDown()、slidUp(),还有一个自定义动画animate()
```
$(document).ready(function(){
  $('.show').on('click',function(){
    $('.hide').show();
  })
  $('.hide').on('click',function(){
    $('.hide').hide();
  });
})
```

题目6： jquery 动画如何使用？
  使用animate方法可以实现更多通用动画效果
  其第一个参数指定动画内容，剩余参数指定如何定制动画。

  ```
  $('#sprite').animate({
    opacity: .25;
    font-size: 10;
  },{
    duration: 500,   // 动画持续半秒
    complete:function(){} //动画完成时调用该函数
  });
  ```


题目7：如何设置和获取元素内部 HTML 内容？如何设置和获取元素内部文本？

* $(‘selector’).html():获取元素内部HTML。
* $(‘selector’).html(‘…’):设置元素内部HTML。
* $(‘selector’).text():获取元素内部文本。
* $(‘selector’).text(‘…’):设置元素内部文本。

题目8：如何设置和获取表单用户输入或者选择的内容？如何设置和获取元素属性？

* $(‘selector’).val():获取表单用户输入值;
* $(‘selector’).val(‘…’):设置输入值;
* $(‘selector’).attr(‘name’):获取元素属性;
* $(‘selector’).attr(‘name’,’xxx’):设置元素属性的值;