## 图片懒加载原理

题目1：如何判断一个元素是否出现在窗口可视范围（浏览器的上边缘和下边缘之间，肉眼可视）。写一个函数 isVisible实现

> 理解懒加载的原理，首先要弄清楚这些个宽高和位置的详细。

* clientWidth AND clientHeight
	该属性指的是元素的可视部分的宽度和高度，即padding+content，如果没有滚动条，即为元素设定的高度和宽度，如果出现股东条，滚动条会遮盖元素的宽高，那么该属性就是本来的宽高减去滚动条的宽高
* offsetWidth AND offsetHeight
	这一属性指的是元素的border + padding + content的宽和高，该属性与其内部的内容是否超出元素大小无关，只和本来设定的border width height 有关
* clientTop AND clientLeft
	这对属性是用来读取元素的border的宽和高的。
* offsetLeft AND offsetTop
	说到这对属性就需要说下offsetParent,所谓offsetParent指的是当前元素的离自己最近的具有定位的（position:absolute或者position：relative）父级元素（不仅仅指的是直接父级元素，只要是它的父元素都可以），该父级元素就是当前元素的offsetParent，如果从该元素向上寻找，找不到这样一个父级元素，那么当前元素的offsetParent就是body元素。而offsetLeft和offsetTop指的是当前元素，相对于其offsetParent左边距离和上边距离，即当前元素的border到包含它的offsetParent的border的距离
* scrollHeight AND scrollWidth
	这两个属性指的是当前元素内部的内容超出宽度和高度的时候，元素内部内容的实际宽度和高度，需要注意其中内容有没有超过其高度或者宽度的时候，该属性与设定的宽高相同（chrome测试）

* scrollTOp AND scrollLeft
	这对属性时可读写的，指的是当元素其中的内容超出宽高的时候，元素被卷起的高度和宽度
* clientX AND clientY
	指当事件发生时，鼠标点击位置相对于浏览器（可视区）的坐标，左上角为原点。
* screenX AND screenY
	发生事件时，鼠标相对于屏幕的坐标

* offsetX AND offsetY
	指当事件发生时，鼠标点击位置相对于该事件源的位置，即点击该div，以div的左上角为原点计算鼠标点击的位置。
* pageX AND pageY
	指事件发生时鼠标点击位置相对于页面的位置，相对于HTML顶部左上角计算的值

> 懒加载的原理：先把img的url存储到自定义属性上，如data-src。当元素出现在可视区时，设置img的src属性。

下面是判断函数
```
function isVisible($ele) {
	var winH = $(window).height(), //窗口的高度
		offsetH = $ele.offset().top(), // 当前元素垂直党项的距离
		scrollT = $(window).scrollTop();// 垂直滚动距离
		if((offsetH>scrollT)&&(offsetH<(scrollT+ winH))){
			return true;
		}
		return false;
}
```
题目2 ：当窗口滚动时，判断一个元素是不是出现在窗口可视范围。每次出现都在控制台打印 true 。用代码实现(基于JQ)

```
	$(window).on('scroll',function(){
			if(isVisible($node)) {
				console.log(true);
			}
	});

```

题目三：当窗口滚动时，判断一个元素是不是出现在窗口可视范围。在元素第一次出现时在控制台打印 true，以后再次出现不做任何处理。用代码实现

```
$(window).on('scroll',function(){
		if( !$node.hasClass('show') && isVisible($node)) {
			$node.addClass('show')
			console.log(true);
		} else {

		}
});

```

题目4 懒加载原理

答：一个网站需要加载的图片会很多，如果要求浏览器在用户请求打开该网站的那一瞬间，加载完所有的图片，会导致加载的时间非常长，且效果不一定好，如果遇到传输问题，有的图片甚至可能出现显示不全的情况，这样的话用户的体验就很差了。 
对于这个问题，我们想到了一个解决办法：直到该图片出现在用户的视线范围内时，才加载该图片。 
关键的步骤： 
①判断图片是否可见:如果：屏幕滚动的高度+窗口高度 > 图片到页面顶部的距离，那么该图片即是可见的； 
②转换图片的可见状态:修改图片原本的src值。我们可以给每一个图片的src设一个相同的初始值，这样只会发起一次请求，如果不设置，可能会出现“X”就很难看。当图片是可见时，再修改图片的src属性，这时，图片的内容就能被加载出来了。


题目5 ：[链接](lazy.html)

题目6： [链接](index.html)