1.引用类型有哪些？非引用类型有哪些

> 引用类型：有对象、数组、函数、正则等，指的是那些保存在堆内存中的对象，变量中保存的实际上只是一个指针，这个指针指向内存中的另一个位置，该位置保存对象

> 非引用类型，Number、Boolean、null和undefined  ： 指的是保存在栈内存中的简单的数据段

2.如下代码输出什么？为什么
```
    var obj1 = {a:1, b:2};
    var obj2 = {a:1, b:2};
    console.log(obj1 == obj2); //false  两个指针指向不懂的堆内存中的地址
    console.log(obj1 = obj2);  //  {a:1, b:2}   赋值操作
    console.log(obj1 == obj2); // true    两个指针自相同一堆内存地址
```

3.如下代码输出什么? 为什么
```
    var a = 1
    var b = 2
    var c = { name: '饥人谷', age: 2 }
    var d = [a, b, c]
    
    var aa = a
    var bb = b
    var cc = c
    var dd = d
    
    a = 11
    b = 22
    c.name = 'hello'
    d[2]['age'] = 3
    
    console.log(aa)    //  1    按值传递
    console.log(bb)    //  2    按值传递
    console.log(cc)    //  {name: 'hello', age:2} c是按引用传递的
    console.log(dd)    //  {1,2,{name: 'hello'，age: 3}}    是按引用传递的
```

4.如下代码输出什么? 为什么
```
    var a = 1
    var c = { name: 'jirengu', age: 2 }
    
    function f1(n){
      ++n
    }
    function f2(obj){
      ++obj.age
    }
    
    f1(a)         //  a = 1    f1改变的是内部变量 n  
    f2(c)         //  c.age=3   按引用传递
    f1(c.age)     
    console.log(a)     //  1
    console.log(c)     //  { name: 'jirengu', age: 3 }
```

5.过滤如下数组，只保留正数，直接在原数组上操作
```
    var arr = [3,1,0,-1,-3,2,-5]
    function filter(arr){
            for (var i=0;i<arr.length;i++) {
                if(arr[i]<1) {
                    console.log("in")
                    arr.splice(i, 1);
                    i--;
                }
            }
            return arr;
    
    }
    filter(arr)
    console.log(arr) // [3,1,2]
```

6.过滤如下数组，只保留正数，原数组不变，生成新数组
```
    var arr = [3,1,0,-1,-3,2,-5]
    function filter(arr){
    
        var newArr = [];
            for (var i=0;i<arr.length;i++) {
                if(arr[i]>0) {
                    newArr.push(arr[i]);
                }
            }
                return newArr;
    }
    var arr2 = filter(arr)
    console.log(arr2) // [3,1,2]
    console.log(arr)  // [3,1,0,-1,-2,2,-5]
```

7.写一个深拷贝函数，用两种方式实现
> 方法1 

```
    function deepCopy(obj) {
        var newObj = {};
        for(var key in obj) {
            if(obj.hasOwnProperty(key)) {
                if(typeof(obj[key])==='string'||typeof(obj[key])==='boolean'||typeof(obj[key])==='undefined'||typeof(obj[key])==='number'||obj[key] === null) {
                    newObj[key] = obj[key];
                } else {
                    newObj[key] = deepCopy(obj[key]);
                }
            }
        }
        return newObj;
    }


    var obj = {
        a:1,
        b: "hello",
        c: {
            d:3,
            e:4,
            f:{
                g: 'world'
            }
        }
    }

    var newObj = deepCopy(obj);
    console.log(newObj);
```
> 方法2  利用JSON

```
  function copy(obj) {
      var newobj = JSON.parse(JSON.stringify(obj));
      return newobj;
  }
  var obj = {
      a: 1,
      b: "hello",
      c: {
          d: 3,
          e: 4,
          f: {
              g: 'world'
          }
      }
  }
  var newObj = copy(obj);
  console.log(newObj);

```

