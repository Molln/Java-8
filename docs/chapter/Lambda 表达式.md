# Lambda 表达式

Lambda 是一个 **匿名函数**，可以把 Lambda 理解为是**一段可以传递的代码**（将代码向数据一样进行传递）。可以写出更简洁、更灵活的代码。作为一种更紧凑的代码风格，使 Java 的语言表达能力得到了提升。

示例：从匿名类到 Lambda 的转换

````java
// 匿名内部类
Runnable r1 = new Runnable(){
    @Override
    public void run(){
        System.out.println("You are my son !");
    }
}

// Lambda 表达式
Runnable r1 = () -> System.out.println("You are my son !");
````

````java
// 使用匿名内部类作为参数传递
TreeSet<String> ts = new TreeSet<>(new Comparator<String>(){
    @Override
    public int compare(String s1,String s2){
        return Integer.compare(s1.length,s2.length);
    }
});

// 使用 Lambda 表达式作为参数传递
TreeSet<String> ts = new TreeSet<>(
	(s1,s2) -> Integer.compare(s1.length,s2.length);
);
````

### Lambda 表达式语法

Lambda 表达式在 Java 语言中引入了一个新的语法元素和操作符。这个操作符为 `->` ，该操作符称为 Lambda 操作符或者箭头操作符。它将 Lambda 分为两个部分：

* 左侧：指定了 Lambda 表达式需要的所有参数
* 右侧：指定了 Lambda 体，即 Lambda 表达式要执行的功能

**语法格式一：无参，无返回值，Lambda 体只有一条语句**

````java
Runnable r1 = () -> System.out.println("You are my son !");
````

**语法格式二：一个参数，无返回值，Lambda 体只有一条语句**

````java
Consumer<String> consumer = (args) -> System.out.println(args);
````

**语法格式三：只有一个参数，左侧参数部分的小括号可以省略**

````java
Consumer<String> consumer = args -> System.out.println(args);
````

**语法格式四：两个参数，有返回值**

```java
BinaryOperation<Long> bo = (x,y) -> {
    System.out.println("You are my son !");
    return x + y;
}
```

**语法格式五：Lambda 只有一条语句时，return 与大括号可以省略**

````java
BinaryOperation<Long> bo = (x,y) -> x + y;
````

**语法格式六：参数加类型（参数部分数据类型可以省略，因为可由编译器推断得出，称为类型推断）**

````java
BinaryOperation<Long> bo = (Long x,Long y) -> {
    System.out.println("You are my son !");
    return x + y;
}
````

**类型推断**

上述 Lambda 表达式中的参数类型都是由编译器推断得出。Lambda 表达式中无需指定类型，程序依然可以编译，这是因为 javac 根据程序的上下文，在后台推断出了参数的类型。Lambda 表达式的类型依赖于上下文环境，是由编译器推断出来的，这就是所谓的”类型推断“

