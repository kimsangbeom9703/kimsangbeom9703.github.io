---
layout: single
title:  "[JAVA] 점프 투 자바 #5 StringBuffer"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 자바 #5] 

## StringBuffer
1. append
2. insert
3. substring

***append***
- 다음은 StringBuffer 객체를 생성하고 문자열을 생성하는 예제이다.
```java
    StringBuffer sb = new StringBuffer();  // StringBuffer 객체 sb 생성
    sb.append("hello");
    sb.append(" ");
    sb.append("jump to java");
    String result = sb.toString();
    System.out.println(result);  // "hello jump to java" 출력
```
```
    StringBuffer 자료형은 String 자료형보다 무거운 편에 속한다. 
    new StringBuffer()로 객체를 생성하면 String을 사용할 때보다 메모리 사용량도 많고 속도도 느리다. 
    따라서 문자열을 추가하거나 변경하는 작업이 많으면 StringBuffer를, 적으면 String을 사용하는 것이 유리하다.
```

### StringBuilder 알아보기
```java
    StringBuilder sb = new StringBuilder();
    sb.append("hello");
    sb.append(" ");
    sb.append("jump to java");
    String result = sb.toString();
    System.out.println(result);
```
```
    hello jump to java
```
```
    tringBuffer는 멀티 스레드 환경에서 안전하고, StringBuilder는 StringBuffer보다 성능이 우수하다는 장점이 있다.
    따라서 동기화를 고려할 필요가 없는 상황에서는 StringBuffer보다 StringBuilder를 사용하는 것이 유리하다.
```

***insert***
- 특정 위치에 원하는 문자열을 삽입할 수 있다.
```java
    StringBuffer sb = new StringBuffer();
    sb.append("jump to java");
    sb.insert(0, "hello ");
    System.out.println(sb.toString());
```
```
    hello jump to java
```

***substring***
- substring 원하는 위치에서 문자를 뽑아낸다.
```java
    StringBuffer sb = new StringBuffer();
    sb.append("Hello jump to java");
    System.out.println(sb.substring(0, 4));
```
```
    hell
```