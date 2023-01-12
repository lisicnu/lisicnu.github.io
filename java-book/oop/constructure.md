# Constructure

- 每个类都有默认构造方法
- 如果自定义了构造方法，则默认的构造方法将<font color=red>不会</font>再自动创建。

创建实例的时候，实际上是通过构造方法来初始化实例的。（即 new 之后的代码）, e.g.

```
Person ming = new Person();
ming.setName("小明");
ming.setAge(12);
```

们先来定义一个构造方法，能在创建Person实例的时候，一次性传入name和age，完成初始化.

```
public class Main {
    public static void main(String[] args) {
        Person p = new Person("Xiao Ming", 15);
        System.out.println(p.getName());
        System.out.println(p.getAge());
    }
}

class Person {
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public String getName() {
        return this.name;
    }

    public int getAge() {
        return this.age;
    }
}

```

## Q&A
如果需要同时 存在 默认构造方法和自定义方法 怎么书写？