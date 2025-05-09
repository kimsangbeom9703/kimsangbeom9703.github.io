---
layout: single
title:  "[NestJS] 03.패키지 의존성 관리 "
date:   2025-05-10 09:30:00 +0900
tags: NodeJS NestJS TypeScript
categories: 
- Study
- NodeJS
- NestJS

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [NestJs로 배우는 백엔드 프로그래밍 - 03.패키지 의존성 관리] 

# package.json

- 애플리케이션이 필요로 하는 패키지 목록을 나열합니다.
- 각 패키지는 시맨틱 버저닝 규칙으로 필요한 버전을 기술합니다.
- 다른 개발자와 같은 빌드환경을 구성할 수 있습니다. 의존성 문제 예방

## 시맨틱 버저닝 규칙
```
[Major].[Minor].[Patch]-[label]
```
Major, Minor, Patch는 각각 숫자를 사용합니다. 예를 들어 1.2.3-beta 와 같이 표기합니다.
- Major: 이전 버전과 호환이 불가능할 때 숫자를 하나 증가시킵니다. Major 버전이 바뀐 패키지를 사용하고자 한다면 반드시 breaking change(하위 호환성이 깨진 기능) 목록을 확인하고 이전 기능을 사용하는 코드를 수정해야 합니다.
- Minor: 기능이 추가되는 경우 숫자를 증가시킵니다. 기능이 추가되었다고 해서 이전 버전의 하위 호환성을 깨뜨리지는 않습니다.
- Patch: 버그 수정 패치를 적용할 때 사용합니다.
- label(선택사항): pre, alpha, beta와 같이 버전에 대해 부가 설명을 붙이고자 할 때 문자열로 작성합니다.

# package-lock.json

프로젝트 루트 디렉토리에서 npm install 명령을 실행하면 node_modules 폴더와 package-lock.json 파일이 생성된다.

package-lock.json은 내가 설치한 패키지의 정확한 버전과 그 의존성 정보를 잠궈두는 파일이다.

package.json 과 package-lcok.json의 차이는 라이브러리 버전을 확인하려면 package.json을 보통 확인하는데 여기에 적혀있는
버전은 특정 버전이 아니라 버전의 범위이다.

비유를 하면

📦 package.json은 쇼핑 목록

🗃️ package-lock.json은 내가 실제로 산 물건의 영수증

- package.json: "express": "^4.18.0" → 4.18.0 이상, 5.0 미만이면 뭐든 OK!
- package-lock.json: "딱! 4.18.2 설치했음", 그리고 express가 쓰는 다른 패키지도 포함!

왜 필요한가?

1. 정확히 동일한 버전 재현 가능
→ 팀원이 npm install 했을 때 똑같은 버전 설치됨!

2. 배포/운영 서버에서도 동일 환경 보장
    → 예상치 못한 버그를 줄여줘.

3. 속도 향상
→ 캐싱이 잘 되고, 의존성 계산이 줄어들어 설치가 빨라짐


요약

| 파일                  | 역할                  | 예시                  |
| ------------------- | ------------------- | ------------------- |
| `package.json`      | 어떤 패키지를 쓸지          | `"axios": "^1.6.0"` |
| `package-lock.json` | 정확히 어떤 버전이 설치됐는지 기록 | `"axios": "1.6.1"`  |
