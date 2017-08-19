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
### 후위증가 Code
```c
const Point operator++(int)
{
	const Point retobj(xpos,ypos);
    xpos+=1;
    ypos+=1;
    return retobj;
}

const Point operator--(Point &ref,int)
{
	const Point retobj(ref);
	ref.xpos-=1;
	ref.ypos-=1;
	return retobj;
}

//code를 보면 우선 증가하기 이전의 값을 복사해 놓은 후
//객체의 값을 증가시키고 마지막으로 복사해 놓은 값을 리턴해줌으로써
//후위증가의 효과를 내는 것을 알 수 있다.
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
	//*this를 Reference를 이용해서 반환해야 ++(++pos)같은 연산이 가능!!
	}
	friend Point& operator--(Point &pos);	
};

Point& operator--(Point &pos)
{
	pos.xpos--; pos.ypos--;
	return pos;
}

```
