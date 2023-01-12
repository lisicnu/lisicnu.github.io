## 题目1
- 实现计数功能。要求如下：
   - 新定义一个 `class。` `class` 要求如下：
      - 实现 `private` 方法，`printCounter`, 调用一次之后，实现值 + 1.
         - 如第一次调用输出 1， 则第二次调用输出 2.
            ```
            // 输出内容如下：
                -- inner print counter: xxx
            ```
      - 实现 `public` 方法，`getCounter`, 调用后，返回当前 `counter`的值。  同时并调用 `private` 方法 `printCounter`
      - 定义 静态变量 `String` `sRoomCode`;
      - 实现静态方法 `getRoomCode()`, 返回值 `sRoomCode`，
        - 方法的实现要求如下：
          - 如果 `sRoomCode` 有值，则直接返回。
          - 如果 `sRoomCode` 没有值， 则使用 `Math.Random()` 生成随机值， 并赋值给 `sRoomCode，` 同时返回。
      - 
   - 在 `main` 函数中 用三种方式实现 **连续20次** 输出 `getCounter` 的返回值, 同时调用 `getRoomCode()` 并输出。
        ```
        输出格式为：
            -- caller print return value: xxx
            -- caller print getRoomCode = xxx
        ```
      - 使用 continue，跳过 3，6，8次输出。


## 题目2
- 定义接口： `IEat` ， 包含 `Eat`  method, 参数为空，无返回值。
- 定义 `Animal` 抽象类，实现 `IEat` 接口， 并添加 `name` filed， 支持构造函数传入。
  - 定义虚方法，`speak()`; 无返回值。
- 新增 `Dog` `class`， 实现 `Animal` 相关。
- 新增 `HuskyDog` `class`,  继承 `Dog` 相关, 重写 `Eat` 方法。
- 新增 `People` `class`， 实现 IEat 相关接口，并定义内部类 `ISoundListener`, 包含 方法 `void sound()`

针对上面的题目，设计一个 使用类，能分别测试到如下场景：
- `overwride` 场景
- `abstract` 的使用
- `interface` 的使用
- `nested class` 的使用
- 比较下列场景的输出值。
```
    public static void main(String[] args) {
        Dog dog = new Dog();
        System.out.println("bofore modify: " + dog.dogHair);

        modifyDogProperty(dog);

        System.out.println("after modify: " + dog.dogHair);
    }

    public static void modifyDogProperty(Dog dog) {
        if (dog == null) {
            return;
        }
        dog.dogHair = "xxxxxxxxxxx";
    }
```


## 题目3
- 引入 com.google.gson jar包。
- 基于题目2中的 `dog` 对象，调用如下方法，输出值。
  ```
  (new Gson()).toJson(dog)
  ```


## 题目4
- 顺序打印出 斐波那契数列 的前面20项目的值。 

附：
在数学上，斐波那契数列以如下被以递推的方法定义：F(0)=0，F(1)=1, F(n)=F(n - 1)+F(n - 2)（n ≥ 2，n ∈ N*），这个数列从第3项开始，每一项都等于前两项之和。
### 参考值
- 1，1，2，3，5，8，13，21，34，55，89...
