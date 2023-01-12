
## Override

在继承关系中，子类如果定义了一个与父类方法签名和返回值完全相同的方法，被称为覆写（Override）。如：
```
class Person {
    private String name;
    private int age;

    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
}

class Student extends Person {
    private int score;

    public int getScore() { 
        return score;
    }
    public void setScore(int score) {
        this.score = score;    
    }

    @Override // @Override 关键字非必须
    public void setAge(int age) {
        super.setAge(age);
        System.out.print("overided setAge method.");
    }
}

```

- 如果某个方法不希望被子类 `Override `， 可以使用 `final` 关键字。

## Q&A
- 如果外面调用 Student 的 setAge 方法， 这时是调用的效果是怎么样的？