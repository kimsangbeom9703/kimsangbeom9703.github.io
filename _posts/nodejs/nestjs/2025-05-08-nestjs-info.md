---
layout: single
title:  "[NestJS] 01. NestJs로 배우는 백엔드 프로그래밍 "
date:   2025-05-08 14:07:00 +0900
tags: NodeJS NestJS TypeScript
categories: 
- Study
- NodeJS
- NestJS

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# 1. NestJS란
```
NestJS는 Node.js 기반의 웹 API 프레임워크로, Express를 좀 더 체계적이고 구조적으로 발전시킨 형태라고 볼 수 있습니다.

Express는 가볍고 유연한 프레임워크이긴 하지만, 그만큼 개발자마다 설계 방식이 제각각이라 팀 단위 개발이나 장기적인 유지보수에는 다소 어려움이 있습니다.

NestJS는 이러한 문제점을 해결하기 위해 일정한 아키텍처 틀을 제공하고, TypeScript 기반으로 작성되어 정적 타입의 안정성과 풍부한 개발 경험을 함께 제공합니다.

또한 NestJS는 객체지향 프로그래밍(OOP), 함수형 프로그래밍(FP), 반응형 프로그래밍(RP) 등 여러 패러다임의 장점을 잘 녹여낸 현대적인 백엔드 프레임워크입니다.

```

# 2. Express VS NestJS

| 구분                | Express                                 | NestJS                               |
| ----------------- | --------------------------------------- | ------------------------------------ |
| **유연함 / 확장성**     | 가볍고 자유도 높아 빠른 프로토타입에 적합. 구조는 직접 설계해야 함. | 아키텍처와 기능이 내장되어 있어 구조적이고 유지보수에 유리함.   |
| **TypeScript 지원** | 기본은 JavaScript. TypeScript는 별도 설정 필요.   | 기본적으로 TypeScript 기반. 설정 없이 바로 사용 가능. |
| **커뮤니티**          | 오래된 만큼 가장 큰 커뮤니티 보유. 자료 풍부.             | 최근 빠르게 성장 중. 공식 문서도 활발히 개선되고 있음.     |


# 3. NodeJS기반 웹 프레임워크가 갖춰야 할 필수 기능

- ✅ 최신 ECMAScript 지원

- ✅ TypeScript (선택사항이지만 거의 필수화됨)

- ✅ CORS 처리

- ✅ HTTP 보안 헤더 (helmet 등 활용)

- ✅ 환경설정 (Configuration 관리)

- ✅ 인터셉터 (Interceptor)

- ✅ 미들웨어 (Middleware)

- ✅ 스케줄링 (Scheduling, 예: cron)

- ✅ 로깅 (Logging)

- ✅ 테스트 코드 작성 환경

- ✅ Swagger를 통한 API 문서화

- ✅ ORM 연동 (TypeORM, Prisma 등)