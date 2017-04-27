1. 函数声明和函数表达式有什么区别
> 函数声明方式
 ```
     function sum ( num1, num2) {
     return num1+num2
 }
 ```

> 函数表达式 

```
    var sum = function(num1,num2) {
        return num1+num2
    }
    
```

> 构造函数的方式

```
    var sum = new Function("num1","num2","return num1+num2");
    
    //   不推荐这种方式创建函数
```

> 区别

解析器在像执行换种加载数据时，对函数声明和函数表达式并非一视同仁。解析器会率先读取函数声明，并使其在执行任何代码之前可用（可以访问）；至于表达式，则必须等到解析器执行到它所在的代码行，才会真正被解释执行

如下代码  

* 正常输出结果 20

```
      console.log(sum(5,15));
      function sum (num1, num2) {
        return num1 + num2;
      }
      
```

* 产生错误 : Uncaught TypeError: sum is not a function
```
    console.log(sum(5, 15));
    
    var sum = function (num1, num2) {
        return num1 + num2; 
    }
```
> 注意  当写成如下形式时,会有一定的难易理解的问题

```
    var sum = function sum(num1,num2){ return num1 + num2 }
```
 这样写，= 号右边值的部分并不会发生 函数声明提升，只会发生 变量sum的声明提升
 
 
2. 什么是变量的声明前置？什么是函数的声明前置

> 变量的声明前置是指 使用var 声明的变量，会被解析器提前解析到当前作用域的顶部，但此时没有被赋值

> 函数声明前置，同样使用函数声明的方式声明函数时，也会被解析器提前解析到当前作用域的顶部，但此时没有被执行
3. arguments 是什么
> arguments: 是函数内部两个特殊函数的对象之一，是一个类数组对象，包含着传入函数中的所有参数；
4. 函数的"重载"怎样实现
> 在JS中，没有重载，但可以在函数体针对不同参数调用执行相应的逻辑。例如
```
    function printPeopleInfo(name, age, sex) {
      if(name) { console.log(name) }
      if(age) { console.log(age) }
      if(sex) { console.log(sex) }
    
    }
    printPeopleInfo( "abc" ,26)
    printPeopleInfo( "abc" ,26, "male")

```
此外应注意，函数的参数是有顺序的，在ES5中不能指定参数默认值

5. 立即执行函数表达式是什么？有什么作用

> 立即执行函数表达式是一个JavaScript函数，它会在定义时立即执行。

两种常用的推荐写法

```
//方法1
( function ( ) {} )();

// 方法2 

(function () {} ());
```
> 作用；隔离作用域

更多请参考[汤姆大叔](http://www.cnblogs.com/tomxu/archive/2011/12/31/2289423.html)
6. 求n!，用递归来实现
```
function factor(n) {
  if(n===1) {
    return 1
  }
  return n * factor(n-1)
}
```
7. 以下代码输出什么？
```
	function getInfo(name, age, sex){
  		console.log('name:',name);
  		console.log('age:', age);
  		console.log('sex:', sex);
  		console.log(arguments);
  		arguments[0] = 'valley';
  		console.log('name', name);
  	}
  
  getInfo('饥人谷', 2, '男'); 
  getInfo('小谷', 3);
  getInfo('男');
```
* getInfo('饥人谷', 2, '男')结果 : name: "饥人谷"，age：2 ，sex："男"，\['饥人谷', 2, '男'], name: "valley"
* getInfo("小谷"，3  )：name: "小谷"，age：3 ，sex：undefined，\['小谷', 3], name: "valley"
* getInfo("男" )：name: "男"，age：undefined ，sex：undefined，\['男'], name: "valley"


8. 写一个函数，返回参数的平方和？
```
   unction sumOfSquares(){
 
      var result = 0;
        for (var i=0;i<arguments.length;i++) {
          result += arguments[i]*arguments[i];
        }
        return result;	
   }
   var result = sumOfSquares(2,3,4)
   var result2 = sumOfSquares(1,3)
   console.log(result)  
   console.log(result)  
```
  

9. 如下代码的输出？为什么
```
	console.log(a); // undefined
	var a = 1; 
	console.log(b);   // 报错  b is not defined
```

10. 如下代码的输出？为什么
```
	sayName('world');
	sayAge(10);
	function sayName(name){
		console.log('hello ', name);
	}
	var sayAge = function(age){
		console.log(age);
	};
```
>  输出 hello world，然后报错 sayAge is not a function; 因为函数表达式不能声明前置，只有先定义好，才能使用
11. 如下代码输出什么? 写出作用域链查找过程伪代码
```
    var x = 10
    bar() 
    function foo() {
      console.log(x)
    }
    function bar(){
      var x = 30
      foo()
    }
```

> 伪代码 
```
    globalContext = {
    	AO: {
    		x:10,
    		foo: function,
    		bar: function
    	},
    	Scope: bull
    }
    foo.[[scope]] = globalContext.AO
    bar.[[scope]] = globalContext.AO
   
    barContext = {
    	AO: {
    		x:30;
    	}
    	Scope:bar.[[scope]]
    }

    fooContext = {
    	AO:{}
    	Scope:foo.[[scope]]s
    }
```

12. 如下代码输出什么? 写出作用域链查找过程伪代码
```
    var x = 10;
    bar() 
    function bar(){
      var x = 30;
      function foo(){
        console.log(x) 
      }
      foo();
    }	
```
> 伪代码
```
    globalContext = {
    	AO: {
    		x:10,
    		foo: function,
    		bar: function
    	},
    	Scope: bull
    }
    bar.[[scope]] = globalContext.AO
   
    barContext = {
    	AO: {
    		x:30;
    	}
    	Scope:bar.[[scope]]
    }
    foo.[[scope]] = barContext.AO

    fooContext = {
    	AO:{}
    	Scope:foo.[[scope]]
    }
```

13. 以下代码输出什么? 写出作用域链的查找过程伪代码
````
      var x = 10;
      bar() 
      function bar(){
        var x = 30;
        (function (){
          console.log(x)
        })()
      }
````
> 伪代码
```
    globalContext = {
    	AO: {
    		x:10,
    		foo: function,
    		bar: function
    	},
    	Scope: bull
    }
    bar.[[scope]] = globalContext.AO
   
    barContext = {
    	AO: {
    		x:30;
    	}
    	Scope:bar.[[scope]]
    }
    foo.[[scope]] = barContext.AO

    fooContext = {
    	AO:{}
    	Scope:foo.[[scope]]
    }
```

14. 以下代码输出什么？ 写出作用域链查找过程伪代码

```
    var a = 1;
    
    function fn(){
      console.log(a)
      var a = 5
      console.log(a)
      a++
      var a
      fn3()
      fn2()
      console.log(a)
    
      function fn2(){
        console.log(a)
        a = 20
      }
    }
    
    function fn3(){
      console.log(a)
      a = 200
    }
    
    fn()
    console.log(a)
```
> 伪代码 

```

    global.Context = {
        AO: {
            a:1,
            fn: function,
            fn3:function
        }
        scope: null
    }

    fn.[[scope]] = global.Context.AO;
    fn3.[[scope]] = global.Context.AO;

    fn.Context = {
        AO: {
            a：undefined  //依次变化 --- 5 --- 6 ---20 
        }
        Scope:fn.[[scope]]
    }
    fn2.[[scope]] = fn.Context.AO;
    fn2.Context = {
        AO: {}
        Scope: fn2[[scope]];
    }
    fn3.Context = {
        AO: {}
        Scope:fn3.[[scope]]
    }
```
