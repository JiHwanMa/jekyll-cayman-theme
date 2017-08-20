---
layout: default
title:  "C++ copy_constructor"
date:   2017-08-17 20:50:00
categories: c++
---

## 복사 생성자란?
~~~
int num=10; C style
int num(10); C++ style
~~~
예를 들어

![sc1](http://postfiles8.naver.net/MjAxNzA4MDFfMjU5/MDAxNTAxNTczMDc0MzUy.xFUWrNdmr7L6zYgQqUmMxEkMmVEaxdGay6tLyzUJhvMg.fPVdQG7Q2mOUQpYVbSlTr6HXMMZ73hgYXEIQjo_4gPAg.JPEG.qwq713/%EB%B3%B5%EC%82%AC%EC%83%9D%EC%84%B1%EC%9E%90.jpg?type=w2)


```c
Sosimple(Sosimple &copy);
//이런식으로 복사 생성자 정의해줄 것
```

~~~
SoSimple sim1(1,2);
SoSimple sim2(sim1);을 컴파일하게 되면, sim2라는 객체가 생성됨과 동시에 해당 멤버변수값으로 
sim1의 해당 멤버변수값과 같은 값이 복사된다.
이때 12줄의 객체를 복사하는 함수를 복사생성자라고 한다. 
~~~

## 디폴트 복사 생성자
~~~
만약 위의 함수에서 12번째 줄을 따로 작성하지 않아도 SoSimple sim2(sim1);은 문제없이 컴파일된다. 
왜냐하면 기본적으로 SoSimple(SoSimple &copy):num1(copy.num1),num2(copy.num2){}라는 비어있는 
디폴트 복사 생성자가 정의되어있기 때문이다.
~~~

## 변환에 의한 초기화(explicit으로 예방가능.)
```c
Sosimple sim2=sim1; //이런식으로 초기화하여도 자동으로 이 코드는 
Sosimple sim2(sim1);//과 같이 변환되어서 초기화된다. 이를 방지하기 위해서는 복사 생성자 앞에
//explicit을 명시해주자
```

## 깊은 복사와 얕은 복사.
![sc2](http://postfiles7.naver.net/MjAxNzA4MDFfMTEw/MDAxNTAxNTczOTY0MjQx.VHoln6Q_yH7l0dkIHtfdvBAo3EBZPHQJgZrkApYHVW8g.0NVOTqSujKghbvRUNC2vf5zfLk68ySnxSIpaCPxtSGwg.JPEG.qwq713/%EA%B9%8A%EB%B3%B5.jpg?type=w2)
~~~
위의 경우 디폴트 복사 생성자가 호출될 경우 메모리를 새로 할당시키지 않고 같은 주소를 두개의 
객체가 가리키게 된다.(얕은 복사) 따라서 복사 생성자가 새로운 메모리를 할당할 수 있도록 위처럼
코드를 작성해주어야한다.(깊은 복사)
~~~

## 복사 생성자가 호출되는 3가지 시점.
~~~
1. 기존에 생성된 객체를 이용해서 새로운 객체를 초기화하는 경우.
2.Call by value 방식의 함수호출 과정에서 객체를 인자로 전달하는 경우.
3.객체를 반환하되, 참조형으로 반환하지 않는 경우.
~~~
