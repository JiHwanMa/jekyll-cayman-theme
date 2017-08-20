---
layout: default
title:  "C++ Additional_C_lang-function-Pointer"
date:   2017-08-20 19:25:00
categories: C++
---


## 함수 포인터(Function_Pointer)
### 형식
```
(반환형)(*ptr)(입력변수들)
예를들어 double power(double,int x);
같은 경우 double(*ptr)(double,int)=power;
C언어에서 함수 또한 특정 위치에 저장되어있다.
따라서 함수 포인터를 선언하여 특정 함수의 주소값을 저장함으로써
해당 함수를 사용할 수 있다.
```
**Code**
~~~c
#include<stdio.h>

int double(int x)
{
return x+x;
}

void sum(int x,int y)
{
printf("%d + %d = %d\n",x,y,x+y);

}

int main()
{
int(*p1)(int)=double;
void(*p2)(int,int)=sum;

puts("Function Ptr\n");
pritnf("double함수의 주소 : %d\n",double);
printf("sum함수의 주소: %d\n",sum);

printf("double(10)= %d\n",double(10));
printf("p1(10)= %d\n",p1(10));

sum(10,15);
p2(10,15);

return 0;
}
~~~
