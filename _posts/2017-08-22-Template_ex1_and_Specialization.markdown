---
layout: default
title:  "C++ Template_Ex1 & Specialization"
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

## 문제2

```
배열의 합을 구하는 Sumarray라는 함수를 템플릿을 이용하여 정의해보자.
```
```c
#include<iostream>
using namespace std;
template<typename T>
T SumArray(T arr[], int len) 
{
	T sum = 0;
	for (int i = 0; i < len; i++) 
	{
		sum += arr[i];
	}
	return sum;
}
```

## 함수 템플릿의 특수화(Specialization)
```
특정 상황의 경우 템플릿만으로는 해결되지 않아 사용자가 직접 해당 경우에 대해 정의해야 한다.
이 경우 정의된 함수 템플릿의 내부 특정 부분을 함수 템플릿의 특수화라고 한다.
아래는 예제코드 이다.
```

```c
#include<iostream>
#include<cstring>
using namespace std;

template<typename T>
T Max(T a, T b) 
{
	return a > b ? a : b;
}

template<>
char* Max(char* a, char* b) 
{
	cout << "char* Max<char*>(char* a,char* b)" << endl;
	return strlen(a) > strlen(b) ? a : b;
}

template<>
const char* Max(const char* a, const char *b) 
{
	cout << "const char* Max<const char* a,const char* b>" << endl;
	return strcmp(a, b) > 0 ? a : b;
}

int main() 
{
	cout << Max(11, 15) << endl;
	cout << Max('T', 'Q') << endl;
	cout << Max("Simle", "Best") << endl;
	// 문자열 선은으로 인해 반환되는 주소 값의 포인터 형은 const char*
	
	char str1[] = "Simple";
	char str2[] = "Best";
	cout << Max(str1, str2) << endl;
	//변수의 형태로 선언된 str1,str2의 포인터 형은 char*
	return 0;
}
```
