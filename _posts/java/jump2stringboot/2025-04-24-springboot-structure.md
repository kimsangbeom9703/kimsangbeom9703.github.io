---
layout: single
title:  "[JAVA] 점프 투 스프링부트 #3 스프링부트 프로젝트 구조"
date:   2025-04-22 14:07:00 +0900
tags: JAVA SpringBoot
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 스프링부트 #03]

# 📁 스프링 부트 프로젝트 구조

```
jump2springboot
├── .gradle/
├── .idea/
├── build/
├── gradle/
│   └── wrapper/
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── ksb.jump2springboot/
│   │   │       ├── HelloController.java
│   │   │       └── Jump2springbootApplication.java
│   │   └── resources/
|   |   |   └── static
|   |   |   └── templates
|   |   |   └── application.properties
│   └── test/
│       └── java/
│           └── ksb.jump2springboot/
│               └── Jump2springbootApplicationTests.java
├── .gitattributes
├── .gitignore
├── build.gradle
├── gradlew
├── gradlew.bat
├── HELP.md
└── settings.gradle
```

## src/main/java
```
src/main/java 디렉터리는 자바 파일을 저장하는 공간이다.
```

## ksb/jump2springboot/
```
이 패키지는 ksb의 자바 파일을 저장하는 공간이다 .
HelloController.java와 같은 스프링 부트의 컨트롤러, 폼과 DTO, 데이터베이스 처리를 위한 엔티티, 서비스 등의 자바 파일이 이 곳에 위치한다.

    컨트롤러는 URL 요청을 처리하고 폼은 사용자의 입력을 검증한다. 
    DTO, 엔티티, 서비스 파일은 데이터베이스를 처리하기 위해 필요한 파일이다
```

## Jump2springbootApplication.java
```
프로그램의 시작을 담당하는 파일
클래스에는 반드시 @SpringBootApplication 애너테이션이 적용되어 있어야 한다. 
@SpringBootApplication 애너테이션을 통해 스프링 부트 애플리케이션을 시작할 수 있다.
```

# src/main/resources
```
src/main/resources 디렉터리는 자바 파일을 제외한 HTML, CSS, 자바스크립트, 환경 파일 등을 저장하는 공간이다.
```

## templates 디렉터리
```
src/main/resources 디렉터리의 하위 디렉터리인 templates에는 템플릿 파일을 저장한다.
템플릿 파일은 자바 코드를 삽입할 수 있는 HTML 형식의 파일로, 스프링 부트에서 생성한 자바 객체를 HTML 형태로 출력할 수 있다.
```
## static 디렉터리
```
static 디렉터리에는 프로젝트의 스타일시트(css 파일), 자바스크립트(js 파일) 그리고 이미지 파일(jpg 파일, png 파일 등) 등을 저장한다.
```
## application.properties
```
프로젝트의 환경 변수, 데이터베이스 등의 설정을 이 파일에 저장한다.
```
## src/test/java 디렉터리
```
src/test/java 디렉터리는 프로젝트에서 작성한 파일을 테스트하는 코드를 저장하는 공간이다. 
JUnit과 스프링 부트의 테스트 도구를 사용하여 서버를 실행하지 않은 상태에서 src/main/java 디렉터리에 작성한 코드를 테스트할 수 있다.

    JUnit은 테스트 코드를 작성하고, 작성한 테스트 코드를 실행할 때 사용하는 자바의 테스트 프레임워크이다.
```
## build.gradle 파일
```
build.gradle은 그레이들(Gradle)이 사용하는 환경 파일이다. 그레이들은 그루비(Groovy)를 기반으로 한 빌드 도구로 Ant, Maven과 같은 이전 세대의 단점을 보완하고 장점을 취합하여 만들었다. build.gradle 파일에는 프로젝트에 필요한 플러그인과 라이브러리를 설치하기 위한 내용을 작성한다.

    그루비는 그레이들 빌드 스크립트를 작성하는 데 사용하는 스크립트 언어로, 문법이 간결하고 가독성이 높다.
    빌드 도구는 소스 코드를 컴파일하고 필요한 라이브러리를 내려받을 때 사용한다.
    프로젝트를 완성하면 단 한 개의 jar 파일로 패키징하여 서버에 배포할 수 있는데 이때에도 역시 빌드 도구를 사용한다.
```
## 실무에 많이 쓰이는 구조
```
src/
└── main/
    ├── java/
    │   └── com/example/myapp/
    │       ├── MyAppApplication.java     ← 메인 클래스
    │
    │       ├── config/                   ← 설정 클래스 (Swagger, Security 등)
    │       │   └── SwaggerConfig.java
    │
    │       ├── controller/               ← REST API 컨트롤러
    │       │   └── UserController.java
    │
    │       ├── service/                  ← 비즈니스 로직
    │       │   ├── UserService.java
    │       │   └── impl/
    │       │       └── UserServiceImpl.java
    │
    │       ├── repository/               ← DB 접근 (JPA)
    │       │   └── UserRepository.java
    │
    │       ├── entity/                   ← JPA Entity
    │       │   └── User.java
    │
    │       ├── dto/                      ← 요청/응답용 DTO
    │       │   ├── UserRequestDto.java
    │       │   └── UserResponseDto.java
    │
    │       ├── exception/                ← 예외 처리 관련
    │       │   ├── GlobalExceptionHandler.java
    │       │   └── UserNotFoundException.java
    │
    │       └── util/                     ← 유틸 클래스
    │           └── DateUtil.java
    │
    └── resources/
        ├── application.properties (또는 application.yml)
        └── static/      ← 정적 파일 (html, js, css)
        └── templates/   ← 템플릿 파일 (Thymeleaf 등)
```