---
layout: default
title:  "Structure_and_Class"
date:   2017-08-15 20:00:00
categories: c++
---

## 구조체(structure)란?
```
연관 있는 데이터를 묶을 수 있는 문법적 장치.
ex)
namespace CAR_CONST
{
enum{name_length=20,basefuel=10}
해당 구조체에서 쓰이는 상수를 namespace이용하여 분류 뒤 열거한것
};

struct Car
{
char ID[20];int fuel;int curspeed;
void initCar(){ID="base";fuel=100;curspeed=0;}
구조체 내부에 함수를 삽입함으로써 보다 확실한 구분 가능
}
Car Mycar={"Good",100,0};
```
 
## 구조체->Class
~~~~
차이: struct선언을 사용할 경우 별도의 접근제어지시자를 사용하지 않을 경우 public으로 설정.
class선언은 private로 설정.->정보 은닉(information hiding)과 관련
~~~~
## 접근제어지시자
~~~~~
public: 어디서든 접근을 허용
protected: 상속관계에 놓여있을 때, 유도 클래스에서 접근 허용
private: 클래스 내에서만 접근을 허용
~~~~~

## 객체(Object)
~~~~~~
이제 class는 변수의 성격만을 가진 것이 아니므로 객체 라고 부를것임.
class= 멤버변수+멤버함수
~~~~~~
## C++에서의 파일분할
~~~~
car.h(헤더파일) ->클래스의 선언 및 인라인함수.
car.cpp(cpp파일)->클래스의 정의
~~~~

## 객체지향 프로그래밍이란?
~~
현실에 존재하는 사물,대상, 그에 따른 행동을 있는 그대로 실체화시키는 형태의 프로그래밍!
객체(Object) =하나이상의 정보(Data,변수로 표현) + 하나 이상의 행동(function,함수로 표현)
~~ 
## C++에서 정의하고 있는 두가지 객체생성 방법.
~~~
1.일반적인 변수의 선언방식  ClassName objName
2.동적 할당방식(by heap)    ClassName *objptr=new ClassName;
~~~
## 객체간의 대화 방법(Message Passing)

~~~~~
객체가 다른 하나의 객체에게 메세지를 전달하는 방법은 함수호출을 기반으로 함
~~~~~~
