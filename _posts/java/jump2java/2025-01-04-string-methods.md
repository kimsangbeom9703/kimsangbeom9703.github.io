---
layout: single
title:  "[JAVA] 점프 투 자바 #4 문자열 내장 메서드"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 자바 #4] 

## 문자열 내장 메서드

***equals***
- equals 메서드는 문자열 2개가 같은지를 비교하여 결괏값을 리턴한다.
```java
    String a = "hello";
    String b = "java";
    String c = "hello";
    System.out.println(a.equals(b)); // false 출력
    System.out.println(a.equals(c)); // true 출력
```
***indexOf***
- 문자열에서 특정 문자열 시작되는 위치 찾기
```java
    String a = "Hello Java";
    System.out.println(a.indexOf("Java"));  // 6 출력
```
***contains***
- 문자열에서 특정 문자열이 포함되어 있는지 여부를 리턴한다.
```java
    String a = "Hello Java";
    System.out.println(a.contains("Java"));  // true 출력
```
***charAt***
- 특정 위치의 문자를 리턴한다.
```java
    String a = "Hello Java";
    System.out.println(a.charAt(6));  // "J" 출력
```
***replaceAll***
- 특정 문자열을 다른 문자열로 치환
```java
    String a = "Hello Java";
    System.out.println(a.replaceAll("Java", "World"));  // Hello World 출력
```
***substring***
- 특정 문자열을 뽑아낼 때 사용
```java
    String a = "Hello Java";
    System.out.println(a.substring(0, 4));  // Hell 출력
```
***toUpperCase***
- 소문자 -> 대문자로 변경
```java
    String a = "Hello Java";
    System.out.println(a.toUpperCase());  // HELLO JAVA 출력
```
***split***
- 특정 구분자로 나누어 문자열 배열로 리턴한다
```java
    String a = "a:b:c:d";
    String[] result = a.split(":");  // result는 {"a", "b", "c", "d"}
```

## 문자열 포매팅
```java
    "현재 온도는 18도입니다."
    System.out.println(String.format("현재 온도는 %d도 입니다.", 3));
```

## 문자열 포맷 코드의 종류
```
코드	설명
%s	    문자열(String)
%c	    문자 1개(character)
%d	    정수(Integer)
%f	    부동소수(floating-point)
%o	    8진수
%x	    16진수
%%	    Literal % (문자 % 자체)
```

***System.out.printf***
```
    함수 출력
```