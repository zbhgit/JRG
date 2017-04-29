题目1： \d，\w,\s,[a-zA-Z0-9],\b,.,*,+,?,x{3},^,$分别是什么？

|字符|含义|
|---|---|
|\d|任何ASCII数字等价于\[0-9]|
|\w|任何ASCII字符组成的单词，等价于\[a-zA-Z0-9]|
|\s|任何Unicode空白符|
|[a-zA-Z0-9]|匹配a-zA-Z0-9任意字符|
|\b|匹配一个单词的边界|
|.|除去换行符和其他Unicode终止符之外的任意字符|
|*|匹配前一项0次货多次，等价于{0,1}|
|+|匹配前一项1次货多次，等价于{1,}|
|?|匹配前一项0次或者1次，等价于{0,1}|
|x{3}|匹配x 3次|
|^|匹配字符串开头|
|$|匹配字符串的结尾|


题目2： 写一个函数trim(str)，去除字符串两边的空白字符

```
    function trim(str){
    
      return str.replace(/^\s+|\s+$/,'');
    }
    
```

题目3： 写一个函数isEmail(str)，判断用户输入的是不是邮箱


```
function isEmail(email) {
    var reg = /^\w+@\w+\.\w+$/;

    return reg.test(email) 

}
```
题目4： 写一个函数isPhoneNum(str)，判断用户输入的是不是手机号
```
function isPhoneNum(num) {
    var reg = /^(\+86)?1[3578]\d{9}$/;

    return reg.test(num) 

}

```
题目5： 写一个函数isValidUsername(str)，判断用户输入的是不是合法的用户名（长度6-20个字符，只能包括字母、数字、下划线）

```
    function isValidUsername(str) {
    
        if(str.length<6||str.length>20||(/\W/).test(str)){
            return false;
        } else {
            return true;
        }
    
    }

```


题目6： 写一个函数isValidPassword(str), 判断用户输入的是不是合法密码（长度6-20个字符，只包括大写字母、小写字母、数字、下划线，且至少至少包括两种）
```
    function isValidUsername(str) {
    
        if(str.length<6||str.length>20||(/\W/).test(str)){
            return false;
        } 
        var count = 0;
        if(/[a-z]/.test(str)) count++;
        if(/[A_Z]/.test(str)) count++;
        if(/[0-9]/.test(str)) count++;
        if(/_/.test(str)) count++;
        if(count>=2) return true;
        return false;
    
    }

```
题目7： 写一个正则表达式，得到如下字符串里所有的颜色
```
var re = /#[0-9a-f]{6}/gi;
var subj = "color: #121212; background-color: #AA00ef; width: 12px; bad-colors: f#fddee "
console.log( subj.match(re) )  // ['#121212', '#AA00ef']
```

题目8： 下面代码输出什么? 为什么? 改写代码，让其输出[""hunger"", ""world""].
```
    var str = 'hello  "hunger" , hello "world"';
    var pat =  /hunger|world/g;
    str.match(pat);

```
