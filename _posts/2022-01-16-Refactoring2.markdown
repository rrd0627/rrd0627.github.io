---
layout: post
title: Refactoring 2
date: 2022-01-16 23:16:07 +0900
category: Refactoring
---
### 코드에서 꼴보기싫은거!

<br>

### 이상한이름!

이름을 기가막히게 깔끔하게 지어야함

1. 함수 선언 바꾸기
1. 변수 이름 바꾸기
1. 필드 이름 바꾸기  

<br>

### 중복 코드

똑같은 구조가 여러곳에서 반복되면 하나로 통합!

1. 함수 추출하기
1. 문장 슬라이드하기
1. 메서드 올리기

<br>

### 긴 함수

간접 호출로 코드를 이해하기 쉽게 만듦

1. 함수 추출하기
1. 임시변수를 질의함수로 바꾸기
1. 매개변수 객체 만들기
1. 객체 통째로 넘기기
1. 함수를 명령으로 바꾸기
1. 조건문 분해하기
1. 조건문을 다형성으로 바꾸기
1. 반복문 쪼개기

<br>

### 긴 매개변수 목록

매개변수 길어지면 이해하기 어려워짐

1. 매개변수를 질의 함수로 바구기
1. 객체 통째로 넘기기
1. 매개변수 객체 만들기
1. 플래그 인수 제거하기
1. 여러함수를 클래스로 묶기


<br>

### 전역 데이터

어디서든 건들수 있기때문에 원인 코드를 알아내기 어려워짐.

1. 변수 캡슐화하기


<br>

### 가변 데이터



<br>

### 뒤엉킨 변경


이러한 것들을 앞으로 배우는 리팩터링 기법으로 처리할것!