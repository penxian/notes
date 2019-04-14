#:nth-child的用法

*支持IE9+以上*

* ：nth-child(2)选取第几个标签，“2可以是你想要的数字”

~~~css
	#demo1 li:nth-child(2){background:#090}
~~~

* :nth-child(n+4)选取大于等于4标签，“n”表示从整数，下同

~~~css
	#demo1 li:nth-child(n+4){background:#090}
~~~
* :nth-child(-n+4)选取小于等于4标签

~~~css
	#demo1 li:nth-child(-n+4){background:#090}
~~~
* :nth-child(2n)选取偶数标签，2n也可以是even

~~~css
	#demo1 li:nth-child(2n){backgound:#090}
~~~
* :nth-child(2n-1)选取奇数标签，2n-1可以是odd

~~~css
	#demo1 li:nth-child(2n-1){backgound:#090}
~~~
* :nth-child(3n+1)自定义选取标签，3n+1表示“隔二取一”

~~~css
	#demo1 li:nth-child(3n+1){backgound:#090}
~~~
* :last-child选取最后一个标签

~~~css
 	#demo1 li:last-child{background:#090}
~~~
* :nth-last-child(3)选取倒数第几个标签,3表示选取第3个

~~~css
	#demo1 li:last-child(3){background:#090}
~~~
[demo](http://jsbin.com/kapuqo/6/edit?html,css,output)