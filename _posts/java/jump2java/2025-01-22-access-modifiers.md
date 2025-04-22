---
layout: single
title:  "[JAVA] 점프 투 자바 #22 접근 제어자"
date:   2025-04-22 14:07:00 +0900
tags: JAVA
categories: 
- Study
- JAVA

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [JAVA - 점프 투 자바 #22] 

# 접근 제어자

- private
- default
- protected
- public

## 접근 허용 범위
```
private < default < protected < public
```

## private
private 붙은 변수나 메서드는 해당 클래스 안에서만 접근이 가능하다.
```
public class Sample {
    private String secret;
    private String getSecret() {
        return this.secret;
    }
}
```

## default
접근 제어자를 별도로 설정하지 않는다면 변수나 메서드는 

default 접근 제어자가 자동으로 설정되어 동일한 패키지 안에서만 접근이 가능하다.

## protected

동일 패키지의 클래스 또는 해당 클래스를 상속받은 클래스에서만 접근이 가능하다.

### house/HousePark.java
```
package house;  // 패키지가 서로 다르다.

public class HousePark {
    protected String lastname = "park";
}
```
### house/person/EungYongPark.java
```
package house.person;  // 패키지가 서로 다르다.

import house.HousePark;

public class EungYongPark extends HousePark {  // HousePark을 상속했다.
    public static void main(String[] args) {
        EungYongPark eyp = new EungYongPark();
        System.out.println(eyp.lastname);  // 상속한 클래스의 protected 변수는 접근이 가능하다.
    }
}
```

## public
접근 제어자가 public으로 설정되었다면 public 접근 제어자가 붙은 변수나 메서드는 어떤 클래스에서도 접근이 가능하다.
```java
package house;

public class HousePark {
    protected String lastname = "park";
    public String info = "this is public message.";
}
```
```java
import house.HousePark;

public class Sample {
    public static void main(String[] args) {
        HousePark housePark = new HousePark();
        System.out.println(housePark.info);
    }
}
```