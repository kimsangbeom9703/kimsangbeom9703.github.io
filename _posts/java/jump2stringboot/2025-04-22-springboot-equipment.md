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

# 롬복 (Lombok)

## 1. Getter와 Setter란?

객체지향 프로그래밍에서 **Getter**와 **Setter**는 클래스의 필드에 안전하게 접근하고 값을 읽거나 설정할 수 있도록 도와주는 메서드입니다.

### ✅ Getter
- 필드의 값을 읽어오는 메서드
- 메서드 이름은 일반적으로 `get`으로 시작

```java
public class Person {
    private String name;

    public String getName() {
        return name;
    }
}
```

### ✅ Setter
- 필드의 값을 설정하는 메서드
- 메서드 이름은 일반적으로 `set`으로 시작

```java
public class Person {
    private String name;

    public void setName(String name) {
        this.name = name;
    }
}
```

### ✅ 전체 사용 예시
```java
public class Person {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person();
        person.setName("John");
        System.out.println(person.getName());
    }
}
```

---

## 2. Lombok이란?

**Lombok**은 Java 코드에서 **Getter**, **Setter**, **toString**, **Constructor** 등 반복적인 코드를 자동으로 생성해주는 라이브러리입니다.  
클래스에 어노테이션만 붙이면 해당 메서드들이 자동 생성되어 코드가 훨씬 간결해집니다.

---

## 설치 방법 
```

```

## 3. Lombok의 @Getter, @Setter

### ✨ 사용 방법
```java
import lombok.Getter;
import lombok.Setter;

@Getter
@Setter
public class Person {
    private String name;
    private int age;
}
```

위 코드에 Lombok을 적용하면 다음과 같은 메서드들이 자동 생성됩니다:

- `getName()`, `getAge()`
- `setName(String name)`, `setAge(int age)`

---

## 4. Lombok 사용 예시

```java
import lombok.Getter;
import lombok.Setter;

@Getter
@Setter
public class Person {
    private String name;
    private int age;
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person();
        person.setName("John");
        person.setAge(25);

        System.out.println(person.getName());
        System.out.println(person.getAge());
    }
}
```

---

## ✅ 정리

| 항목         | 설명                                |
|--------------|-------------------------------------|
| **@Getter**  | 필드의 Getter 메서드를 자동 생성    |
| **@Setter**  | 필드의 Setter 메서드를 자동 생성    |
| **장점**     | 반복 코드 감소, 가독성 향상, 유지보수 용이 |

---
