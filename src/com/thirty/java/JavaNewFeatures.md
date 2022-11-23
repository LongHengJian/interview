### Java新特性
#### Java8 
##### Q1. 什么是函数式编程？Lambda表达式？
1. 函数式编程 
   - 面向对象编程是对数据进行抽象；函数式编程是对行为进行抽象。 
   - 核心思想: 使用不可变值和函数，函数对一个值进行处理，映射成另一个值。
2. Lambda表达式
   - lambda表达式仅能放入如下代码: 预定义使用了 @Functional 注释的函数式接口，自带一个抽象函数的方法，或者SAM(Single Abstract Method 单个抽象方法)类型
   - 这些称为lambda表达式的目标类型，可以用作返回类型，或lambda目标代码的参数。

##### Q2. Stream中常用方法？
1. stream(), parallelStream()
2. filter()
3. findAny() findFirst()
4. sort
5. forEach void
6. map(), reduce()
7. flatMap() - 将多个Stream连接成一个Stream
8. collect(Collectors.toList())
9. distinct, limit
10. count
11. min, max, summaryStatistics

##### Q3. 什么是FunctionalInterface？
1. interface做注解的注解类型，被定义成java语言规范
2. 一个被它注解的接口只能有一个抽象方法，有两种例外
   - 第一是接口允许有实现的方法，这种实现的方法是用default关键字来标记的(java反射中java.lang.reflect.Method#isDefault()方法用来判断是否是default方法)
   - 第二如果声明的方法和java.lang.Object中的某个方法一样，它可以不当做未实现的方法，不违背这个原则: 一个被它注解的接口只能有一个抽象方法
3. 如果一个类型被这个注解修饰，那么编译器会要求这个类型必须满足如下条件:
   - 这个类型必须是一个interface，而不是其他的注解类型、枚举enum或者类class
   - 这个类型必须满足function interface的所有要求，如你个包含两个抽象方法的接口增加这个注解，会有编译错误。
4. 编译器会自动把满足function interface要求的接口自动识别为function interface。

##### Q4. 如何自定义函数接口？
```java
@FunctionalInterface
public interface IMyInterface {
    void study();
}

public class TestIMyInterface {
    public static void main(String[] args) {
        IMyInterface iMyInterface = () -> System.out.println("I like study");
        iMyInterface.study();
    }
}
```

##### Q5. 内置的四大函数接口及使用？
1. 消费型接口: Consumer< T> void accept(T t)有参数，无返回值的抽象方法；
2. 供给型接口: Supplier < T> T get() 无参有返回值的抽象方法,以stream().collect(Collector<? super T, A, R> collector)为例:
3. 断定型接口: Predicate<T> boolean test(T t):有参，但是返回值类型是固定的boolean,比如: steam().filter()中参数就是Predicate
4. 函数型接口: Function<T,R> R apply(T t)有参有返回值的抽象方法；比如：: steam().map() 中参数就是Function<? super T, ? extends R>

##### Q6. Optional要解决什么问题？
是一个可以为null的容器对象，如果值存在则isPresent()方法会返回true，调用get()方法会返回该对象。主要是为了解决空指针问题

##### Q7. 什么是默认方法:什么是默认方法，为什么要有默认方法？
简单说，就是接口可以有实现方法，而且不需要实现类去实现其方法。只需在方法名前面加个default关键字即可。

1. 为什么出现默认方法？
  - 首先，之前的接口是个双刃剑，好处是面向抽象而不是面向具体编程，缺陷是，当需要修改接口时候，需要修改全部实现该接口的类
  - 目前的java 8之前的集合框架没有foreach方法，通常能想到的解决办法是在JDK里给相关的接口添加新的方法及实现
  - 然而，对于已经发布的版本，是没法在给接口添加新方法的同时不影响已有的实现。所以引进的默认方法
  - 他们的目的是为了解决接口的修改与现有的实现不兼容的问题

##### Q8. 什么是类型注解？
类型注解被用来支持在Java的程序中做强类型检查。配合插件式的check framework，可以在编译的时候检测出runtime error，以提高代码质量。这就是类型注解的作用了。

1. 在java 8之前，注解只能是在声明的地方所使用，比如类，方法，属性；
2. java 8里面，注解可以应用在任何地方，比如:
3. 需要注意的是，类型注解只是语法而不是语义，并不会影响java的编译时间，加载时间，以及运行时间，也就是说，编译成class文件的时候并不包含类型注解

##### Q9. 什么是重复注解？
允许在同一申明类型(类，属性，或方法)的多次使用同一个注解
jdk8之前：由另一个注解来存储重复注解，在使用时候，用存储注解Authorities来扩展重复注解。
jdk8重复注解: 在重复注解上面加上@Repeatable即可

#### Java9新特性

##### Q1. Java 9后续新版本中你知道哪些？
1. Java10 - 并行全垃圾回收器 G1
2. Java11 - ZGC：可伸缩低延迟垃圾收集器
3. Java 14 - Switch 表达式（正式版）
4. Java 15 - 文本块