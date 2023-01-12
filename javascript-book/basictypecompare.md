
## 基本数据类型不能绑定属性和方法

属性和方法只能添加给对象，不能添加给基本数据类型。
如：
- `string` 无法绑定属性和方法
- `String` 可以帮到属性和方法


### 基本包装类型


### 介绍

我们都知道，js 中的数据类型包括以下几种。

-   基本数据类型：String、Number、Boolean、Null、Undefined

-   引用数据类型：Object

JS 为我们提供了三个**基本包装类**：

-   String()：将基本数据类型字符串，转换为 String 对象。

-   Number()：将基本数据类型的数字，转换为 Number 对象。

-   Boolean()：将基本数据类型的布尔值，转换为 Boolean 对象。

通过上面这这三个包装类，我们可以**将基本数据类型的数据转换为对象**。

代码举例：

```javascript
let str1 = 'Ethan';
let str2 = new String('Ethan');

let num = new Number(3);

let bool = new Boolean(true);

console.log(typeof str1); // 打印结果：string
console.log(typeof str2); // 注意，打印结果：object
```

**需要注意的是**：我们在实际应用中一般不会使用基本数据类型的**对象**。如果使用基本数据类型的对象，在做一些比较时可能会带来一些**不可预期**的结果。

比如说：

```javascript
var boo1 = new Boolean(true);
var boo2 = new Boolean(true);

console.log(boo1 === boo2); // 打印结果竟然是：false
```

再比如说：

```javascript
var boo3 = new Boolean(false);

if (boo3) {
    console.log('Ethan'); // 这行代码竟然执行了
}
```

### 基本包装类型的作用

当我们对一些基本数据类型的值去调用属性和方法时，JS引擎会**临时使用包装类将基本数据类型转换为引用数据类型**（即“隐式类型转换”），这样的话，基本数据类型就有了属性和方法，然后再调用对象的属性和方法；调用完以后，再将其转换为基本数据类型。

举例：

```js
var str = 'Ethan';
console.log(str.length); // 打印结果：5
```

比如，上面的代码，执行顺序是这样的：

```js
// 步骤（1）：把简单数据类型 string 转换为 引用数据类型  String，保存到临时变量中
var temp = new String('Ethan');

// 步骤（2）：把临时变量的值 赋值给 str
str = temp;

//  步骤（3）：销毁临时变量
temp = null;

```

## 在底层，字符串以字符数组的形式保存

在底层，字符串是以字符数组的形式保存的。代码举例：

```javascript
var str = 'Ethan';
console.log(str.length); // 获取字符串的长度
console.log(str[2]); // 获取字符串中的第3个字符（下标为2的字符）
```

上方代码中，`Ethan`这个字符串在底层是以`["E", "t", "h", "a", "n"]`的形式保存的。因此，我们既可以获取字符串的长度，也可以获取指定索引 index 位置的单个字符。这很像数组中的操作。

再比如，String 对象的很多内置方法，也可以直接给字符串用。此时，也是临时将字符串转换为 String 对象，然后再调用内置方法。
