---
layout: single
title:  "[JAVA] 점프 투 자바 #20 추상 클래스"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 자바 #20] 

# 추상 클래스

추상 클래스는 인터페이스의 역할도 하면서 클래스의 기능도 가지고 있는 자바의 돌연변이 클래스이다.
```java
abstract class Predator extends Animal {
    abstract String getFood();

    void printFood() {  // default 를 제거한다.
        System.out.printf("my food is %s\n", getFood());
    }
}

interface Barkable {
    void bark();
}

class Animal {
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Tiger extends Predator implements Barkable  {
    public String getFood() {
        return "apple";
    }

    public void bark() {
        System.out.println("어흥");
    }
}

class Lion extends Predator implements Barkable {
    public String getFood() {
        return "banana";
    }

    public void bark() {
        System.out.println("으르렁");
    }
}

class ZooKeeper {
    void feed(Predator predator) {
        System.out.println("feed " + predator.getFood());
    }
}

class Bouncer {
    void barkAnimal(Barkable animal) {
        animal.bark();
    }
}

public class Sample {
    public static void main(String[] args) {
        Tiger tiger = new Tiger();
        Lion lion = new Lion();

        Bouncer bouncer = new Bouncer();
        bouncer.barkAnimal(tiger);
        bouncer.barkAnimal(lion);
    }
}

```