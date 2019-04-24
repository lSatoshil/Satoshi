---
layout: post
title: Java Language Basics
categories: Java
description: Java语言基础。
keywords: Java, Learn, Basics
---

**目录**

* TOC
{:toc}

## 变量

### 变量种类
1. 实例变量：独立方法之外的非static变量
2. 类变量：独立方法之外的static变量
3. 局部变量：方法中的变量
4. 参数：方法后面括号类的参数

### 命名规则
1. 变量名区别大小写，以字母、$、_ 开头，后面为字母，数字，$和_。人们习惯以字母开头命名变量
2. 变量名不能包含关键字和保留字段
3. 建议命名遵循驼峰式命名规则，一个单词时变量全部小写，两个单词以上组成，第二个开始首字母大写；常量建议全部大写，每个单词以下划线隔开

### 基本数据类型
**Java共有八中基础数据类型**  

| 类型 | 字节|取值范围 | 默认值 |
| :-----: | :------: | :-----: | :-----: |
| byte | 8 | -2^7 ~ 2^7-1 | 0 |
| short | 16 |-2^15 ~ 2^15-1 | 0 |
| int | 32 | -2^31 ~ 2^31-1 | 0 |
| long | 64 |-2^63 ~ 2^63-1 | 0L |
| float | 32 | / | 0.0f |
| double | 64 | / | 0.0d |
| char | 16 | \u0000 ~ \uffff | '\u0000' |
| boolean | / | true/false | false |

Java SE 7及以上的版本可以在数字之间加上下划线，但需要遵守以下规则
+ 在数字的开头和结尾不能使用
+ 于浮点类型的小数点附件
+ 在F、L等尾缀之前
+ 在需要一串数字的地方

### 数组
**数组是一个对象容器，类型相同，个数固定**  
下列代码演示创建一个数组，给数组复制，打印数组
```
public class ArrayDemo {
    public static void main(String[] args) {
        // declares an array of integers
        int[] anArray;

        // allocates memory for 10 integers
        anArray = new int[10];

        // initialize first element
        anArray[0] = 100;
        // initialize second element
        anArray[1] = 200;
        // and so forth
        anArray[2] = 300;
        anArray[3] = 400;
        anArray[4] = 500;
        anArray[5] = 600;
        anArray[6] = 700;
        anArray[7] = 800;
        anArray[8] = 900;
        anArray[9] = 1000;

        for (int i = 0 ; i < anArray.length ; i++) {
            System.out.println("Element at index "+i+":"+
            + anArray[i]);
        }
    }
}
```
输出如下图所示  
![ArrayDemo](https://www.zhouxinye.com/images/blog/java/ArrayDemo.png "ArrayDemo结果")  

声明一个数组需要使用[],该符号可以放在类型后面，也可以放在变量后面
```
float[] anArray;
float anArray[];
```
声明只是声明一个数组，并不是创建一个数组  
创建一个数组需要使用new关键字，例如ArrayDemo中创建一个int数组  
数组的初始化既可以如ArrayDemo一个一个赋值，也可以以如下方式赋值  
```
int[] anArray = {
    100, 200, 300,
    400, 500, 600,
    700, 800, 900, 1000
};
```
数组的大小由大括号内的逗号相隔的值的数量决定

**复制数组**
```
public static void arraycopy(Object src, int srcPos,Object dest, int destPos, int length)
```
从src的第srcPos个元素开始复制（length-destPos）个元素到数组dest的destPos和length
```
public class ArrayCopyDemo {
    public static void main(String[] args) {
        char[] copyFrom = { 'd', 'e', 'c', 'a', 'f', 'f', 'e',
                'i', 'n', 'a', 't', 'e', 'd' };
        char[] copyTo = new char[7];

        System.arraycopy(copyFrom, 2, copyTo, 0, 7);
        System.out.println(new String(copyTo));
    }
}
```
输出如下图所示  
![ArrayCopyDemo](https://www.zhouxinye.com/images/blog/java/ArrayCopyDemo.png "ArrayCopyDemo结果")  

**数组操作**
+ 复制数组copyOfRange
+ 获取数组中特定值的位置binarySearch
+ 比较两个数组 equals
+ 用特定值填充数组 fill
+ 按升序进行排序sort，Java SE

## 运算符
**优先级（由高到低）**

|运算符|优先度|
|:---|:---|
|postfix |	expr++ expr--|
|unary |	++expr --expr +expr -expr ~ !|
|multiplicative |	* / %|
|additive |	+ -|
|shift |	<< >> >>>|
|relational |	< > <= >= instanceof|
|equality |	== !=|
|bitwise AND | & |
|bitwise exclusive OR |	^ |
|bitwise inclusive OR	| &#124; |
|logical AND	| && |
|logical OR |	&#124;&#124;|
|ternary |	? :|
|assignment |	= += -= *= /= %= &= ^= &#124;= <<= >>= >>>=|

### 赋值、算术、一元运算
赋值运算“=”:将右边的值赋值给左边
```
int i = 0;
boolean b = false;
```
算术运算“+、-、&#42;、/、%”，用法如下所示
```
class ArithmeticDemo {

    public static void main (String[] args) {

        int result = 1 + 2;
        // result is now 3
        System.out.println("1 + 2 = " + result);
        int original_result = result;

        result = result - 1;
        // result is now 2
        System.out.println(original_result + " - 1 = " + result);
        original_result = result;

        result = result * 2;
        // result is now 4
        System.out.println(original_result + " * 2 = " + result);
        original_result = result;

        result = result / 2;
        // result is now 2
        System.out.println(original_result + " / 2 = " + result);
        original_result = result;

        result = result + 8;
        // result is now 10
        System.out.println(original_result + " + 8 = " + result);
        original_result = result;

        result = result % 7;
        // result is now 3
        System.out.println(original_result + " % 7 = " + result);
    }
}
```

'='其他用法: **和其他运算符结合**,比如上述代码可以改写成:  
```
class ArithmeticDemo {

    public static void main (String[] args) {

        int result = 1 + 2;
        // result is now 3
        System.out.println("1 + 2 = " + result);
        int original_result = result;

        result -= 1;
        // result is now 2
        System.out.println(original_result + " - 1 = " + result);
        original_result = result;

        result *= 2;
        // result is now 4
        System.out.println(original_result + " * 2 = " + result);
        original_result = result;

        result /= 2;
        // result is now 2
        System.out.println(original_result + " / 2 = " + result);
        original_result = result;

        result += 8;
        // result is now 10
        System.out.println(original_result + " + 8 = " + result);
        original_result = result;

        result %= 7;
        // result is now 3
        System.out.println(original_result + " % 7 = " + result);
    }
}
```
'+'其他用法: **拼接字符串**
```
class ConcatDemo {
    public static void main(String[] args){
        String firstString = "This is";
        String secondString = " a concatenated string.";
        String thirdString = firstString+secondString;
        System.out.println(thirdString);
    }
}
```
输出结果为:
```
This is a concatenated string.
```

### 一元运算符
+ '+'一元加运算符，表示正值
+ '-'一元减运算符，对一个数值取反值
+ '++(--)'自增(减)运算符，讲一个数值加(减)1
+ '!'布尔值反转，和逻辑补运算

```
class UnaryDemo {

    public static void main(String[] args) {

        int result = +1;
        // result is now 1
        System.out.println(result);

        result--;
        // result is now 0
        System.out.println(result);

        result++;
        // result is now 1
        System.out.println(result);

        result = -result;
        // result is now -1
        System.out.println(result);

        boolean success = false;
        // false
        System.out.println(success);
        // true
        System.out.println(!success);
    }
}
```
**++x(--x)和x++(x--)的区别**  
这两者的区别体现在复合表达式当中，++x(--x)先加(减)1,在参与运算；x++(x--)先参与运算，在改变值
```
class PrePostDemo {
    public static void main(String[] args){
        int i = 3;
        i++;
        // prints 4
        System.out.println(i);
        ++i;			   
        // prints 5
        System.out.println(i);
        // prints 6
        System.out.println(++i);
        // prints 6
        System.out.println(i++);
        // prints 7
        System.out.println(i);
    }
}
```

### 关系运算符
+ ==
+ !=
+ >
+ >=
+ <
+ <=

### 条件运算符
+ &&，逻辑与，表示两边都为true才为true
+ ||，逻辑或，表示两边其中一个为true就为true
+ 布尔类型表达式 ? 表达式1 : 表达式2，布尔类型表达式为true去表达式1否则为2

### 类型比较运算符 instanceof
instanceof可以将对象与指定类型进行比较，可以用来测试对象是否为类或子类的实例，以及接口的实现类的实例

### 位操作符和位移操作符
操作符为 ~ << >> >>> & ^ |
