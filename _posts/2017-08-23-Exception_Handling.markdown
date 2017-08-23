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


## C++의 예외처리 메커니즘

```
try   : 예외를 발견한다.
catch : 예외를 잡는다.
throw : 예외를 던진다.

```

```c
try
{
....
if(예외가 발생한다면)
	{
    throw expn;
    }
....

}

catch(type exn)
{
	//예외의 처리 ->try블록에서 발생하는 예외는
    //이어서 등장하는 catch 블록에 의해 처리된다.
}
```

Code
```c
#include<iostream>
using namespace std;

int main() 
{
	int num1, num2;
	cout << "2 inputs" << endl;
	cin >> num1 >> num2;

	try 
	{
		if (num2 == 0) 
		{
			throw num2;
		}
		cout << num1 / num2 << endl;
		cout << num1%num2 << endl;
	}
	catch (int expn) 
	{
		cout << "제수는 " << expn << "이 될 수 없습니다." << endl;
		cout << "다 시 실 행~" << endl;
	}
	cout << "end of main" << endl;
	return 0;
}
```

```
실행의 흐름은 try 블록 안으로 들어간다. 그 안에서 예외가 발생하면 이후에 등장하는 catch 블록을 실행하게 된다.
예외가 발생하지 않으면 try 블록을 빠져 나와  try ~catch 블록 이후를 실행하게 된다.
따라서 try 블록을 잘 설정해서 묶을 것.!
```

