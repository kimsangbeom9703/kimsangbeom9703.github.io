---
layout: single
title:  "[JAVA] 점프 투 자바 #13 객체 지향 프로그래밍이란"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---
# [JAVA - 점프 투 자바 #13] 

# 객체 지향 프로그래밍이란

```java
    class Calculator {
        static int result = 0;

        static int add(int num) {
            result += num;
            return result;
        }
        
        static int sub(int num) {
            result -= num;
            return result;
        }
    }


    public class Sample {
        public static void main(String[] args) {
            System.out.println(Calculator.add(3));
            System.out.println(Calculator.add(4));
        }
    }
```
## 차이점
```
만약 객체지향에 대해 잘 모른다면 계산기를 두개 사용하려면

class Calculator1 {
    static int result = 0;

    static int add(int num) {
        result += num;
        return result;
    }
}

class Calculator2 {
    static int result = 0;

    static int add(int num) {
        result += num;
        return result;
    }
}


public class Sample {
    public static void main(String[] args) {
        System.out.println(Calculator1.add(3));
        System.out.println(Calculator1.add(4));

        System.out.println(Calculator2.add(3));
        System.out.println(Calculator2.add(7));
    }
}

이런식으로 두번 만들 수도 있다
그러나

class Calculator {
    int result = 0;

    int add(int num) {
        result += num;
        return result;
    }
}


public class Sample {
    public static void main(String[] args) {
        Calculator cal1 = new Calculator();  // 계산기1 객체를 생성한다.
        Calculator cal2 = new Calculator();  // 계산기2 객체를 생성한다.

        System.out.println(cal1.add(3));
        System.out.println(cal1.add(4));

        System.out.println(cal2.add(3));
        System.out.println(cal2.add(7));
    }
}
이렇게 하면 된다
```