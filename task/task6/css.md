1. CSS 全称Cascading Style sheets 层叠样式表

2. 引入方式

  * 内联样式 ` <h1 style="color: red;"></h1> `
  * 内嵌样式

    ```
      <style>
      
        h1 {
          color: red;
        }
      </style>
    ```
  *  外部样式

    ```
      // index.html
      <head>
        <link rel="stylesheet" href="index.css">
      </head>

      //index.css
      h1 {
        color: red;
      }
    ```
  * CSS样式表中引入其他CSS文件

    ```
        @import url("hello.css")
        @import "world.css"
    ```

  * 此外浏览器还有自己的默认样式

  