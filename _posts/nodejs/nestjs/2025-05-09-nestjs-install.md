---
layout: single
title:  "[NestJS] 02. NestJs 설치 "
date:   2025-05-09 09:30:00 +0900
tags: NodeJS NestJS TypeScript
categories: 
- Study
- NodeJS
- NestJS

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [NestJs로 배우는 백엔드 프로그래밍 - 02.설치하기] 

# 설치하기

## 1. Node.js 설치

NestJS는 Nodejs 기반으로 돌아가기 때문에 [공식 페이지](https://nodejs.org/ko/download/) 에서 다운받는다.

안정적인 버전인 LTS버전을 선택하자.


## 2. NestJS 설치
```BASH
npm i -g @nestjs/cli // nestjs 전역설치
```
```
nest new project-name

npm
yarn
중 패키지 매니저를 고를 수 있다

cd 프로젝트명
npm run start

```

## 팁
[깃허브 다운로드](https://github.com/nestjs/typescript-starter) 여기에서 다운을 받으면 nest new로 프로젝트를 셋업한 것 보다 더 최신 버전의 라이브러리들로 구성해 준다.
```
$ git clone https://github.com/dextto/book-nestjs-backend.git
$ cd book-nestjs-backend/examples/ch1-intro/
$ npm install  // 필요한 패키지를 설치합니다.
$ npm run start
```

### 주의사항
```
운영 서버가 아닌 개발 단계에서는 npm run start:dev 명령어를 이용하시길 바랍니다.
package.json에 기술된 스크립트를 보면 "start:dev": "nest start --watch" 라고 되어 있습니다.
—watch 옵션으로 소스코드 변경을 감지하여 코드를 저장할 때 마다 서버를 다시 구동시켜 줍니다.
```