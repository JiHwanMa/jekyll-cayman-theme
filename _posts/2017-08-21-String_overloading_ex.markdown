---
layout: default
title:  "C++ String_Class_Overloading_ex"
date:   2017-08-21 17:37:00
categories: C++
---

## string class를 오버로딩해보자.

### 실습코드

```c
#include<iostream>
#include<cstring>

using namespace std;
class String 
{
private:
	int len;
	char *str;
public:
	String();
	String(const char *s);
	String(const String& s);
	~String();
	String& operator=(const String& s);
	String& operator+=(const String& s);
	bool operator==(const String& s);
	String operator+(const String& s);

	friend ostream& operator<<(ostream& os, const String& s);
	friend istream& operator>>(istream& is,String& s);

};

String::String() 
{
	len = 0;
	str = NULL;
}

String::String(const char *s) 
{
	len = strlen(s) + 1;
	str = new char[len];
	strcpy(str, s);
}
String::String(const String& s) 
{
	len = s.len;
	str = new char[s.len];
	strcpy(str, s.str);
}
String::~String() 
{
	if (str != NULL) 
	{
		delete[] str;
	}
}
String& String::operator=(const String& s) 
{
	len = s.len;
	if (str != NULL) { delete[] str; }
	str = new char[len];
	strcpy(str, s.str);
	return *this;
}
String String::operator+(const String& s) //새로운 것을 만들어내기 때문에 참조자가 아님.
{

	char *temp = new char[len+s.len];
	strcpy(temp, str);
	strcat(temp, s.str);

	String Sttemp(temp);
	delete[] temp;
	return Sttemp;
}
String& String::operator+=(const String& s) 
{
	len += (s.len - 1);
	char *temp = new char[len];
	strcpy(temp, str);
	strcat(temp, s.str);
	if (str != NULL) { delete[] str; }
	str = temp;
	return *this;
	
}
bool String::operator==(const String& s) 
{
	return strcmp(str, s.str) ? false : true;
}
ostream& operator<<(ostream& os, const String& s) 
{
	os << s.str;
	return os;
}
istream& operator>>(istream& is,String& s) 
{
	char str[100];
	is >> str;
	s=String(str);
	return is;
}
int main() 
{
	String str1 = "I like ";
	String str2 = "string class";
	String str3 = str1 + str2;

	cout << str1 << endl;
	cout << str2 << endl;
	cout << str3 << endl;

	str1 += str2;
	if (str1 == str3) 
	{
		cout << "Same" << endl;
	}
	else 
	{
		cout << "Differ" << endl;
	}

	String str4;
	cout << "input.." << endl;
	cin >> str4;
	cout << "input Values: " << str4 << endl;
	return 0;
}
```
