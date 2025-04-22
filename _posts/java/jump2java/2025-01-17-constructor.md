---
layout: single
title:  "[JAVA] 점프 투 자바 #17 생성자"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 자바 #17] 

# 생성자

메서드명이 클래스명과 동일하고 리턴 자료형을 정의하지 않는 메서드를 생성자라고 한다. 생성자 규칙은 다음과 같다.
- 클래스명과 메서드명이 같다
- 리턴 타입을 정의하지 않는다(void도 사용하지 않는다.)
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
    HouseDog(String name) {
        this.setName(name);
    }
    void sleep() {
        System.out.println(this.name + " zzz in house");
    }

    void sleep(int hour) {
        System.out.println(this.name + " zzz in house for " + hour + " hours");
    }
}

public class Sample {
    public static void main(String[] args) {
        HouseDog dog = new HouseDog("happy");
        System.out.println(dog.name);
    }
}
```
```
저렇게 생성자를 생성을 하면
객체 변수에 값을 무조건 설정해야만 객체가 생성된다.

HouseDog dog = new HouseDog(); 이렇게 하면 컴파일 오류가 발생하고

HouseDog dog = new HouseDog("happy");   // 생성자 호출 시 문자열을 전달해야 한다.
```

## 생성자 오버로딩
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
    HouseDog(String name) {
        this.setName(name);
    }

    HouseDog(int type) {
        if (type == 1) {
            this.setName("yorkshire");
        } else if (type == 2) {
            this.setName("bulldog");
        }
    }

    void sleep() {
        System.out.println(this.name + " zzz in house");
    }

    void sleep(int hour) {
        System.out.println(this.name + " zzz in house for " + hour + " hours");
    }
}

public class Sample {
    public static void main(String[] args) {
        HouseDog happy = new HouseDog("happy");
        HouseDog yorkshire = new HouseDog(1);
        System.out.println(happy.name);  // happy 출력
        System.out.println(yorkshire.name);  // yorkshire 출력
        happy.sleep();      // happy zzz in house
        yorkshire.sleep();  // yorkshire zzz in house
    }
}

```