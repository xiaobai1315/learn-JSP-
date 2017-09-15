##JSP语法
JavaScript 中的所有事物都是对象：字符串、数值、数组、函数...

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

###“==” 和 “===”
```
==	等于
===	全等（值和类型）

var a = 5;

a == 5; 		//true
a == "5"; 	//true
a === "5";	//false,比较值的同时还比较了类型
a === 5;		//true

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

###array/MAp/Set创建及遍历

```
var arr = ['a', 'b', 'c'];
//遍历方法1：
for(item of arr){
    console.log(item);  // a b c d e
}

//遍历方法2：
//数组的forEach方法中的回调函数的参数依次是：数组元素、元素下标、数组本身
arr.forEach((item, index, _arr)=>{

    console.log(`item=${item} ,index=${index} _arr=${_arr}`);
    
    //item=a ,index=0 _arr=a,b,c,d,e
    //item=b ,index=1 _arr=a,b,c,d,e
    //item=c ,index=2 _arr=a,b,c,d,e
    //item=d ,index=3 _arr=a,b,c,d,e
    //item=e ,index=4 _arr=a,b,c,d,e
});

//map 就是 OC 中的字典
var map = new Map([['name','xiaobai'],['age',20]]);

//清空map
map.clear();

//删除map中某一个键值对
map.delete('name');

//遍历map,map的 forEach回调方法的参数依次是：值、键、map本身；
map.forEach((value, key, _map)=>{
    console.log(`value=${value}, key=${key}, _map=${_map}`);
});


var set = new Set(['a', 'b', 'c']);

//添加元素
set.add('e');

//遍历set,set的 forEach回调方法的参数依次是：值、值、set本身；
set.forEach((value, samevalue, _set)=>{
    console.log(`value=${value}, samevalue=${samevalue}, _set=${_set}`);
});
```

###创建方法
```
//方式1：
function func(name, age){	//name 和 age 是形参，不需要加类型
	document.writeln(name, age);
}

func("xiaobai", 20);

//方式2
var func = function(name, age){
	document.writeln(name, age);
}

func("xiaoahei", 22);
```

###创建对象
```
//方法1：创建一个空对象
var obj = {};
//添加属性
obj.name = "xiaobai";
obj.age = 20;
obc.friend = ["xiaohei", "xiaohong"]

//方法2：创建对象的同时添加属性
var obj = {
	name:"xiaobai", 
	age:20
	obc.friend = ["xiaohei", "xiaohong"]	
};

//访问对象的属性
obj.name;
obj.age;
obj.friend[0]; //"xiaohei"

//给对象添加方法
obj.showFriend = function(){
	for(index in this.friend){
		document.writeln(this.friend[index]);
	}
}
this :代表当前对象

//调用对象方法： obc.showFirend();
```

##ECMASRIPT 6
###1、let
let 定义的变量只在变量的作用域内有效，出了作用域将无法访问

```
var a = 100;
let b = 100;
document.writeln(a);
document.writeln(b); //a b 都有效

var a = 100;
{
	let b = 100;
}
document.writeln(a);
document.writeln(b); //a有效，b无效，因为b出了作用域，无法被访问；
```

###2、const

const修饰的变量是常量，const限制的是给常量分配值的动作，不是限制常量的值；也就是const修饰的常量不允许重新分配值，但是如果是数组常量，可以继续添加数据；也就是说const修饰的常量的指针是不能改变的；

```
const a = 100;
a = 200; //报错，不能修改常量的值

const a = [];
a.push(1); //不会报错，
a = []; //报错，这样相当于从新给a赋值，修改a指针的地址；
```

###3、destructuring 解构

```
//解构数组,分别将数组中的元素赋值给指定变量
let [a, b] = ["apple", "orange"]; //a = "apple" b = "orange"

//解构对象
function breakfast() {	//函数返回一个对象
    return {apple : "apple1", orange : "orange1"};
}
let {apple : a, orange : b} = breakfast();
//解构函数返回的对象，将apple属性的值赋给a,orange属性的值赋给b
document.writeln(a, b); //apple1orange1

```

###4、字符模板
```
let str1 = "面包";
let str2 = "咖啡"；

拼接字符串方法1：let food  = "早餐吃" + str1 + str2;
使用字符模板拼接字符串：
let food = `早餐吃 ${str1} ${str2}` //早餐吃 面包 咖啡

多行显示文字
let food = `早餐吃 
${str1} ${str2}` 
//早餐吃 
面包 咖啡
```

###5、标签模板
标签模板的实质是函数，功能是处理字符模板中的数据

```
let str1 = "面包";
let str2 = "咖啡"；
let food = `早餐是 ${str1} ${str2}`;

使用标签模板
let food = tagFunction`早餐是 ${str1} 和 ${str2} !`;
//定义标签函数
function tagFunction(string, ...values){
	//string参数是字符模板中被${}分割的字符串的数组，本例中的string的值为:[“早餐是 ”," 和 "," !"]
	//values的值是字符串中${}中内容的数组，本例中的values的值为：["面包"，"咖啡"]；
}
```

###6、字符串函数

```
startWith : 判读字符串是否已某个字符串开头，返回bool类型；
endWith : 判读字符串是否已某个字符串结尾，返回bool类型；
includes : 判读字符串是否包含某个字符串，返回bool类型；
```

###7、函数的默认值
定义函数的时候可以指定参数的默认值，调用函数如果不传递参数，就会使用默认值

```
function breakfast(food = "🍞", drink = "☕️") {
    console.log(`${food} ${drink}`);
}

breakfast();	//🍞 ☕️
breakfast("面包", "🍵");	//面包 🍵
breakfast( ,"🍵");	//报错，
```

###8、"..."操作符
... 根据位置不同，可以用作展开操作符和剩余操作符；

```
1、spread 展开操作符：
let food = ["🍎", "🍌"];
let food1 = ["🍋", ...food]; //展开food数组，将food数组内容添加到food1数组

console.log(...food);	//展开food数组：🍎 🍌
console.log(...food1); //🍋 🍎 🍌

2、rest 剩余操作符

函数接收多个参数，第一参数赋值给dessert 第二个参数赋值给drink 剩余参数已数组的形式赋值给foods；
function breakfast(dessert, drink, ...foods) {
    console.log(dessert, drink, ...foods); //展开foods数组输出内容
}

breakfast("🍞", "☕️", "🍎", "🍋");	//🍞 ☕️ 🍎 🍋
```

###9、解构参数

```
function breakfast(dessert, drink, {location, restrount} = {}) {
    console.log(dessert, drink, location, restrount);
}

breakfast("🍞", "☕️", {location : "beijing", restrount : "kendeji"});	//🍞 ☕️ beijing kendeji

```

###10、输出函数的名字

```
let breakfast = function () {}
console.log(breakfast.name);	//匿名函数的名字默认为变量的名字 breakfast

let breakfast1 = function mybreakfast() {}
console.log(breakfast1.name); //输出函数的名字 mybreakfast
```

###11、箭头函数,定义函数的简写方式

```
var fun = name => name;	
    函数名 参数    返回值
    
var func = (name, age) => {	//多个参数
	console.log(name);
	console.log(age);
}

var fun = name => {}; 	//函数返回值为空，返回值必须用{}
```

###12、对象表达式

```
给对象添加属性，如果属性名和变量名一致，只需要添加属性名即可
var name = "xiaobai";
var age = 22;
var obj = {
	name,
	age,
	
	method(){	//添加方法,可省略Function关键字
	
	}
}	

console.log(obj) //{name: "xiaoba1", age: 22}
```

###13、对象属性名带空格

```
var obj = {};
obj.name = "xiaobai";
obj.first name = "wang";	//报错，属性名不可以带空格

解决办法：
1、 obj['first name'] = "wang"; //{name: "xiaobai", first name: "wang"}

2、var firstName = "first name";
obj.firstName = "wang";  //{name: "xiaobai", first name: "wang"}
```

###14、Object.is 判断两个值是否相等

```
//通常情况可以使用 == 或 === 来判断，
// == 判断值是否相等
// === 同时判断值和类型

//特殊情况,-0 和 +0 是两个不同的值；
-0 == +0; //true
-0 === +0; //true
NAN == NAN; //false
NAN === NAN; //false

//解决办法：
Object.is(-0, +0); //false
Object.is(NAN, NAN);	//true
```

###15、Object.assign 把对象的值赋值给其他对象

```
var ojb = {};
//第一个参数是目标对象，接收传递的值；第二个参数是复制的元对象；
Object.assign(ojb, {name : "xiaobai"}); 
console.log(ojb);	//{name: "xiaobai"}
```

###16、Object.getprototypeof /setPrototypeof

```

var breakfase = {
    drink(){
        console.log("breakfast drink");
    }
}

var dinner = {
    drink(){
        console.log("dinner drink");
    }
}

//Object.create 基于已经存在的对象创建新对象，会继承对象的属性和方法
let obj = Object.create(breakfase);
obj.drink();    //breakfast drink

console.log(Object.getPrototypeOf(obj) == breakfase);   //true

Object.setPrototypeOf(obj, dinner); //  修改obj对象的原型对象
obj.drink();    //dinner drink
console.log(Object.getPrototypeOf(obj) == dinner);  //true
```

```
// __proto__: 用来获取或设置对象的protoType

var obj = {
    __proto__ : breakfase

}

obj.drink(); //breakfast drink
obj.__proto__ = dinner;
obj.drink();	//dinner drink

var obj = {};
obj.__proto__ = dinner;
obj.drink(); //dinner drink
```

###17、super 重写父对象的方法

```
var breakfase = {
    drink(){
        return "breakfast drink";
    }
};

var obj = {
    __proto__ : breakfase,

    drink() {	//利用super.drink()调用父对象的方法，然后重写
        return super.drink() + " my way";
    }
}

console.log(obj.drink());breakfast drink my way
```

###18、迭代器 - Iterators
迭代器每次执行时会通过next方法返回一个对象{value ，done},value代表当前执行的值，done表示是否执行完毕；

```

function chef(foods) {
    let i = 0;

    return{
        next(){
            let done = (i == foods.length);
            let value = !done ? foods[i++] : undefined;

            return{
                done : done,
                value : value
            }
        }
    }
}

let obj = chef(["🍅", "🥚"]);
console.log(obj.next());//{done: false, value: "🍅"}
console.log(obj.next());//{done: false, value: "🥚"}
console.log(obj.next());//{done: true, value: undefined}
```

###19 生成器 - Generators
ES6中使用生成器代替迭代器,生成器使用 “function*”定义；

```
function* chef(foods) {
    for(index in foods){
        yield foods[index];
    }
}

let obj = chef(["🍅", "🥚"]);

do {
    var a = obj.next();
    console.log(a);

}while ((a.value != undefined))

//{value: "🍅", done: false}
//{value: "🥚", done: false}
//{value: undefined, done: true}
```

###20 class

```
class chef{
    constructor(food){
        this.food = food;
    }

    show(){
        return this.food;
    }
}

let cooker = new chef("😯");
console.log(cooker.show());	//😯
```
###21class属性的 get set 方法

```
class chef{
    constructor(food){
        this.food = food;
        this.menu = [];		//定义属性
    }

    show(){
        return this.food;
    }
	//属性menu的get方法，注意：方法名不能与属性名相同，会报错；
    get myMenu(){		
        return this.menu;
    }
    //get menu(){		报错	
    //    return this.menu;
    //}
	//属性menu的set方法，注意：方法名不能与属性名相同，会报错；
    set myMenu(food){
        this.menu.push(food);
    }
    
    //set menu(food){	//报错
    //    this.menu.push(food);
    //}
}

let cooker = new chef("😯");
console.log(cooker.show());
console.log(cooker.myMenu = "西红柿");
console.log(cooker.myMenu = "🥚");
console.log(cooker.menu);
```

###22 static 静态方法
static修饰的方法是静态方法，调用时不需要初始化事例，使用类名调用；

```
class chef{
    constructor(name, age){
        this.name = name;
        this.age = age;
        this.menu = [];
    }
    static cook(food){
        return food;
    }
}
console.log(chef.cook("🥔")); //🥔
```

###23、继承 extends
```
class Person{
    constructor(name, age){
        this.name = name;
        this.age = age;
    }

    info(){
        return `${this.name} ${this.age}`;
    }
}

class Chef extends Person{
    info(){
        return super.info();
    }
}

var cooker = new Chef("xiaobai", 22);
console.log(cooker.info());
```

###24、set
set类似数组，set中的元素是不重复的；
```
let foods = new Set("🍎🍊🍓");
console.log(foods.add("🍉"));
console.log(foods.add("🍎"));	//添加元素
console.log(foods.delete("🍎"));	//删除元素
console.log(foods.size);	//set的大小
console.log(foods.has("🍎"))	//是否包含元素

foods.forEach(food => {	//遍历set中的元素
    console.log(food);
})

foods.clear();	//清空set
```

###25、map

```
let foods = new Map();
let obj = {}, fun = function () {}, str = "xiaobai";

foods.set(obj, "pingguo");  //map添加数据，键-值
foods.set(fun, "juzi");
foods.set(str, "name");

console.log(foods);
console.log(foods.size);    //元素个数

console.log(foods.get(obj));    //根据键获取值
foods.delete(fun);  //删除元素
console.log(foods);

console.log(foods.has(fun()));  //是否包含元素
foods.forEach((value, key) =>{  //遍历map
    console.log(`${value} ${key}`);
})
```

###26、安装工具
webstrom 创建React项目时，会提示unspecified create-react-app, 这是因为本机没有安装 create-react-app，终端执行npm install -g create-react-app，安装完成后webstrom会自动识别create-react-app路径；

```
Homebrew :  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

node.js :  brew install node

创建package.json ： npm init

安装babel : npm install babel-cli --save-dev
```

安装 JSPM、react
 
```
1、新建一个文件夹作为工程项目；
2、npm init 执行完毕后会自动创建 package.json文件
3、 npm install jspm --save-dev，
执行完毕后会创建 node_modules		package-lock.json	package.json
4、 jspm init
5、 jspm install react
6、jspm install react-dom
```

安装React Native

```
1、安装homeBrow /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
2、安装Node.js ： brew install node
3、安装React Native ：npm install -g react-native-cli
4、初始化项目 ： react-native init firstApp //firstApp是项目名称
```

问题：

```
1、初始化项目报错 找不到bundleID，在package.json里面，看到自己的react-native的版本是0.45.*以后的，出现这个错误
这是因为是0.45官方有重大改动，无法使用react-native init项目来启动，
直接react-native init mydemo --version 0.44.3指定之前的版本就可以了；
2、webstrom preference打不开，是因为汉化的问题，删掉汉化包就可以了；
```