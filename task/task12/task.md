1. 什么是 CSS hack

> 由于不同厂商的浏览器，比如Internet Explorer,Safari,Mozilla Firefox,Chrome等，或者是同一厂商的浏览器的不同版本，如IE6和IE7，对CSS的解析认识不完全一样，因此会导致生成的页面效果不一样，得不到我们所需要的页面效果。
  这个时候我们就需要针对不同的浏览器去写不同的CSS，让它能在不同的浏览器中也能得到我们想要的页面效果。 


> 表现形式： CSS属性前缀法、选择器前缀法以及IE条件注释法

* 属性前缀法：例如IE6能识别下划线“ _ ”和“ * ”，IE7能识别星号“ * ”，但不能识别下划线“ _ ” ,IE6~IE10都认识“\9”,但firefox前边三个都不能认识

* 选择器前缀法（即选择器hack）

* IE条件注释法（IE10 不再支持）

2. 谈一谈浏览器兼容的思路

    > 第一 要不要做兼容
    
    * 产品的角度（产品的受众，受众的浏览器比例、效果优先还是基本的功能优先）
        
    * 成本的角度（有无必要做某件事）
    
    > 第二 做到什么程度
        
    * 让那些浏览器支持哪些效果 
    
    > 第三如何做
        
     * 根据兼容需求选择技术框架/库（jquery）
        
     * 根据兼容需求选择兼容工具([html5chiv.js](https://github.com/aFarkas/html5shiv)
        
        、[response.js](https://github.com/scottjehl/Respond)、[css rest](https://segmentfault.com/a/1190000003021766)、[normalize.css](https://github.com/necolas/normalize.css)、[Moderizr](https://github.com/Modernizr/Modernizr)）
        
   * [postCSS](https://github.com/postcss/postcss)
   
   * 条件注释、CSS hack、js 能力检测做一些修补

3. 列举5种以上浏览器兼容的写法

* 选择合适的框架

```
    1. Bootstrap(>=ie8)
    2. jQuery.1.~ (>=ie6),jQuery.2.~（ie9）
    3. Vue(>=ie9)
```

* 条件注释：用来向IE提供及隐藏代码

|项目|范例|说明|
|---|---|---|
|！|[if !IE]|非IE|
|lt|[if lt IE 5.5]|小于IE5.5|
|lte|[if lte IE 6]|小于等于IE6|
|gt|[if gt IE 5]|大于IE5|
|gte|[if gte IE 7]|大于等于IE7|

*  属性前缀法

* 选择器前缀法

* 使用modernizr直接使用其在html中生成的class

* 如果浏览器不支持某标签，使用html5shiv.js，创建这个标签，使之可以被渲染。一般结合条件注释使用。



4.以下工具/名词是做什么的

* 条件注释

> 条件注释（conditional comment）是于HTML源码中被IE有田间解释的语句，可被用来向ie提供及隐藏代码

```
     < !--[if IE 6]>
    <p>You are using Internet Explorer 6.</p>
    <![endif]-->
    <!--[if !IE]><!-->
    <script>alert(1);</script>
    <!--<![endif]-->
    <!--[if IE 8]>
    <link href="ie8only.css" rel="stylesheet">
    <![endif]-->
```
  
  


* IE Hack
* js 能力检测

> 浏览器的能力检测目标不是检测特定浏览器，而是检测浏览器的能力。这样，只需要检测浏览器是否支持特定的能力，就可以给出特定的决绝方案，这一部分检测是解决浏览器兼容问题的主要检测


* html5shiv.js

> 使IE6 7 8 支持一些HTML5的一些标签

* respond.js

> 于为 IE6-8 以及其它不支持 CSS3 媒体查询功能的浏览器提供媒体查询的 min-width 和 max-width 特性，实现响应式网页设计。

* css reset
 
 > 样式重置文件，去除浏览器默认样式，比较暴力的方式，去除了一些有用的默认样式

* normalize.css

> 比较友好的重置浏览器默认样式，使不同浏览器对相同的标签具有基本相同的样式

* Modernizr

> Modernizr 使你可以方便地为各种情况编写 JavaScript 和 CSS，无论浏览器是否支持这些特性。这是处理渐进增强的完美方案。
  Modernizr 会在页面加载后立即检测特性；然后创建一个包含检测结果的 JavaScript 对象，同时在 html 元素加入方便你调整 CSS 的 class 名。 

* postCSS

> PostCSS 是目前流行的一个工具，它使用 JavaScript 代码来转换 CSS 中的样式。PostCSS 通过不同的插件来支持对 CSS 的不同处理，目前已有 200 多个不同的插件。PostCSS 的插件可以完成各种不同的功能，如支持变量和混入，支持未来的 CSS 语法和添加浏览器特定前缀等

5. 一般在哪个网站查询属性兼容性？

    >浏览器市场份额 [百度统计](http://tongji.baidu.com/data/browser)    
    > 一般查询兼容性网站 [canIUse](caniuse.com)
    >查写hack方法 [Browserhacks](http://browserhacks.com/)
    
    [html5chiv.js](https://github.com/aFarkas/html5shiv)
    
    
6. 渐进增强和优雅降级
    
    * 渐进增强（progressive enhancement）：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器进行效果、交互等改进和追加功能达到更好的用户体验。
    
    * 优雅降级（graceful degradation）: 一开始就构建完整功能，然后再针对低版本的浏览器进行兼容
    
    > [两者的区别-stackoverflow](http://stackoverflow.com/questions/2550431/what-is-the-difference-between-progressive-enhancement-and-graceful-degradation)
