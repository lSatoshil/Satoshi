---
layout: post
title: Java 面向对象编程的概念
categories: Java
description: Java 面向对象编写概念的学习。
keywords: Java, Learn, Object-Oriented
---

**目录**

* TOC
{:toc}

## What Is an Object?
**对象是由相关状态和行为组成的**
+ 将代码块放到对象的好处
   1. 模块化
   2. 信息隐藏
   3. 代码重复利用
   4. 可插入和可调式

## What Is a Class?
**类是创建对象的蓝图或原型**
在现实世界中，你会发现有许多相同特征的个体。比如：
所有的自行车都是按照一个蓝图进行设计，以下是自行车一种可能实现的类
```
class Bicycle {

    int cadence = 0;

    int speed = 0;

    int gear = 1;

    void changeCadence(int newValue) {
        cadence = newValue;
    }

    void changeGear(int newValue) {
        gear = newValue;
    }

    void speedUp(int increment) {
        speed = speed + increment;
    }

    void applyBrakes(int decrement) {
        speed = speed - decrement;
    }

    void printStates() {
        System.out.println("cadence:" +
                cadence + " speed:" +
                speed + " gear:" + gear);
    }
}
```
字段cadence、speed和gear表示自行车的状态，
方法changeCadence、changeGear等表示他和外界的交互

下面是一个BicycleDemo，创建对象并调用他的方法
```
class BicycleDemo {
    public static void main(String[] args) {

        // Create two different
        // Bicycle objects
        Bicycle bike1 = new Bicycle();
        Bicycle bike2 = new Bicycle();

        // Invoke methods on
        // those objects
        bike1.changeCadence(50);
        bike1.speedUp(10);
        bike1.changeGear(2);
        bike1.printStates();

        bike2.changeCadence(50);
        bike2.speedUp(10);
        bike2.changeGear(2);
        bike2.changeCadence(40);
        bike2.speedUp(10);
        bike2.changeGear(3);
        bike2.printStates();
    }
}
```
运行结果截图
![BicycleDemo](https://www.zhouxinye.com/images/blog/java/BicycleDemo.pnghttps://www.zhouxinye.com/images/blog/java/BicycleDemo.png "BicycleDemo结果")

## What Is Inheritance?
**继继承为组织和构造软件提供了一种强大的机制**
在面向对象编程语言中，一个父类可以拥有许多子类，但只允许继承一个父类
创建子类的关键字为**extends**,如下列代码所示
```
class MountainBike extends Bicycle {

    // new fields and methods defining
    // a mountain bike would go here

}
```

## What Is an Interface?
**接口是连接类与外部的桥梁**
接口是抽象方法的集合，下面声明了一个自行车的接口
```
interface Bicycle {

    //  wheel revolutions per minute
    void changeCadence(int newValue);

    void changeGear(int newValue);

    void speedUp(int increment);

    void applyBrakes(int decrement);
}
```
实现接口需要使用关键字**implements**,一个类可以实现多个接口
下面为实现上面接口的一个类
```
class ACMEBicycle implements Bicycle {

    int cadence = 0;
    int speed = 0;
    int gear = 1;

   // The compiler will now require that methods
   // changeCadence, changeGear, speedUp, and applyBrakes
   // all be implemented. Compilation will fail if those
   // methods are missing from this class.

    void changeCadence(int newValue) {
         cadence = newValue;
    }

    void changeGear(int newValue) {
         gear = newValue;
    }

    void speedUp(int increment) {
         speed = speed + increment;
    }

    void applyBrakes(int decrement) {
         speed = speed - decrement;
    }

    void printStates() {
         System.out.println("cadence:" +
             cadence + " speed:" +
             speed + " gear:" + gear);
    }
}
```

## What Is a Package?
**包是以逻辑的方式组织类和接口**
[Java Platform API Specification ]（https://docs.oracle.com/javase/8/docs/api/index.html,Java SE平台提供的所有包、接口、类、字段和方法的完整清
