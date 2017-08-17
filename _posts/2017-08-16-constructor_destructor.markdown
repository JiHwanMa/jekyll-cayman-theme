---
layout: default
title:  "C++_Constructor & Destructor"
date:   2017-08-16 20:00:00
categories: C++
---


## 생성자란?
~~~
특징1. : 클래스의 이름과 함수의 이름이 동일하다.
특징2. : 반환형이 선언되어있지 않으며, 실제로 반환하지 않는다. 
->객체 생성 시 딱 1회만 호출됨.
->오버로딩, 디폴트값 설정 가능.
~~~
## 소멸자란?
~~~
특징1. : 클래스의 이름 앞에 ~가 붙은 형태.
특징2. : 반환형이 없으며 실제로 반환하지 않는다.
특징3. : 매개변수는 void 형으로 선언되어야 하기 때문에 오버로딩,디폴트 값 설정이 둘다 불가하다.
~~~
실습코드.

![screenshot1](http://postfiles4.naver.net/MjAxNzA3MzFfMTEy/MDAxNTAxNDk3NDE4Mjk5.9K_02O7-qn9YGe8yyW8wQ4n4Zz904nwCtaFWbqUb4YQg.awHXDap4Msli-qhdMZjIoUIzMZW1Y10wDk-G0pyfx48g.JPEG.qwq713/1.jpg?type=w2)
![screenshot2](http://postfiles10.naver.net/MjAxNzA3MzFfOTkg/MDAxNTAxNDk3NDE4NDY3.Sj1RYeokBG1O0Ff2ycri82EWRmMQM20jcbyw-cyNAXcg.Tmax_L8af6r-BirtWvbHqZ04Xhg_0E7RirmJF0c5qUkg.JPEG.qwq713/2.jpg?type=w2)
![screenshot3](http://postfiles13.naver.net/MjAxNzA3MzFfMjYz/MDAxNTAxNDk3NDE4NjYz.aJjJQ9J5zP4owCZ5Hw-HzmaZqLip7VxZmlnFfzO1ZWYg.WvnZfTmM15ebIFrPhEnkhHTivuuCUbpC_2fJX_r1pLIg.JPEG.qwq713/3.jpg?type=w2)
![screenshot4](http://postfiles6.naver.net/MjAxNzA3MzFfNjcg/MDAxNTAxNDk3NDE4ODQ1.g_SPXs-AiQGth0L2Fkly8Drxr2uFi2wQju1w3xwDFIAg.6HjShLokqH-KMOAD2-9EbyaS6obXcDCYFSMFXg9LzZsg.JPEG.qwq713/4.jpg?type=w2)
![screenshot5](http://postfiles13.naver.net/MjAxNzA3MzFfMTk0/MDAxNTAxNDk3NTQxOTAz.EnUZjEDXt5huBEU6eTScVUFg47d5pL5FeJQX94TS-k0g.1njoTrW2jQQvSGseIaGq5M6onCn_f1-bDEbZR_pIf3Ug.JPEG.qwq713/1.jpg?type=w2)
![scrrenshot6](http://postfiles12.naver.net/MjAxNzA3MzFfMjYg/MDAxNTAxNDk3NTQyMTA2.TuO_Yyj2_r6tpzMewp-AfsFJPMeyKJBvsIA-4nkXCpgg.vhvV_0ggRG2UjpmMt5dXJATHJSQkU4KBiMxaxep3T7wg.JPEG.qwq713/2.jpg?type=w2)
![screenshot7](http://postfiles16.naver.net/MjAxNzA3MzFfMTk5/MDAxNTAxNDk3NTQyMzA2.Q3V2SoCrKnVFSGh_l3VEyzGESDXWx1f3_y1g_Zs9nY0g.mX-pSI_X5CinFVT6MAsHWbbKc8gF9ab8H0HzwFLh0UYg.JPEG.qwq713/3.jpg?type=w2)
