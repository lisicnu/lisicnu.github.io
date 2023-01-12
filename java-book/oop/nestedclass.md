## Nested Class
可以在一个类的内部定义另一个类，这种类称为嵌套类（`nested classes`），它有两种类型：静态嵌套类和非静态嵌套类。静态嵌套类使用很少，最重要的是非静态嵌套类，也被称作为内部类. e.g.（`inner class`）
  ```
  public class Person {
    private int age;
    private Working work;
    class Working {
        void printAge(){
          System.out.print(age);
        }
    }
  }
  ```


## 好处
- 嵌套类可以访问外部类的所有数据成员和方法，即使它是私有的。
- 提高可读性和可维护性：因为如果一个类只对另外一个类可用，那么将它们放在一起，这更便于理解和维护。
- 提高封装性：给定两个类A和B，如果需要访问A类中的私有成员，则可以将B类封装在A类中，这样不仅可以使得B类可以访问A类中的私有成员，并且可以在外部隐藏B类本身。
- 减少代码的编写量。

## 使用场景
如需要设置 `listener` 的时候。



## demo

### 静态嵌套类
```
public class StaticTest {
    private static String name = "javaJohn";
    private String id = "X001";

    static class Person {
        private String address = "swjtu,chenDu,China";
        public String mail = "josserchai@yahoo.com";//内部类公有成员

        public void display() {
            //System.out.println(id);//不能直接访问外部类的非静态成员
            System.out.println(name);//只能直接访问外部类的静态成员
            System.out.println("Inner " + address);//访问本内部类成员。
        }
    }

    public void printInfo() {
        Person person = new Person();
        person.display();
        // System.out.println(mail);//不可访问
        // System.out.println(address);//不可访问
        // System.out.println(person.address);//可以访问内部类的私有成员
        // System.out.println(person.mail);//可以访问内部类的公有成员
    }

    public static void main(String[] args) {
        StaticTest staticTest = new StaticTest();
        staticTest.printInfo();
    }
}

```

### 普通内部类 
```
public class Outer {
    int outer_x = 100;

    class Inner {
        public int y = 10;
        private int z = 9;
        int m = 5;

        public void display() {
            System.out.println("display outer_x:" + outer_x);
        }

        private void display2() {
            System.out.println("display outer_x:" + outer_x);
        }
    }

    void test() {
        Inner inner = new Inner();
        inner.display();
        inner.display2();
        // System.out.println("Inner y:" + y);//不能访问内部内变量
        System.out.println("Inner y:" + inner.y);//可以访问
        System.out.println("Inner z:" + inner.z);//可以访问
        System.out.println("Inner m:" + inner.m);//可以访问
        InnerTwo innerTwo = new InnerTwo();
        innerTwo.show();
    }

    class InnerTwo {
        Inner innerx = new Inner();

        public void show() {
            // System.out.println(y);//不可访问Innter的y成员
            // System.out.println(Inner.y);//不可直接访问Inner的任何成员和方法
            innerx.display();//可以访问
            innerx.display2();//可以访问
            System.out.println(innerx.y);//可以访问
            System.out.println(innerx.z);//可以访问
            System.out.println(innerx.m);//可以访问
        }
    }

    public static void main(String args[]) {
        Outer outer = new Outer();
        outer.test();
    }
}
```

## 方法内部类
- 使用比较少，不做讲解


## 匿名内部类
- 使用频率非常高
```
    new Thread(new Runnable() {
        @Override
        public void run() {
            System.out.println("..");     
        }
    }).start();
```
在支持 `lambda` 的java 版本后 可以使用 `lambda` 实现。
```
    new Thread(() -> System.out.println("..")).start();
```
