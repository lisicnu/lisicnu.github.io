## Static Filed

```
class Person {
    public static int number;
}
```

## Static Method

```
class Person {
    public static int number = 0;
    public static int getNumber(){
        return number;
    }
}
```

- 实例可以访问静态方法及静态变量。 静态变量，全局仅此一份。

## Q&A
- 自己动手测试，接口类是否可以有静态变量或者静态方法？


### Tips
- 静态方法经常用于工具类。例如：
```
Arrays.sort()
Math.random()
```
- 静态方法也经常用于辅助方法。注意到Java程序的入口`main()`也是静态方法。