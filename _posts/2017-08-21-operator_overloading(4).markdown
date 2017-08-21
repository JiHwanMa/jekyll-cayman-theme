---
layout: default
title:  "C++ Operator_Overloading(4)-Arrclass"
date:   2017-08-21 15:11:00
categories: C++
---

## 배열 클래스

```
배열의 역할을 하는 클래스로써 배열과는 달리 경계검사를 추가할 수 있다.
해당 클래스가 배열같은 역할을 하기 위해서는 생성자 및 =연산자를 제대로 정의해주어야한다.
```

```c
#include<iostream>
using namespace std;

class Arrclass 
{
private:
	int *arr;
	int len;
public:
	Arrclass(int length) :len(length) 
	{
		arr = new int[length];
	}
	int& operator[](int idx) 
	{
		if (idx < 0 || idx >= len) 
		{
			cout << "범위를 초과하였습니다." << endl;
			exit(1);
		}
		return arr[idx];
	}
	~Arrclass() 
	{
		delete []arr;
	}
};
int main() 
{
	Arrclass arr(5);
	for (int i = 0; i < 5; i++) 
	{
		arr[i] = (i + 1) * 11;
	}
	for (int i = 0; i < 6; i++)
	{
		cout << arr[i] << endl;
	}
	return 0;
}
```
