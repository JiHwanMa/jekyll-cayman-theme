---
layout: default
title:  "C++ function overloading"
date:   2017-08-15 20:00:00
categories: C++
---

# C++ Function overloading

## 함수 오버로딩이란?
`
C++은 함수의 이름만을 이용하여 호출함수를 찾는 C언어와 달리 호출대상을 함수의
이름과 매개변수의 선언을 이용하여 찾는다. 따라서 함수호출 시 전달되는 인자를 
통하여 호출하고자 하는 함수의 구분이 가능하므로 같은 이름, 다른 매개변수를 
갖는 서로 다른 역할을 하는 함수를 선언할 수 있다. 
단 함수 오버로딩은 매개변수는 바꾸어 구현하지만 반환형은 일치하여야 한다.  
`

~~~c
int Func(int num) 
 num++;
 return num;
int Func(int a, int b) 

 return a + b;

 //함수 오버로딩의 잘못된 예.
 void Func(int num) 
 cout<<"call func"<<endl;
~~~
