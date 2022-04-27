---
layout: single
title:  "Jquery data 속성으로 요소 검색하기"
date:   2022-03-11 10:36:52 +0900
tags: Javascript
categories: 
- Study
- Javascript
  
toc: false   #Table Of Contents 목차
toc_sticky: false
---

jquery를 사용할 때 자주 쓰는 기능이다

tag에 data 속성을 주고 제어할 때 주로 사용한다.

## html

```html
<div data-id ="test"> </div>
```

## js

```javascript
  $('[data-id="test"').addClass('add_class');
```

data-id 가 test 인 tag에 add_class 란 클래스를 추가한다.

## 응용?

li 나 여러 개의 div 중에 class 도 같고 그렇다고 일일이 id를 줄 수 있는 상황이 아닐 때 유용하다.