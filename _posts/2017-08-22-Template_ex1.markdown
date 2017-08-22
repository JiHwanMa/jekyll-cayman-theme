---
layout: default
title:  "C++ Template_Ex1"
date:   2017-08-22 14:21:00
categories: C++
---

## 문제1
```
인자로 전달되는 두 변수에 저장된 값을 서로 교환하는 SwapData라는 이름의 함수를 템플릿으로 정의해보자.
그 후 main함수에서 확인해보자.
```

```c
#include<iostream>
using namespace std;

class Point 
{
private:
	int xpos, ypos;
public:
	Point(int x = 0, int y = 0) :xpos(x), ypos(y) {}
	Point() { xpos = 0; ypos = 0; }
	void ShowPosition() const
	{
		cout << "[" << xpos << "," << ypos << "]" << endl;
	}
	template<typename T>
	void SwapData()
	{
		T temp = xpos;
		xpos = ypos;
		ypos = temp;
	}
};

int main(void) 
{
	Point pos(1, 2);
	pos.SwapData<int>();
	pos.ShowPosition();
	return 0;
}
```
