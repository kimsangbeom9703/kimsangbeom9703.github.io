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

# 📁 스프링 부트 프로젝트 구조 - 계층형

```plaintext
jump2springboot/
├── build.gradle
├── settings.gradle
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/project/
│   │   │       ├── ProjectApplication.java       // 메인 클래스
│   │   │       ├── config/                       // 설정 (Security, Swagger 등)
│   │   │       ├── controller/                   // API 컨트롤러
│   │   │       ├── service/                      // 비즈니스 로직
│   │   │       │   └── impl/                     // 서비스 구현체
│   │   │       ├── repository/                   // JPA Repository
│   │   │       ├── entity/                       // DB Entity
│   │   │       ├── dto/                          // DTO 객체
│   │   │       ├── exception/                    // 예외 처리
│   │   │       └── util/                         // 유틸 클래스
│   │   └── resources/
│   │       ├── static/                           // 정적 자원 (css, js, img)
│   │       ├── templates/                        // HTML 템플릿 (Thymeleaf)
│   │       └── application.properties            // 환경 설정 파일
│   └── test/
│       └── java/com/example/project/             // 테스트 코드
```

---

## 📁 도메인 기반 폴더 예시: `Users`, `Board`, `Comment`

```plaintext
src/main/java/com/example/project/
├── users/
│   ├── controller/
│   │   └── UsersController.java
│   ├── service/
│   │   └── UsersService.java
│   ├── repository/
│   │   └── UsersRepository.java
│   ├── dto/
│   │   ├── UsersRequestDto.java
│   │   └── UsersResponseDto.java
│   └── entity/
│       └── Users.java

├── board/
│   ├── controller/
│   │   └── BoardController.java
│   ├── service/
│   │   └── BoardService.java
│   ├── repository/
│   │   └── BoardRepository.java
│   ├── dto/
│   │   ├── BoardRequestDto.java
│   │   └── BoardResponseDto.java
│   └── entity/
│       └── Board.java

├── comment/
│   ├── controller/
│   │   └── CommentController.java
│   ├── service/
│   │   └── CommentService.java
│   ├── repository/
│   │   └── CommentRepository.java
│   ├── dto/
│   │   ├── CommentRequestDto.java
│   │   └── CommentResponseDto.java
│   └── entity/
│       └── Comment.java
└── resources/
    ├── static/                 # 정적 파일 (css, js, img 등)
    ├── templates/              # 템플릿 파일 (Thymeleaf 등)
    ├── application.properties  # 환경 설정 파일
```

---

## 📝 핵심 용어 정리

| 용어        | 설명                                                                 |
|-------------|----------------------------------------------------------------------|
| Entity      | DB 테이블과 매핑되는 클래스. `@Entity`, `@Id` 사용                    |
| DTO         | 계층 간 데이터 전달용 클래스. 외부에 노출될 구조만 포함              |
| Controller  | URL 요청을 받고 응답을 처리하는 계층                                 |
| Service     | 비즈니스 로직을 처리. Controller가 호출                              |
| Repository  | DB 접근을 담당. JpaRepository, CrudRepository 상속                   |
| Config      | 설정 클래스들. Swagger, Security, WebMvc 등                          |
| Exception   | 예외 처리 관련 클래스. 전역 예외 처리기 포함                         |
| Templates   | 동적 HTML 생성용 템플릿 (Thymeleaf)                                   |
| Static      | 정적 리소스 파일(css, js, img 등)                                    |
