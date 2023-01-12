## string

[String Tutorial](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

常用方法：
### slice()

语法：

```javascript
新字符串 = str.slice(开始索引, 结束索引); //两个参数都是索引值。包左不包右。
```

从字符串中截取指定的内容。不会修改原字符串，而是将截取到的内容返回。

**注意**：上面的参数，包左不包右。参数举例如下：

- `(2, 5)` 截取时，包左不包右。

- `(2)` 表示**从指定的索引位置开始，截取到最后**。

- `(-3)` 表示从倒数第三个开始，截取到最后。

- `(1, -1)` 表示从第一个截取到倒数第一个。

- `(5, 2)` 表示前面的大，后面的小，返回值为空。

### substring()

语法：

```javascript
新字符串 = str.substring(开始索引, 结束索引); //两个参数都是索引值。包左不包右。
```

从字符串中截取指定的内容。和`slice()`类似。

`substring()`和`slice()`是类似的。但不同之处在于：

- `substring()`不能接受负值作为参数。如果传递了一个**负值**，则默认使用 0。

- `substring()`还会自动调整参数的位置，如果第二个参数小于第一个，则自动交换。比如说， `substring(1, 0)`相当于截取的是第一个字符。

### substr()

语法：

```javascript
字符串 = str.substr(开始索引, 截取的长度);
```

解释：从字符串中截取指定的内容。不会修改原字符串，而是将截取到的内容返回。

注意，这个方法的第二个参数**截取的长度**，不是结束索引。

参数举例：

- `(2,4)` 从索引值为 2 的字符开始，截取 4 个字符。

- `(1)` 从指定位置开始，截取到最后。

- `(-3)` 从倒数第几个开始，截取到最后。

**TIPS**：ECMAscript 没有对 `substr()` 方法进行标准化，因此不建议使用它。

### String.fromCharCode()
[Tutorial](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/fromCharCode)

`String.fromCharCode()`：根据字符的 Unicode 编码获取字符。

代码举例：

```javascript
var result1 = String.fromCharCode(72);
var result2 = String.fromCharCode(20013);

console.log(result1); // 打印结果：H
console.log(result2); // 打印结果：中

console.log(String.fromCharCode(72,20013));

```

### concat()

和 `+` 效果一样，不在赘述。

### split()

解释：通过指定的分隔符，将一个字符串拆分成一个**数组**。不会改变原字符串。

备注：`split()`这个方法在实际开发中用得非常多。


```javascript
var str = 'zhan,qian,sun,li'; // 用逗号隔开的字符串
var array = str.split(','); // 将字符串 str 拆分成数组，通过逗号来拆分

console.log(array); // 打印结果是数组：Array ["zhan", "qian", "sun", "li"]
```

**试试将 array 的元素逐个输出？**

### replace()

将字符串中的指定内容，替换为新的内容并返回。不会修改原字符串。

注意：这个方法，默认只会替换第一个被匹配到的字符。如果要全局替换，需要使用正则。


```javascript
//replace()方法：替换
var str2 = 'Today is fine day,today is fine day !';
console.log(str2);

console.log(str2.replace('today', 'tomorrow')); //只能替换一个today
console.log(str2.replace(/today/gi, 'tomorrow')); //这里用到了正则，才能替换所有的today
```

**自己试试**

### repeat(

将字符串重复指定的次数。会返回新的值，不会修改原字符串。

```js
const name = 'ethan';

console.log(name.repeat(2)); // 打印内容：ethanethan
```

### trim()

去除字符串前后的空白

```javascript
//去除字符串前后的空格，trim();
let str = '   a   b   c   ';
console.log(str);
console.log(str.length);

console.log(str.trim());
console.log(str.trim().length);
```

**自己试试**

### toLowerCase() toUpperCase()

大小写转换

### startWiths()

判断一个字符串是否以另外一个字符串开始，返回值为 `true` 或者 `false`

```javascript
const str1 = 'Saturday night plans';

console.log(str1.startsWith('Sat'));
// expected output: true

console.log(str1.startsWith('Sat', 3));
// expected output: false
```

### endWiths()

判断一个字符串是否以另外一个字符串结尾，返回值为 `true` 或者 `false`

```javascript
const str1 = 'Cats are the best!';

console.log(str1.endsWith('best!'));
// expected output: true

console.log(str1.endsWith('best', 17));
// expected output: true

const str2 = 'Is this a question?';

console.log(str2.endsWith('question'));
// expected output: false
```

## Number
### isInteger()

返回值为 `true` 或者 `false` 判断是否是整数。

### toFixed()

小数点后面保留多少位，将数字的小数点后面保留 X 位小数（四舍五入），并返回。不会改变原数字。注意，**返回结果是字符串**。

### parseInt()

将传入的 `string` 转换为 整数。

### parseFloat()

将传入的 `string` 转换为 浮点数。

## Math
| 方法              | 描述                                       | 备注              |
| :---------------- | :----------------------------------------- | :---------------- |
| Math.PI           | 圆周率                                     | Math对象的属性    |
| Math.abs()        | **返回绝对值**                             |                   |
| Math.random()     | 生成0-1之间的**随机浮点数**                | 取值范围是 [0，1) |
| Math.floor()      | **向下取整**（往小取值）                   |                   |
| Math.ceil()       | **向上取整**（往大取值）                   |                   |
| Math.round()      | 四舍五入取整（正数四舍五入，负数五舍六入） |                   |
| Math.max(x, y, z) | 返回多个数中的最大值                       |                   |
| Math.min(x, y, z) | 返回多个数中的最小值                       |                   |
| Math.pow(x,y)     | 乘方：返回 x 的 y 次幂                     |                   |
| Math.sqrt()       | 开方：对一个数进行开方运算                 |                   |

## Date

Date 用来处理日期和时间，实际开发中使用非常频繁

### 创建 Date 对象

[Date Tutorial](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

- 构造函数 
  - 写法一：如果Date()不写参数，就返回当前时间对象
  - 写法二：如果Date()里面写参数，就返回括号里输入的时间对象

### 常用方法

Date对象 有如下方法，可以获取日期和时间的**指定部分**：

| 方法名            | 含义              | 备注                 |
| ----------------- | ----------------- | -------------------- |
| getFullYear()     | 获取年份          |                      |
| getMonth()        | **获取月： 0-11** | 0代表一月            |
| getDate()         | **获取日：1-31**  | 获取的是几号         |
| getDay()          | **获取星期：0-6** | 0代表周日，1代表周一 |
| getHours()        | 获取小时：0-23    |                      |
| getMinutes()      | 获取分钟：0-59    |                      |
| getSeconds()      | 获取秒：0-59      |                      |
| getMilliseconds() | 获取毫秒          | 1s = 1000ms          |



### 格式化
```
const date = new Date("2020-05-12T23:50:21.817Z");
date.toString()               // Tue May 12 2020 18:50:21 GMT-0500 (Central Daylight Time)
date.toDateString()           // Tue May 12 2020
date.toTimeString()           // 18:50:21 GMT-0500 (Central Daylight Time)
date.toISOString()            // 2020-05-12T23:50:21.817Z
date.toUTCString()            // Tue, 12 May 2020 23:50:21 GMT
date.toGMTString()            // Tue, 12 May 2020 23:50:21 GMT
date.toJSON()                 // 2020-05-12T23:50:21.817Z
date.toLocaleString()         // 5/12/2020, 6:50:21 PM
date.toLocaleDateString()     // 5/12/2020
date.toLocaleTimeString()     // 6:50:21 PM

```

**验证下上面的方法是否有错误**

### 时间戳

**时间戳**：指的是从格林威治标准时间的`1970年1月1日，0时0分0秒`到当前日期所花费的**毫秒数**（1秒 = 1000毫秒）。

计算机底层在保存时间时，使用的都是时间戳。时间戳的存在，就是为了**统一**时间的单位。

我们经常会利用时间戳来计算时间，因为它更精确。而且，在实战开发中，接口返回给前端的日期数据，都是以时间戳的形式。

### getTime()：获取时间戳

`getTime()`  获取日期对象的**时间戳**（单位：毫秒）。这个方法在实战开发中，用得比较多。


```js
const timestamp1 = +new Date();
console.log(timestamp1);

const timestamp2 = new Date().getTime();
console.log(timestamp2);

const timestamp3 = new Date().valueOf();
console.log(timestamp3);

const timestamp4 = new Date() * 1;
console.log(timestamp4);

const timestamp5 = Number(new Date());
console.log(timestamp5);

```

**判断上面的写法是否正确**

### Date.now()

 获取当前的时间戳

### JS日期格式化转换方法

**自己试试如何输出 `yyyy-MM-dd HH:mm:ss` 格式的字符串**



**自己试试没有例子的方法**