## 面向对象

面向对象编程，英文是Object-Oriented Programming，简称OOP。
面向对象编程，是一种通过对象的方式，把现实世界映射到计算机模型的一种编程方法。  
举个例子： 
我们定义了“人”这种抽象概念，而具体的人则是“小明”、“小红”、“小军”等一个个具体的人。所以，“人”可以定义为一个类（class），而具体的人则是实例（instance）：  

| 现实世界 | 计算机模型  |          Java代码          |
| :------- | :---------: | :------------------------: |
| 人	类    |   / class   |      class Person { }      |
| 小明     | 实例 / ming | Person ming = new Person() |
| 小红     | 实例 / hong | Person hong = new Person() |
| 小军     | 实例 / jun  | Person jun = new Person()  |

定义 `class` 在 Java 中，创建一个 `class` ，名字为 `Person` 
```
class Person {
    public String name;
    public int age;
}
```
一个`class`可以包含多个字段`field`，字段用来描述一个类的特征。上面的`Person`类，我们定义了两个字段，一个是`String`类型的字段，命名为`name`，一个是`int`类型的字段，命名为`age`。因此，通过`class`，把一组数据汇集到一个对象上，实现了数据封装。  

创建实例
```
Person ming = new Person();
ming.name = "Xiao Ming"; // 赋值操作
ming.age = 12; // 赋值操作
System.out.println(ming.name); // 访问属性

Person hong = new Person();
hong.name = "Xiao Hong";
hong.age = 15;
```
