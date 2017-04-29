* Math任务

[Math对象的简单介绍](Math.md)

1.写一个函数，返回从min到max之间的 随机整数，包括min不包括max 

```
    function selectFrom(lowerValue,upperValue){
        var choices = upperValue - lowerValue;
        return Math.floor(Math.random()*choices+lowerValue)
    }
```

2.写一个函数，返回从min都max之间的 随机整数，包括min包括max 

```
  function selectFrom(lowerValue,upperValue){
      var choices = upperValue - lowerValue +1;
      return Math.floor(Math.random()*choices+lowerValue)
}
```

3.写一个函数，生成一个长度为 n 的随机字符串，字符串字符的取值范围包括0到9，a到 z，A到Z。

```
    // 随机函数
    function selectFrom(lowerValue,upperValue){
        var choices = upperValue - lowerValue +1;
        return Math.floor(Math.random()*choices+lowerValue)
    }
    // 生成字符串函数
    function getRanStr(n){
        if(n === 0 ){ return '';}
        var str='0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
        console.log(str);
        var newStr = '';
        for(var i=0;i<n;i++) {
            var num = selectFrom(0,61);
            newStr += str.charAt(num)
        }
        return newStr;
    }
    
    var str = getRanStr(10);
    console.log(str);

```


4、写一个函数，生成一个随机 IP 地址，一个合法的 IP 地址为 0.0.0.0~255.255.255.255
```
    // 随机函数
    function selectFrom(lowerValue,upperValue){
        var choices = upperValue - lowerValue +1;
        return Math.floor(Math.random()*choices+lowerValue)
    }
    // 生成IP地址
    function getRanIP(){
        var newIP = null;
        var arr =[]
        for(var i=0;i<4;i++) {
            var num = selectFrom(0,255);
            arr.push(num);  
        }
        newIP = arr.join('.');
        return newIP;
    }
    var ip = getRanIP();
    console.log(ip);
```



5写一个函数，生成一个随机颜色字符串，合法的颜色为#000000~ #ffffff
```
    
    // 随机函数
        function selectFrom(lowerValue,upperValue){
            var choices = upperValue - lowerValue +1;
            return Math.floor(Math.random()*choices+lowerValue)
     }
     
     // 获取颜色
    function getRanColor(){
        var str='0123456789abcdef';
        console.log(str);
        var newColor = '#';
        for(var i=0;i<6;i++) {
            var num = selectFrom(0,15);
            newColor += str.charAt(num)
        }
        return newColor;
    }

    console.log(getRanColor());
```

# 数组任务

[数组相关方法的简单介绍](Array.md)

1. 数组方法里push、pop、shift、unshift、join、splice分别是什么作用？用 splice函数分别实现push、pop、shift、unshift方法

  > 作用 查看 [介绍](Array.md);
  
  > 实现函数
  
  ```
  // push
  function rePush(arr,item) {
  
      for (var i=1;i<arguments.length;i++) {
          arr.splice(arr.length,0,arguments[i]);
      }
      return arr.length;
  }
  
  // pop
  function rePop (arr){
      return  arr.splice(arr.length-1,1)[0];
  }
  
  // shift
  function reShift(arr) {
      return  arr.splice(0,1)[0];
  }
  
  // unshift
  function reUnShift(arr,item) {
  
      for (var i=arguments.length-1;i>0;i--) {
          arr.splice(0,0,arguments[i]);
      }
      return arr.length;
  }
  ```

2. 写一个函数，操作数组，数组中的每一项变为原来的平方，在原数组上操作

```
    function squareArr(arr){
       for(var i=0;i<arr.length;i++){
           arr[i] = arr[i]*arr[i];
       }
       return arr;    
    }
    var arr = [2, 4, 6]
    squareArr(arr)
    console.log(arr) // [4, 16, 36]
```

3. 写一个函数，操作数组，返回一个新数组，新数组中只包含正数，原数组不变
```
    function filterPositive(arr){
    
        var newArr = [];
        for(var i=0;i<arr.length;i++) {
            if((typeof arr[i] === 'number') &&arr[i]>0) {
                newArr.push(arr[i]);
            }

        }
        return newArr;
   
    }
    var arr = [3, -1,  2,  '饥人谷', true]
    var newArr = filterPositive(arr)
    console.log(newArr) //[3, 2]
    console.log(arr) //[3, -1,  2,  '饥人谷', true]
```
#  Date任务

1. 写一个函数getChIntv，获取从当前时间到指定日期的间隔时间

```
var str = getChIntv("2017-02-08");

function getIntv(timeStr){
    var now = new Date();
    var end = new Date(timeStr);
    var times = (end.getTime()-now.getTime())/1000;
    var d = parseInt(times/(60*60*24));
    var h = parseInt(times/60/60%24);
    var m = parseInt(times/60%60);
    var s = parseInt(times%60);
    console.log(d,h,m,s);
    var str = '距离目标日期还有：'+t+'天'+h+'小时'+m+'分钟'+s+'秒';
    return str；
}

console.log(str);

```
2. 把hh-mm-dd格式数字日期改成中文日期

```
var str = getChsDate('2065-12-28');
function getChsDate(date){
	var d=date.split('-');
	var str='';
	var number=['零','一','二','三','四','五','六','七','八','九','十','十一','十二','十三','十四','十五','十六','十七','十八','十九','二十','二十一','二十二','二十三','二十四','二十五','二十六','二十七','二十八','二十九','三十','三十一'];
	var str=number[parseInt(d[0]/1000)]+number[parseInt(d[0]%1000/100)]+
number[parseInt(d[0]%1000%100/10)]+number[parseInt(d[0]%1000%10)]+'年';
	str=str+number[parseInt(d[1])]+'月';
	str=str+number[parseInt(d[2])]+'日';
	return str;
}
console.log(str);

```

3.写一个函数，参数为时间对象毫秒数的字符串格式，返回值为字符串。假设参数为时间对象毫秒数t，根据t的时间分别返回如下字符串:
  
  * 刚刚（ t 距当前时间不到1分钟时间间隔）
  * 3分钟前 (t距当前时间大于等于1分钟，小1小时)
 *  8小时前 (t 距离当前时间大于等于1小时，小于24小时)
  *  3天前 (t 距离当前时间大于等于24小时，小于30天)
  *  2个月前 (t 距离当前时间大于等于30天小于12个月)
  *  8年前 (t 距离当前时间大于等于12个月)
  ```
    function friendlyDate(time){
      var d=new Date().getTime();
      console.log(d);
      var str='';
      var passTime=parseInt((d-time)/1000);//计算时间间隔
      if(passTime<60){str='刚刚'}
      if(passTime>=60 && passTime<3600){
        str=parseInt(passTime/60)+'分钟前';
      }
      if(passTime>=3600 && passTime<86400){
        str=parseInt(passTime/3600)+'小时前';
      }
      if(passTime>=86400 && passTime<2592000){
        str=parseInt(passTime/(86400))+'天前';
      }
      if(passTime>=2592000 && passTime<31104000){
        str=parseInt(passTime/2592000)+'月前';
      }
      if(passTime>=31104000)
        str=parseInt(passTime/31104000)+'年前';
      return str;
    }
    var str = friendlyDate( '1492941056710' );
    var str2 = friendlyDate('1483941245793');
    console.log(str);
    console.log(str2);
  ```
  
