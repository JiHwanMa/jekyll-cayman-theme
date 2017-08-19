---
layout: default
title:  "C++ Operator_Overloading(2)"
date:   2017-08-18 17:25:00
categories: C++
---

## 단항 연산자의 오버로딩

```
전위
			pos.operator++(); 멤버함수로 오버로딩
++pos;
			operator++(pos); 전역함수로 오버로딩
```
```
후위(int)
			pos.operator++(int); 멤버함수로 오버로딩
pos++; 
			operator++(pos,int); 전역함수로 오버로딩

```
### Code
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
	Point& operator++() 
	{
		xpos++; ypos++;
		return *this; //this는 객체자신의 포인터 값을 의미하므로, *this는 객체자신을 의미한다.
	}
	friend Point& operator--(Point &pos);	
};

Point& operator--(Point &pos)
{
	pos.xpos--; pos.ypos--;
	return pos;
}

```
