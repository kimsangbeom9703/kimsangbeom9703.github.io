---
layout: single
title:  "[JAVA] 점프 투 자바 #12 제어문"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---
# [JAVA - 점프 투 자바 #12] 

# 제어문

## if 문 (조건문)
```java
int money = 2000;
if (money >= 3000) {
    System.out.println("택시를 타고 가라");
}else {
    System.out.println("걸어가라");
}
```

### and, or, not
```java
x && y	x와 y 모두 참이어야 참이다
x || y	x와 y 둘 중 적어도 하나가 참이면 참이다
!x	x가 거짓이면 참이다
```

### contains
```java
ArrayList<String> pocket = new ArrayList<String>();
pocket.add("paper");
pocket.add("handphone");
pocket.add("money");

if (pocket.contains("money")) {
    System.out.println("택시를 타고 가라");
}else {
    System.out.println("걸어가라");
}
```
## switch/case (조건문)
```java
public class Sample {
    public static void main(String[] args) {
        int month = 8;
        String monthString = "";
        switch (month) {  // 입력 변수의 자료형은 byte, short, char, int, enum, String만 가능하다.
            case 1:  monthString = "January";
                     break;
            case 2:  monthString = "February";
                     break;
            case 3:  monthString = "March";
                     break;
            case 4:  monthString = "April";
                     break;
            case 5:  monthString = "May";
                     break;
            case 6:  monthString = "June";
                     break;
            case 7:  monthString = "July";
                     break;
            case 8:  monthString = "August";
                     break;
            case 9:  monthString = "September";
                     break;
            case 10: monthString = "October";
                     break;
            case 11: monthString = "November";
                     break;
            case 12: monthString = "December";
                     break;
            default: monthString = "Invalid month";
                     break;
        }
        System.out.println(monthString);
    }
}
```
## while 문 (반복문)
```java
int treeHit = 0;
while (treeHit < 10) {
    treeHit++;  // treeHit += 1 로도 표현 가능
    System.out.println("나무를  " + treeHit + "번 찍었습니다.");
    if (treeHit == 10) {
        System.out.println("나무 넘어갑니다.");
    }
}
```
## while 문 break
```java
int coffee = 10;
int money = 300;

while (money > 0) {
    System.out.println("돈을 받았으니 커피를 줍니다.");
    coffee--;
    System.out.println("남은 커피의 양은 " + coffee + "입니다.");
    if (coffee == 0) {
        System.out.println("커피가 다 떨어졌습니다. 판매를 중지합니다.");
        break;
    }
}
```
## while 문 continue
```java
int a = 0;
while (a < 10) {
    a++;
    if (a % 2 == 0) {
        continue;  // 짝수인 경우 조건문으로 돌아간다.
    }
    System.out.println(a);  // 홀수만 출력된다.
}
```

## for문 (반복문)
```java
int[] marks = {90, 25, 67, 45, 80};
for(int i=0; i<marks.length; i++) {
    if (marks[i] < 60) {
        continue;  // 조건문으로 돌아간다.
    }
    System.out.println((i+1)+"번 학생 축하합니다. 합격입니다.");
}
```

## for each 문(반복문)
```java
String[] numbers = {"one", "two", "three"};
for(String number: numbers) {
    System.out.println(number);
}
```