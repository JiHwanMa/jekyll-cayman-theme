---
layout: default
title:  "C++ Poly_Virtual_Function"
date:   2017-08-17 23:54:00
categories: C++
---

## 기초 클래스의 포인터로 객체를 참조할 경우 ?

```c
/*예를 들어 Base class와 Derived class가 존재한다고 가정하고 D class는 Base로부터 
public 상속을 받았다고 가정하자.*/
Base *ptr= new base;
Base *ptr2=new Derived;

ptr2->DerivedFunc(); //컴파일에러
//C++ 컴파일러는 포인터 연산의 가능성 여부를 판단 할 때, 포인터의 자료형을 기준으로 판단한다.
//따라서 ptr2의 자료형은 Base이므로 Base의 멤버함수만을 실행가능하다.
//즉 포인터가 실제 가리키는 대상이 기준이 아닌 포인터의 자료형을 기준으로 연산 가능성 여부를 판단한다.
```
이때 필요한 것이 Virtual Function(가상함수)이다.

## Virtual Function
~~~
코드로 직접 확인하자. 
~~~
```c

class First
{
public:
	virtual void MyFunc(){cout<<"FirstFunc"<<endl;}
};

class Second: public First
{
public:
	virtual void MyFunc(){cout<<"SecondFunc"<<endl;}

};
//이런식으로 virtual 선언을 함수 앞에 해줄 경우

int main()
{
First *fptr=new Second();
fptr->MyFunc();
}

```

```
SecondFunc
```
실제 가리키는 객체의 함수를 호출하게됨!

## 가상 소멸자 (Virtual Destructor)
```
virtual선언은 함수 외에도 소멸자에도 해주어야 한다.
객체 소멸 시 실제 포인터의 자료형에 해당하는 소멸자만 호출이 되기 때문에 문제가 발생 할 수 있다.
따라서 기초 클래스의 소멸자에 virtual 선언을 꼭 해줄 것!
```
