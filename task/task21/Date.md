# Date类型

> ECMAScript中的Date类型是在早起Java中java.util.Date类基础上构建的。为此，Date类型使用自UTC（国际协调时间）1970年1月1日午夜零点开始经过的毫秒数

创建一个日期对象 

` var now = new Date()`

1. 几个静态方法

* Date.now()

> 此方法返回当前距离170.1.1 零时的毫秒数

`Date.now()
 //1493448385977`

* Date.parse() 

> 用来解析日期字符串，返回距离距离170.1.1 零时的毫秒数

日期字符串的格式应该完全或者部分符合YYYY-MM-DDTHH:mm:ss.sssZ格式，Z表示时区，是可选的。
如果解析失败，返回NaN

`Date.parse("2017-10-10")
 // 1507593600000`
 
 * Date.UTC()
 
 > 默认情况下，Date对象返回都是当前时区的时间
