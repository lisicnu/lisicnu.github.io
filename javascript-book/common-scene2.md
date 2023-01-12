## 变量的命名规则（重要）

JS是大小敏感的语言。也就是说 A 和 a 是两个变量。大写字母是可以使用的，比如：

```javascript
var A = 250; //变量1
var a = 888; //变量2
```

我们来整理一下**变量的命名规则**，非常重要。

必须遵守：

-   只能由字母(A-Z、a-z)、数字(0-9)、下划线(\_)、美元符( $ )组成。
-   不能以数字开头。必须以字母(A-Z、a-z)、下划线(\_)或者美元符( $ )开头。变量名中不允许出现空格。尤其注意，变量名中不能出现**中划线**`-`，很多人写了多年代码都不知道这一点，让人大跌眼镜。
-   严格区分大小写（JS 是区分大小写的语言）。
-   不能使用 JS 语言中保留的「关键字」和「保留字」作为变量名。下一篇文章会讲。
-   变量名长度不能超过 255 个字符。

建议遵守：

- 命名要有可读性，方便顾名思义。

- 建议用驼峰命名法。比如 getElementById、getUserInfo、aaaOrBbbAndCcc

**Tips**：

1、不能以数字开头，是为了把数字和字母区分开。 

2、JS底层保存标识符的时候，是采用的 Unicode 编码。所以理论上讲，在遵守命名规则的前提下，utf-8中包含的所有内容都可以作为标识符。

## 标识符

**标识符**：在 JS 中所有的可以由我们**自主命名**的都可以称之为标识符。包括：**变量名、函数名、属性名、参数名**都是属于标识符。

通俗来讲，标识符就是我们写代码时为某些东西起的名字。类似于人出生的时候，起个人名。

**标识符的命名规则**和变量的命令规则是一样的。关于变量的命名规则。

标识符不能使用语言中保留的**关键字**及**保留字**。

## 关键字

**关键字**：被JS赋予了特殊含义的单词。也就是说，关键字是 JS 本身已经使用了的单词，我们不能再用它们充当变量名、函数名等标识符。关键字在开发工具中会显示特殊的颜色。

JS 中的关键字如下：

```bash
if、else、switch、break、case、default、for、in、do、while、

var、let、const、void、function、continue、return、

try、catch、finally、throw、debugger、

this、typeof、instanceof、delete、with、

export、new、class、extends、super、with、yield、import、static、

true、false、null、undefined、NaN
```
## 保留字

**保留字**：实际上就是预留的“关键字”。它们虽然现在还不是关键字，但是未来可能会成为关键字。同样不能用它们当充当变量名、函数名等标识符。

JS 中的保留字如下：

```bash
enum、await

abstract、boolean、byte、char、double、final、float、goto、int、long、native、short、synchronized、transient、volatile、

arguments eval Infinity

# 以下关键字只在严格模式中被当成保留字，在ES6中是属于关键字
implements、interface、package、private、protected、public
```

记住一点：上面提到的所有**关键字**和**保留字**，我们都不要用它们作为变量名或者参数名。不要尝试这些奇怪的做法。
