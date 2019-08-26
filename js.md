
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
  + 闭包
    + 自执行函数
