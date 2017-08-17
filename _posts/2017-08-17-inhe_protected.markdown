---
layout: default
title:  "C++ Inheritance(2_pro_isa_hasa)"
date:   2017-08-17 23:22:00
categories: C++
---

## C++에서의 접근제어 지시자
```
1.private 클래스 외부에서 접근 불가
2.protected 클래스 외부에서 접근 불가
3.public 클래스 외부에서 접근 가능
```

## Protected
```
protected로 선언된 멤버변수는 이를 상속하는 유도 클래스에서 접근이 가능하다.

```

## 상속을 위한 조건 (IS-A Has-A)

### IS-A
```
상속관계가 성립하려면 기초 클래스와 유도 클래스간에 IS-A관계가 성립해야 한다.
Ex.
wireless_telephone is a telephone.
notebook_computer is a computer
```

## HAS-A

```
HAS-A 관계 또한 상속의 조건이 될 수 있다.
Ex.
Policeman has a Gun.
단 이 경우 앞의 경우처럼 public상속을 해도 되지만, 해당 객체를 다른 방식으로도 표현할 수 있다.
```

```c
class gun{}
class Police
{
private:
int numofhandcuffs;
Gun *pistol;

public:
	Police(int bnum,int bcuff):handcuffs(bcuff)
	{
	if(bnum>0){pistol=new Gun(bnum);}
    else{pistol=NULL;}
	}
}
//상속하는 것이 아니라 생성자에서 Gun 객체를 생성하여 이를 참조
```
