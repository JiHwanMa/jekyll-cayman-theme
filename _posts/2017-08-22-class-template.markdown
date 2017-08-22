---
layout: default
title:  "C++ Class Template"
date:   2017-08-22 15:08:00
categories: C++
---

## 클래스 템플릿
```
제공되는 기능과 내부의 행동이 모두 동일한데, 저장의 대상이 다르다는 이유만으로
유사한 클래스를 세 개 씩이나 정의한다는 것은 불합리하게 느껴진다. 
이럴 때는 클래스 템플릿을 정의해서 이러한 불합리한 점을 해결할 수 있다.
하나의 클래스 템플릿정의 -> 자료형만 변환시켜줌.
```

```c
#include<iostream>
using namespace std;

template<typename T>
class Point 
{
private:
	T xpos, ypos;
public:
	Point(T n1 = (T)0, T n2 = (T)0) :xpos(n1), ypos(n2) {}
	void Showdata() const 
	{
		cout << "[" << xpos << "," << ypos << "]" << endl;
	}
};

int main(void) 
{
	Point<int> pos1(1, 2);
	Point<char> pos2('a', 'b');
	pos1.Showdata();
	pos2.Showdata();
	return 0;
}
```

## 클래스 템플릿의 선언과 정의의 분리

클래스 템플릿도 멤버함수를 **클래스 외부에 정의**하는 것이 가능하다. 
예를 들어서 다음과 같이 정의된 클래스 템플릿이 있다면 아래와 같이 정의하자.

```c
template<typename T>
class SimpleTemplate
{
public:
	T SimpleFunc(const T& ref);
}

//외부에 정의
template<typename T>
T SimpleTemplate<T>::SimpleFunc(const T& ref){}

```

```
단 파일을 나눌 때는 cpp,h모두를 메인함수에 넣어주어야된다.
왜냐하면 템플릿함수는 컴파일러가 함수 템플릿을 이용하여 파일 단위로 생성하기 때문에
~.h만으로는 생성이 불가하다. 따라서 둘 다 포함시켜줄 것!!!
```
