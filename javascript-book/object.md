
## 简介

### 什么是对象

在 JavaScript 中，对象是一组**无序**的相关属性和方法的集合。

**对象的作用是：封装信息**。比如 Student 类里可以封装学生的姓名、年龄、成绩等。

对象具有**特征**（属性）和**行为**（方法）。

### 为什么需要对象

保存一个值时，可以使用**变量**，保存多个值（一组值）时，可以使用**数组**。

比如，如果要保存一个人的信息，通过数组的方式可以这样保存：

```javascript
const arr = ['王二', 35, '男', '180'];
```

上面这种表达方式比较乱。而如果用**对象**来表达，**结构会更清晰**。如下：

```javascript
const person = {
    name: 'Ethan',
    age: 29,
    sex: '男',
    favor: ['阅读', '羽毛球'],
};
```

由此可见，对象里面的属性均是**键值对（key: value）**，表示属性和值的映射关系：

-   键/属性：属性名。

-   值：属性值，可以是任意类型的值（数字类型、字符串类型、布尔类型，函数类型等）。

### 自定义对象

语法：

```js
const obj = {
    key: value,
    key: value,
    key: value,
};
```

key 和 value 之间用冒号分隔，每组 key:vaue 之间用逗号分隔，最后一对 key:value 的末尾可以写逗号，也可以不写逗号。

问：对象的属性名是否需要加引号？

答：如果属性名不符合 JS 标识符的命名规范，则需要用引号包裹。比如：

```js
const person = {
    'my-name': 'Ethan',
    sex : 'Male'
};

```

### Tips


对象的属性可以是任意的数据类型，如：
- 函数
- 对象

example：

```javascript
//创建对象 obj1
var obj1 = new Object();
obj1.test = undefined;

//创建对象 obj2
var obj2 = new Object();
obj2.name = 'Ethan';
obj2.sayName = function () {
    console.log('call function say: Ethan');
};

//将整个 obj2 对象，设置为 obj1 的属性
obj1.test = obj2;

console.log(obj1.test.name);

// 比如下面两行代码的区别。
console.log(obj1.test.sayName);
console.log(obj1.test.sayName());

```

## 对象和数据类型之间的关系

### 数据类型分类

-   **基本数据类型（值类型）**：String 字符串、Number 数值、Boolean 布尔值、Null 空值、Undefined 未定义。

-   **引用数据类型（引用类型）**：Object 对象。

**基本数据类型**：

基本数据类型的值直接保存在**栈内存**中，值与值之间是独立存在，修改一个变量不会影响其他的变量。

**对象**：

只要不是那五种基本数据类型，就全都是对象。对象是保存到**堆内存**中的，每创建一个新的对象，就会在堆内存中开辟出一个新的空间。变量保存的是对象的内存地址（对象的引用）。换而言之，对象的值是保存在**堆内存**中的，而对象的引用（即变量）是保存在**栈内存**中的。

**如果两个变量保存的是同一个对象引用，当一个通过一个变量修改属性时，另一个也会受到影响**。


## 传值和传址的区别

### 传值

代码举例：

```js
let a = 1;
let b = a; // 将 a 赋值给 b
b = 2; // 修改 b 的值
```

上方代码中，当我修改 b 的值之后，a 的值并不会发生改变。这个大家都知道。我们继续往下看。

### 传地址

代码举例：

```javascript
var obj1 = new Object();
obj1.name = '孙悟空';

var obj2 = obj1; // 将 obj1 的地址赋值给 obj2。从此， obj1 和 obj2 指向了同一个堆内存空间

//修改obj2的name属性
obj2.name = '猪八戒';
```

上面的代码中，当我修改 obj2 的 name 属性后，会发现，obj1 的 name 属性也会被修改。因为 obj1 和 obj2 指向的是堆内存中的同一个地址。

对于引用类型的数据，赋值相当于地址拷贝，a、b 指向了同一个堆内存地址。所以改了 b，a 也会变；本质上 a、b 就是一个东西。

如果你打算把引用类型 A 的值赋值给 B，让 A 和 B 相互不受影响的话，可以通过 Object.assign() 来复制对象。效果如下：

```js
var obj1 = { name: '孙悟空' };

// 复制对象：把 obj1 赋值给 obj3。两者之间互不影响
var obj3 = Object.assign({}, obj1);
```