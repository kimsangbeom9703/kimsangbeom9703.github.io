---
layout: single
title:  "[PHP] 두 날짜의 차이 구하기"
date:   2022-12-14 09:00:00 +0900
tags: PHP 날짜차이
categories: 
- Study
- PHP

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

## 설명
``
  간단하지만 은근 유용하게 사용하기 때문에 잘 기억해두자!
``

## 소스

```php
  $first_date  = new DateTime('2022-12-14'); 
  $second_date = new DateTime('2022-12-16');
  $diff_value  = date_diff($first_date, $second_date);
  echo $diff_value->days; // 2
```

## 풀이

```php
  var_dump($diff_value);
  object(DateInterval)#155 (16) {
    ["y"]=> 
    int(0)
    ["m"]=>
    int(0)
    ["d"]=>
    int(2)
    ["h"]=>
    int(0)
    ["i"]=>
    int(0)
    ["s"]=>
    int(0)
    ["f"]=>
    float(0)
    ["weekday"]=>
    int(0)
    ["weekday_behavior"]=>
    int(0)
    ["first_last_day_of"]=>
    int(0)
    ["invert"]=>
    int(0)
    ["days"]=>
    int(2)
    ["special_type"]=>
    int(0)
    ["special_amount"]=>
    int(0)
    ["have_weekday_relative"]=>
    int(0)
    ["have_special_relative"]=>
    int(0)
  }
  필요한 값들은 골라서 사용하면 된다
```
