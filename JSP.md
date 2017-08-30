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