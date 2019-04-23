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
+ 按升序进行排序sort，Java SE 8以上可以使用parallelSort
