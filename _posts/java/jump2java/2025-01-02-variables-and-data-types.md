---
layout: single
title:  "[JAVA] 점프 투 자바 #2 변수와 자료형"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---
# [JAVA - 점프 투 자바 #2] 

## 변수와 자료형

```java
int a;
String b;
```

변수 이름을 지을 때 지켜야 할 규칙
1. 변수명은 숫자로 시작할 수 없다.
2. `_`와 `$` 이외의 특수 문자는 사용할 수 없다.
3. `int,class,return` 등 자바의 키워드는 변수명으로 사용할 수 없다.

**피해야 할 키워드**
```
abstract  continue  for         new        switch
assert    default   goto        package    synchronized
boolean   do        if          private    this
break     double    implements  protected  throw
byte      else      import      public     throws
case      enum      instanceof  return     transient
catch     extends   int         short      try
char      final     interface   static     void
class     finally   long        strictfp   volatile
const     float     native      super      while
```

**자주 쓰이는 자료형**
```
int
long
double
boolean
char
String
StringBuffer
List
Map
Set
```

### `int`
- 정수를 저장하는 자료형 (32비트, 약 -21억 ~ 21억)
- 예:  
  ```java
  int num = 100;
  ```

### `long`
- 더 큰 정수를 저장하는 자료형 (64비트)
- 예:  
  ```java
  long bigNum = 10000000000L; // 'L'을 붙여야 함
  ```

### `double`
- 실수를 저장하는 자료형 (64비트, 부동소수점)
- 예:  
  ```java
  double pi = 3.14159;
  ```

### `boolean`
- 참(`true`) 또는 거짓(`false`) 값을 저장하는 자료형
- 예:  
  ```java
  boolean isOn = true;
  ```

### `char`
- 한 개의 문자를 저장하는 자료형 (16비트 유니코드 문자)
- 예:  
  ```java
  char grade = 'A';
  ```

## 참조 자료형 (Reference Types)

### `String`
- 문자열을 저장하는 클래스 (불변, `immutable`)
- 예:  
  ```java
  String name = "Java";
  String greeting = "Hello, " + name;
  ```

### `StringBuffer`
- 가변(`mutable`) 문자열을 다룰 수 있는 클래스 (멀티쓰레드 환경에서 안전)
- 예:  
  ```java
  StringBuffer sb = new StringBuffer("Hello");
  sb.append(" World"); // 문자열 수정 가능
  ```

## 컬렉션 프레임워크 (Collection Framework)

### `List` (인터페이스, 대표 구현체: `ArrayList`, `LinkedList`)
- 순서가 있는 데이터 저장 구조 (중복 허용)
- 예:  
  ```java
  List<String> list = new ArrayList<>();
  list.add("A");
  list.add("B");
  ```

### `Map` (인터페이스, 대표 구현체: `HashMap`, `TreeMap`)
- 키-값(`key-value`) 쌍을 저장하는 자료구조 (키 중복 불가, 값 중복 가능)
- 예:  
  ```java
  Map<String, Integer> map = new HashMap<>();
  map.put("Apple", 1000);
  map.put("Banana", 2000);
  ```

### `Set` (인터페이스, 대표 구현체: `HashSet`, `TreeSet`)
- 중복을 허용하지 않는 데이터 저장 구조
- 예:  
  ```java
  Set<Integer> set = new HashSet<>();
  set.add(1);
  set.add(2);
  set.add(2); // 중복이므로 추가되지 않음
  ```

