## Abstract
抽象类，又称虚类。

```
class Person {
    public void run() { … }
}

class Student extends Person {
    @Override
    public void run() { … }
}

class Teacher extends Person {
    @Override
    public void run() { … }
}
```

- `Student` 和 `Teacher` 都实现了 `Person` 的 `run` 方法， 实际上 `run` 方法 对于`Person`来说 没有任何价值， 那么我们是不是可以去掉呢？  **此处需要自己动手尝试**


- 如果父类的方法本身不需要实现任何功能，仅仅是为了定义方法签名，目的是让子类去覆写它，那么，可以把父类的方法声明为抽象方法：
```
class Person {
    public abstract void run();
}
```
- 一个方法声明为`abstract`，表示它是一个抽象方法，本身没有实现任何方法语句。因为这个抽象方法本身是无法执行的，所以，`Person`类也无法被实例化。编译器会告诉我们，无法编译Person类，因为它包含抽象方法。

必须把`Person`类本身也声明为`abstract`，才能正确编译它：
```
abstract class Person {
    public abstract void run();
}
```

## 本质
- 上层定义规范
- 不需要子类就可以实现业务逻辑，且正常编译。
- 具体的业务由子类，调用者不关心。

## Tips
- 抽象类不能被实例化，如果被实例化，就会报错，编译无法通过。只有抽象类的非抽象子类可以创建对象。
- 抽象类中不一定包含抽象方法，但是有抽象方法的类必定是抽象类。
- 抽象类中的抽象方法只是声明，不包含方法体，就是不给出方法的具体实现也就是方法的具体功能。
- 构造方法，静态方法（用 static 修饰的方法）不能声明为抽象方法。
- 抽象类的子类必须给出抽象类中的抽象方法的具体实现，除非该子类也是抽象类。

