1. JavaScript 定义了几种数据类型? 哪些是原始类型?哪些是复杂类型?原始类型和复杂类型的区别是什么?

> 数据类型 共六种

  * String ：字符组成的文本
  * Number：整数或者小数
  * Boolean：true和false 两个特定值
  * undefined： 表示“未定义”或者不存在，即此处目前没有任何值
  * null： 表示空缺，即此处应该有一个值，但目前为空
  * Object

> 基本数据类型 
  
  Number、String、Bollean ，是最基本的数据类型，不能再细分了
  
> 复杂类型
  
  Object对象类型为复杂类型的值，一个对象往往是多个原始类型的值的合成，可以看做是一个存放各种值的容器
  
  对象又可分成三个子类型
  
  * 狭义的对象（Object）
  * 数组（array）
  * 函数（function）
  * 正则表达式
  
  
> undefined 和 null ,一般将他们看成两个特殊值

2. typeof和instanceof的作用和区别?

  > typeof 运算符 可以确定一个值到底是什么类型 
  
  |typeof x| x |
  |:---|:---|
  |undefined| "undefined"|
  |null | "object"|
  |true或false|"boolean" |
  |任意数字或NAN|"number"|
  |任意字符串| "string"|
  |任意函数| "function"|
  |任意内置对象（非函数）|"object"|
  
  > instanceof 同样也可以确定一个值到底是什么类型，
  
  两者的区别是： typeof不能确定具体的 Object对象的具体的类型，对原始类型的区分还是很有帮助

3. 如何判断一个变量是否是数字、字符串、布尔、函数
```
    typeof 123 === 'number' 判断是否是数字
    typeof '123' === 'string' 判断是否为字符串
    typeof true ==='boolean' 判断是否为布尔
    typeof a ==='function' 判断是否为函数
```
4. NaN是什么? 有什么特别之处?

  > NaN的含义是Not a Number， 表示非数字，NaN和任何值都不相等，包括自己
  
5. 如何把非数值转化为数值?

  > 使用Number() parseInt()  parseFloat()

6. ==与===有什么区别

    > == 具有类型转换的功能
    
    > ===  是严格相等，先检测类型是否相同
7. break与continue有什么区别
  > 这两个关键词多用于循环语句中
  
  * break 用于强制退出循环体，执行循环后面的语句
  ```
           for(var i =1; i <10 ;i++) {
              if(i===5) { 
                break;
              } 
              console.log(i) 
           }
  ```
    结果打印 1，2,3,4
  * continue用于退出本次循环，执行下次循环

   ```
            for(var i =1; i <10 ;i++) {
                  if(i===5) { 
                    continue;
                  } 
                  console.log(i) 
             }
   ```
    结果输出 1，2，3，4，6，7，8，9
8. void 0 和 undefined在使用场景上有什么区别

> void 会执行后面的表达式并返回 undefined，但是某些情境下undefined是可以被赋值的，比如在函数中，这样的话就不能用undefined来进行判断了。所以用void 0返回undefined来进行判断。既减少了在原形链上查找 window.undefined 的时间，也避免了误用被修改过的 undefined。

9. 以下代码的输出结果是?为什么?
```
        console.log(1+1);    
        console.log("2"+"4");  
        console.log(2+"4"); 
        console.log(+"4");
        
```
     
   > 结果  2 , "24" , "24" , 4 , 
   
   " + " 号 规律
   * 在两个操作数都是数字的时候，会做加法运算
   * 在两个参数都是字符串或在有一个参数是字符串的情况下会把另外一个参数转换为字符串做字符串拼接
   * 在参数有对象的情况下会对其调用其valueOf或投String为数字
   
   * 在只有一个数字参数的时候返回其正数值

10. 以下代码的输出结果是?

```
    var a = 1;  
    a+++a; 
    typeof a+2;
```
> 结果 "number2"

11. 以下代码的输出结果是? 为什么
```
     var a = 1;
     var b = 3;
     console.log( a+++b );
```
> 结果  4  , a+++b  先进行 a++ 再运行 +b，后置++ 返回的是++前的值

12. 遍历数组，把数组里的打印数组每一项的平方

```
    var arr = [3,4,5]
```
 
 > for(var i =0 ; i < arr.length; i++ ) {
      console.log(arr[i]*arr[i])
 }
 
13. 遍历 JSON, 打印里面的值
```
    var obj = {
      name: 'hunger', 
      sex: 'male', 
      age: 28 
    }
```
> for (var key in obj) {
  	console.log(obj[key])
  }
14. 以下代码输出结果是? 为什么 （选做题目）

```
    var a = 1, b = 2, c = 3;
    var val = typeof a + b || c >0
    console.log(val) 
    
    var d = 5;
    var data = d ==5 && console.log('bb')
    console.log(data)
    
    var data2 = d = 0 || console.log('haha')
    console.log(data2)
     
    var x = !!"Hello" + (!"world", !!"from here!!");
    console.log(x)
```

