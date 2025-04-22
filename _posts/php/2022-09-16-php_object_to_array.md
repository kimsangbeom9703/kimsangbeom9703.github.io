---
layout: single
title:  "PHP 객체를 배열로 변경하기 - 1차원 , 다차원 ( object to array )"
date:   2022-09-16 09:00:52 +0900
tags: Study PHP
categories:
- Study
- PHP

toc: true   #Table Of Contents 목차
toc_sticky: true
---

## 포스팅 하는 이유
```text

공개된 API를 사용하다 보면 그 API를 내 입맛에 맞게 변경하거나 내가 맞춰야 하는 경우가 있다.
객체를 배열로 변경하는 방법은 간단하지만 그래도 자주 까먹으니 적어두자!

```
## 📌 해결


```php
    $object     =   curl($url) // api 를 호출한 예를 나타냄.
    $apiReturn  =   (array)$object ;    
```
이렇게 간단히 객체를 배열로 변경할 수 있다.

## ❓❓ 다차원 배열이라면 ❓❓

```php
    $object     =   curl($url) // api 를 호출한 예를 나타냄.
    $apiReturn  =   (array)$object ;    
```

다차원 배열인 경우 위 상태와 동일하게 진행한다면 부모 배열 즉 1차원 배열만 객체가 배열로 변경되고 하위 배열은 변경되지 않는다.

## 📌 해결


```php
    $object     =   curl($url) // api 를 호출한 예를 나타냄.
    $apiReturn  =   json_decode (json_encode ($object), true);  
```

이렇게 하면 다차원 배열도 편리하게 바꿀 수 있다!!

## 마치며

되게 간단한 내용이지만 그래도 도움이 됐으면 좋겠다~!
