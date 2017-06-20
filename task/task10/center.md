### 居中的使用场景

1. 文字居中

```
 tex-align: center  //水平居中

 line-height:  // 与height相等 垂直居中
``` 
2. 块级元素居中


* 已知宽高块级元素居中
```
  .center {
    width:200px;
    height: 200px;
    /* margin: 0 auto; // 水平居中 */
    position: absolute;  // 以下垂直水平居中
    left: 50%;
    top: 50%;
    margin-left: -100px;
    margin-top: -100px;   
  }
```
