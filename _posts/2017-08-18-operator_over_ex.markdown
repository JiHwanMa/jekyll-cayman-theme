---
layout: default
title:  "C++ Operator_Overloading(exercise)"
date:   2017-08-18 15:42:00
categories: C++
---
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
	friend Point operator-(const Point &pos1, const Point &pos2);
	Point& operator+=(const Point &pos1) 
	{
		xpos += pos1.xpos;
		ypos += pos1.ypos;
		return *this;
	}
	Point& operator-=(const Point &pos1)
	{
		xpos -= pos1.xpos;
		ypos -= pos1.ypos;
		return *this;
	}
	friend bool operator==(const Point &pos1,const Point &pos2);
	friend bool operator!=(const Point &pos1, const Point &pos2);
};
Point operator+(const Point &pos1, const Point &pos2) 
{
	Point pos3(pos1.xpos+pos2.xpos,pos1.ypos+pos2.ypos);
	return pos3;
}//+연산자에 대해서 전역함수의 형태로 오버로딩한것.
Point operator-(const Point &pos1, const Point &pos2) 
{
	Point pos3(pos1.xpos - pos2.xpos, pos1.ypos - pos2.ypos);
	return pos3;
}
bool operator==(const Point &pos1, const Point &pos2) 
{
	return (pos1.xpos == pos2.xpos&&pos1.ypos == pos2.ypos);
}
bool operator!=(const Point &pos1, const Point &pos2)
{
	return !(pos1==pos2);
}

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
