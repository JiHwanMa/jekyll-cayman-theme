---
layout: default
title:  "C++ Operator_Overloading(ex2)"
date:   2017-08-18 17:42:00
categories: C++
---
## 단항 연산자 오버로딩 연습문제
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
		return *this;
	}
	friend Point& operator--(Point &pos);	

	Point& operator-(void) 
	{
		Point pos3(-1 * xpos, -1 * ypos);
		return pos3;
	}
	Point& operator~(void) 
	{
		Point pos3(~xpos, ~ypos);
		return pos3;
	}
};

Point& operator--(Point &pos)
{
	pos.xpos--; pos.ypos--;
	return pos;
}

int main()
{
	Point pos1(1, 5);
	Point pos2 = -pos1;
	Point pos3 = ~pos1;
	pos2.ShowPosition();
	pos3.ShowPosition();
	return 0;
}

```
