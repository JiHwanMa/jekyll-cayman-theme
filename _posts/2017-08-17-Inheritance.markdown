---
layout: default
title:  "C++ Inheritance(Basic)"
date:   2017-08-17 23:00:00
categories: C++
---

## Inheritance(상속)

```c
//Univ클래스가 Person클래스를 상속한다.
class Person{}

class Univ :public Person
{}
```
~~~
univ클래스는 Person클래스의 모든 멤버를 물려받는다.
모든 멤버에는 멤버변수 뿐 아니라 멤버함수도 포함한다.
~~~

## 상속받은 클래스의 생성자 정의
~~~
상속받은 클래스의 생성자는 2가지로 분류된다.
첫번째로 상속받은 멤버변수에 대해서는 해당 클래스의 생성자를 사용하며
그 외의 멤버변수에 대해서는 추가로 생성자에 정의한다.
~~~
```c
#include<iostream>
using namespace std;

class Person 
{
private:
	int age;
	char name[50];
public:
	Person(int Myage, char *name) :age(Myage)
	{
		strcpy(this->name, name);
	}
	void WhatYourname() const 
	{
		cout << "My name is " << name << endl;
	}
	void HowoldAreYou() const 
	{
		cout << "i'm " << age << "years old" << endl;
	}
};

class UnivStudent :public Person 
{
private:
	char major[50];
public:
	UnivStudent(int myage, char *myname, char *mymajor):Person(myage,myname)
	{
		strcpy(major, mymajor);
	}//상속받은 클래스의 생성자
	//부모클래스에서 상속받은 멤버변수는 부모클래스의 생성자로 초기화.
	void WhoAreYou() const 
	{
		WhatYourname();
		HowoldAreYou();
		cout << "My major is " << major << endl << endl;
	}
};
```

## 유도 클래스의 객체 생성
1.유도 클래스의 객체생성 과정에서 기초 클래스의 생성자는 100%호출된다.
2.유도 클래스의 생성자에서 기초 클래스의 생성자 호출을 명시하지 않으면, 기초 클래스의 void 생성자가 호출된다.

## 유도 클래스 객체의 소멸과정
1.유도 클래스의 객체가 소멸될 때에는, 유도 클래스의 소멸자가 실행되고 난 다음에 기초 클래스의 소멸자가 실행.
2.스택에 생성된 객체의 소멸순서는 생성순서와 반대이다.
3.생성자에서 동적 할당한 메모리 공간은 소멸자에서 해제한다.
