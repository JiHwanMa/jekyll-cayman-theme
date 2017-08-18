---
layout: default
title:  "C++ Operator_Overloading(1)"
date:   2017-08-18 15:00:00
categories: C++
---

## 연산자 오버로딩

~~~
'operator' (Keyword) + 'operator(+,-,*,/...)'
ex] operator+
이런식으로 둘을 묶어서 함수의 이름을 정의하면, 함수의 이름을 이용한
함수의 호출뿐만 아니라, 연산자를 이용한 함수의 호출도 허용한다.
ex]pos1+pos2 == pos1.operator+(pos2)
좌측의 명령어가 우측의 명령어로 실행이 된다.
~~~
### 즉 아래와 같이 변환이된다.
```
pos1+pos2
1.pos1 2.+ 3.pos2 ;
1.:(pos1) 2.:(.operator+) 3.:pos2
pos1.operator+(pos2)
```

## 연산자를 오버로딩 하는 두 가지 방법
```
1.멤버함수에 의한 연산자 오버로딩
    pos1.operator+(pos2);
2.전역함수에 의한 연산자 오버로딩
    operator+(pos1,pos2);
  이때 멤버함수에 의한 연산자 오버로딩이 전역함수에 의한 것보다 우선시됨.
```
### 전역함수에 의한 연산자 오버로딩ex
```c 
#include<iostream>
using namespace std;

class Point 
{
private:
	int xpos;
	int ypos;
public:
	Point(int x = 0, int y = 0) :xpos(x), ypos(y) {}
	void ShowPosition() const 
	{
		cout << '[' << xpos << ',' << ypos << ']' << endl;
	}
	friend Point operator+(const Point &pos1, const Point &pos2);
	//operator+ 함수는 private 영역의 멤버변수에 접근해야하므로 friend선언이 필요하다.
};
Point operator+(const Point &pos1, const Point &pos2) 
{
	Point pos3(pos1.xpos+pos2.xpos,pos1.ypos+pos2.ypos);
	return pos3;
}//+연산자에 대해서 전역함수의 형태로 오버로딩한것.
int main() 
{
	Point pos1(3, 4);
	Point pos2(10, 20);
	Point pos3 = pos1 + pos2;

	pos1.ShowPosition();
	pos2.ShowPosition();
	pos3.ShowPosition();
	return 0;
}
```
