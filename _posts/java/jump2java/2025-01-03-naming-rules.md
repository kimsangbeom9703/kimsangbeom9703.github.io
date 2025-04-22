---
layout: single
title:  "[JAVA] 점프 투 자바 #3 이름 짓는 규칙"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories:
- Study
- JAVA


toc: true   #Table Of Contents 목차
toc_sticky: true
---
# [JAVA - 점프 투 자바 #3] 

## 이름 짓는 규칙

1. 클래스 이름 짓기
2. 메서드 이름 짓기
3. 변수 이름 짓기

## 클래스 이름 짓기
- 클래스명은 명사로 한다.
- 클래스명은 대문자로 시작한다.
- 파스칼 케이스를 사용한다
```
    class Cookie{}
    class ChocoCookie{}
```

## 메서드 이름 짓기
- 메서드명은 동사로 한다.
- 메서드명은 소문자로 시작한다.
- 카멜 케이스를 시작한다
```
    run();
    runFast();
    getBackground();
```

## 변수 이름 짓기
- 짧고 의미가 있어야 한다.
- 순서를 의미하고 임시로 쓰이는 변수명은 i,j,k,m,n을 사용하고 문자의 경우는 c,d,e를 사용한다.
- 변수명에 `_`,`$`를 쓸 수 있지만 시작 문자로 사용하는 것은 지양한다.
```
    String userName;
    float lineWidth;
    int i;  // 주로 반복문에서 사용
    char c;  // 주로 반복문에서 사용
```