# 模块化

1. AMD 

  基于CommonJS规范的nodeJS出来以后，服务端的模块概念已经形成，很自然地，大家就想要客户端模块。而且最后两者能够兼容。

AMD 是“Asynchronous Module Definition”的缩写。它采用异步方式加载模块，模块的加载不影响他后面语句的运行。所有依赖这个模块的语句，东定义在一个毁掉函数中，等到加载完成之后，这个回调函数才会执行。

> AMD也采用require()语句加载模块，但是不同于CommonJS，它要求两个参数

```
  require([module],callback);
```
第一个参数为[module],是一个数组，里面的成员就是要加载的模块；第二个参数是callback，等到加载完成之后买这个回调函数才会运行。

1.1 Require.js

解决的主要问题

* 实现JS文件的异步加载，避免网页失去相应；
* 管理模块之间的依赖性，便于代码的编写和维护

使用方法 

```
// data-main 属性的作用是指定网页程序主模块，程序主入口文件
<script src="js/require.js" data-main="js/main"></script>
````
假如主模块的依赖模块是['jquery', 'underscore', 'backbone']。默认情况下，require.js假定这三个模块与main.js在同一个目录，文件名分别为jquery.js，underscore.js和backbone.js，然后自动加载

```
  require(['jquery','underscore','backone'],function($, _, backbone){
    // code here
    console.log($, _, backbone);
  });

```

还可以设置参数 

```
  require.config({
    path: {
      "jquery": "jquery.min",
      "underscore": "underscore.min",
      "backbone": "backbone.min"
    }

  })
```

如果不在同一目录 

```
  require.config({
    baseUrl: 'js/lib',
    path: {
      "jquery": "jquery.min",
      "underscore": "underscore.min",
      "backbone": "backbone.min"
    }

  })
  // 这样加载时，文件路径为 "js/lib/jquery.min"  ....
```

require.js 要求每个模块都是一个单独的js文件。

1.2 AMD模块的写法。

require.js 加载的模块，采用AMD规范。也就是说模块必须按照AMD规定来写。

具体说，就是模块必须采用特定的define()函数来定义。

假如定义一个math模块，创建math.js 文件。

```
  // math.js  定义模块（不需要其他依赖）
  define(function(){
    var add = function(n,m){
      return n + m;
    } 

    return {
      add: add
    }
  });
  // 如果需要其他依赖

  define(['jquery'],function($){
    function foo() {
      $('body).css('background','black'); 
    }
  });

```

加载不符合AMD规范的库

加载之前，需要用require.config()方法定义参数。

```
  require.config({
    shim: {
      'underscore': {
        exports: '_'
      },
      "backbone": {
        deps: ["underscore","jquery"],
        exports: "Backbone"
      }
    }
  })

  //  加载Jquery插件
  require.config({
    "jquery.scroll": {
      deps: ["jquery"],
      exports: "jQuery.fn.scroll"
    }
  });

```

--------------------------------

2. CMD 规范

[CMD与AMD的最大的不同](https://www.douban.com/note/283566440/)
















