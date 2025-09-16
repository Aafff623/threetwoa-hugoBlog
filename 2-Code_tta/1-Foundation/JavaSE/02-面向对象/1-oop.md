
# 🧠 Java面向对象编程（OOP）详解

## 一、面向过程 vs 面向对象

### 面向过程（Procedural Programming）
- 线性思维，逐步执行
- 适合简单任务（如：上厕所）
- 复杂任务容易导致代码混乱

### 面向对象（Object-Oriented Programming）
- 分类思维，模块化设计
- 适合复杂系统，多人协作
- 核心思想：**抽象、封装、继承、多态**

---

## 二、OOP 四大特征

### 1. 抽象（Abstraction）
- 忽略无关细节，关注核心属性与行为
- 例如：学生管理系统只关心学号、成绩，不关心身高体重

### 2. 封装（Encapsulation）
- 将数据和行为包装在一起，隐藏实现细节
- 通过`private`保护数据，提供`get/set`方法访问
- 提高安全性、可维护性和代码复用性

```java
public class Student {
    private String name;
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}
```

### 3. 继承（Inheritance）
- 子类继承父类的属性和方法
- 使用`extends`关键字
- Java是单继承，但支持多接口实现

```java
public class Student extends Person {
    // 继承Person的属性和方法
}
```

### 4. 多态（Polymorphism）
- 同一方法在不同对象上有不同行为
- 实现方式：方法重写 + 父类引用指向子类对象

```java
Person p = new Student();
p.run(); // 调用的是Student的run方法
```

---

## 三、类与对象

### 类（Class）
- 抽象模板，描述一类事物的属性和行为
- 例如：`Person`、`Car`、`Animal`

### 对象（Object）
- 类的具体实例
- 例如：`new Student()`、`new Car()`

### 对象与引用的关系
- 引用指向对象，如遥控器指向电视机
- 引用类型变量存储的是对象的内存地址

---

## 四、构造器（Constructor）

- 与类名相同，无返回类型
- 用于初始化对象属性
- 支持重载，可使用`this()`调用其他构造器

```java
public class Student {
    private String name;
    public Student() { this("Tom"); }
    public Student(String name) { this.name = name; }
}
```

---

## 五、方法（Method）

### 方法定义
```java
修饰符 返回类型 方法名(参数列表) [throws 异常] {
    // 方法体
}
```

### 方法重载（Overload）
- 方法名相同，参数列表不同
- 与返回值类型无关

### 方法重写（Override）
- 子类重写父类方法
- 方法名、参数列表必须相同
- 访问权限不能更严格，返回类型可协变

---

## 六、关键字详解

### `this`
- 指向当前对象
- 用于区分成员变量与局部变量
- 可调用其他构造器（必须放在第一行）

### `super`
- 指向父类对象
- 调用父类属性、方法、构造器
- 必须出现在子类构造器第一行

### `static`
- 修饰变量、方法、代码块、内部类
- 属于类，不属于对象
- 静态方法中不能使用`this`和`super`

### `final`
- 修饰类：不可继承
- 修饰方法：不可重写
- 修饰变量：常量，只能赋值一次

### `abstract`
- 修饰类：抽象类，不能实例化
- 修饰方法：抽象方法，无实现，需子类重写

---

## 七、接口（Interface）

- 只有规范，没有实现
- 方法默认是`public abstract`
- 变量默认是`public static final`
- 支持多实现、多继承（接口之间）

```java
public interface Swim {
    void swim();
}

public class Duck implements Swim {
    @Override
    public void swim() { System.out.println("Duck swimming"); }
}
```

---

## 八、内部类（Inner Class）

### 1. 成员内部类
- 属于外部类对象
- 可访问外部类所有成员

### 2. 静态内部类
- 属于外部类
- 只能访问外部类静态成员

### 3. 局部内部类
- 定义在方法中
- 只能访问`final`局部变量

### 4. 匿名内部类
- 无类名，直接实现接口或继承类
- 常用于一次性使用场景

```java
Runnable r = new Runnable() {
    @Override
    public void run() { System.out.println("Running"); }
};
```

---

## 九、内存分析

- **栈**：局部变量、引用变量
- **堆**：对象实例
- **方法区**：类信息、静态变量、常量池

---

## 十、总结

| 特性         | 说明 |
|--------------|------|
| 抽象         | 关注核心，忽略细节 |
| 封装         | 隐藏实现，提供接口 |
| 继承         | 子类继承父类特性 |
| 多态         | 同一方法不同行为 |
| 类与对象     | 模板与实例 |
| 构造器       | 初始化对象 |
| 方法重载/重写 | 多态实现方式 |
| 接口         | 纯规范，多实现 |
| 内部类       | 类中定义类，增强封装 |
