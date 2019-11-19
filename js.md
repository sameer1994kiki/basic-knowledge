
1. [test](http://www.baidu.com)
     + <font color="red">我有颜色</font>
     + 我后面有空格&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;嘿嘿
2. Arry中map方法的参数和使用方法
```
['1','2','3'].map(parseInt)
等同于
['1','2','3'].map((item,index)=>parseInt(item,index))
parseInt第二个参数是基数
parseInt('1', 0) //radix为0时，且string参数不以“0x”和“0”开头时，按照10为基数处理。这个时候返回1
parseInt('2', 1) //基数为1（1进制）表示的数中，最大值小于2，所以无法解析，返回NaN
parseInt('3', 2) //基数为2（2进制）表示的数中，最大值小于3，所以无法解析，返回NaN
```
3. [防抖和节流](https://codepen.io/sameer1994kiki/pen/VwZPZWB)
   + [闭包](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)
        + 自执行函数
        作用：创建一个独立的作用域,避免变量污染
        ```
        Q：为什么自执行函数需要加额外的括号
        //就函数表达式来说，在后面直接加括号是可以的，比如
        var fnc = function () {
            console.log( 'test' )
        }()
        //但是！如果是函数声明直接加括号就是不行滴
        function () {
            console.log( 'test' )
        }()
        Uncaught SyntaxError: Function statements require a function name
        //因为js引擎在解析js的时间遇到function开头的代码会把它当做函数声明，会报没有名字的错误，为函数声明   
        加上函数名以后依然会报错. 因为函数声明到第二个花括号处，就已经算是结尾了，后面的()会被当作分组操作符，   
        这个()实际上已经和函数声明没关系了，但是既然有了分组操作符，那就要有表达式，不然会报错
        function test () {
            console.log( 'test' )
        }()
        Uncaught SyntaxError: Unexpected token )
        //在第二个()中加入表达式，函数不会报错，但是函数还是不会执行,因为函数声明到大括号结尾声明就结束了
        function test () {
            console.log( 'test' )
        }(1)
        //如果我们想要函数直接执行，我们可以在function前面加一些操作符，这样js在解析的时间就不会把它作为一个函数声明了
        //常用写法
        (function(){alert('test')} ()) // 用括号把整个表达式包起来,避免全局变量污染
        (function(){alert('test')}) () //用括号把函数包起来,把函数当作表达式解析，然后执行解析后的函数

        //不常用写法
        !function(){alert('test')}() // 求反，我们不在意值是多少，只想通过语法检查。
        +function(){alert('test')}()
        -function(){alert('test')}()
        ~function(){alert('test')}()
        void function(){alert('test')}()
        new function(){alert('test')}()
        ```
		
		+ new Date()可以将该元素转换为Number类型，+new Date() 将会调用 Date.prototype 上的 valueOf() 方法，根据MDN，Date.prototype.value方法等同于Date.prototype.getTime()
		+ 定时器清除以后为什么还要设置null，返回值timeoutID是一个正整数，表示定时器的编号。这个值可以传递给clearTimeout()来取消该定时器。清除这个值，同时也清除了内存占用。
		  ```
		  let timer = setTimeout(()=>{
			  console.log("test")
		  },2000)
		  console.log(timer)   //53293,非固定值（好像和时间有关
		  clearTimeout(timer);
		  console.log(timer)	//53293
		  ```
4. 类型判断
    + Object.prototype.toString.call()
		
		```
		<!-- 可以通过 toString() 来获取每个对象的类型。为了每个对象都能通过 Object.prototype.toString() 来检测，需要以 Function.prototype.call() 或者 Function.prototype.apply() 的形式来调用，传递要检查的对象作为第一个参数，称为 thisArg。 -->

		var toString = Object.prototype.toString;
		toString.call(new Date); // [object Date]
		toString.call(new String); // [object String]
		toString.call(Math); // [object Math]
		toString.call(undefined); // [object Undefined]
		toString.call(null); // [object Null]
		```
	+  instanceof
	  	```
		<!--   instanceof 运算符用来检测 constructor.prototype 是否存在于参数 object 的原型链上 -->
		object instanceof constructor

		object  要检测的对象.
		constructor  某个构造函数
	 	```
    + typeof
		```
		typeof 只能检测 基本数据类型:boolean、undefined、string、number、symbol，
		而null ,Array、function、Object ,使用typeof出来都是Objec。无法检测具体是哪种引用类型。
		```
5. 非匿名自执行函数，函数名只读
  ```
	var b = 10;
	(function b(){
	    b = 20;
	    console.log(b);  //function b
	})();


	 var a = 10;
	(function () {
	    console.log(a) //undefined,下面的var变量提升
	    a = 5
	    console.log(window.a) //10
	    var a = 20;
	    console.log(a) //20
	})()
  ```
6. 类数组
   ```
   <!-- 因为obj具有 length 属性和 splice 方法，故将其作为数组进行打印 -->
	var obj = {
	    '2': 3,
	    '3': 4,
	    'length': 2,
	    'splice': Array.prototype.splice,
	    'push': Array.prototype.push
	}
	obj.push(1)
	obj.push(2)
	console.log(obj) //[empty × 2, 1, 2, splice: ƒ, push: ƒ]

   ```

7. ES6转ES5
    + 将ES6的代码转换为AST语法树，然后再将ES6 AST转为ES5 AST，再将AST转为代码

8. Event Loop
9. 宏任务 & 微任务（浏览器）（区别于node）
    + 宏任务
		1. I/O 操作
        2. setTimeout
		3. setInterval
        4. requestAnimationFrame
	+ 微任务
		1. Promise.then catch finally
        2. MutationObserver
10. 手动实现一个promise
    
11. 三次握手四次挥手
    + A:你好，我是A    B:收到，我是B      A:那么咱们连接了
    + A:你好，我要关了  B:等下，我还有最后一个包   B：我已经好了，随时关闭  A:你关闭吧，不用回复（A等2ms无回复，关闭）

12. test
