---
layout: single
title:  "CodeIgniter4 Pagination 코드이그나이터 페이징"
date:   2022-03-25 14:53:52 +0900
tags: PHP CodeIgniter4 CI4
categories: 
- Study
- PHP

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

CodeIgniter4 즉 CI4 는 단순하지만 유연한 페이지네이션 라이브러리를 제공한다.

페이지네이션은 페이징 이라고도 하는데 게시물 갯수에 맞게 사용자가 원하는 길이에 맞춰 나누어서 보여주는 방식이다.

사용하는 이유는 많은 데이터를 한 화면에 전부 보기에는 가독성이 좋지않기 때문에 사용한다.

예전에는 라이브러리를 제공받지 못하면 DB 에서 데이터를 SELECT 할때 offset 과 limit 를 계산해서 일일이 만들어 줬어야했다.

```
  limit   = 노출할 데이터 수
  offset  = 데이터 시작 위치
```

## 쿼리결과 페이지네이션

모델 클래스에 내장된 paginate() 메소드를 사용하면 된다.

사용법은 
```php
ex)
    $data = $this->model->paginate(10);
```
이게 끝이다.. 되게 간단하게 사용할 수 있다.

paginate 메소드 안에 있는 숫자는 노출할 데이터 수이다.

## 여러결과 페이지네이션
나는 주로
```php
ex)
    $data = $this->model->paginate(10,'admin');
```
이렇게 사용하는데 저기서 admin 은 그룹명이다.
그룹명을 지정하는 이유는 

📌사실 이거때문에 글을 쓰려고 했다.

하나의 페이지에서 서로 다른 결과의 데이터를 페이징 해야 하는 경우가 있다.

그룹을 지정하지 않는 경우 페이징 이동시 두 결과 모두 페이징 되기 때문에 그룹으로 나누어 줘야한다.


## 정리

paginate() 는 findAll() 메소드의 기능을 가지고 있다고 보면 된다.

```php
ex)
  $data = [
    'data'    =>  $this->model->paginate(10),   //10개의 데이터.
    'pager'   =>  $this->model->pager,      //페이징 링크.
  ];
  echo view('test/index', $data);
```
이런식으로 view 에 data를 전달하면 view 에서는

```php
  <?=$pager->links();?>
```

입력하면 페이징이 노출된다.

간단한 출력을 원하면 simpleLinks() 을 사용하면된다.

위에서 말했던 여러 결과에 대한 페이징을 하려면

```php
ex)
  $testData  = $this->model->paginate(10,'test');
  $testData2 = $this->model->paginate(10,'test2');

    $data = [
    'testData'      =>  $this->model->paginate(10,'test'),
    'testPager'     =>  $this->model->pager,
    'testData2'     =>  $this->model->paginate(10,'test1'),
    'testPager2'    =>  $this->model->pager,
  ];
  echo view('test/index', $data);
```
view
```php
  <?=$testPager->links('test');?>
  <?=$testPager2->links('test1');?>
```
으로 사용하면된다.


## 📌링크사용자 정의

뷰를 사이트에 맞게 바꿔 줘야 될 경우가 있다.

- view 구성

  - 링크가 페이지에 렌더링 되면서 보이는 view 파일 수정하기 위해서는 app/Config/Pager.php 파일을 편집하면 된다.
  ```php
      public $templates = [
          'default_full'   => 'CodeIgniter\Pager\Views\default_full',   //기본
          'default_simple' => 'CodeIgniter\Pager\Views\default_simple', //기본
          'test'           => 'App\Views\test\page\test_page', //추가
      ];
  ```
  테스트 변수를 추가했고 이제는 view 파일을 만들어보자.

  ```php
      <?php $pager->setSurroundCount(5) ?>
      <nav aria-label="<?= lang('Pager.pageNavigation') ?>">
          <ul class="pagination">
              <li class="page-item"><a class="page-link" href="<?= $pager->getFirst() ?>">First</a></li>
              <li class="page-item"><a class="page-link" href="<?= $pager->getPreviousPage() ?>">Previous</a></li>
              <?php foreach ($pager->links() as $link) : ?>
                  <li class="page-item <?= $link['active'] ? 'active' : '' ?>"><a class="page-link" href="<?= $link['uri'] ?>"><?= $link['title'] ?></a></li>
              <?php endforeach ?>
              <li class="page-item"><a class="page-link" href="<?= $pager->getNextPage() ?>">Next</a></li>
              <li class="page-item"><a class="page-link" href="<?= $pager->getLast() ?>">Last</a></li>
          </ul>
      </nav>
  ```
  이런식으로 view 파일을 만들어 준다.

- 렌더링
  - 만든 파일로 페이징 결과를 렌더링 하고 싶으면 
  ```php
    <?=$testPager->links('test','test');?>
  ```
  이렇게 입력하면된다.


## ❗마치며
CI4 의 페이징에 대해 간단히 알아봤는데 정말 쉽고 간편하게 라이브러리가 제공되는 거 같아서 행복하다~~

더욱 써보고 부족하거나 좋은 기능이 있으면 추가하겠습니다!

