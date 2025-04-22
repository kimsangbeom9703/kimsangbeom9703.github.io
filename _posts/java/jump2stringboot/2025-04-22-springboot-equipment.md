---
layout: single
title:  "[JAVA] 점프 투 스프링부트 #2 스프링부트 도구 설치하기"
date:   2025-04-22 14:07:00 +0900
tags: JAVA SpringBoot
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 스프링부트 #02]

# 스프링 부트도구 설정하기

## 기존 HelloController
```java
package sysmate.jump2springboot;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class HelloController {
    @GetMapping("/hello")
    @ResponseBody
    public String hello() {
        return "Hello World";
    }
}
```

## 수정
```java
package sysmate.jump2springboot;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
public class HelloController {
    @GetMapping("/hello")
    @ResponseBody
    public String hello() {
        return "Hello KSB";
    }
}
```

이렇게 수정을 해도 서버를 재시작하지 않는 경우 적용 되지 않는다.

이러한 문제를 해결하려면 Spring Boot Devtools를 설치해야 한다.

build.gradle 파일을 수정하자

* STS를 설치할 때 Gradle-Groovy를 선택하였기 때문에 build.gradle파일을 수정해야 한다.

## build.gradle
```java
plugins {
    id 'java'
    id 'org.springframework.boot' version '3.4.4'
    id 'io.spring.dependency-management' version '1.1.7'
}

group = 'sysmate'
version = '0.0.1-SNAPSHOT'

java {
    toolchain {
        languageVersion = JavaLanguageVersion.of(21)
    }
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
    testRuntimeOnly 'org.junit.platform:junit-platform-launcher'
    developmentOnly 'org.springframework.boot:spring-boot-devtools' //추가
}

tasks.named('test') {
    useJUnitPlatform()
}
```
* developmentOnly: 해당 라이브러리는 개발 환경에만 적용된다는 의미로, 운영 환경에 배포되는 jar, war 파일에는 이 라이브러리가 포함되지 않는다.

나는 인텔리제이로 개발하기 때문에

## 라이브러리 설치
```
build.gradle 파일을 선택한 후 마우스 오른쪽 버튼을 눌러 [Gradle → Refresh Gradle Project]를 클릭하여 필요한 라이브러리를 설치해야 한다.
```
## 설정
```
컨트롤러 코드를 바꿨다면 .class 파일이 재빌드돼야 DevTools가 인식합니다.

IntelliJ 상단 메뉴에서:
File > Settings > Build, Execution, Deployment > Compiler

[✔] Build project automatically 체크

그리고 같은 메뉴에서: Advanced Settings (오른쪽 아래)

[✔] Allow auto-make to start even if developed application is currently running 체크
```

# 롬복

## 롬복이란?
```
롬복을 알기전에 getter , setter 를 먼저 알자

Getter와 Setter는 객체지향 프로그래밍에서 클래스의 속성(필드)을 외부에서 안전하게 접근하고 수정할 수 있도록 하는 메서드이다.
```

# 1. Getter
* Getter는 필드의 값을 읽어오는 메서드입니다.
* 주로 **get**으로 시작하는 메서드 이름을 가집니다.
* 클래스 내부에서 값을 저장한 후, 외부에서 그 값을 읽기 위해 사용됩니다.

## 예시
```java
public class Person {
    private String name; // 필드

    // Getter 메서드
    public String getName() {
        return name; // 필드의 값을 반환
    }
}
getName()을 호출하면, name 필드의 값을 읽을 수 있습니다.
```
# 2. Setter
* Setter는 필드의 값을 설정하는 메서드입니다.
* 주로 **set**으로 시작하는 메서드 이름을 가집니다.
* 외부에서 값을 입력받아, 클래스 내부의 필드에 값을 설정하는 데 사용됩니다.
## 예시
```java
public class Person {
    private String name; // 필드

    // Setter 메서드
    public void setName(String name) {
        this.name = name; // 필드에 값을 설정
    }
}
setName("John")을 호출하면, name 필드에 **"John"**이라는 값을 설정할 수 있습니다.
```

## 전체 예시
```java
public class Person {
    private String name; // 필드

    // Getter 메서드
    public String getName() {
        return name;
    }

    // Setter 메서드
    public void setName(String name) {
        this.name = name;
    }
}
```
## 사용법
```java
public class Main {
    public static void main(String[] args) {
        Person person = new Person(); // 객체 생성
        person.setName("John");       // Setter로 name 설정
        System.out.println(person.getName()); // Getter로 name 읽기
    }
}
```

## 롬복이란
```
Lombok은 getter와 setter를 자동으로 만들어주는 라이브러리입니다. 자바에서는 클래스에 필드를 선언하고 그에 대한 getter와 setter를 일일이 작성해야 하는데, Lombok을 사용하면 이 과정을 자동화할 수 있다.
```

# 1. Lombok의 @Getter, @Setter

* @Getter: getter 메서드를 자동으로 생성
* @Setter: setter 메서드를 자동으로 생성

## 롬복 사용 예시

### 롬복 없이 작성한 코드
```java
public class Person {
    private String name; // 필드
    private int age;     // 필드

    // Getter 메서드
    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    // Setter 메서드
    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```
### 롬복을 사용한 코드
```java
import lombok.Getter;
import lombok.Setter;

@Getter  // 자동으로 getter 메서드 생성
@Setter  // 자동으로 setter 메서드 생성
public class Person {
    private String name; // 필드
    private int age;     // 필드
}
```
위처럼 @Getter와 @Setter를 클래스에만 붙여주면, 자동으로 아래와 같은 메서드들이 생성됩니다:

* getName()
* getAge()
* setName(String name)
* setAge(int age)

# 2. Lombok의 사용법

* @Getter와 @Setter는 필드를 자동으로 읽고 쓸 수 있게 해주는 어노테이션입니다.
* 롬복을 사용하면 메서드를 직접 작성할 필요 없이, 자동으로 생성되기 때문에 코드가 간결해집니다.

# 3. 예시 사용
```java
import lombok.Getter;
import lombok.Setter;

@Getter  // getter 메서드를 자동으로 생성
@Setter  // setter 메서드를 자동으로 생성
public class Person {
    private String name; // 필드
    private int age;     // 필드
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person(); // Person 객체 생성
        person.setName("John");       // setter로 name 설정
        person.setAge(25);            // setter로 age 설정

        System.out.println(person.getName()); // getter로 name 읽기
        System.out.println(person.getAge());  // getter로 age 읽기
    }
}
```

# 4. @Getter와 @Setter만 있는 클래스에서의 메서드 사용
```
위 코드에서 볼 수 있듯이, Lombok을 사용하면 getName()과 setName()을 직접 작성하지 않고도 쉽게 속성에 접근할 수 있습니다.
```