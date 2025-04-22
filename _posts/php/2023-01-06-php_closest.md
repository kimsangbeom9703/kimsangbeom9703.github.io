---
layout: single
title:  "[PHP] 배열에서 가장 가까운 수 구하기"
date:   2023-01-06 09:00:00 +0900
tags: PHP 
categories: 
- Study
- PHP

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

## 설명
``
  배열에서 특정 값과 가장 가까운 수를 구하는 경우가 많다.
``

## 소스

```php
      function getClosest($search,$arr){
          $closest = null;
          foreach ($arr as $item) {
              if($closest === null || abs($search-$closest) > abs($item - $search) ){
                  $closest = $item;
              }
          }
          return $closest;
      }
```

## 풀이

```php
  $callArrays = ['0210','0510','0810','1110','1410','1710','2010','2310']; 
  $search = '1200';
  $return = getClosest($search,$callArrays);
  echo $return // 1110
```
