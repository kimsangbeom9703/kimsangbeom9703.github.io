---
layout: single
title:  "PHP __construct 생성자"
date:   2022-03-25 16:00:00 +0900
tags: PHP 객체지향프로그래밍
categories: 
- Study
- PHP

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

## 설명
__construct 생성자라고도 하며 클래스에서 처음으로 호출되는 함수이다.

php 에서 클래스를 선언할 후에 인스턴스를 생성하게 되고 자동으로 호출되는 함수이다

주로 나같은 경우에는 생성자에 객체에서 공통으로 사용할 모델 , 렌더링될 view 를 선언하는 편이다.

```php
class Test 
{
    public function __construct(){
        $this->testModel        =   new TestModel();
        $this->data['footer']   =   view('test/include/footer' );
    }
}
```

## 예시

```php
class Testclass
{
  public $name ;
 
  function __construct ( $name )
  {
    $this->name = $name ;
  }
 
  public function name ()
  {
    print_r( "저의 이름은 { $this -> name } 입니다. );
  }
}
```
라고 쓰고 다른 클래스에서
```php
class Nameclass
{
  public  function index(){
    $testClass  =   new Testclass();
    $testNmae   =   $testClass->name('김상범');
    echo $testNmae; 
  }
}
```
호출하게 되면 결과는
```
저의 이름은 김상범 입니다.
```
라고 나온다.


## 부모의 생성자 호출

```php
class Testclass extends BigTestController
{
  function __construct ( $name )
  {
    parent::__construct();
  }
}
```
Testclass 에서 부모 즉 BigTestController 의 생성자를 호출할 수 있다.
```php
  abstract class BigTestController extends Controller
  {
	public function __construct()
    {
      $this->test = 'test';
    }
  }
```

```php
class Testclass extends BigTestController
{
  function __construct ( $name )
  {
    parent::__construct(); //부모의 생성자 사용
  }
  public function index(){
    echo $this->test;
  }
}
```
하면 test가 노출된다.
## 소멸자

📌 __destruct()

__construct() 즉 생성자 처럼 초기에 실행되는 메소드가 있다고 하면 반대로 php 의 모든 스크립트의 소스 실행이 끝나면 실행하는 __destruct() 메소드 함수가 있다.


## ❗마치며

조금씩 쌓이는 게시물을 보니 기분이 좋다.

시간을 더 내서 다음에는 더 자세한 객체지향 프로그래밍과  Modern PHP 를 적어봐야겠다.


