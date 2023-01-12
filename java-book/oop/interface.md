## Interface
在抽象类中，抽象方法本质上是定义接口规范：即规定高层类的接口，从而保证所有子类都有相同的接口实现，这样，多态就能发挥出威力。

如果一个抽象类没有字段，所有方法全部都是抽象方法：
```
abstract class Person {
    public abstract void run();
    public abstract String getName();
}
```
就可以把该抽象类改写为接口：`interface`。
```
interface Person {
    void run();
    String getName();
}
```

当一个具体的`class`去实现一个`interface`时，需要使用`implements`关键字。e.g.：
```
class Student implements Person {
    private String name;

    public Student(String name) {
        this.name = name;
    }

    @Override
    public void run() {
        System.out.println(this.name + " run");
    }

    @Override
    public String getName() {
        return this.name;
    }
}
```

- `interface`可以继承其他的 `interface`
- 单个 `class` 可以 实现多个 `interface`