
## 函数的介绍

函数：就是一些功能或语句的**封装**。在需要的时候，通过**调用**的形式，执行这些语句。

Tips：

- **函数也是一个对象**

- 使用`typeof`检查一个函数对象时，会返回 function

**函数的作用**：

- 一次定义，多次调用。

- 简化代码，可读性更强，让编程模块化。高内聚、低耦合。

> 实际编码过程中，会要求尽可能的剥离为函数。

来看个例子：

```javascript
console.log("你好");
sayHello();	// 调用函数
sayHello();	// 再调用一次函数

// 定义函数
function sayHello(){
	console.log("欢迎");
	console.log("welcome");
}
```

## 函数的定义/声明

使用`function`关键字定义函数。

### 函数声明（命名函数）

使用`函数声明`来创建一个函数。语法：

```javascript
function 函数名([形参1,形参2...形参N]){  // 备注：语法中的中括号，表示“可选”
	// 函数体语句
}
```

举例：

```javascript
function sum(a, b){
	return a+b;
}
```

解释如下：

- 函数名：命名规定和变量的命名规定一样，必须符合JS标识符的命名规则。只能是字母、数字、下划线、美元符号，不能以数字开头。

- 圆括号里，是形参列表，可选。即使没有形参，也必须书写圆括号。

- 大括号里，是函数体语句。

### 函数表达式（匿名函数）

使用`函数表达式`来创建一个函数。语法：

```javascript
const 变量名  = function([形参1,形参2...形参N]){
	语句....
}
```

举例：

```javascript
const fun2 = function() {
	console.log("我是匿名函数中封装的代码");
};
```

解释如下：

- 上面的 fun2 是变量名，不是函数名。
- 函数表达式的声明方式跟声明变量类似，只不过变量里存的是值，而函数表达式里存的是函数。
- 函数表达式也可以传递参数。

从函数表达式的举例中可以看出：所谓的“函数表达式”，其实就是将匿名函数赋值给一个变量。因为，一个匿名函数终究还是要给它一个接收对象，进而方便地调用这个函数。

### 使用构造函数 new Function()

使用构造函数`new Function()`来创建一个对象。这种方式几乎不用。

原因如下：
- 不方便书写：写法过于啰嗦和麻烦。
- 执行效率较低：首先需要把字符串转换为 js 代码，然后再执行。

语法：

```javascript
const 变量名/函数名  = new Function('形参1', '形参2', '函数体');
```


### 小结

1、**所有的函数，都是 `Fuction` 的“实例”**（或者说是“实例对象”）。函数本质上都是通过 new Function 得到的。

2、函数既然是实例对象，那么，**函数也属于“对象”**。还可以通过如下特征，来佐证函数属于对象：

（1）我们直接打印某一个函数，比如 `console.log(fun2)`，发现它的里面有`__proto__`。（这个是属于原型的知识，后续再讲）

（2）我们还可以打印 `console.log(fun2 instanceof Object)`，发现打印结果为 `true`。这说明 fun2 函数就是属于 Object。

## 函数的调用

### 普通函数的调用

函数调用的语法：

```javascript
// 写法1（最常用）
函数名();
// 写法2
函数名.call();
```


代码举例：

```javascript
function fn1() {
	console.log('我是函数体里面的内容1');
}

function fn2() {
	console.log('我是函数体里面的内容2');
}

fn1(); // 调用函数
fn2.call(); // 调用函数
```

### 通过对象的方法来调用

```javascript
var obj = {
	a: 'Ethan',
	fn2: function() {
		console.log('Stay Hungry Stay Foolish.');
	},
};

obj.fn2(); // 调用函数
```

如果一个函数是作为一个对象的属性保存，那么，我们称这个函数是这个对象的**方法**。

### 立即执行函数（IIFE）

代码举例：

```javascript
(function() {
	console.log('我是立即执行函数');
})();

```

立即执行函数在定义后，会自动调用，且只执行一次. 


### 通过构造函数来调用（几乎不使用）

代码举例：

```javascript
function Fun3() {
	console.log('Stay Hungry Stay Foolish.');
}

new Fun3();
```

### 绑定事件函数

代码举例：

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
    </head>
    <body>
        <div id="btn">我是按钮，请点击我</div>

        <script>
            var btn = document.getElementById('btn');
            //2.绑定事件
            btn.onclick = function() {
                console.log('点击按钮后，要做的事情');
            };
        </script>
    </body>
</html>

```

### 定时器函数

代码举例：（每间隔一秒，将 数字 加1）

```javascript
    let num = 1;
   setInterval(function () {
       num ++;
       console.log(num);
   }, 1000);
```

`setInterval` 是定时器。 内置方法。

## 函数的参数：形参和实参

### 定义

函数的参数包括形参和实参。形参是函数内的一些**待定值**。在调用函数时，需传入这些参数的具体值（即实参）。

简单的理解是： 

- 形参是名字， 实参是真实的值。
- 声明形参相当于在函数内部声明了变量，但并不赋值。也可以说，**形参的默认值是 undefined**。

可以在函数的`()`中指定一个或多个参数，也可以不指定参数。多个参数之间用英文逗号隔开。

举例：

```js
// a, b 是形参，表示待定值
function add(a, b) {
	const sum = a + b;
	console.log(sum);
}

// 1, 2 是实参，表示传入的具体值。调用函数时，传入实参
add(1, 2);
```


### 形参和实参的个数

实际参数和形式参数的个数，可以不同。调用函数时，解析器不会检查实参的数量。

- 如果实参个数 > 形参个数，则末尾的实参是多余的，不会被赋值，因为没有形参能接收它。
- 如果实参个数 < 形参个数，则末尾的形参是多余的，值是 undefined，因为它没有接收到实参。（undefined参与运算时，表达式的运算结果为NaN）

> 通常我们是建议，形参和实参一一对应，即有多少形参，在实际调用时就传多少实参。

代码举例：

```javascript
	function sum(a, b) {
		console.log(a + b);
	}

	sum(1, 2);
	sum(1, 2, 3);
	sum(1);
```

打印结果：

```
3
3
NaN
```

### 实参的数据类型

函数的实参可以是任意的数据类型。调用函数时，解析器不会检查实参类型，所以要注意，是否有可能会接收到非法的参数，如果有可能则需要对参数进行类型检查。

## 函数的返回值

### return 关键字

函数体内可以没有返回值，也可以根据需要加返回值。语法格式：`return 函数的返回值`。

- return 只能返回一个值。如果用逗号隔开多个值，则以最后一个为准
- 返回值可以是任意的数据类型，可以是对象，也可以是函数
- 如果函数中不写 return 或者 return之后不跟任何值，则返回undefined
- return 会结束当前的函数体内的代码，退出当前函数。

举例：

```javascript
console.log(sum(3, 4)); // 将函数的返回值打印出来

//函数：求和
function sum(a, b) {
	return a + b;
}
```

## 函数名、函数体和函数加载问题

```javascript
//定义fn方法
function fn(){
	alert(1)
};

console.log(fn) == console.log(function fn(){alert(1)});
```

> **思考一下** 试试上面的输出， 你能得出什么信息， 为什么会这样

**函数的加载问题**：JS加载的时候，只加载函数名，不加载函数体。所以如果想使用内部的成员变量，需要调用函数。

### fn()  和 fn 的区别【重要】

- `fn()`：调用函数。调用之后，还获取了函数的返回值。

- `fn`：函数对象。相当于直接获取了整个函数对象。


## 方法

函数也可以成为对象的属性。**如果一个函数是作为一个对象的属性保存，那么，我们称这个函数是这个对象的方法**。

调用这个函数就说调用对象的方法（method）。函数和方法，它只是名称上的区别，并没有其他的区别。

## 类数组对象 arguments

> 这部分，初学者知道就行，不用深入。

在调用函数时，浏览器每次都会传递进两个隐含的参数：

- 1.函数的上下文对象 this
- 2.**封装实参的对象** arguments

### 定义

arguments 存储的是它接收到的**实参列表**。所有函数都内置了一个 arguments 对象，（只有函数才有arguments）。

具体来说，在调用函数时，我们所传递的实参都会在 arguments 中保存。**arguments 代表的是所有实参**。

arguments 的展示形式是一个**伪数组**。有以下特点：

- 可以进行遍历；具有数组的 length 属性，可以获取长度。
- 可以通过索引（从0开始计数）存储数据、获取和操作数据。比如，我们可以通过索引访问某个实参。
- 不能调用数组的方法。比如push()、pop() 等方法都没有。

### arguments.length 返回函数实参的个数

arguments.length 可以用来获取**实参的个数**。

### arguments.callee 返回正在执行的函数

arguments 里边有一个属性叫做 callee，这个属性对应一个函数对象，就是当前正在指向的函数对象。

```javascript
function fun() {
    console.log(arguments.callee == fun); // 打印结果为true
}

fun('hello');
```

在使用函数**递归**调用时，推荐使用 arguments.callee 代替函数名本身。

### arguments 可以修改元素

arguments 还可以**修改元素，但不能改变数组的长度**。

### 使用场景举例

当我们不确定有多少个参数传递的时候，可以用 **arguments** 来获取。 实际代码中，应该尽量避免这种参数数量不确定的情况。


