

## 变量的类型转换的分类

类型转换分为两种：显式类型转换、隐式类型转换。

### 显式类型转换

-   toString()

-   String()

-   Number()

-   parseInt(string)

-   parseFloat(string)

-   Boolean()

### 隐式类型转换

-   isNaN ()

-   自增/自减运算符：`++`、`—-`

-   正号/负号：`+a`、`-a`

-   加号：`+`

-   运算符：`-`、`*`、`/`

### 隐式类型转换（特殊）

-   逻辑运算符：`&&`、`||`、`!` 。非布尔值进行**与或**运算时，会先将其转换为布尔值，然后再运算。`&&`、`||`的运算结果是**原值**，`!`的运算结果为布尔值。

-   关系运算符：`<`、`>` `<=` `>=`等。关系运算符，得到的运算结果都是布尔值：要么是 true，要么是 false。

针对上面这两种类型转换，这篇文章来详细介绍。

## 一、转换为 String

### 1. 调用 toString()方法

语法：

```javascript
变量.toString();
常量.toString(); // 这里的常量，不允许是数字，但可以是其它常量

// 或者用一个新的变量接收转换结果
var result = 变量.toString();
```

【重要】该方法**不会影响到原变量**，它会将转换的结果返回。当然我们还可以直接写成`a = a.toString()`，这样的话，就是直接修改原变量。

举例：

```js
// 基本数据类型
var a1 = 'Ethan';
var a2 = 29;
var a3 = true;

// 引用数据类型
var a4 = [1, 2, 3];
var a5 = { name: 'Ethan', age: 29 };

// null 和 undefined
var a6 = null;
var a7 = undefined;

// 打印结果都是字符串
console.log(a1.toString()); // "Ethan"
console.log(a2.toString()); // "29"
console.log(a3.toString()); // "true"
console.log(a4.toString()); // "1,2,3"
console.log(a5.toString()); // "object"

// 下面这两个，打印报错
console.log(a6.toString()); // 报错：Uncaught TypeError: Cannot read properties of null
console.log(a7.toString()); // 报错：Uncaught TypeError: Cannot read properties of undefined
```

小技巧：在 chrome 浏览器的控制台中，Number类型、Boolean类型的打印结果是蓝色的，String类型的打印结果是黑色的。

一起来看看 toString() 的注意事项。

（1）null 和 undefined 这两个值没有 toString() 方法，所以它们不能用 toString() 。如果调用，会报错。

如果你不确定一个值是不是`null`或`undefined`，可以使用`String()`函数。

（2）多数情况下，`toString()`不接收任何参数；当然也有例外：Number 类型的变量，在调用 toString()时，可以在方法中传递一个整数作为参数。此时它会把数字转换为指定的进制，如果不指定则默认转换为 10 进制。例如：

```javascript
var a = 255;

//Number数值在调用toString()时，可以在方法中传递一个整数作为参数
//此时它将会把数字转换为指定的进制,如果不指定则默认转换为10进制
a = a.toString(2); // 转换为二进制

console.log(a); // "11111111"
console.log(typeof a); // string
```

（3）纯小数的小数点后面，如果紧跟连续6个或6个以上的“0”时，那么，将用e来表示这个小数。代码举例：

```js
const num1 = 0.000001; // 小数点后面紧跟五个零
console.log(num1.toString()); // 打印结果："0.000001"

const num2 = 0.0000001; // 小数点后面紧跟六个零
console.log(num2.toString()); // 【重点关注】打印结果："1e-7"

const num3 = 1.0000001;
console.log(num3.toString()); // 打印结果："1.0000001"

const num4 = 0.10000001;
console.log(num4.toString()); // 打印结果："0.10000001"
```

（4）常量可以直接调用 toString() 方法，但这里的常量，不允许是数字。举例如下：

```js
1.toString(); // 注意，会报错
1..toString(); // 合法。得到的结果是字符串"1"
1.2.toString(); // 合法。得到的结果是字符串"1.2"
(1).toString(); // 合法。得到的结果是字符串"1"
```

**为什么 第一个会报错**

（5）既然常量没有方法，那它为什么可以调用 toString()呢？这是因为，除了 null、undefined之外，其他的常量都有对应的特殊的引用类型——**基本包装类型**，所以代码在解释执行的时候，会将常量转为基本包装类型，这样就可以调用相应的引用类型的方法。


### 2. 使用 String()函数

语法：

```javascript
String(变量/常量);
```

使用 String()函数做强制类型转换时：

-   对于 Number、Boolean、String、Object 而言，本质上就是调用 toString()方法，返回结果同 toString()方法。
-   但是对于 null 和 undefined，则不会调用 toString()方法。它会将 null 直接转换为 "null"。将 undefined 直接转换为 "undefined"。

该方法**不会影响到原数值**，它会将转换的结果返回。

### 3. 隐式类型转换：字符串拼接

格式：变量+"" 或者 变量+"abc"

举例：

```javascript
var a = 123; // Number 类型
console.log(a + ''); // 打印结果："123"
console.log(a + 'haha'); // 打印结果："123haha"
```

上面的例子中，打印的结果，都是字符串类型的数据。实际上底层是调用的 String() 函数。

## 二、转换为 Number

### 1. 使用 Number() 函数

语法：

```js
const result = Number(变量/常量);
```

**情况一：字符串 --> 数字**

（1）如果字符串中是纯数字，则直接将其转换为数字。

（2）如果字符串是一个**空串**或者是一个**全是空格**的字符串，则转换为 0。

（3）只要字符串中包含了其他非数字的内容（`小数点`按数字来算），则转换为 NaN。怎么理解这里的 **NaN** 呢？可以这样理解，使用 Number() 函数之后，**如果无法转换为数字，就会转换为 NaN**。

**情况二：布尔 --> 数字**

（1）true 转成 1

（2）false 转成 0

**情况三：null --> 数字**，结果为：0

**情况四：undefined --> 数字**，结果为：NaN

### 2. 隐式类型转换：正负号 `+a`、`-a`

> 注意，这里说的是正号/负号，不是加号/减号。

任何值做`+a`、`-a`运算时， 底层调用的是 Number() 函数。不会改变原数值；得到的结果，会改变正负性。

代码举例：

```js
const a1 = '123';
console.log(+a1); // 123
console.log(-a1); // -123

const a2 = '123abc';
console.log(+a2); // NaN
console.log(-a2); // NaN

const a3 = true;
console.log(+a3); // 1
console.log(-a3); // -1


const a4 = false;
console.log(+a4); // 0
console.log(-a4); // -0

const a5 = null;
console.log(+a5); // 0
console.log(-a5); // -0

const a6 = undefined;
console.log(+a6); // NaN
console.log(-a6); // NaN
```

### 3. parseInt()函数：字符串 -> 整数

语法：

```js
const result = parseInt(需要转换的字符串)
```

**parseInt()**：将传入的数据当作**字符串**来处理，从左至右提取数值，一旦遇到非数值就立即停止；停止时如果还没有提取到数值，就返回NaN。

parse 表示“转换”，Int 表示“整数”。例如：

```javascript
parseInt('5'); // 得到的结果是数字 5
```

按照上面的规律，parseInt()的转换结果，列举如下。

**情况一：字符串 --> 数字**

（1）**只保留字符串最开头的数字**，后面的中文自动消失。

（2）如果字符串不是以数字开头，则转换为 NaN。

（3）如果字符串是一个空串或者是一个全是空格的字符串，转换时会报错。

**情况二：Boolean --> 数字**，结果为：NaN

**情况三：Null --> 数字**，结果为：NaN

**情况四：Undefined --> 数字**，结果为：NaN

---

Number() 函数和 parseInt() 函数的区别：

就拿`Number(true)` 和 `parseInt(true)/parseFloat(true)`来举例，二者在使用时，是有区别的：

-   Number(true) ：千方百计地想转换为数字；如果转换不了则返回 NaN。

-   parseInt(true)/parseFloat(true) ：提取出最前面的数字部分；没提取出来，那就返回 NaN。

（4）带两个参数时，表示在转换时，包含了进制转换。

代码举例：

```javascript
var a = '110';

var num = parseInt(a, 16); // 【重要】将 a 当成 十六进制 来看待，转换成 十进制 的 num

console.log(num);
```

打印结果：

```
272
```

## 三、转换为 Boolean

### 转换结果列举【重要】

其他的数据类型都可以转换为 Boolean 类型。无论是隐式转换，还是显示转换，转换结果都是一样的。有下面几种情况：

（1）情况一：数字 --> 布尔。 0 和 NaN的转换结果 false，其余的都是 true。比如 `Boolean(NaN)`的结果是 false。

（2）情况二：字符串 ---> 布尔。空串的转换结果是false，其余的都是 true。全是空格的字符串，转换结果也是 true。字符串`'0'`的转换结果也是 true。

（3）情况三：null 和 undefined 都会转换为 false。

（4）情况四：引用数据类型会转换为 true。注意，空数组`[]`和空对象`{}`，**转换结果也是 true**。

**重中之重来了：**

转换为 Boolean 的上面这几种情况，**极其重要**，开发中会频繁用到。比如说，我们在项目开发中，经常需要对一些**非布尔值**做逻辑判断，符合条件后，才做下一步的事情。这个逻辑判断就是依据上面的四种情况。

举例：（接口返回的内容不为空，前端才做进一步的事情）

```js
const result1 = '';
const result2 = { a: 'data1', b: 'data2' };

if (result1) {
    console.log('因为 result1的内容为空，所以代码进不了这里');
}

if (result2 && result2.a) {
    // 接口返回了 result2，且 result2.a 里面有值，前端才做进一步的事情
    console.log('代码能进来，前端继续在这里干活儿');
}
```

这里再次强调一下，空数组`[]`和空对象`{}`转换为 Boolean 值时，转换结果为 true。

### 1. 隐式类型转换：逻辑运算

当非 Boolean 类型的数值和 Boolean 类型的数值做比较时，会先把前者**临时**进行隐式转换为 Boolean 类型，然后再做比较；且不会改变前者的数据类型。举例如下：

```js
const a = 1;

console.log(a == true); // 打印结果：true
console.log(typeof a); // 打印结果：number。可见，上面一行代码里，a 做了隐式类型转换，但是 a 的数据类型并没有发生变化，仍然是 Number 类型

console.log(0 == true); // 打印结果：false
```

### 2. 使用 `!!`

使用 `!!`可以显式转换为 Boolean 类型。比如 `!!3`的结果是 true。

### 3. 使用  Boolean()函数

使用 Boolean()函数可以显式转换为 Boolean 类型。

## 数字的进制

-   16 进制的数字，以`0x`开头

-   8 进制的数字，以`0`开头

-   2 进制的数字，`0b`开头（不是所有的浏览器都支持：chrome 和火狐支持，IE 不支持）

比如`070`这个字符串，如果我调用 parseInt()转成数字时，有些浏览器会当成 8 进制解析，有些会当成 10 进制解析。

所以，比较建议的做法是：可以在 parseInt()中传递第二个参数，来指定当前数字的进制。例如：

```javascript
var a = '070';

a = parseInt(a, 8); //将 070 当成八进制来看待，转换结果为十进制。
console.log(a); // 打印结果：56。这个地方要好好理解。
```

## 隐式类型转换

重点：**隐式类型转换，内部调用的都是显式类型的方法**。

常见的隐式类型转换，包括下面这几种：

- isNaN() 函数

- 运算符：加号 `+`
- 运算符：`-`、`*`、`/`、`%`
- 运算符：正号/负号 +a`、`-a`
- 自增/自减运算符：`++`、`—-`


```javascript
console.log(isNaN('123')); // 返回结果：false。

console.log(isNaN(null)); // 返回结果：false

console.log(isNaN('abc')); // 返回结果：true。因为 Number('abc') 的返回结果是 NaN

console.log(isNaN(undefined)); // 返回结果：true

console.log(isNaN(NaN)); // 返回结果：true
```
