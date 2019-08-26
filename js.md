
1. [test](http://www.baidu.com)
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
3. [防抖和节流]()
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
        <font color="ff0000" >Uncaught SyntaxError: Function statements require a function name</font>
        //因为js引擎在解析js的时间遇到function开头的代码会把它当做函数声明，会报没有名字的错误，为函数声明加上函数名以后依然会报错.因为函数声明到第二个花括号处，就已经算是结尾了，后面的()会被当作分组操作符，这个()实际上已经和函数声明没关系了，但是既然有了分组操作符，那就要有表达式，不然会报错
        function test () {
            console.log( 'test' )
        }()
        <font color="ff0000" >Uncaught SyntaxError: Unexpected token )</font>
        //在第二个()中加入表达式，函数不会报错，但是函数还是不会执行,因为函数声明到大括号结尾声明就结束了
        function test () {
            console.log( 'test' )
        }(1)
        //如果我们想要函数直接执行，我们可以在function前面加一些操作符，这样js在解析的时间就不会把它作为一个函数声明了
        //常用写法
        (function(){alert('test')} ()) // 用括号把整个表达式包起来
        (function(){alert('test')}) () //用括号把函数包起来
        //不常用写法
        !function(){alert('test')}() // 求反，我们不在意值是多少，只想通过语法检查。
        +function(){alert('test')}()
        -function(){alert('test')}()
        ~function(){alert('test')}()
        void function(){alert('test')}()
        new function(){alert('test')}()
        ```
