---
layout: default
title:  "C++ Exception_Handling_Stack_Unwinding"
date:   2017-08-24 15:18:00
categories: C++
---

## Stack Unwinding
```
예외가 처리되지 않아서, 함수를 호출한 영역으로 예외 데이터가 전달되는 현상을 가리켜
'스택 풀기'라고 한다. 다음의 예제코드를 보자.
```

```c
#include<iostream>
using namespace std;

void SimpleFuncone(void);
void SimpleFunctwo(void);
void SimpleFuncthree(void);

int main() 
{
	try 
	{
		SimpleFuncone();
	}
	catch (int expn) 
	{
	
		cout << "예외코드: " << expn << endl;
	}
	return 0;
}

void SimpleFuncone(void) 
{
	cout << "SimpleOne" << endl;
	SimpleFunctwo();
}
void SimpleFunctwo(void) 
{
	cout << "SimpleTwo" << endl;
	SimpleFuncthree();
}
void SimpleFuncthree(void) 
{
	cout << "SimpleThree" << endl;
	throw - 1;
}

```

SimpleFuncThree스택
---
SimpleFuncTwo스택
---
SimpleFuncOne스택
---
main 스택
---
```
스택이 쌓이는 방향과 예외 데이터가 전달되면서 스택이 해제되는 순서는 반대이다.
결국 main함수에서까지 처리하지 못할 경우 terminate 함수가 호출되면서 프로그램이 종료된다.
```

### 하나의 try블록과 여러개의 Catch블록또한 사용가능하다.
```
catch함수를 오버로딩하듯이 다른 매개변수에 대해서 정의해주면 된다.
이때 catch순서는 명시된 순서와 일치하므로 순서가 중요하다.
```

### 전달되는 예외의 명시
```
함수 내에서 발생할 수 있는 예외의 종류도 함수의 특징으로 간주된다. 따라서 함수를 정의할 때에는
함수 내에서 발생 가능한 예외의 종류를 다음과 같이 명시해 주는 것이 좋다.
```

```c
int ThrowFunc(int num) throw (int,char)


try
{
	...
	ThrowFunc(20);
	...
}

catch(int expn){}
catch(char expn){}

//만약 아래와같이 명시하면 예외 전달 시 바로 terminate호출
int SimpleFunc(void) throw()
{
...
}
```

## 예외 클래스와 예외객체

```
예외발생을 알리는데 사용되는 객체를 가리켜 '예외객체'라 하며, 예외객체의 생성을 위해 정의된 클래스를
'예외 클래스'라 한다.
```

### new 연산자에 의해서 발생하는 예외
```
공간이 부족하면 bad_alloc 라는 예외가 발생.
이때 catch(bad_alloc &bad){}로 처리해줄것
```

### 모든 예외를 처리하는 catch 블록
```
catch(...)//...은 발생하는 모든 예외를 다 받아주겠다는 선언. 별로 좋지는 않음.

```

### 예외 던지기
```
catch블록에 의해 전달된 예외는 다시 던져질 수 있다.
```
