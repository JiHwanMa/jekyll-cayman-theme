---
layout: default
title:  "this_pointer"
date:   2017-08-17 20:49:00
categories: c++
---

## this 포인터?
~~~
this 포인터란 아래에 첨부할 코드를 보면 더욱 더 이해가 잘 가겠지만, 굳이 설명하자면
객체 내에서 this 사용 시 객체 자기자신을 가리킨다고 생각하면 된다. 따라서 this 이용 시 
매개변수의 이름과 멤버변수의 이름이 같더라도 둘을 구분할 수 있다.
실습코드 참고하자.
~~~
![sc1](http://postfiles8.naver.net/MjAxNzA3MzFfNDkg/MDAxNTAxNDk4MDY1ODgy.iRQ3T7QDxX72rmq1rxjxb3gu-ja8YaXbDi6Zh1XF-2Mg.59pOHo1T_V0fq7bYErvCLHnHV8BdUOxMEboEHfRUeb0g.JPEG.qwq713/1.jpg?type=w2)
![sc2](http://postfiles13.naver.net/MjAxNzA3MzFfMjgz/MDAxNTAxNDk4MDY2MDQ3.ZrW3i0qA2taDE8o2H0Aaj14udlWISkwffgsgSYeD9ccg.PDTw1MDk-zcATso04cDFTjBdQ7Q9BaGBgF74TINCMOkg.JPEG.qwq713/2.jpg?type=w2)
![sc3](http://postfiles3.naver.net/MjAxNzA3MzFfODMg/MDAxNTAxNDk4MDY2MjA4.nZGC9sVYtf9ua-35DSoRTOzo3BEKQLTQDEwHeKbrjgIg.Nqc9g3S90dNIDYOfI_raBye-9VSwzVoUcEeZoxDUC0Ag.JPEG.qwq713/3.jpg?type=w2)
