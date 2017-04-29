1、使用数组拼接出如下字符串
```
var prod = {
    name: '女装',
    styles: ['短款', '冬季', '春装']
};
function getTpl(data){
     var arr = [];
      arr.push("<dl class=\"product\">" + "\n");
      arr.push("\t" + "<dt>" + data.name + "</dt>" + "\n");
      for(var key in data.styles){
        arr.push("\t" + "<dd>" + data.styles[key] + "</dd>" + "\n");
      }
      arr.push("</dl>");
    
      return arr.join("");  
};
var result = getTplStr(prod);  //result为下面的字符串
<dl class="product">
    <dt>女装</dt>
    <dd>短款</dd>
    <dd>冬季</dd>
    <dd>春装</dd>
</dl>
```
2、写出两种以上声明多行字符串的方法

```
    var str =  "一" + “二”
              + "三"
              + "四";
              
     var str2 =  "一\
     二\
     三\
     四" ;  
```
3、补全如下代码,让输出结果为字符串: hello\\饥人谷
```
var str = 'hello\\\\饥人谷'
console.log(str)
```
4、以下代码输出什么?为什么
```
var str = 'jirengu\nruoyu'
console.log(str.length)

```
>输出结果 13 ；因为\n 代表一个字符，换行符

5、写一个函数，判断一个字符串是回文字符串，如 abcdcba是回文字符串, abcdcbb不是

```
    function judge(str) {
        return str === str.split('').reverse().join('');
    }
```


6、写一个函数，统计字符串里出现出现频率最多的字符
```
    function judge(str) {
        var obj = {};
        for(var i = 0; i < str.length;i++) {
            if(obj[str[i]]) {
                obj[str[i]]++;
            } else {
                obj[str[i]] = 1;
            }
        }
        var most = 0;
        var mostChar;
        for(var key in obj) {
            if(obj[key]>most) {
                most = obj[key]
                mostChar = key;
            }
        }
        return mostChar+':'+ most;
    }
```
7、写一个camelize函数，把my-short-string形式的字符串转化成myShortString形式的字符串，如
```
camelize("background-color") == 'backgroundColor'
camelize("list-style-image") == 'listStyleImage'
```
camelize函数

```
    function camelize(str){
        var newArr = [];
        var newStr = '';
        newArr = str.split('-')
    
        for(var i=0;i<newArr.length;i++){
            if(i>0){
                newStr += newArr[i].charAt(0).toUpperCase()+newArr[i].substring(1);
            } else {
                newStr += newArr[i];
            }
        }
        return newStr;
    }
```
8、写一个 ucFirst函数，返回第一个字母为大写的字符 （***）
```
   console.log( ucFirst("hunger") == "Hunger")

    function ucFirst(str){
      
      return  str.charAt(0).toUpperCase() + str.substring(1);
    
    }


```

9、写一个函数truncate(str, maxlength), 如果str的长度大于maxlength，会把str截断到maxlength长，并加上...，如
```
      truncate("hello, this is hunger valley,", 10) == "hello, thi...";
      truncate("hello world", 20) == "hello world"
      
      function truncate(str,maxlength) {
          var newStr='';
          if(str.length > maxlength) {
              newStr = str.substring(0,maxlength)+ '...'
          } else {
              newStr = str;
          }
          return newStr;
      }
```
10、什么是 json？什么是 json 语言？JSON 语言如何表示对象？window.JSON 是什么？

> json 一种轻量级用于数据交换的文本格式
JSON是JavaScript的一个严格的子集，利用了JavaScript中的一些模式来表示结构化数据。

JSON 的语法可以表示以下三种类型的值。
*  简单值：使用与 JavaScript 相同的语法，可以在 JSON 中表示字符串、数值、布尔值和 null 。
但 JSON 不支持 JavaScript 中的特殊值 undefined 。
*  对象：对象作为一种复杂数据类型，表示的是一组无序的键值对儿。而每个键值对儿中的值可
以是简单值，也可以是复杂数据类型的值。
*  数组：数组也是一种复杂数据类型，表示一组有序的值的列表，可以通过数值索引来访问其中
的值。数组的值也可以是任意类型——简单值、对象或数组。

JSON 数据的书写格式是：名称/值对，名称/值对组合中的名称写在前面（在双引号中），值对写在后面(同样在双引号中)，中间用冒号隔开：

```
    var json1 = {"name": "Byron", "age": "24"}
    
    var json2 = [
        {"name": "Byron", "age": "24"}, 
        {"name": "Byron2", "age": "25"}
    ]
```

window.JSON 是 window对象下的JSON属性？

11、如何把JSON 格式的字符串转换为 JS 对象？如何把 JS对象转换为 JSON 格式的字符串?

> JSON.parse() 把字符串转化成json
> JSON.stringify() 把json转化成字符串
