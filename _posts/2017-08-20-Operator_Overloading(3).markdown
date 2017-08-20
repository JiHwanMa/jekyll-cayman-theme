---
layout: default
title:  "C++ Operator_Overloading(3)"
date:   2017-08-20 21:28:00
categories: C++
---

## 객체간 대입연산 -> 디폴트 대입 연산자

## 복사 생성자
```
1.정의하지 않으면 디폴트 복사 생성자가 삽입된다.
2.디폴트 복사 생성자는 **멤버 대 멤버의 복사(얕은 복사)**를 진행한다.
3.생성자 내에서 **동적 할당**을 한다면, 그리고 **깊은 복사**가 필요하다면 **직접 정의**해야 한다.
```
### 대입 연산자
```
1.정의하지 않으면 **디폴트 대입 연산자**가 삽입된다.
2.디폴트 대입 연산자는 멤버 대 멤버의 복사(얕은 복사)를 진행한다.
3.연산자 내에서 동적 할당을 한다면, 그리고 깊은 복사가 필요하다면 직접 정의해야 한다.
4.**이미 생성 및 초기화가 진행된 객체간의 대입연산때 호출됨.**
```
**둘이 매우 유사함**

**차이는 호출되는 시점**

**Default 대입 연산자의 Code**
```c
Classname& operator=(const Classname& ref)
{
//대입연산
return *this;
}
```

### 디폴트 대입연산자의 문제점.
```
1.얕은 복사 : 깊은 복사가 이뤄지도록 정의 할 것.
2.상속 시 문제 : 유도 클래스에 기초 클래스의 대입 연산자를 명시하지 않으면
 기초 클래스의 대입 연산자가 호출되지 않음. 따라서 명시적으로 호출 해야함
```
## 얕은 복사 해결코드 예제.
```c
#include<iostream>
#include<cstring>

using namespace std;

class Person 
{
private:
	char *name;
	int age;
public:
	Person(char *Myname, int Myage) :age(Myage) 
	{
		name = new char[strlen(Myname) + 1];
		strcpy(name, Myname);
	}
	void ShowInfo() 
	{
		cout << "이름: " << name << endl;
		cout << "나이: " << age << endl;
	}
	Person& operator=(const Person& ref)
	{
		delete[]name; //우선 메모리누수방지를 위해 삭제
		char *name = new char[strlen(ref.name) + 1];//메모리 새로 할당
		strcpy(name, ref.name);//그곳에 복사
		age = ref.age;
		return *this;//a=b=c;같은 코드를 실행시킬 수 있게하려면 객체를 참조자로 반환.
	}
	~Person() 
	{
		delete []name;
	}
};
```

## 상속 시 문제 해결코드
```c
#include<iostream>
using namespace std;

class First 
{
private:
	int num1, num2;

public:
	First(int temp1=0, int temp2=0) :num1(temp1), num2(temp2) 
	{}
	void Showdata() 
	{
		cout << num1 << "," << num2 << endl;
	}
	First& operator=(const First& ref) 
	{
		num1 = ref.num1;
		num2 = ref.num2;
		return *this;
	}
};

class Second :public First 
{
private:
	int num3, num4;
public:
	Second(int temp1,int temp2,int temp3 = 0, int temp4 = 0) :First(temp1,temp2),num3(temp3), num4(temp4) {}
	void Showdata() 
	{
		First::Showdata();
		cout << num3 << "," << num4 << endl;
	}
	Second& operator=(const Second& ref) 
	{
		First::operator=(ref);//기초 클래스의 대입 연산자 호출을 명령! 이 코드가 핵심
		num3 = ref.num3;
		num4 = ref.num4;
		return *this;
	}
};

int main(void) 
{
	Second ssrc(111, 222, 333, 444);
	Second scpy(0, 0, 0, 0);
	scpy = ssrc;
	scpy.Showdata();
	return 0;
}
```

```
유도 클래스의 대입 연산자 정의에서, 명시적으로 기초 클래스의 대입 연산자 호출문을 삽입하지 않으면,
기초 클래스의 대입 연산자는 호출되지 않아서, 기초 클래스의 멤버변수는 멤버 대 멤버의 복사 대상에서
제외된다.
```
