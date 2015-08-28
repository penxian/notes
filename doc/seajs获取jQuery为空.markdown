###seajs获取jquery为空
 今天在使用seajs获取jQuery获取为空，代码

```
seajs.use("jquery",function($){
	console.log($)
}
```
然后打印的值为空，我就很奇怪，而这个jQuery是我随便到其他地方copy过来的。

后来发现：seajs获取的js使用模块ID来获取，如果模块中使用`define(module_id, dependency, factory)`
则使用seajs.use("module_id")来获取js文件。如果是个匿名的则可以使用路径来获取。  
 而在jQuery中发现

```
define("jquery/jquery/1.10.1/jquery-debug", [], function () { return jQuery; } );
```

所以引入jQuery的时候我们需要这样子：

```
seajs.use("jquery/jquery/1.10.1/jquery-debug", function($){} );
```

但是每次都要这样写是不是很费劲，所以seajs提供了别名功能
加入配置：

```
seajs.config({
   alias: {
      'jquery': 'jquery/jquery/1.10.1/jquery'
    }
})
```

然后我们就可以使用这样使用了

```
seajs.use("jquery",function($){
	console.log($)
}
```

当然我们也可以剔除jQuery模块名，使用路径引入进来