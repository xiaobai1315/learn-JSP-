###JSP语法
1、定义变量：

```
var a;
a = 10;
var b = 10, c = 20;
var d = "123", e = '123'; //定义字符串 用单引号 双引号都可以

查看变量类型：typeof
typeof(d) -> string
typeof(a) -> number

字符串拼接：不仅可以字符串拼接，还可以数字和字符串拼接，jsp会先将数字转换成字符串，然后和字符串拼接
var f = d + e; //f="123123"
var f = a + e; //f="10123"

类型转换：
parseInt：将变量转换成整型,
var d = "132"
parseInt(d) -> 132
parseFloat :将变量转换成浮点型
```

###数组

~~~
//创建数组
var arr = []; //创建空数组
var arr = [1,2,3,4]; 
var arr = ["1", "2", 3, 4];

//返回数组长度
arr.length 

//合并数组
var arr = [1,2,3];
var arr1 = ["a", "b"];
var arr2 = arr.concat(arr1); //[1, 2, 3, "a", "b"]

//join:把数组的所有元素放入一个字符串,并通过指定的分隔符进行分隔。
var arr = ["aaa", "bbb", "ccc"];
var str = arr.join("."); //"aaa.bbb.ccc"

//push : 向数组的末尾添加一个或更多元素，并返回新的长度。
var arr = [1,2];
arr.push(3,4); // [1,2,3,4]

//pop : 删除并返回数组的最后一个元素
var arr = [1,2,3,4];
arr.pop();	//[1,2,3]

//shift()	删除并返回数组的第一个元素
var arr = [1,2,3,4];
arr.shift(); //[2,3,4]

//unshift()	向数组的开头添加一个或更多元素，并返回新的长度。
var arr = [1,2];
arr.unshift("a", "b"); //["a", "b", 1, 2];

//reverse()	颠倒数组中元素的顺序。
var arr = [1,2];
arr.reverse(); // [2,1]

//slice()	截取数组指定位置的元素，形成新的数组
var arr = [1, 2, 3, 4];
arr.slice(0, 2);  //[1, 2]

//splice()	删除元素，并向数组添加新元素。arrayObject.splice(index,howmany,item1,.....,itemX)
index：删除/添加操作的起始位置
howmany：删除元素的个数
item1,.....,itemX：要添加的元素
var arr = [1, 2, 3, 4];
//从位置 1 开始 删除 2 个元素，添加 5 6 7 三个元素
arr.splice(1,2,5,6,7); //[1, 5, 6, 7, 4]
//在 0 位置添加 “a” "b"
arr.splice(0, 0, "a", "b"); //["a", "b", 1, 2, 3, 4]

//sort()	对数组的元素进行排序
参数可选，如果参数为空，将按照字母顺序默认排序；
参数必须是函数，，该函数要比较两个值，然后返回一个用于说明这两个值的相对顺序的数字。比较函数应该具有两个参数 a 和 b，其返回值如下：
若 a 小于 b，在排序后的数组中 a 应该出现在 b 之前，则返回一个小于 0 的值。
若 a 等于 b，则返回 0。
若 a 大于 b，则返回一个大于 0 的值。
//默认排序
var arr = ["tom", "jermy", "xiaobai", "zhang"];
arr.sort(); //["jermy", "tom", "xiaobai", "zhang"]
//指定排序算法
arr = [3,5,1,8,2];
function sortFunc(a, b){return a - b};
arr.sort(sortFunc);  //[1, 2, 3, 5, 8]

//toString()	把数组转换为字符串，并返回结果。
var arr = [1, 2, 3, 4];
arr.toString(); //"1,2,3,4"
~~~

###Number对象
在 JavaScript 中，数字是一种基本的数据类型。JavaScript 还支持 Number 对象，该对象是原始数值的包装对象。在必要时，JavaScript 会自动地在原始数据和对象之间转换。

```
var a = 10;
var b = Number(a);
typeof(a) -> "number"
typeof(b) -> "number"
可以看出 定义一个数字变量时，jsp会自动将其转换成 Number对象

Number的属性
//MAX_VALUE	可表示的最大的数。
var a = Number.MAX_VALUE;
 
//MIN_VALUE	可表示的最小的数。
var a = Number.MIN_VALUE;

//NaN	非数字值。
NaN 属性用于引用特殊的非数字值。
无法使用 for/in 循环来枚举 NaN 属性，也不能用 delete 运算符来删除它。
NaN 不是常量，可以把它设置为其他值。
提示：请使用 isNaN() 来判断一个值是否是数字。原因是 NaN 与所有值都不相等，包括它自己。

//NEGATIVE_INFINITY	负无穷大，溢出时返回该值。
Number. NEGATIVE_INFINITY
//POSITIVE_INFINITY	正无穷大，溢出时返回该值。
Number. POSITIVE_INFINITY

Number 对象方法
//toString	把数字转换为字符串，使用指定的基数。
参数：如果不带参数，默认按照10进制输出；有参数，按照对应进制输出；
var a = 16
a.toString() //"16"
a.toString(2); //"10000"
a.toString(8) //"20"
a.toString(16) //"10"

//toFixed	把数字转换为字符串，结果的小数点后有指定位数的数字。
参数必需：规定小数的位数，是 0 ~ 20 之间的值，包括 0 和 20，有些实现可以支持更大的数值范围。如果省略了该参数，将用 0 代替。
a = 1.2423
a.toFixed(3); //"1.242"
a.toFixed() //"1"。默认不显示小数
a = 1.453
a.toFixed(1); //"1.5",四舍五入

//toExponential	把对象的值转换为指数计数法。
必需。规定指数计数法中的小数位数，是 0 ~ 20 之间的值，包括 0 和 20，有些实现可以支持更大的数值范围。如果省略了该参数，将使用尽可能多的数字。
a = 234234234234234
a.toExponential(3) //"2.342e+14"
a.toExponential() //"2.34234234234234e+14"

//toPrecision	把数字格式化为指定的长度。
必需。规定必须被转换为指数计数法的最小位数。该参数是 1 ~ 21 之间（且包括 1 和 21）的值。
有效实现允许有选择地支持更大或更小的 num。
如果省略了该参数，则调用方法 toString()，而不是把数字转换成十进制的值。
```