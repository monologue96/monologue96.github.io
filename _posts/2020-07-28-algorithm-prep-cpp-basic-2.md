---  
layout: post  
title: "[Dev] 알고리즘 준비학습 - C++ 기초 학습 (2)"  
subtitle: ""  
categories: dev  
tags: Algorithm C++   
comments: true  
<!--header-img: img/review/review-book-automate-tasks-1.png-->
---
**인프런 C++ 강좌 (53강~59강) 학습내용**  

강의 : [C 와 C++ 을 동시에 배워보자 - 두들낙서의 C/C++](https://www.inflearn.com/course/c%EC%96%B8%EC%96%B4-%EB%91%90%EB%93%A4%EB%82%99%EC%84%9C/lecture/2766?tab=curriculum "강의")

- c++에서는 구조체 내에 함수 정의가 가능하다. 또한 c에서와 달리 typedef 키워드를 사용하지 않아도 구조체의 태그명을 타입명으로 인식한다.
- namespace, class, this 포인터, 객체의 생성과 소멸, 생성자의 다양한 사용법, 정적 멤버에 대해 학습하였다.

**&gt;&gt; 소스코드**
>네임스페이스

```c++
/*
두들낙서의 C/C++ 53강(네임스페이스) 예제1
*/

#include <iostream>

using namespace std;

int n;	// 어떤 네임스페이스에도 속하지 않음(전역변수)
void set() {
	::n = 10;	// 명시적 전역변수
}
namespace doodle {
	int n;
	void set();
}
namespace google {
	int n;
	void set();
}

int main() {
	::set();
	doodle::set();
	google::set();

	cout << ::n << endl;
	cout << doodle::n << endl;
	cout << google::n << endl;
}

namespace google {	// namespace google을 떼어서 set() 구현 가능
	void set() {
		google::n = 30;	// n = 30; 도 ok
	}
}

void doodle::set() {
	// namespace doodle에서는 set() 선언만 하고
	// 구현은 따로 가능
	n = 20;
}

/*-----------실행결과-----------
10
20
30
*/
```

```c++
/*
두들낙서의 C/C++ 53강(네임스페이스) 예제2
*/

#include <iostream>

using namespace std;	// main() 함수 안에서 사용해도 됨

int n;
void set() {
	n = 10;
}

namespace doodle {
	int n;
	void set() {
		n = 20;
	}

	namespace google {
		int n;
		void set();
	}
}

int main() {
	::set();	// 전역 set() 호출
	doodle::set();	// doodle set() 호출
	doodle::google::set();	// google set() 호출
	// main 함수 안에 using namespace doodle; 을 선언하면
	// google::set(); 으로도 호출 가능

	cout << ::n << endl;
	cout << doodle::n << endl;
	cout << doodle::google::n << endl;

}

void doodle::google::set() {
	n = 30;
}

/*-----------실행결과-----------
10
20
30
*/
```
<br>

>클래스와 구조체

```c++
/*
두들낙서의 C/C++ 54강(클래스=구조체?) 예제1
*/

#include <iostream>

using namespace std;

// 접근제어지시자: private, protected, public

struct TV {
private:	// struct: 접근제어지시자를 명시하지 않으면 디폴트는 public
	bool powerOn;
	int channel;
	int volume;

public:
	void on() {
		powerOn = true;
		cout << "TV를 켰습니다." << endl;
	}

	void off() {
		powerOn = false;
		cout << "TV를 껐습니다." << endl;
	}

	void setChannel(int cnl) {
		if (cnl >= 1 && cnl <= 999) {
			channel = cnl;
			cout << "채널을 " << cnl << "(으)로 바꿨습니다." << endl;
		}
	}

	void setVolume(int vol) {
		if (vol >= 0 && vol <= 100) {
			volume = vol;
			cout << "볼륨을 " << vol << "(으)로 바꿨습니다." << endl;
		}
	}
};

class TV_2 {
	// class: 접근제어지시자를 명시하지 않으면 디폴트는 private
	bool powerOn;
	int channel;
	int volume;

public:
	void on() {
		powerOn = true;
		cout << "TV_2를 켰습니다." << endl;
	}

	void off() {
		powerOn = false;
		cout << "TV_2를 껐습니다." << endl;
	}

	void setChannel(int cnl) {
		if (cnl >= 1 && cnl <= 999) {
			channel = cnl;
			cout << "채널을 " << cnl << "(으)로 바꿨습니다." << endl;
		}
	}

	void setVolume(int vol) {
		if (vol >= 0 && vol <= 100) {
			volume = vol;
			cout << "볼륨을 " << vol << "(으)로 바꿨습니다." << endl;
		}
	}
};

int main() {
	cout << ">> TV" << endl;
	TV lg;
	lg.on();
	lg.setChannel(10);
	lg.setVolume(50);
	lg.setVolume(-73);	// if문 내부 실행되지 않음.
	cout << ">> TV2" << endl;
	TV_2 lg_2;
	lg_2.on();
	lg_2.setChannel(10);
	lg_2.setVolume(50);
	lg_2.setVolume(-73);	// if문 내부 실행되지 않음.
}

/*---------실행결과---------
>> TV
TV를 켰습니다.
채널을 10(으)로 바꿨습니다.
볼륨을 50(으)로 바꿨습니다.
>> TV2
TV_2를 켰습니다.
채널을 10(으)로 바꿨습니다.
볼륨을 50(으)로 바꿨습니다.
*/
```
<br>

> this 포인터

```c++
/*
두들낙서의 C/C++ 55강(this 포인터) 예제1
*/

#include <iostream>

using namespace std;

class MyClass {
	// 클래스나 struct 안의 멤버 함수들은 this 포인터를
	// 보이지 않는 매개변수 형태로 받는다.
	// 함수 printThis()는 각 객체 안에 존재하는 것이 아니라
	// 다른 공간에 있지만 this 포인터를 통해 printThis를 호출한 객체 주소를 알 수 있다.
public:
	void printThis() {
		cout << "나의 주소는 " << this << endl;
	}
};

int main() {
	MyClass a, b;

	cout << "a의 주소는 " << &a << endl;
	cout << "b의 주소는 " << &b << endl;

	a.printThis();
	b.printThis();
}

/*---------실행결과---------
a의 주소는 0093FCBF
b의 주소는 0093FCB3
나의 주소는 0093FCBF
나의 주소는 0093FCB3
*/
```
<br>

> 객체의 생성과 소멸

```c++
/*
두들낙서의 C/C++ 56강(객체의 생성과 소멸) 예제1
*/

#include <iostream>

using namespace std;

class MyClass {
public:
	MyClass() {		// 생성자
		cout << "생성자 호출됨" << endl;
	}

	~MyClass() {	// 소멸자
		cout << "소멸자 호출됨" << endl;
	}
};

MyClass globalObj;	// 전역 MyClass 객체

void testLocalObj() {
	cout << "testLocalObj 함수 시작" << endl;
	MyClass localObj;	// 지역 MyClass 객체
	// 자신이 속한 메서드의 시작 후에 생성자 호출
	// 자신이 속한 메서드가 끝나면 소멸자 호출
	cout << "testLocalObj 함수 끝" << endl;
}
int main() {
	cout << "main함수 시작" << endl;
	testLocalObj();
	cout << "main함수 끝" << endl;
}

/*---------실행결과---------
생성자 호출됨
main함수 시작
testLocalObj 함수 시작
생성자 호출됨
testLocalObj 함수 끝
소멸자 호출됨
main함수 끝
소멸자 호출됨
*/
```
```c++
/*
두들낙서의 C/C++ 56강(객체의 생성과 소멸) 예제2
*/

#include <iostream>

using namespace std;

// 생성자: 객체 생성 시 멤버 변수 초기화
// 소멸자: 메모리 해제

// 복소수(real, imag)

class Complex {
public:
	Complex() {
		real = 0;
		imag = 0;
	}
	Complex(double _real, double _imag) {
		real = _real;
		imag = _imag;
	}
	// 초기화 리스트 형태
	// Complex(double rea, double imag) : real(real), imag(imag) { }

	double getReal() {
		return real;
	}
	void setReal(double _real) {
		real = _real;
	}
	double getImag() {
		return imag;
	}
	void setImag(double _imag) {
		imag = _imag;
	}

private:
	double real;
	double imag;
};

int main() {
	Complex c1;	// 매개변수가 없는 Complex 생성자 호출됨
	Complex c2 = Complex(2, 3);	// 매개변수가 있는 Complex 생성자 호출됨
	Complex c3(2, 3);	// 위와 같은 표현

	// 중괄호를 사용할 수도 있음(균일한 초기화)
	// 괄호 '()' 를 사용하는 경우 C++의 컴파일러가 함수의 정의처럼 보이는 것들을 함수의 정의로 해석하여
	// 객체를 만들지 않고 함수를 정의한 것으로 해석하는 경우가 생김
	// ex) 객체 A의 생성자 A()를 구현하였는데
	// main 함수에서 A a(); 라고 작성한 후 실행했을때 생성자 A()가 호출되지 않고
	// 리턴타입이 A인 함수 a()을 정의한 것으로 컴파일러가 해석

	Complex c4 = { 2,3 };
	Complex c5 = { 2,3 };
	Complex c6{ 2,3 };

	cout << "c1 = " << c1.getReal() << ", " << c1.getImag() << endl;
	cout << "c1 = " << c2.getReal() << ", " << c2.getImag() << endl;
	cout << "c1 = " << c3.getReal() << ", " << c3.getImag() << endl;
}

/*---------실행결과---------
c1 = 0, 0
c1 = 2, 3
c1 = 2, 3
*/
```
<br>

> 생성자의 다양한 사용 방법

```c++
/*
두들낙서의 C/C++ 57강(생성자의 다양한 사용 방법) 예제1
*/

#include <iostream>

using namespace std;

class Time {
public:
	Time() : h(0), m(0), s(0) {	}
	Time(int s_) : Time() {	// 생성자 위임: 특정 생성자에서 자신의 클래스 내의 다른 생성자를 호출
		s = s_;
	}
	Time(int m_, int s_) : Time(s_) {
		m = m_;
	}
	Time(int h_, int m_, int s_) : Time(m_, s_) {
		h = h_;
	}

	int h;
	int m;
	int s;
};

int main() {
	Time t1;
	Time t2(5);
	Time t3(3, 16);
	Time t4(2, 42, 15);

	cout << "t1 : " << t1.h << ":" << t1.m << ":" << t1.s << endl;
	cout << "t2 : " << t2.h << ":" << t2.m << ":" << t2.s << endl;
	cout << "t3 : " << t3.h << ":" << t3.m << ":" << t3.s << endl;
	cout << "t4 : " << t4.h << ":" << t4.m << ":" << t4.s << endl;
}

/*-------실행결과--------
t1 : 0:0:0
t2 : 0:0:5
t3 : 0:3:16
t4 : 2:42:15
*/
```
<br>

> 정적 멤버

```c++
/*
두들낙서의 C/C++ 58강(정적멤버-1) 예제1
*/

#include <iostream>

using namespace std;

// 0~1 float R G B

class Color {
public:
	Color() : r(0), g(0), b(0) { }
	Color(float r, float g, float b) : r(r), g(g), b(b) { }

	float getR() { return r; }
	float getG() { return g; }
	float getB() { return b; }

	// 매개변수로 받은 두 Color객체의 rgb를 각각 평균내어 섞인 새 Color 객체를 반환하는 메서드
	static Color MixColors(Color a, Color b) {	// 정적 메서드
		return Color((a.r + b.r) / 2, (a.g + b.g) / 2, (a.b + b.b) / 2);
	}

private:
	float r;
	float g;
	float b;
};



int main() {
	Color blue(0, 0, 1);
	Color red(1, 0, 0);

	Color purple = Color::MixColors(blue, red);	// 정적 메소드 호출

	cout << "r = " << purple.getR() << ", g = " << purple.getG() << ", b = " << purple.getB();
}

/*-----실행결과-----
r = 0.5, g = 0, b = 0.5
*/
```
```c++
/*
두들낙서의 C/C++ 59강(정적멤버-2) 예제1
*/

#include <iostream>

using namespace std;

// 0~1 float R G B

class Color {
public:
	Color() : r(0), g(0), b(0), id(idCounter++) { }
	Color(float r, float g, float b) : r(r), g(g), b(b), id(idCounter++) { }

	float getR() { return r; }
	float getG() { return g; }
	float getB() { return b; }
	int getId() { return id; }

	// 매개변수로 받은 두 Color객체의 rgb를 각각 평균내어 섞인 새 Color 객체를 반환하는 메서드
	static Color MixColors(Color a, Color b) {	// 정적 메서드
		return Color((a.r + b.r) / 2, (a.g + b.g) / 2, (a.b + b.b) / 2);
	}

	static int idCounter;	// 객체가 아니라 클래스에 관련되어 있는 정적 변수

private:
	float r;
	float g;
	float b;

	int id;
};

int Color::idCounter = 1;	// 정적 변수의 선언과 정의 분리

int main() {
	Color blue(0, 0, 1);
	Color red(1, 0, 0);

	Color purple = Color::MixColors(blue, red);	// 정적 메소드 호출

	cout << "r = " << purple.getR() << ", g = " << purple.getG() << ", b = " << purple.getB() << endl;

	cout << "blue.getId() = " << blue.getId() << endl;
	cout << "red.getId() = " << red.getId() << endl;
	cout << "purple.getId() = " << purple.getId() << endl;
}

/*-----실행결과-----
r = 0.5, g = 0, b = 0.5
blue.getId() = 1
red.getId() = 2
purple.getId() = 3
*/
```
