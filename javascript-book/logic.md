
## 代码块

用`{}`包围起来的代码，就是代码块。

在 ES5 语法中，代码块，只具有**分组**的作用，没有其他的用途。代码块中的内容，在外部是完全可见的。举例：

```javascript
{
    var a = 2;
    alert('Ethan');
    console.log('1');
}

console.log('a = ' + a);
```

打印结果：（可以看出，虽然变量 a 是定义在代码块中的，但是在外部依然可以访问）

```
1
a = 2
```

## 流程控制语句

在一个程序执行的过程中，各条语句的执行顺序对程序的结果是有直接影响的。所以，我们必须清楚每条语句的执行流程。而且，很多时候我们要通过控制语句的执行顺序来实现我们想要的业务逻辑和功能。

### 流程控制语句分类

-   顺序结构

-   选择结构：if 语句、switch 语句

-   循环结构：while 语句、for 语句

## 顺序结构

按照代码的先后顺序，依次执行。结构图如下：

![](/images/20181227_1200.png)

## if 语句

if 语句有以下三种形式。

### if 语句的三种形式

形式1：（条件成立才执行。如果条件不成立，那就什么都不做）

```javascript
if (条件表达式) {
    // 条件为真时，做的事情
}
```

对于非布尔类型的数据，会先转换成布尔类型再判断。下同。

形式 2：

```javascript
if (条件表达式) {
    // 条件为真时，做的事情
} else {
    // 条件为假时，做的事情
}
```

形式3：（多分支的 if 语句）

```javascript
if (条件表达式1) {
    // 条件1为真时，做的事情
} else if (条件表达式2) {
    // 条件1不满足，条件2满足时，做的事情
} else if (条件表达式3) {
    // 条件1、2不满足，条件3满足时，做的事情
} else {
    // 条件1、2、3都不满足时，做的事情
}
```

以上所有的语句体中，只执行其中一个。

### 试一试

```
根据BMI（身体质量指数）显示一个人的体型。
BMI指数，就是体重、身高的一个计算公式。公式是：
BMI =体重÷身高的平方

过轻：低于18.5
正常：18.5-24.99999999
过重：25-27.9999999
肥胖：28-32
非常肥胖, 高于32

用JavaScript开发一个程序，让用户先输入自己的体重，然后输入自己的身高（弹出两次prompt框）。
计算它的BMI，根据上表，弹出用户的身体情况。比如“过轻” 、 “正常” 、“过重” 、 “肥胖” 、“非常肥胖”。
```


<details>
<summary>答案</summary>

```javascript
//第一步，输入身高和体重
const height = parseFloat(prompt('请输入身高，单位是米'));
const weight = parseFloat(prompt('请输入体重，单位是公斤'));
//第二步，计算BMI指数
const BMI = weight / Math.pow(height, 2);
//第三步，if语句来判断
if (BMI > 32) {
    alert('非常肥胖');
} else if (BMI >= 28) {
    alert('肥胖');
} else if (BMI >= 25) {
    alert('过重');
} else if (BMI >= 18.5) {
    alert('正常');
} else {
    alert('偏瘦');
}
```

</details>


## switch 语句

switch 语句也叫条件分支语句。

### 语法格式

```javascript
switch(表达式) {
	case 值1：
		语句体1;
		break;

	case 值2：
		语句体2;
		break;

	...
	...

	default：
		语句体 n+1;
		break;
}
```

### switch 语句的执行流程

流程图如下：

![](/images/20190815_1501.png)

执行流程如下：

（1）首先，计算出表达式的值，和各个 case 依次比较，一旦有对应的值，就会执行相应的语句，在执行的过程中，遇到 break 就会结束。

（2）然后，如果所有的 case 都和表达式的值不匹配，就会执行 default 语句体部分。

### 注意点

1、switch 后面的括号里可以是变量、常量、表达式， 通常是一个**变量**（一般做法是：先把表达式存放到变量中）。

case 后面的值可以是变量、常量、表达式。

2、**case的判断逻辑是`===`，不是`==`**。因此，字符串`'6'`和 数字 `6` 是不一样的。

举例 1：

```js
let msg = 'notice';

switch (msg) {
    case 'notice':
        console.log('提示');
        break;
    case 'warning':
        console.log('警告');
        break;
    case 'error':
        console.log('错误');
        break;
    default:
        console.log('默认文案');
        break;
}
```

举例 2：（case 后面的是表达式）

```js
let age = 28;

switch (true) {
    case age < 18:
        console.log('未成年人');
        break;
    case age >= 18 && age <= 65:
        console.log('还能干活儿');
        break;
    case age > 65:
        console.log('该退休了');
        break;
    default:
        console.log('默认文案');
        break;
}
```

上方代码解释：由于 switch 里的值是 true，所以，在众多的 case 语句中，会去匹配第一个符合 `case true`的语句，然后命中这条语句。

### case 穿透

switch 语句中的`break`可以省略，但一般不建议（对于新手而言）。否则结果可能不是你想要的，会出现一个现象：**case 穿透**。

当然，如果你能利用好 case 穿透，会让代码写得十分优雅。

**举例 1**：（case 穿透的情况）

```javascript
const num = 4;

//switch判断语句
switch (num) {
    case 1:
        console.log('星期一');
        break;
    case 2:
        console.log('星期二');
        break;
    case 3:
        console.log('星期三');
        break;
    case 4:
        console.log('星期四');
    //break;
    case 5:
        console.log('星期五');
    //break;
    case 6:
        console.log('星期六');
        break;
    case 7:
        console.log('星期日');
        break;
    default:
        console.log('你输入的数据有误');
        break;
}
```

上方代码的运行结果，可能会令你感到意外：

```
星期四
星期五
星期六
```

上方代码的解释：因为在 case 4 和 case 5 中都没有 break，那语句走到 case 6 的 break 才会停止。

## 动手练一练
我们实战开发中，经常需要根据接口的返回码 retCode ，来让前端做不同的展示。

### 改写如下代码

```javascript
let retCode = 1003; // 返回码 retCode 的值可能有很多种情况

if (retCode == 0) {
    alert('接口联调成功');
} else if (retCode == 101) {
    alert('活动不存在');
} else if (retCode == 103) {
    alert('活动未开始');
} else if (retCode == 104) {
    alert('活动已结束');
} else if (retCode == 1001) {
    alert('参数错误');
} else if (retCode == 1002) {
    alert('接口频率限制');
} else if (retCode == 1003) {
    alert('未登录');
} else if (retCode == 1004) {
    alert('（风控用户）提示 活动太火爆啦~军万马都在挤，请稍后再试');
} else {
    // 其他异常返回码
    alert('系统君失联了，请稍候再试');
}
```

如果你是按照上面的 `if else`的方式来写各种条件判断。这种写法，容易导致**嵌套太深，可读性很差**。

**试试用 switch 改写上面的代码**

<details>

<summary>答案</summary>


```javascript
let retCode = 1003; // 返回码 retCode 的值可能有很多种情况

switch (retCode) {
    case 0:
        alert('接口联调成功');
        break;
    case 101:
        alert('活动不存在');
        break;
    case 103:
        alert('活动未开始');
        break;
    case 104:
        alert('活动已结束');
        break;
    case 1001:
        alert('参数错误');
        break;
    case 1002:
        alert('接口频率限制');
        break;
    case 1003:
        alert('未登录');
        break;
    case 1004:
        alert('（风控用户）提示 活动太火爆啦~军万马都在挤，请稍后再试');
        break;
    // 其他异常返回码
    default:
        alert('系统君失联了，请稍候再试');
        break;
}
```

</details>


### switch 语句的优雅写法：适时地去掉 break

我们先来看看下面这段代码：（不推荐）

```javascript
let day = 2;

switch (day) {
    case 1:
        console.log('work');
        break;
    case 2:
        console.log('work');
        break;
    case 3:
        console.log('relax');
        break;
    case 4:
        console.log('relax');
        break;
    default:
        break;
}
```

上面的代码，咋一看，好像没啥毛病。但你有没有发现，重复代码太多了？

实战开发中，凡是有重复的地方，我们都必须要想办法简化。写代码就是在不断重构的过程。

上面的代码，可以改进如下：（推荐，非常优雅）

```javascript
let day = 2;

switch (day) {
    case 1:
    case 2:
        console.log('work');
        break; // 在这里放一个 break
    case 3:
    case 4:
        console.log('relax');
        break; // 在这里放一个 break
    default:
        break;
}

```


## for 循环

### 语法

语法：

```
for(①初始化表达式; ②条件表达式; ④更新表达式){
	③语句...
}
```

执行流程：

```
①执行初始化表达式，初始化变量（初始化表达式只会执行一次）

②执行条件表达式，判断是否执行循环：
	如果为true，则执行循环③
	如果为false，终止循环

④执行更新表达式，更新表达式执行完毕继续重复②
```

### 试一试

```javascript
for (let i = 1; i < 13; i = i + 4) {
    console.log(i);
}
```

上方代码的遍历步骤：

```
程序一运行，将执行let i = 1;这条语句， 所以i的值是1。
然后程序会验证一下i < 13是否满足，1<13是真，所以执行一次循环体（就是大括号里面的语句）。
执行完循环体之后，会执行i=i+4这条语句，所以i的值，是5。

程序会会验证一下i < 13是否满足，5<13是真，所以执行一次循环体（就是大括号里面的语句）。
执行完循环体之后，会执行i=i+4这条语句，所以i的值，是9。

程序会会验证一下i < 13是否满足，9<13是真，所以执行一次循环体（就是大括号里面的语句）。
执行完循环体之后，会执行i=i+4这条语句，所以i的值，是13。

程序会会验证一下i < 13是否满足，13<13是假，所以不执行循环体了，将退出循环。

最终输出输出结果为：1、5、9
```

## while 循环

### 语法


```javascript
while(条件表达式){
	语句...
}
```

执行流程：

```
while语句在执行时，先对条件表达式进行求值判断：

	如果值为true，则执行循环体：
		循环体执行完毕后，继续对表达式进行判断
		如果为true，则继续执行循环体，以此类推

	如果值为false，则终止循环
```

**如果有必要的话，我们可以使用 break 来终止循环**。

### do...while 循环

语法：

```javascript
do{
	语句...
}while(条件表达式)

```

执行流程：

```
do...while语句在执行时，会先执行循环体：

	循环体执行完毕以后，再对while后的条件表达式进行判断：
		如果结果为true，则继续执行循环体，执行完毕继续判断，以此类推
		如果结果为false，则终止循环

```

### while 循环和 do...while 循环的区别

这两个语句的功能类似，不同的是：

-   while：先判断后执行。只有条件表达式为真，才会执行循环体。
-   do...while：先执行后判断。无论条件表达式是否为真，循环体至少会被执行一次。


## break 和 continue

### break

-   break 可以用来退出 switch 语句或退出**整个**循环语句（循环语句包括 for 循环、while 循环。不包括 if。单独的 if 语句里不能用 break 和 continue，否则会报错）。

-   break 会立即终止离它**最近**的那个循环语句。

-   可以为循环语句创建一个 label，来标识当前的循环（格式：label:循环语句）。使用 break 语句时，可以在 break 后跟着一个 label，这样 break 将会结束指定的循环，而不是最近的。

**举例 1**：通过 break 终止循环语句

```javascript
for (let i = 0; i < 5; i++) {
    console.log('i的值:' + i);
    if (i == 2) {
        break; // 注意，虽然在 if 里 使用了 break，但这里的 break 是服务于外面的 for 循环。
    }
}
```

打印结果：

```
i的值:0
i的值:1
i的值:2
```

**举例 2**：label 的使用

```javascript
outer: for (let i = 0; i < 5; i++) {
    console.log('外层循环 i 的值：' + i);
    for (let j = 0; j < 5; j++) {
        break outer; // 直接跳出outer所在的外层循环（这个outer是我自定义的label）
        console.log('内层循环 j 的值:' + j);
    }
}
```

打印结果：

```
外层循环 i 的值：0
```

### continue

-   continue 只能用于循环语句（包括 for 循环、while 循环，不包括 if。单独的 if 语句里不能用 break 和 continue，否则会报错）。可以用来跳过**当次**循环，继续下一次循环。

-   同样，continue 默认只会离他**最近**的循环起作用。

-   同样，如果需要跳过指定的当次循环，可以使用 label 标签。

举例：

```javascript
for (let i = 0; i < 10; i++) {
    if (i % 2 == 0) {
        continue;
    }
    console.log('i的值:' + i);
}
```

打印结果：

```
i的值:1

i的值:3

i的值:5

i的值:7

i的值:9
```

## 动手练一练

**题目**：打印 1~100 之间的所有质数
