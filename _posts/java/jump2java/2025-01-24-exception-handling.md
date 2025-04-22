---
layout: single
title:  "[JAVA] 점프 투 자바 #24 예외처리"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 자바 #24] 

# 예외처리
```
자바 프로그램을 만들다 보면 수많은 예외 상황이 발생한다. 
예외 처리 방법을 알게 되면 보다 안전하고 유연한 프로그래밍을 만들 수 있다.
```
## 예외 예제 
```java
public class Sample {
    public static void main(String[] args){
        int c = 4 / 0;
    }
}
```
```
Exception in thread "main" java.lang.ArithmeticException: / by zero
    at Test.main(Test.java:14)
```
4를 0으로 나눌 수가 없으므로 이와 같이 산술에 문제가 생겼다는 ArithmeticException 예외가 발생한다.
## 예외 예제2
```java
public class Sample {
    public static void main(String[] args) {
        int[] a = {1, 2, 3};
        System.out.println(a[3]);
    }
}    
```
```
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 3
    at Test.main(Test.java:17)
```
a[3]은 a 배열의 4번째 값이므로 a 배열에서 구할 수 없다. 그래서 배열에서 아무것도 없는 곳을 가리켰다는 ArrayIndexOutOfBoundsException 예외가 발생했다.

## 예외 처리
```java
public class Sample {
    public static void main(String[] args) {
        int c;
        try {
            c = 4 / 0;
            System.out.print(c);
        } catch(ArithmeticException e) {
            c = -1;  // 예외가 발생하여 이 문장이 수행된다.
            System.out.print(c);
        }
    }
}
```
## finally
프로그램 수행 도중 예외가 발생하면 프로그램이 중지되거나 예외 처리에 의해 catch 구문이 실행된다.

어떤 예외가 발생하더라도 반드시 실행되어야 하는 부분이 있으면 finally를 사용한다.
```java
public class Sample {
    public void shouldBeRun() {
        System.out.println("ok thanks");
    }

    public static void main(String[] args) {
        Sample sample = new Sample();
        int c;
        try {
            c = 4 / 0;
        } catch (ArithmeticException e) {
            c = -1;
        } finally {
            sample.shouldBeRun();  // 예외에 상관없이 무조건 수행된다.
        }
    }
}
```
## 예외 활용하기 - RuntimeException과 Exception
```java
public class Sample {
    public void sayNick(String nick) {
        if("바보".equals(nick)) {
            return;
        }
        System.out.println("당신의 별명은 "+nick+" 입니다.");
    }

    public static void main(String[] args) {
        Sample sample = new Sample();
        sample.sayNick("바보");
        sample.sayNick("야호");
    }
}
```
예외는 크게 두 가지로 구분된다.

1. RuntimeException: 실행 시 발생하는 예외
    -   RuntimeException는 발생할 수도 있고 발생하지 않을 수도 있는 경우에 사용한다.
2. Exception: 컴파일 시 발생하는 예외
    -   Exception 는 예측이 가능한 경우에 사용한다

```java
class FoolException extends Exception {
}

public class Sample {
    public void sayNick(String nick) {
        try {
            if("바보".equals(nick)) {
                throw new FoolException();
            }
            System.out.println("당신의 별명은 "+nick+" 입니다.");
        }catch(FoolException e) {
            System.err.println("FoolException이 발생했습니다.");
        }
    }

    public static void main(String[] args) {
        Sample sample = new Sample();
        sample.sayNick("바보");
        sample.sayNick("야호");
    }
}
```
## 트랜잭션
```
하나의 작업 단위라고 뜻하고
ex)
포장
영수증 발행
발송
쇼핑몰의 운영자는 이 3가지 일 중 하나라도 실패하면 3가지 모두 취소하고 ‘상품발송’ 전의 상태로 되돌리고 싶어 한다.

상품발송() {
    try {
        포장();
        영수증발행();
        발송();
    }catch(예외) {
        모두취소();  // 하나라도 실패하면 모두 취소한다.
    }
}

포장() throws 예외 {
   ...
}

영수증발행() throws 예외 {
   ...
}

발송() throws 예외 {
   ...
}
```