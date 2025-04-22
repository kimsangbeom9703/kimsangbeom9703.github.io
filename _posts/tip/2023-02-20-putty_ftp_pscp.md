---
layout: single
title:  "[Tip] Putty 사용하여 리눅스 에서 윈도우로 파일 가져오기"
date:   2023-02-20 09:00:00 +0900
tags: Tip 리눅스 윈도우 ftp
categories: 
- Study
- Tip

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

## 설명
``
개발을 하다보면 서버에 파일을 업로드 하거나 다운받아야 되는 상황이 무조건 생기는데 파일질라 같은 ftp 프로그램을 사용하면 쉽지만
중간에 서버를 거쳐서 가는 경우나 접속을 못하게 해놓는 경우가 있다.
``

## 다운로드

```
  C:\Program Files\PuTTY>pscp 사용자@서버:파일명 다운받을경로/파일명
  pscp [옵션] [서버 계정@ ip주소 : 소스파일 경로 및 파일명] [다운받을 경로]
```
포트가 22번이 아닐경우

```
  C:\Program Files\PuTTY>pscp -P 포트 사용자@서버:파일명 다운받을경로/파일명
```

## 업로드

```
   C:\Program Files\PuTTY>pscp 옵션 업로드할 파일 및 경로 사용자@서버:업로드할 경로 
```


