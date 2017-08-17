---
layout: default
title:  "C++ Information_Hiding_and_Encapsulation"
date:   2017-08-15 20:00:00
categories: c++
---

## 정보은닉(Information Hiding)이란?
~~~~
프로그래머는 코딩 중 실수를 저지를 수 있음. 이에 대한 일종의 대비책으로써 
제한된 방법으로만 클래스의 멤버변수에 대한 접근을 허용시켜서 잘못된 값이
저장되는것을 예방할 수 있음.
예를들어 클래스의 멤버변수에 private선언 후, 멤버함수의 값을 초기화시켜주는 함수를 만들 때 
그 함수의 기능으로써 잘못된 값이 멤버변수에 저장되려 하면 해당 함수의 동작을 취소시켜줌.
~~~~
## const함수
~~~~~
ex) int GetX() const{}
const선언 시 해당 함수의 내부에서는 멤버변수의 값을 변경할 수 없음. 또한 const선언이 되면 
해당 함수 내부에 함수를 쓸 경우에는 const선언이 되어있는 함수만 사용 가능.
~~~~~
## 캡슐화(Encapsulation)란?
~~~~
관련 있는 함수와 변수를 하나의 클래스 안에 묶는 것.
캡슐화의 범위를 결정하는 일이 쉽지않다. 어렵다..
~~~~

~~~c
#include<iostream>
using namespace std;

class Point 
{
 private:
 int xpos, ypos;

 public:
  void init(int x, int y) 
  {
   xpos = x;
   ypos = y;
  }
  void ShowPointInfo() const 
  {
   cout << "[" << xpos << "," << ypos << "]" << endl;
  }
};

class Circle 
{
private:
 Point XY;
 int radius;
public:
 void init(int x,int y, int r) 
 {
  if (r < 0) { printf("r값은 0보다 커야합니다. 초기화가 이뤄지지 않았습니다.\n"); }
//멤버변수인 XY는 private으로 선언 후(정보은닉), 
//그에 대한 접근을 함수로 할 시에 잘못된 값의 저장에 대한 대책을 마련해둠.
  else {
   XY.init(x, y);
   radius = r;
  }
 }
 void ShowCircle() const 
 {
  cout << "radius:" << radius << endl;
  XY.ShowPointInfo();
 }
 

};


class Ring 
{
private:
 Circle one;
 Circle two;
public:
 void init(int x1, int y1, int r1, int x2, int y2, int r2) 
 {
  one.init(x1, y1, r1);
  two.init(x2, y2, r2);
 }
 void ShowRing() const
 {
  printf("Inner Circle Information\n");
  one.ShowCircle();
  printf("Outer Circle Information\n");
  two.ShowCircle();
 }

};

int main() 
{
 Ring ring;
 ring.init(1, 1, -3, 2, 2, 9);
 ring.ShowRing(); 
//객체는 그 내부에 Circle,point가 모두 포함되어있음에도 불구하고 
//링 객체의 ShowRing 만으로 해당 정보를 모두 보여준다 이러한 코딩기법을 캡슐화 라고 한다.
 return 0;
}
~~~
