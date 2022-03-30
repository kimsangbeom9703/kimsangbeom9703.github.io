---
layout: single
title:  "CodeIgniter4 구성(configuration) 파일 팁 - 1"
date:   2022-03-30 10:58:52 +0900
tags: PHP CodeIgniter4 CI4
categories:
- Study
- PHP
  
toc: false   #Table Of Contents 목차
toc_sticky: false
---
CI4 를 사용하다 보면 .env 파일 즉 구성파일을 사용하여 매개변수 및 초기 설정을 한다.

간단하게 📌일부만 살펴보면

```
  # CI_ENVIRONMENT = production
  CI_ENVIRONMENT = development
  #app.baseURL = 'http://127.0.0.1:8000/';
  app.defaultLocale = 'ko';
  app.appTimezone = 'Asia/Seoul';
  app.indexPage = '';
  app.appName = '테스트';
  app.admin_logo = 'logo.gif';
  #--------------------------------------------------------------------
  # DATABASE
  #--------------------------------------------------------------------
  
  database.default.hostname = localhost
  database.default.database = test
  database.default.username = test_manager
  database.default.password = 'test1234'
  database.default.DBDriver = MySQLi
```
이런식으로 되어있다.

```
  CI_ENVIRONMENT  = production or development //서비스환경인지 개발환경인지.
  
  app.baseURL = 'http://127.0.0.1:8000/'; //app의 기본url 
  app.defaultLocale = 'ko'; //언어셋
  app.appTimezone = 'Asia/Seoul'; //시간존
  app.indexPage = ''; //기본페이지
  
  app.appName = '테스트'; 
  app.adminLogo = 'logo.png';  
```
등으로 볼 수 있고 app.appName , app.adminLogo 와 같이 변수를 정의할 수 있다.

보통 나는 env에 정의하고 다른 서비스에서도 공통으로 사용하는 곳에 사용하고 있다.
예를 들면 관리자 페이지의 로그인 페이지 같은 경우 서비스명을 제외하면 폼의 형태는 비슷하기 때문이다.


```html
ex)
<div class="login_footer">
	<img src="/assets/images/<?=env('app.admin_logo')?>">
</div>
```
이렇게 사용했는데 문제가 생겼다.❗❗❗
새로고침을 계속 하다보면 ci4 에서 env 파일을 못읽는건지 선언한 변수가 깨져서 오는거였다.

그래서 수정방법으로
```php
  getenv();
```
를 사용했지만 ci4 에서 사용한 function 에서도 getenv()를 사용하고 있어 같은 문제점이 발생했다.

현재는

```php
  $_ENV['app.admin_logo'];
```
를 사용하고 있는데 아직까지는 문제가 발견되지 않고있다. 

## ❗마치며

계속된 문제가 생긴다면 또 다른 방법으로 해결해 업데이트해야겠다...



