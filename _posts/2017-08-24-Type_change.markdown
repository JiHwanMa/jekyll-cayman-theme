---
layout: default
title:  "C++ Type_Change in C++"
date:   2017-08-24 16:00:00
categories: C++
---

## C++에서의 형 변환

### dynamic_cast
```
상속관계에서의 안전한 형 변환.
상속관계에 놓여 있는 두 클래스 사이에서 유도 클래스의 포인터 및 참조형 데이터를
기초 클래스의 포인터 및 참조형 데이터로 형 변환하는 경우.

class Car{}
class Truck :public Car{}
Car* pcar=new Truck(80,200);  // Car형 포인터
Truck* ptruck=dynamic_cast<Truck*>(pcar);//컴파일 에러 (Car->Truck)으로 형변환은 안됨 
```

### static_cast
```
A type에서 B type으로 변환. 가급적 사용하지 x 것.
주로 기본 자료형 데이터간의 형 변환에 사용.
double result=static_cast<double>(20)/3;
```

### const_cast
```
Const의 성향을 삭제하는 형변환.
const char* name="Lee Sung";
ShowSTring(const_cast<char*>(name));//ShowSTring은 const선언이 안된 함수이다. 하지만 변환을 이용하여 호출
```

### reinterpret_cast
```
상관없는 자료형으로의 형 변환
포인터를 대상으로 하는, 그리고 포인터와 관련이 있는 모든 유형의 형 변환을 허용한다.
int num=0x010203;
char *ptr=reinterpret_cast<char*>(&num);
```
