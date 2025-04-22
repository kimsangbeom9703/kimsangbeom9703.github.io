---
layout: single
title:  "[JAVA] 점프 투 자바 #18 인터페이스"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---
# [JAVA - 점프 투 자바 #18] 

# 인터페이스

인터페이스란 극단적으로 동일한 목적 하에 동일한 기능을 수행하게끔 강제하는 것이 바로 인터페이스의 역할이자 개념이다. 
인터페이스는 interface 키워드를 통해 선언할 수 있으며 implements 키워드를 통해 일반 클래스에서 인터페이스를 구현할 수 있다.

```java
interface Animal{
    //추상메소드 선언
    public void cry();
    //디폴트 메소드 선언
    public default void introduce(){
        //실행코드 작성
        System.out.println("나는 동물이다");
    }
}

//구현 클래스 선언
class Cat implements Animal{
    //추상 메소드 강제구현
    public void cry(){
        System.out.println("야옹");
    }
}
class Dog implements Animal{
    //추상 메소드 강제구현
    public void cry(){
        System.out.println("멍멍");
    }
}

public class Sample{
    public static void main(String[] args){
        Cat cat = new Cat();
        Dog dog = new Dog();

        //오버라이딩 메소드 호출
        cat.cry();
        dog.cry();

        //디폴트 메소드 호출
        cat.introduce();
        dog.introduce();
    }
}
```

## 오류나는 인터페이스
```java
interface Animal {
    //추상메소드 선언
    public void cry();

    public void ksb();

    //디폴트 메소드 선언
    public default void introduce() {
        //실행코드 작성
        System.out.println("나는 동물이다");
    }
}

//구현 클래스 선언
class Cat implements Animal {
    //추상 메소드 강제구현
    public void ksb() {
        System.out.println("김상범");
    }

    public void cry() {
        System.out.println("야옹");
    }
}

class Dog implements Animal {
    //추상 메소드 강제구현
    public void cry() {
        System.out.println("멍멍");
    }
}

public class Sample {
    public static void main(String[] args) {
        Cat cat = new Cat();
        Dog dog = new Dog();

        //오버라이딩 메소드 호출
        cat.cry();
        dog.cry();

        //디폴트 메소드 호출
        cat.introduce();
        dog.introduce();
    }
}
```
```
구현 클래스에서 강제한 인터페이스를 사용하지 않을 경우 오류가 발생한다.
```

## 디폴트 메서드
```java
interface Predator {
    String getFood();

    default void printFood() {
        System.out.printf("my food is %s\n", getFood());
    }
}

class Animal {
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Tiger extends Animal implements Predator {
    public String getFood() {
        return "apple";
    }
}

class Lion extends Animal implements Predator {
    public String getFood() {
        return "banana";
    }
}

class ZooKeeper {
    void feed(Predator predator) {
        System.out.println("feed "+predator.getFood());
    }
}

public class Sample {
    public static void main(String[] args) {
        ZooKeeper zooKeeper = new ZooKeeper();
        Tiger tiger = new Tiger();
        Lion lion = new Lion();
        zooKeeper.feed(tiger);  // feed apple 출력
        zooKeeper.feed(lion);  // feed banana 출력

        tiger.printFood();
        lion.printFood();
    }
}
```
```
디폴트 메서드를 설정하면 구현클래스에 메서드가 없더라도 사용할 수 있다.
```