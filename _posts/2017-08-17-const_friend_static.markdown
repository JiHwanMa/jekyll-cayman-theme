---
layout: default
title:  "C++ Const_Friend_Static"
date:   2017-08-17 20:49:00
categories: c++
---

## Const
~~~
기본적으로 Const는 상수화 선언에 사용되며, 해당 선언 사용 시 이니셜라이저를 이
용한 변경 이외에는 변경이 허용되지 않는다. 또한 이 const선언은 변수 뿐 아니라 객체, 함수에도 선언할 수 있다. 

예를들어
const Sosimple obj(7);
이라고 하면 Sosimple이라는 클래스의 객체 obj의 멤버변수를 7로 초기화시킨 후 이제부터는 해당 클래스의 멤버변수에
대한 변경을 허용하지 않겠다는 의미이다.

1또한 Const를 이용하여 함수 오버로딩 또한 가능하며 const선언을 객체에게 하게되면, 해당 객체는 const선언이 된 
멤버함수만을 호출 할 수 있다.
~~~
![sc1](http://postfiles16.naver.net/MjAxNzA4MDJfNCAg/MDAxNTAxNjU5MDYyMTk4.7FNy6uWYCZLFsdEDLMGH14pEy3ZlL6UzEcJiEvEhOZog.JktP-GQM1yzjarG14xDQ7CRfLCVnt_6cFfcBYFuZhWEg.JPEG.qwq713/const.jpg?type=w2)

## Friend
~~~
클래스의 Friend선언.
A클래스가 B클래스를 대상으로 freind 선언을 하면, B클래스는 A클래스의 private 멤버에 직접 접근이 가능하다.
서로 접근을 가능하게 하려면, B클래스 또한 A클래스에 Friend선언을 해줄 것.
~~~
```c
#include<iostream>
#include<cstring>
using namespace std;

class Girl;

class Boy 
{
private:
 int height;
 friend class Girl; //friend선언 클래스 내의 아무데서나 다 가능.
 public:
 Boy(int len) :height(len) {}
 void ShowyourfriendInfo(Girl &frn);
};
class Girl 
{
private:
 char phNum[20];
 friend class Boy;
public:
 Girl(char *phNum) 
 {
  strcpy(this->phNum, phNum);
 }
 void ShowyourfriendInfo(Boy &frn);
};
void Boy::ShowyourfriendInfo(Girl &frn)  //Boy에서 Girl클래스의 height에 접근
{
 cout << frn.phNum << endl;
}
void Girl::ShowyourfriendInfo(Boy &frn) //Girl에서 Boy클래스의 height에 접근
{
 cout << frn.height << endl;
}
int main(void) 
{
 Boy boy(170);
 Girl girl("010-1234-5678");
 boy.ShowyourfriendInfo(girl);
 girl.ShowyourfriendInfo(boy);
 return 0;
}
```
~~~
함수를 대상으로도 friend 선언이 가능하다.(ex)해당 함수가 타 클래스의 멤버함수를 이용하여 연산 시 Friend 선언을 사용.)
~~~
## Static
~~~
C언어에서의 static>>
전역변수에 선언된 Static :  선언된 파일 내에서만 참조를 허용하겠다는 의미
함수 내에 선언된 static의 의미 : 한번만 초기화되고, 지역변수와 달리 함수를 빠져나가도 소멸되지 X
~~~
ex)
```c
void show(void)
{
static int A=0;
A++;
printf("%d\n",A);
}
```
![sc2](http://postfiles13.naver.net/MjAxNzA4MDJfMTQw/MDAxNTAxNjYwNjgyODIw.pS1QtwXr-_Hgecldr_6NB0Rj-nupqbmWGF-IDgv1KFsg.3FItvCoaEX67R_860hqcqPTvBWG1wXEKDKOeqr-76lYg.JPEG.qwq713/2.jpg?type=w2)
~~~
위 화면과 같이 초기화는 한번만 된 후 증가하는 모습을 볼 수 있음.

이제부터는 C++에서의 Static 선언에 대하여 이야기해보자.

만약 한 클래스객체의 갯수를 카운팅 할 필요가 있다면 어떻게 할것인가?
첫번째 방법으로는 전역변수를 생각해 볼 수 있다. 하지만 전역변수는 타 클래스 및 모든 부분에서 접근이 가능하므로, 
안전하지 않다. 이때 클래스 내부에 static 멤버변수를 사용해보자.
단 static 멤버변수는 사용 시 별도로 초기화를 외부에서 시켜주어야 함 12번째 코드 참고. 
~~~
![sc3](http://postfiles14.naver.net/MjAxNzA4MDJfMjcz/MDAxNTAxNjYxMjUwODA2.cQgAfGq-CmxCuQyLpZ8Q-dpMFVkvfdUS13mAV00lYZYg.c23Ko5_2lIisiE7-1D27229jQwdojIQCikSJoPo57T4g.JPEG.qwq713/3.jpg?type=w2)

## Static 멤버함수
~~~
static 멤버함수 역시 static 멤버변수와 특성이 동일함 따라서.
1.선언된 클래스의 모든 객체가 공유한다.
2.public으로 선언이 되면, 클래스의 이름을 이용하여 호출이 가능하다(classname.())
3.객체의 멤버로 존재하는 것이 아니다.

단 static 멤버함수 내에서는 static 멤버변수와 static 멤버함수만 호출이 가능하다.
또한 const static 멤버변수는 선언과 동시에 초기화가 가능

즉
public:
const static int Russia = 18704; 과 같이 초기화 가능.
+)mutable선언을 하면 const함수로의 변경이 가능해진다. 하지만 가급적 줄여야하는 코드.
~~~
