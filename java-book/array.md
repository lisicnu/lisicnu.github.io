## 特性
- 数组所有元素初始化为默认值，整型都是0，浮点型是0.0，布尔型是`false`；
- 数组一旦创建后，大小就不可改变。
- 要访问数组中的某一个元素，需要使用索引。数组索引`从0开始`，例如，5个元素的数组，索引范围是0~4
- 可以修改数组中的某一个元素，使用赋值语句，例如，`ns[1] = 79;`
- 可以用数组变量`.length`获取数组大小

## 创建数组的方式
- 使用`new`操作符来创建数组，语法如下：`arrayRefVar = new dataType[arraySize];`
- `dataType[] arrayRefVar = {value0, value1, ..., valuek};`

## 数组的遍历
```
public class Main {
    public static void main(String[] args) {
        int[] ns = { 1, 4, 9, 16, 25 };
        for (int i=0; i<ns.length; i++) {
            int n = ns[i];
            System.out.println(n);
        }
    }
}
```

## Tips
数组相关的操作， `Arrays`.


## 多维数组
多维数组可以看成是数组的数组，比如二维数组就是一个特殊的一维数组，其每一个元素都是一个一维数组，例如：

```
String[][] strAry = new String[2][];
strAry[0] = new String[2];
strAry[1] = new Strng[2];

strAry[0][0] = "Hello";
strAry[0][1] = "World";

strAry[1][0] = "Hi";
strAry[1][1] = "I'm study java.";
```

