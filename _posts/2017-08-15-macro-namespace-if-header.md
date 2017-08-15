---
layout: default
title:  "C++ macro,namespace,header"
date:   2017-08-15 20:00:00
categories: C++
---

#C++ 

##매크로함수란?
~~~ruby
+)일반 함수에 비해서 실행 속도가 빠르다.
자료형에 따라 별도로 자료형을 지정하지 않는다.

-)정의하기가 까다로우며, 디버깅이 어렵다.

아래의 단점을 해결하기위해 c++에서는 인라인 함수를 지원.

단 인라인함수는 자료형을 써주어야함.

ex)
#define SQ(x) ((x)*(x))
inline int SQ(int x){return x*x;}
~~~
##namespace?
~~~
한 프로그램을 여러 프로그래머가 협동하여 제작 시, 충돌을 방지해줌.
같은 이름을 갖는 함수여도 namespace가 다르면 다른 함수로 인식.

~~~
##if,ifdef,ifndef,endif
~~~ruby
#if()   괄호 안이 참이면 내용 실행
#elif
#endif

#ifdef ()   #ifndef   괄호 안이 정의되어 있으면 아래 문장 실행
#endif
->헤더파일 한번만 사용해야할 시 아래처럼 쓰면 
#ifndef __head__H
#define __head__H
#endif
~~~
##헤더파일
~~~
파일을 나누어서 각각의 용도 및 특성 별로 함수, 변수를 나누어서 저장하는데 쓰임. =>관리가 용이함.
단, 분할 시 컴파일러는 파일단위로 컴파일하기때문에 선언&정의의 위치를 컴파일러에게 알려주어야 함.
=>변수의 경우 extern 선언을 통해 알려줄 수 있음
ex) extern int num;
만약 타 파일에서의 접근을 금지하고싶을 경우 , static변수를 사용. (함수에도 추가가능하며 이때 함수에 추가하면 외부접근을 차단한다.)
~~~
## include의미
~~~
이 위치에 ~h에 저장된 내용을 그대로 가져다 놓는것.
~~~
##Const
~~~
const int num=10; num에 10이 할당되며 변경 x.. const는 선언과 동시에 초기화 시켜주어야함.
~~~