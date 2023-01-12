# Method
- `Method` 是一些逻辑的封装。
- `Method` 单个 `class` 可以有多个 `Method`。
- 每个方法有自己的访问权限， `public`, `private`等。

一个`class`可以包含多个`field`，例如，我们给`Person`类就定义了两个`field`：
```Java
class Person {
    public String name;
    public int age;
}
```
但是，直接把`field`用`public`暴露给外部可能会破坏封装性。比如，代码可以这样写：
```
Person ming = new Person();
ming.name = "Xiao Ming";
ming.age = -99; // age设置为负数 
```
显然，直接操作`field`，容易造成逻辑混乱。为了避免外部代码直接去访问`field`，我们可以用`private`修饰`field`，拒绝外部访问：
```
class Person {
    private String name;
    private int age;
}
```

Q: 试试`private`修饰的`field`有什么效果？
此时 我们就可以使用 method 进行封装。
```
class Person {
    private String name;
    private int age;
    public int getAge() {
        return age;
    }
    public void setAge(int age){
        this.age = age;
    }
}
```
