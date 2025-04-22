---
layout: single
title:  "[JAVA] 점프 투 자바 #15 값에 의한 호출과 객체에 의한 호출"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 자바 #15] 

# 값에 의한 호출과 객체에 의한 호출
```java
class Updater {
    void update(Counter counter) {
        counter.count++;
    }
}

class Counter {
    int count = 0;  // 객체변수
}

public class Sample {
    public static void main(String[] args) {
        Counter myCounter = new Counter();
        System.out.println("before update:"+myCounter.count);
        Updater myUpdater = new Updater();
        myUpdater.update(myCounter);
        System.out.println("after update:"+myCounter.count);
    }
}
```
```
before update:0
after update:1
```

## 한 개의 자바 파일에 2개 이상의 클래스 선언하기
```
Sample.java 파일 내에 Sample, Updater, Counter라는 클래스 3개가 등장했다. 
이와 같이 하나의 java 파일 내에는 여러 개의 클래스를 선언할 수 있다.
단, 파일명이 Sample.java라면 Sample.java 내의 Sample 클래스는 public으로 선언하라는 관례(규칙)가 있다.
```