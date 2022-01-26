---
layout: post
title: Refactoring 5
date: 2022-01-25 00:37:09 +0900
category: Refactoring
---
## 데이터 조직화

<br>

### 변수 쪼개기

변수에는 대입을 한번만 하기!

여러번 대입하면 혼란스러움

### 필드 이름 바꾸기

햇갈리지 않는 기가막히는 이름

### 파생 변수를 질의 함수로 바꾸기

### 참조를 값으로 바꾸기

아무곳이나 사용할 수 있어서 좋지만 특정 객체를 여러 객체에서 공유하는 경우는 쓰면 안됨

### 값을 참조로 바꾸기

객체를 공유하는 경우에는 참조로 바꾸어 사용

### 매직 리터럴 바꾸기

상수를 정의하거나 함수를 활용

<br>
<br>

## 조건부 로직 간소화

<br>

### 조건문 분해하기

조건식 부분이 복잡하다면 따로 때어서 함수로 만들고

조건이 만족햇을떄 로직도 함수로 호출

### 조건식 통합하기

조건식들을 논리 연산자로 결합하기

### 중첩 조건문을 보호구문으로 바꾸기

if else 어쩌구 하지말고

if(one)return 1;
if(two)return 2;
if(three)return 3;

### 조건부 로직을 다형성(클래스)로 바꾸기

```csharp
Switch(number)
case 1:
    return 1;
// 어쩌구 하는걸

class one
{
    getNumber(){return 1;}
}
```

### 특이 케이스 추가하기

예를들어 널값 체크후 어떤 동작을 수행하는 코드 가 있으면 

해당하는 곳에 함수로 바꾸어 동작까지 하기!

### 어서션 추가하기

Debug.Assert(조건식, "콘솔내용");

디버그 모드에서 활용되는 반드시 참이여야만 하는 내용!

해당 조건식에 들어간다면 프로그램 정지됨

### 제어 플래그를 탈출문으로 바꾸기

반복문에서 break continue return 을 통해서 탈출 할것!

이상한 변수로 하지말고



<br>

## 조건부 로직 간소화

<br>

### 질의 함수와 변경 함수 분리하기

읽기 함수는 오직 읽기만 하기

변경 (쓰기) 함수는 오직 쓰기만 하기

### 함수 매개변수화 하기

```csharp
void PlusOne()
{
    number+=1;
}
void PlusTwo()
{
    number+=2;
}

//이걸 아래처럼 바꾸기

void PlusNumber(int num)
{
    number+=num;
}
```

### 플래그 인수 제거하기

```csharp
if(isOne)
{
    func(1);
}
else if(isTwo)
{
    func(2);
}

//이걸 아래처럼 바꾸기

void oneFunc();
void twoFunc();
```

### 객체 통째로 넘기기

```csharp
width = rect.width;
height = rect.height;
SetSize(width,height);
//이걸 아래처럼 바꾸기

SetSize(rect);
```

### 세터 제거하기

생성자에서만 필드를 수정한뒤에 세터를 제거하여 값이 바뀌면 안된다는 뜻을 넣음

### 생성자를 팩터리 함수로 바꾸기

```csharp
Junior = new Employee(person.Junior);
//이걸 아래처럼 바꾸기
Junior = createPerson(person.Junior);
```

### 함수를 명령으로 바꾸기

객체내에 함수를 활용하는 것... 이름이 왜이래?

### 명령을 함수로 바꾸기

위에 함수가 매우 간단하다면 클래스내부의 함수로 쓰지말고 바로 함수로 사용

### 수정된 값 반환하기

```csharp
int number =0;
Calculate();
void Calculate()
{
    number++;
}

//이걸 아래처럼 바꾸기
int number = Calculate();
void Calculate()
{
    int retNum =0;
    retNum++;
    return retNum;
}
```


<br>

## 상속 다루기

<br>

### 슈퍼클래스 추출하기

비슷한 일을 하는 두 클래스는 상속 메커니즘을 활용한다.

