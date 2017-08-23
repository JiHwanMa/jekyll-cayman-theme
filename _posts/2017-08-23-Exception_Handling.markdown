---
layout: default
title:  "C++ Exception_handling"
date:   2017-08-23 20:00:00
categories: C++
---


## 예외처리란?

```
예외상황이란 프로그램 실행 중에 발생하는 문제의 상황을 의미한다.
예)
나이를 입력하라고했는데 0보다 작은 값이 입력됨.
```
**즉 예외는 문법적 오류가 아닌, 프로그램 논리에 맞지 않는 오류를 뜻한다.**

## If문을 이용한 예외의 처리

```c
#include<iostream>
using namespace std;

int main()
{
int num1,num2;
cout<<"input two numbers"<<endl;
cin>>num1>>num2;//예외가 발생하는 위치

if(num2==0)//예외를 발견하는 위치
{
	cout<<"Error!"<<endl; //예외를 처리하는 위치
}
else
{
	cout<<num1/num2<<endl; 
	cout<<"num1%num2<<endl;"
}
return 0;
}
```

```

단점 : 예외처리를 위한 코드와 프로그램의 흐름을 구성하는 코드를 쉽게 구분하지 못한다.
따라서 C++은 별도의 예외처리 메커니즘을 제공하고 있다.
```
