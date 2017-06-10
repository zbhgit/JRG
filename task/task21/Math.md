
# Math对象

1. Math对象的属性

|属性|说明|
|:---|:---|
|Math.e|自然对数的底数，即常量e的值|
|Math.LN10|10的自然对数|
|Math.LN2|2的自然对数|
|Math.LOG2E|以2为底e的对数|
|Math.LOG10E|以10为底e的对数|
|Math.PI|π的值|
|Math.SQRT1_2|1/2的平方根|
|Math.SQRT2|2的平方根|

2. min(),max()方法

 > 用于确定一组数值中的最小值和最大值，这两个方法都可以接收任意多个参数值
 
 ```
     var max = Math.max(3, 54, 32, 16);
     alert(max); //54
     var min = Math.min(3, 54, 32, 16);
     alert(min);  //3  
 ```
 还可以使用apply方法，把Math对象作为apply（）的第一个参数，从而正确的设置this的值。然后可以将任何数组作为第二个参数。
 
 ```
     var values = [1,2,3,4,5,6,7,8];
     var max = Math.max.apply(Math,values)
 ```
3. 舍入方法

* Math.ceil()执行向上舍入，即它总是将数值向上舍入为最接近的整数；
* Math.floor()执行向下舍入，即它总是将数值向下舍入为最接近的整数；
* Math.round()执行标准舍入，即它总是将数值四舍五入为最接近的整数

```
    alert(Math.ceil(25.9)); //26
    alert(Math.ceil(25.5)); //26
    alert(Math.ceil(25.1)); //26
    
    alert(Math.round(25.9)); //26
    alert(Math.round(25.5)); //26
    alert(Math.round(25.1)); //25
    
    alert(Math.floor(25.9)); //25
    alert(Math.floor(25.5)); //25
    alert(Math.floor(25.1)); //25
```

4. random()方法

Math.random()方法返回大于等于0小于1的一个随机数。
一个非常有用的公式
> 值 = Math.floor(Math.random()*可能值的总数 + 第一个可能的值)

公式中用到了 Math.floor()方法，这是因为Math.random总返回一个小数，所以要进行取整

可利用下列函数：
```
    function selectFrom(lowerValue,upperValue){
        var choices = upperValue - lowerValue +1;
        return Math.floor(Math.random()*choices+lowerValue)
    }
    
    var sum = selectFrom(2,10);
    console.log(sum);
```

5. 其他方法

|方法|介绍|
|:---|:---|
|Math.abs(num)|返回 num 的绝对值|
|Math.asin(x)|返回 x 的反正弦值|
|Math.exp(num)|返回 Math.E 的 num 次幂|
|Math.atan(x)|返回 x 的反正切值|
|Math.log(num)|返回 num 的自然对数|
|Math.atan2(y,x)|返回 y/x 的反正切值|
|Math.pow(num,power)|返回 num 的 power 次幂|
|Math.cos(x)|返回 x 的余弦值|
|Math.sqrt(num)|返回 num 的平方根|
|Math.sin(x)|返回 x 的正弦值|
|Math.acos(x)|返回 x 的反余弦值|
|Math.tan(x)|返回 x 的正切值|





