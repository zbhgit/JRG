1. 平时写代码遵守的编码规范
  * tab 用两个空格表示
  * css的：后加个空格 { 钱加个空格
  
 * 每条属性和属性值写完后换行
 * 颜色用小写，用缩写，#fff
 * 小数不用写前缀，0.5s-> .5s; 0 省略单位
 * 尽量缩写属性 
 
 * 声明顺序
 ```
 div {
   /* Positioning */
   position: absolute;
   top:0;
   right:0;
   bottom:0;
   left:0;
   z-index:100;
   /* box-model */
   display: block;
   float: left;
   width: 100px;
   height: 100px;
   /* typography */
 
   font: normal 13px "Helvetica Neue",sans-serif;
   line-height:1.5;
   color: #333;
   text-align: center;
 
   /* Visual */
   background-color: #fff;
   border:1px solid #000000;
   border-radius:3px;
 
   /* Misc */
  }
 ```
 
 
 
 * 将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部
 
 
2. 垂直居中有几种实现方式，给出代码范例

* 已知宽高的div

```
  <style>
    .dialog {
      position: absolute;
      top:50%;
      left:50%;
      margin-top: -150px;
      margin-left: -200px;

      width: 400px;
      height: 300px;
      background-color: #333333;
      color: #ffffff;

    }
  </style>
  
  
  
  <div class="dialog">
  <h1>对话框</h1>
  </div>
```
* vertical-align实现居中

```
    .img-wrap {
      width: 400px;
      height: 300px
      text-align: center;
    }

    .img-wrap:before {
      content: '';
      display: inline-block;
      height: 100%;
      vertical-align: middle;
    }

    .img-wrap img {
      width: 300px;
      vertical-align: middle;

    }
    
    
    <div class="img-wrap">
        <img src="img.png" alt="风景">
      </div>
```


* table-cell实现居中

```
    .img-wrap {
      display: table-cell;
      width: 400px;
      height: 300px;
      text-align: center;
      vertical-align: middle;
      box-shadow: 0 0 4px rgba(0, 0, 0, .4);
    }
    .img-wrap img {
      width: 300px;
    }


      <div class="img-wrap">
        <img src="img.png"https://zbhgit.github.io/learn-task/task13 alt="风景">
      </div>
```


3 实现tips  

> [链接]()
