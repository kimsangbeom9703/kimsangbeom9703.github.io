---
layout: single
title:  "[JAVA] 점프 투 자바 #16 상속"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---
# [JAVA - 점프 투 자바 #16] 

# 상속
자바에는 자식 클래스가 부모 클래스의 기능을 물려받을 수 있는 기능이 있다.

```java
class Animal {
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Dog extends Animal {  // Animal 클래스를 상속한다.
}

public class Sample {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.setName("poppy");
        System.out.println(dog.name);
    }
}
```

## 자식 클래스의 기능 확장하기
```java
class Animal {
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
    void sleep() {
        System.out.println(this.name+" zzz");
    }
}

public class Sample {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.setName("poppy");
        System.out.println(dog.name);
        dog.sleep();
    }
}
```
## 메서드 오버라이딩
이미 선언된 메서드를 사용하지 않고 새로운 객체에 같은 메서드를 사용하므로써 수정하여 사용하는 방법.
```java
class Animal {
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
    void sleep() {
        System.out.println(this.name + " zzz");
    }
}

class HouseDog extends Dog {
    void sleep() {
        System.out.println(this.name + " zzz in house");
    }
}

public class Sample {
    public static void main(String[] args) {
        HouseDog houseDog = new HouseDog();
        houseDog.setName("happy");
        houseDog.sleep();  // happy zzz in house 출력
    }
}
```

## 메서드 오버로딩
동일한 이름의 메서드를 추가할 수 있다.
```java
class Animal {
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
    void sleep() {
        System.out.println(this.name + " zzz");
    }
}

class HouseDog extends Dog {
    void sleep() {
        System.out.println(this.name + " zzz in house");
    }

    void sleep(int hour) {
        System.out.println(this.name + " zzz in house for " + hour + " hours");
    }
}

public class Sample {
    public static void main(String[] args) {
        HouseDog houseDog = new HouseDog();
        houseDog.setName("happy");
        houseDog.sleep();  // happy zzz in house 출력
        houseDog.sleep(3);  // happy zzz in house for 3 hours 출력
    }
}
```
## 자바는 다중 상속을 지원하지 않는다.
```java
class A {
    public void msg() {
        System.out.println("A message");
    }
}

class B {
    public void msg() {
        System.out.println("B message");
    }
}

class C extends A, B {
    public void static main(String[] args) {
        C test = new C();
        test.msg();
    }
}
```
