---
layout: default
title:  "C++ Polymorphism_objpointer"
date:   2017-08-17 23:42:00
categories: C++
---

## 객체 포인터 변수
```c
//객체의 주소 값을 저장하는 포인터 변수
Person *ptr; //포인터 변수 선언
ptr= new Person();//포인터 변수의 객체 참조
```
### Person형 포인터는 Person을 상속하는 유도 클래스의 객체도 가리킬 수 있다

### Code
```c
#include<iostream>
using namespace std;

class Person 
{
public:
	void Sleep() { cout << "Sleep" << endl; }
};
class Student :public Person 
{
public:
	void Study() { cout << "Study" << endl; }
};
class ParttimeStudent : public Student
{
public:
	void Work() { cout << "Work" << endl; }
};

int main(void) 
{
	Person *ptr1 = new Student();  //Person-> Student ->ParttimeStudent
	Person *ptr2 = new ParttimeStudent(); 
	Student *ptr3 = new ParttimeStudent();

}
```

## Function Overiding ex.

```c
#include<iostream>
#include<cstring>
#define LEN 100
using namespace std;

class Employee 
{
private:
	char name[LEN];
public:
	Employee(char *name) 
	{
		strcpy(this->name, name);
	}
	void ShowYourName() const 
	{
		cout << "name: " << name << endl;
	}
};
class PermanentWorker :public Employee 
{
private:
	int salary;
public:
	PermanentWorker(char *Myname, int Mysalary):Employee(Myname),salary(Mysalary)
	{}
	int GetPay() const { return salary; }
	void ShowSalaryInfo() const 
	{
		ShowYourName();
		cout << "Salary: " << GetPay << endl;//GetPay와 다른점
	}
};


class TemporaryWorker :public Employee 
{
private:
	int workTime;
	int payPerhour;
public:
	TemporaryWorker(char *Myname, int Mypay) :Employee(Myname), payPerhour(Mypay), workTime(0) {}

	void AddWorkTime(int time) { workTime += time; }
	int GetPay() const 
	{
		return workTime*payPerhour;
	}
	void ShowSalaryInfo() const 
	{
		ShowYourName();
		cout << "salary: " << GetPay() << endl << endl;
	}

};
class SalesWorker :public PermanentWorker 
{
private:
	int salesResult;
	double bonusRatio;
public:
	SalesWorker(char *Myname, int Mysalary, double ratio) :PermanentWorker(Myname, Mysalary), bonusRatio(ratio), salesResult(0) {}
	void AddSalesResult(int value) 
	{
		salesResult += value;
	}
	int GetPay() const 
	{
		return PermanentWorker::GetPay() + (int)(salesResult*bonusRatio);
	}
	void ShowSalaryInfo() 
	{
		ShowYourName();
		cout << "salary: " << SalesWorker::GetPay() << endl << endl;
	}
};
class EmployeeHandler
{
private:
	Employee *empList[50];
	int empNum;
public:
	EmployeeHandler() :empNum(0) {}
	void AddEmployee(Employee *emp)
	{
		empList[empNum++] = emp;
	}

};
int main() 
{
	EmployeeHandler handler;
	handler.AddEmployee(new PermanentWorker("Kim", 100));
	handler.AddEmployee(new PermanentWorker("LEE", 150));//handler는 employee형 포인터인데 자식클래스도 가리킬 

}
```

## 함수 오버라이딩 vs 함수 오버로딩

```
기초 클래스와 동일한 이름의 함수를 유도 클래스에서 정의한다고 해서 무조건 함수 오버라이딩이 되는 것은
아니다. 매개변수의 자료형 및 개수가 다르면, 이는 함수 오버로딩이 되어, 전달되는 인자에 따라서 호출되는
함수가 결정된다. 즉, 함수 오버로딩은 상속의 관계에서도 구성이 될 수 있다.
```
