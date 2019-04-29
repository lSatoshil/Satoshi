---
layout: post
title: Class And Object
categories: Java
description: Java类和对象。
keywords: Java, Learn, Class, Object
---

**目录**

* TOC
{:toc}

## 类

### 1.创建类
下面定义一个简单类:
```
class MyClass {
    // field, constructor, and
    // method declarations
}
```
<br>
声明一个类需要注意以下几点
+ 需要修饰符，像public这样的
+ 类名首字母要大写
+ 继承父类需要使用关键字 ***extends*** ，一个子类只能继承一个父类
+ 实现一个类需要使用关键字 ***implements*** ，一个类可以实现多个类，类名之间用逗号隔开
+ 类的主体被大括号包围

<br>
1.1 声明成员变量

<br>

字段的声明由三部分组成
+ 修饰符：比如public
+ 字段类型
+ 字段名称

1.1.1 修饰符访问权限
+ public 所有类都可以访问
+ private 只有类自己可以访问
+ default 类自己和同包下的其他类  

1.1.2 类型  
成员变量必须有一个类型，可以使基础类型，也可以是引用对象（数组，对象等）  
<br>
1.1.3 变量名  
遵循变量命名规则，除此之外还要遵循以下规则：
+ 类名首字母大写
+ 方法名第一个词为动词

1.2 定义方法
```
public double calculateAnswer(double wingSpan, int numberOfEngines,
                              double length, double grossTons) {
    //do the calculation here
}
```
上面代码定义一个简单的方法，一个方法拥有以下组件：
+ 修饰符，private等
+ 返回类型，方法返回值的类型，如果没有可以使用void
+ 方法名，字段名的命名规则也适用方法名的命名
+ 参数列表，如果没有则为空
+ 异常类型列表，可以不加
+ 方法体<br>

方法声明需要方法名和参数列表：
```
demo(parameter1,parameter2);
```
1.2.1 方法名命名建议使用动词或者第一个单词为动词之后可以使用其他类型单词  <br>

1.2.3 方法重载
方法重载是方法名相同，但是参数列表不一样<br>

1.3 构造器
构造器的定义和定义一个方法类似，但是没有返回类型，且名称和类名一样  
构造器可以重载  
如果一个类无法调用另一个类的构造器，则就无法创建该方法对象  

1.4 传递信息给方法和构造器

1.4.1 参数类型  
基本类型和引用类型<br>

1.4.2 可变参数
```
public Polygon polygonFrom(Point... corners) {
    int numberOfSides = corners.length;
    double squareOfSide1, lengthOfSide1;
    squareOfSide1 = (corners[1].x - corners[0].x)
                     * (corners[1].x - corners[0].x)
                     + (corners[1].y - corners[0].y)
                     * (corners[1].y - corners[0].y);
    lengthOfSide1 = Math.sqrt(squareOfSide1);

    // more method body code follows that creates and returns a
    // polygon connecting the Points
}
```
上述Point为一个有x和y字段的类  
在方法内，将可变参数当成一个数组进行处理  
我们平时使用的printf就是一个使用可变参数的方法<br>

1.4.3 参数名  
1.参数名在方法类必须唯一  
2.参数名可以类的字段名称相同，在方法使用相同名称的类的字段需要加上 **this** 关键字<br>

1.4.4 传递的参数类型  
可以是基础类型和引用类型，但是需要注意  
使用基本类型，在方法结束返回后，对于参数的修改将消失  
使用引用类型，可以保留对参数的修改  <br>

### 2.方法返回值  
当出现以下情况时，调用方法时会返回：
+ 执行完方法所有语句
+ 遇到关键字 **return**
+ 抛出异常

方法的声明类型如果不是 **void** 则需要有返回语句，返回值的类型必须与声明类型一致  
声明类型为 **void** 的方法需要 **return** 语句，则可以这样使用
```
public void methodDemo(){
  //Statement
  return;
}
```

### 3关键字 **this**   
使用关键字 **this** 表示调用当前类的字段或方法  
```
public class Point {
    public int x = 0;
    public int y = 0;

    //constructor
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```
使用关键字 **this** 还可以代指调用构造参数，但是只能在构造函数第一行调用其他构造函数
```
public class Rectangle {
    private int x, y;
    private int width, height;

    public Rectangle() {
        this(0, 0, 1, 1);
    }
    public Rectangle(int width, int height) {
        this(0, 0, width, height);
    }
    public Rectangle(int x, int y, int width, int height) {
        this.x = x;
        this.y = y;
        this.width = width;
        this.height = height;
    }
    ...
}
```

## 对象  
### 1. 创建对象  
创建一个对象有三个部分组成
+ 声明
+ 实例化
+ 初始化  <br>

1.1 声明对象  
声明对象只需对象类型(Object)和变量名称(objName)  
声明一个类不等于创建一个对象，在创建之前无法使用该变量  
```
Object objName
```
1.2 实例化  
使用关键字 **new** 来实例化一个类，为新对象分配内存并返回该对象的引用   

1.3 初始化一个对象  
每个类至少有一个构造函数，如果在创建类时没有创建构造函数，在编译时，java编译器会默认提供一个无参构造函数  
初始化一个对象需要使用关键字 **new** 根据参数类型和数量来调用类的构造函数

### 2. 使用对象
创建对象后，我们可以：
+ 引用对象的字段
+ 调用对象的方法
