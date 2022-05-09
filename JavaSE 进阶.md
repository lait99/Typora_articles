# JavaSE 进阶

## 1：面向对象和面对过程的思想对比

**面向对象和面向过程的思想对比 : **

​	**面向过程 ：**是一种以过程为中心的编程思想，实现功能的每一步，都是自己实现的

​	**面向对象 ：**是一种以对象为中心的编程思想，通过指挥对象实现具体的功能

![image-20220503185411732](C:%5CUsers%5Cpc%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20220503185411732.png)

![image-20220503185449556](C:%5CUsers%5Cpc%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20220503185449556.png)

## 2：类和对象的关系

客观存在的事物皆为对象 ，所以我们也常常说万物皆对象。

* 类
  * 类的理解
    * 类是对现实生活中一类具有共同属性和行为的事物的抽象
    * 类是对象的数据类型，类是具有相同属性和行为的一组对象的集合
    * 简单理解：类就是对现实事物的一种描述
  * 类的组成
    * 属性：指事物的特征，例如：手机事物（品牌，价格，尺寸）
    * 行为：指事物能执行的操作，例如：手机事物（打电话，发短信）
* 类和对象的关系
  * 类：类是对现实生活中一类具有共同属性和行为的事物的抽象
  * 对象：是能够看得到摸的着的真实存在的实体
  * 简单理解：**类是对事物的一种描述，对象则为具体存在的事物**

## 3： 创建字符串对象的区别对比

- **通过构造方法创建**

  ​	通过 new 创建的字符串对象，每一次 new 都会申请一个内存空间，虽然内容相同，但是地址值不同

- **直接赋值方式创建**

  ​	以“”方式给出的字符串，只要字符序列相同(顺序和大小写)，无论在程序代码中出现几次，JVM 都只会建立一个 String 对象，并在字符串池中维护

**双引号创建的字符串对象，在字符串常量池中存储，通过构造方法创建的字符串对象，在堆内存中存储。**

**java存在常量优化机制，在编译的时候，将会将“a”+"b"+"c"拼接为“abc”。**

## **4：集合和数组的区别 :** 

​	共同点：都是存储数据的容器

​	不同点：数组的容量是固定的，集合的容量是可变的

## 5：switch 退出while循环

```
        int  i = 0 ;
        io:while (true){
            i++;
            System.out.println(i);
            String aa = "1";
            switch (i){
                case 1:
                    System.out.println("i="+i);
                    break;
                case 5:
                    System.out.println("i="+i);
                    break io;
            }
            if ( i>10 ){
                break;
            }
        }
```

输出结果：

```
1
i=1
2
3
4
5
i=5
```

## 6：退出当前运行的jvm虚拟机

```
System.exit(0);
```

## 7：静态与非静态的区别

1. 静态随着类的加载而加载，优先于对象存在
2. 非静态需要再创建对象后，才可以使用。
3. 静态方法只能访问静态成员（成员变量，成员方法）。
4. 非静态方法中，可以使用静态成员，也可以使用非静态成员。
5. 静态方法中，没有this关键字。
6. 静态成员被所有类对象共享。
7. 静态成员存在内存静态区。

## 8：继承

继承可以让类与类之间产生关系，子父类关系，产生子父类后，子类则可以使用父类中非私有的成员。

### 8.1 继承的好处和弊端（理解）

- 继承好处
  - 提高了代码的复用性(多个类相同的成员可以放到同一个类中)
  - 提高了代码的维护性(如果方法的代码需要修改，修改一处即可)
- 继承弊端
  - 继承让类与类之间产生了关系，类的耦合性增强了，当父类发生变化时子类实现也不得不跟着变化，削弱了子类的独立性
- 继承的应用场景：
  - 使用继承，需要考虑类与类之间是否存在is..a的关系，不能盲目使用继承
    - is..a的关系：谁是谁的一种，例如：老师和学生是人的一种，那人就是父类，学生和老师就是子类

### 8.2 耦合性

代码与代码之间存在关联都可以将其称之为“耦合”。

### 8.3 继承的特点

1. Java中类只支持单继承，不支持多继承
2. Java中类支持多层继承

**为什么不能多继承？**

若继承多个父类中存在相同方法，调用该方法时无法确认该调用A父类还是B父类。

### 8.4 继承中的成员访问特点

#### 8.4.1 继承中变量的访问特点（掌握）

在子类方法中访问一个变量，采用的是就近原则。

1. 子类局部范围找
2. 子类成员范围找
3. 父类成员范围找
4. 如果都没有就报错(不考虑父亲的父亲…)

- 示例代码

  ```java
  class Fu {
      int num = 10;
  }
  class Zi {
      int num = 20;
      public void show(){
          int num = 30;
          System.out.println(num);
      }
  }
  public class Demo1 {
      public static void main(String[] args) {
          Zi z = new Zi();
          z.show();	// 输出show方法中的局部变量30
      }
  }
  ```

#### 8.4.2 方法重写的注意事项（掌握）

- 方法重写的注意事项

1. 私有方法不能被重写(父类私有成员子类是不能继承的)
2. 子类方法访问权限不能更低(public > 默认 > 私有)
3. 静态方法不能被重写,如果子类也有相同的方法,并不是重写的父类的方法

- 示例代码

```java
public class Fu {
    private void show() {
        System.out.println("Fu中show()方法被调用");
    }

    void method() {
        System.out.println("Fu中method()方法被调用");
    }
}

public class Zi extends Fu {

    /* 编译【出错】，子类不能重写父类私有的方法*/
    @Override
    private void show() {
        System.out.println("Zi中show()方法被调用");
    }
   
    /* 编译【出错】，子类重写父类方法的时候，访问权限需要大于等于父类 */
    @Override
    private void method() {
        System.out.println("Zi中method()方法被调用");
    }

    /* 编译【通过】，子类重写父类方法的时候，访问权限需要大于等于父类 */
    @Override
    public void method() {
        System.out.println("Zi中method()方法被调用");
    }
}
```

#### 8.4.3 @Override 注解作用

检查当前的方法是否是一个正确的重写方法。

#### 8.4.4 权限修饰符 (理解) 

![02_权限修饰符](JavaSE%20%E8%BF%9B%E9%98%B6.assets/02_%E6%9D%83%E9%99%90%E4%BF%AE%E9%A5%B0%E7%AC%A6.png)

#### 8.4.5 final（应用）

- fianl关键字的作用

  - final代表最终的意思，可以修饰成员方法，成员变量，类

- final修饰类、方法、变量的效果  

  - fianl修饰类：该类不能被继承（不能有子类，但是可以有父类）

  - final修饰方法：该方法不能被重写

  - final修饰变量：表明该变量是一个常量，不能再次赋值

    + 变量是基本类型,不能改变的是值

    + 变量是引用类型,不能改变的是地址值,但地址里面的内容是可以改变的

    + 举例

      ```java
      public static void main(String[] args){
          final Student s = new Student(23);
        	s = new Student(24);  // 错误
       	s.setAge(24);  // 正确
      }
      ```

## 9：代码块 

### 9.1代码块概述 (理解)

在Java中，使用 { } 括起来的代码被称为代码块

### 9.2代码块分类 (理解) 

+ 局部代码块

  + 位置: 方法中定义

  + 作用: 限定变量的生命周期，及早释放，提高内存利用率

  + 示例代码

    ```java
    public class Test {
        /*
            局部代码块
                位置：方法中定义
                作用：限定变量的生命周期，及早释放，提高内存利用率
         */
        public static void main(String[] args) {
            {
                int a = 10;
                System.out.println(a);
            }
    
           // System.out.println(a);
        }
    }
    ```

+ 构造代码块

  + 位置: 类中方法外定义

  + 特点: 每次构造方法执行的时，都会执行该代码块中的代码，并且在构造方法执行前执行

  + 作用: 将多个构造方法中相同的代码，抽取到构造代码块中，提高代码的复用性

  + 示例代码

    ```java
    public class Test {
        /*
            构造代码块:
                位置：类中方法外定义
                特点：每次构造方法执行的时，都会执行该代码块中的代码，并且在构造方法执行前执行
                作用：将多个构造方法中相同的代码，抽取到构造代码块中，提高代码的复用性
         */
        public static void main(String[] args) {
            Student stu1 = new Student();
            Student stu2 = new Student(10);
        }
    }
    
    class Student {
    
        {
            System.out.println("好好学习");
        }
    
        public Student(){
            System.out.println("空参数构造方法");
        }
    
        public Student(int a){
            System.out.println("带参数构造方法...........");
        }
    }
    ```

+ 静态代码块

  + 位置: 类中方法外定义

  + 特点: 需要通过static关键字修饰，随着类的加载而加载，并且只执行一次

  + 作用: 在类加载的时候做一些数据初始化的操作

  + 示例代码

    ```java
    public class Test {
        /*
            静态代码块:
                位置：类中方法外定义
                特点：需要通过static关键字修饰，随着类的加载而加载，并且只执行一次
                作用：在类加载的时候做一些数据初始化的操作
         */
        public static void main(String[] args) {
            Person p1 = new Person();
            Person p2 = new Person(10);
        }
    }
    
    class Person {
        static {
            System.out.println("我是静态代码块, 我执行了");
        }
    
        public Person(){
            System.out.println("我是Person类的空参数构造方法");
        }
    
        public Person(int a){
            System.out.println("我是Person类的带...........参数构造方法");
        }
    }
    ```

## 10：接口

### 10.1 接口的概述（理解）

+ 接口就是一种公共的规范标准，只要符合规范标准，大家都可以通用。
+ Java中接口存在的两个意义
  1. 用来定义规范
  2. 用来做功能的拓展

### 10.2 接口的特点（记忆）

- 接口用关键字interface修饰

  ```java
  public interface 接口名 {} 
  ```

- 类实现接口用implements表示

  ```java
  public class 类名 implements 接口名 {}
  ```

- 接口不能实例化

  ​	我们可以创建接口的实现类对象使用

- 接口的子类

  ​	要么重写接口中的所有抽象方法

  ​	要么子类也是抽象类

### 10.3 接口的成员特点（记忆）

- 成员特点

  - 成员变量

    ​	 只能是常量
    ​	 默认修饰符：public static final

  - 构造方法

    ​	没有，因为接口主要是扩展功能的，而没有具体存在

  - 成员方法

    ​	只能是抽象方法

    ​	默认修饰符：public abstract

    ​	关于接口中的方法，JDK8和JDK9中有一些新特性，后面再讲解

### 10.4 JDK8版中接口成员的特点

#### 10.4.1 default 关键字

![image-20220508205446992](JavaSE%20%E8%BF%9B%E9%98%B6.assets/image-20220508205446992.png)

#### 10.4.2 static关键字

![image-20220508210822100](JavaSE%20%E8%BF%9B%E9%98%B6.assets/image-20220508210822100.png)