# Array类型

创建数组的两种方式
* 构造函数 
`var colors = new Array()`
` var names = new Array('greg'')`
* 使用数字字面量表示法

`var colors = []`
`var names = ['greg']`

在读取和设置数组的值时，要是用方括号并提供相应值的基于0的数字索引
```
    var colors = ["red", "blue", "green"]; // 定义一个字符串数组
    alert(colors[0]); // 显示第一项
    colors[2] = "black"; // 修改第三项
    colors[3] = "brown"; // 新增第四项

```

1. 检测数组
    > ECMAScript 3  定义的  instanceOf  可以检测
    
    > ECMAScript 5 定义的 Array isArray 也可以检测
    
    > Object.prototype.toString.call(Array) === "[object Array]"
2. 数组的一些方法

* 栈方法：栈是一种 LIFO（Last-In-First-Out，后进先出）的数据结构，也就是最新添加的项最早被移除

> push方法可以接收任意数量的参数，把他们逐个添加到数组末尾，并返回修改后数组的长度

> pop()放法则从数组末尾一处最后一项，减少数组的length值，然后返回一处的项


* 队列方法

> shift()方法：移除数组中的第一项，并返回该项，同时数组的长度减1

> unshift()方法： 能在数组前端添加任意个项，并返回新数组的长度

* 重排序方法

> reverse(): 方法会反转数组项的顺序

> sort()方法：默认情况下，按升序排列数组项，sort()方法会调用每个数组项的toString()方法，然后比较得到的字符串。即使数组中的每一项都是数值，sort()方法比较的也是字符串
```
    var values = [0,1,5,10,15];
    values.sort();
    console.log(values); //0,1,10,15,5
    
```
sort()方法可以接收一个比较函数作为参数，以便我们制定那个值位于那个值的前面。
比较函数接收两个参数，如果第一个参数应该位于第二个之前则返回一个负数，如果两个参数相等则返回 0，如果第一个参数应该位于第二个之后则返回一个正数

注意：everse() 和 sort() 方法的返回值是经过排序之后的数组。

* 操作方法

> concat()方法：可以基于当前数组中的所有项创建一个新数组

```
    var colors = ['red','green','blue'];
    var colors2 = colors.concat('yellow',['black','brown']);
    console.log(colors2);
```
> slice(): 能够基于当前数组中的一或者多个项创建一个新数组。，可以接收一或两个参数，即要返回项的起始和结束位置。不会影响原数组

```
      var colors = ["red", "green", "blue", "yellow", "purple"];
      var colors2 = colors.slice(1);
      var colors3 = colors.slice(1,4);  // 没有包含位置为4的项
      alert(colors2); //green,blue,yellow,purple
      alert(colors3); //green,blue,yellow
```

> splice()方法，很强大

   * 删除：可以删除任意数量的项，只需指定 2 个参数：要删除的第一项的位置和要删除的项数。
例如， splice(0,2) 会删除数组中的前两项。
   *  插入：可以向指定位置插入任意数量的项，只需提供 3 个参数：起始位置、0（要删除的项数）
和要插入的项。如果要插入多个项，可以再传入第四、第五，以至任意多个项。例如，splice(2,0,"red","green") 会从当前数组的位置 2 开始插入字符串 "red" 和 "green" 。
   *  替换：可以向指定位置插入任意数量的项，且同时删除任意数量的项，只需指定 3 个参数：起始位置、要删除的项数和要插入的任意数量的项。插入的项数不必与删除的项数相等。例如，splice (2,1,"red","green") 会删除当前数组位置 2 的项，然后再从位置 2 开始插入字符串"red" 和 "green" 。
    
    注意 ：splice() 方法始终都会返回一个数组，该数组中包含从原始数组中删除的项（如果没有删除任何项，则返回一个空数组）。
    
    
> join() 方法则可以使用不同的分隔符来构建一个字符串。 join()法只接收一个参数，即用作分隔符的字符串，然后返回包含所有数组项的字符串


* 位置方法 ECMAScript5 增加的位置方法

> indexOf()和lastIndexOf(),这两个方法都接收两个参数，要查找的项和（可选得）表示查找起点为值的索引，indexOf()从数组的

    开头开始向后查找，lastIndexOf()从数组的末尾向前查找返回值：返回要查找项在数组中的位置，或者在没有找到的情况下返回 -1
    
    
* 迭代方法 ECMAScript 5 定义的 
   
   * every() ：对数组中的每一项运行给定函数，如果该函数对每一项都返回 true ，则返回 true 。
    * filter() ：对数组中的每一项运行给定函数，返回该函数会返回 true 的项组成的数组。
    * forEach() ：对数组中的每一项运行给定函数。这个方法没有返回值。
    * map() ：对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组。
    * some() ：对数组中的每一项运行给定函数，如果该函数对任一项返回 true ，则返回 true 。
    
    
* 归并方法  ECMAScript 5 定义的 

  > reduce()和reduceRight()这两个方法都会迭代数组的所有项，然后构建一个最终返回的值。其中， reduce() 方法从数组的第一项开始，逐个遍历到最后。而 reduceRight() 则从数组的最后一项开始，向前遍历到第一项。这两个方法都接收两个参数：一个在每一项上调用的函数和（可选的）作为归并基础的初始值

```
    ar values = [1,2,3,4,5];
    var sum = values.reduce(function(prev, cur, index, array){
    return prev + cur;
    });
    alert(sum); //15
```
