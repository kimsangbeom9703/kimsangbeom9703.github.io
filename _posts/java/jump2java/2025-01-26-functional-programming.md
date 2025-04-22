---
layout: single
title:  "[JAVA] 점프 투 자바 #26 함수형 프로그래밍"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 자바 #26] 

# 함수형 프로그래밍

자바는 버전8부터 함수형 프로그래밍을 지원하기 위해 람다와 스트림이 도입되었다.
람다와 스트림을 사용하여 작성한 코드를 일반 스타일의 자바 코드로 바꾸어 작성하는 것이 불가능하지는 않다.
그러나 람다와 스트림을 사용하는 이유는 코드의 양이 줄어들고 읽기 쉬운 코드로 만들 수 있다.

## 람다(lambda)
람다(lambda)는 익명 함수(anonymous function)를 의미한다. 
일반적인 코드와 람다를 적용한 코드를 비교하며 람다에 대해서 자세히 알아보자.

### 일반적인 코드
```java
interface Calculator {
    int sum(int a, int b);
}

class MyCalculator implements Calculator {
    public int sum(int a, int b) {
        return a+b;
    }
}

public class Sample {
    public static void main(String[] args) {
        MyCalculator mc = new MyCalculator();
        int result = mc.sum(3, 4);
        System.out.println(result);  // 7 출력
    }
}
```

### 람다를 적용한 코드
```java
interface Calculator {
    int sum(int a, int b);
}

public class Sample {
    public static void main(String[] args) {
        Calculator mc = (int a, int b) -> a +b;  // 람다를 적용한 코드
        int result = mc.sum(3, 4);
        System.out.println(result);
    }
}
```

괄호 사이의 int a, int b는 Calculator 인터페이스의 sum 함수의 입력 항목에 해당하고 -> 뒤의 a+b가 리턴값에 해당한다. 

이렇게 람다 함수를 사용하면 MyCalculator와 같은 실제 클래스 없이도 Calculator 객체를 생성할 수 있고, 일반적인 코드보다 훨씬 간단해진다.

### 인터페이스 사용 시 주의 사항

여기서 주의해야 할 점은 Calculator 인터페이스의 메서드가 1개 이상이면 람다 함수를 사용할 수 없다는 점이다

```java
interface Calculator {
    int sum(int a, int b);
    int mul(int a, int b);  // mul 메서드를 추가하면 컴파일 에러가 발생한다.
}
```

### 람다 축약하기
```java
interface Calculator {
    int sum(int a, int b);
}

public class Sample {
    public static void main(String[] args) {
        Calculator mc = (a, b) -> a +b;
        int result = mc.sum(3, 4);
        System.out.println(result);
    }
}
```

### 람다 더 축약하기
```java
@FunctionalInterface
interface Calculator {
    int sum(int a, int b);
}

public class Sample {
    public static void main(String[] args) {
        Calculator mc = Integer::sum;
        int result = mc.sum(3, 4);
        System.out.println(result);
    }
}
```

## 스트림

스트림(stream)은 글자 그대로 해석하면 ‘흐름’이라는 뜻이다.

데이터가 물결처럼 흘러가면서 필터링 과정을 통해 여러 번 변경되어 반환되기 때문에 이러한 이름을 갖게 되었다. 

다음 문제를 통해 스트림을 이해해 보자.
```java
import java.util.*;

public class Sample {
    public static void main(String[] args) {
        int[] data = {5, 6, 4, 2, 3, 1, 1, 2, 2, 4, 8};

        // 짝수만 포함하는 ArrayList 생성
        ArrayList<Integer> dataList = new ArrayList<>();
        for(int i=0; i<data.length; i++) {
            if(data[i] % 2 == 0) {
                dataList.add(data[i]);
            }
        }

        // Set을 사용하여 중복을 제거
        HashSet<Integer> dataSet = new HashSet<>(dataList);

        // Set을 다시 List로 변경
        ArrayList<Integer> distinctList = new ArrayList<>(dataSet);

        // 역순으로 정렬
        distinctList.sort(Comparator.reverseOrder());

        // Integer 리스트를 정수 배열로 변환
        int[] result = new int[distinctList.size()];
        for(int i=0; i< distinctList.size(); i++) {
            result[i] = distinctList.get(i);
        }
        System.out.println(Arrays.toString(result));
    }
}
```

## 스트림 사용
```java
import java.util.Arrays;
import java.util.Comparator;

public class Sample {
    public static void main(String[] args) {
        int[] data = {5, 6, 4, 2, 3, 1, 1, 2, 2, 4, 8};
        int[] result = Arrays.stream(data)  // IntStream을 생성한다.
                .boxed()  // IntStream을 Stream<Integer>로 변경한다.
                .filter((a) -> a % 2 == 0)  //  짝수만 뽑아낸다.
                .distinct()  // 중복을 제거한다.
                .sorted(Comparator.reverseOrder())  // 역순으로 정렬한다.
                .mapToInt(Integer::intValue)  // Stream<Integer>를 IntStream으로 변경한다.
                .toArray()  // int[] 배열로 반환한다.
                ;
        System.out.println(Arrays.toString(result));
    }
}
```
이 코드는 다음과 같은 순서로 동작한다.

1. Arrays.stream(data)로 정수 배열을 IntStream으로 생성한다.
2. .boxed()로 IntStream을 Integer의 Stream으로 변경한다. 이렇게 하는 이유는 뒤에서 사용할 Comparator.reverseOrder 메서드는 원시 타입인 int 대신 Integer를 사용해야 하기 때문이다.
3. .filter((a) -> a % 2 == 0)로 짝수만 필터링한다. 이때 사용한 (a) -> a % 2 == 0 구문은 앞에서 공부한 람다 함수이다. 입력 a가 짝수인지를 조사하는 람다 함수로 짝수에 해당되는 데이터만 필터링한다.
4. .distinct()로 스트림에서 중복을 제거한다.
5. .sorted(Comparator.reverseOrder())로 역순으로 정렬한다.
6. .mapToInt(Integer::intValue)로 Integer의 Stream을 IntStream으로 변경한다. 왜냐하면 최종적으로 int[] 타입의 배열을 리턴해야 하기 때문이다.
7. .toArray()를 호출하여 IntStream의 배열인 int[] 배열을 리턴한다.

스트림 방식은 일반적인 코드보다 확실히 간결하고 가독성이 좋다는 것을 확인할 수 있을 것이다.
```
사실 Arrays.stream처럼 스트림을 생성하고 boxed, filter, distinct, sorted, mapToInt처럼 스트림을 가공하고, 
toArray처럼 스트림을 원하는 형태로 반환하는 방법에는 이것 말고도 여러 가지가 있다.
하지만 이 책에서는 스트림을 이해하기 위한 목적으로 이와 같이 몇 가지만 알고 넘어가자.
```