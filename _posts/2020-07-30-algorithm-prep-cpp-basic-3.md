---  
layout: post  
title: "[Dev] 알고리즘 준비학습 - C++ 기초 학습 (3)"  
subtitle: ""  
categories: dev  
tags: Algorithm C++   
comments: true  
<!--header-img: img/review/review-book-automate-tasks-1.png-->
---
**인프런 C++ 강좌 (60강~62강) 학습내용**  

강의 : [C 와 C++ 을 동시에 배워보자 - 두들낙서의 C/C++](https://www.inflearn.com/course/c%EC%96%B8%EC%96%B4-%EB%91%90%EB%93%A4%EB%82%99%EC%84%9C/lecture/2766?tab=curriculum "강의")

- 모든 함수에 대한 매개변수의 상수화, 멤버 메서드에 대한 메서드 상수화, 멤버 메서드의 선언과 정의 분리, 연산자 오버로딩에 대해 학습하였다.
<br>

**PC 환경에 최적화되어 있는 포스트입니다.<br>
모바일 환경에서 소스코드가 잘려 보일 경우 '소스코드(github)' 링크를 확인해 주세요.**

**&gt;&gt; 소스코드**
>**상수형 매개변수와 상수형 메서드**<br>
[소스코드(github)](https://github.com/monologue96/cpp_beginner_practice/blob/master/const_parameter_const_method/ex1.cpp "소스코드(깃허브)")

```c++
/*
두들낙서의 C/C++ 60강(상수형 매개변수와 상수형 메서드) 예제1
*/

// 1. 매개변수의 상수화 (모든 함수)
// 2. 메서드의 상수화 (멤버 메서드)

#include <iostream>

using namespace std;

class Account {
public:
	Account() : money(0) {}
	Account(int money) : money(money) {}

	void deposit(const int d) {
		// 매개변수를 그대로 사용할 수 있도록(바꿀 수 없도록) 매개변수 상수화

		// d = money (오류-컴파일에 실패함)
		money += d;
		cout << d << "원을 예금했다" << endl;
	}
	void draw(int d) {
		if (money >= d) {
			money -= d;
			cout << d << "원을 인출했다" << endl;
		}
	}

	int viewMoney() const{
		// 멤버 변수를 바꿀 수 없도록(컴파일에 실패함) 메서드를 상수화

		// money++;	(오류-컴파일에 실패함)
		return money;
	}
private:
	int money;
};

int main() {
	Account doodle(100);

	doodle.deposit(100);
	doodle.draw(20);

	cout << doodle.viewMoney() << endl;
}

/*-----실행결과-----
100원을 예금했다
20원을 인출했다
180
*/
```
<br>

>**멤버 메서드 활용하기**<br>
[소스코드(github)](https://github.com/monologue96/cpp_beginner_practice/blob/master/member_method_and_operator_overloading/ex1.cpp "소스코드(깃허브)")

```c++
/*
두들낙서의 C/C++ 61강(멤버 메서드 활용하기) 예제1
*/

// 벡터
// 멤버 메서드의 선언, 정의 분리하기

#include <iostream>

using namespace std;

class Vector2 {
public:
	Vector2();
	Vector2(float x, float y);

	float getX() const;
	float getY() const;

	static Vector2 Sum(Vector2 a, Vector2 b) {
		// 정적(클래스에 소속 - 어떤 벡터에 더하는지 매개변수로 설정해야 함)

		return Vector2(a.x + b.x, a.y + b.y);
	}

	Vector2 Add(Vector2 rhs) {	// 동적(특정 객체에 소속)
		return Vector2(x + rhs.x, y + rhs.y);
	}

private:
	float x;
	float y;
};

int main() {
	Vector2 a(2, 3);
	Vector2 b(-1, 4);
	Vector2 c1 = Vector2::Sum(a, b);
	Vector2 c2 = a.Add(b);

	cout << a.getX() << ", " << a.getY() << endl;
	cout << b.getX() << ", " << b.getY() << endl;
	cout << c1.getX() << ", " << c1.getY() << endl;
	cout << c2.getX() << ", " << c2.getY() << endl;
}

Vector2::Vector2() : x(0), y(0) {}
Vector2::Vector2(float x, float y) : x(x), y(y) {}
float Vector2::getX() const { return x; };
float Vector2::getY() const { return y; };

/*-----실행결과-----
2, 3
-1, 4
1, 7
1, 7
*/
```
<br>

>**연산자 오버로딩**<br>
[소스코드(github)](https://github.com/monologue96/cpp_beginner_practice/blob/master/member_method_and_operator_overloading/ex2.cpp "소스코드(깃허브)")

```c++
/*
두들낙서의 C/C++ 62강(연산자 오버로딩) 예제1
*/

// 벡터
// 멤버 메서드의 선언, 정의 분리하기

#include <iostream>

using namespace std;

class Vector2 {
public:
	Vector2();
	Vector2(float x, float y);

	float getX() const;
	float getY() const;

	Vector2 operator+(const Vector2 rhs) const;	// 벡터+벡터
	Vector2 operator-(const Vector2 rhs) const;	// 벡터-벡터
	Vector2 operator*(const float rhs) const;	// 벡터*실수
	Vector2 operator/(const float rhs) const;	// 벡터/실수
	float operator*(const Vector2 rhs) const;	// 벡터*벡터(내적. 결과값은 실수)

private:
	float x;
	float y;
};

Vector2 operator*(const float a, const Vector2 b) {	// 매개변수 2개인 연산자 오버로딩
	return Vector2(a * b.getX(), a * b.getY());
}


int main() {
	Vector2 a(2, 3);
	Vector2 b(-1, 4);
	Vector2 c1 = a - b;	// 연산자 오버로딩이 적용됨
	Vector2 c2 = a * 1.6;
	Vector2 c3 = 1.6 * a;
	float c4 = a * b;

	cout << a.getX() << ", " << a.getY() << endl;
	cout << b.getX() << ", " << b.getY() << endl;
	cout << c1.getX() << ", " << c1.getY() << endl;
	cout << c2.getX() << ", " << c2.getY() << endl;
	cout << c3.getX() << ", " << c3.getY() << endl;
	cout << c4 << endl;
}

Vector2::Vector2() : x(0), y(0) {}
Vector2::Vector2(float x, float y) : x(x), y(y) {}
float Vector2::getX() const { return x; };
float Vector2::getY() const { return y; };

Vector2 Vector2::operator+(const Vector2 rhs) const {	// 연산자 오버로딩
	return Vector2(x + rhs.x, y + rhs.y);
}
Vector2 Vector2::operator-(const Vector2 rhs) const {	// 연산자 오버로딩
	return Vector2(x - rhs.x, y - rhs.y);
}
Vector2 Vector2::operator*(const float rhs) const {	// 연산자 오버로딩
	return Vector2(x * rhs, y * rhs);
}
Vector2 Vector2::operator/(const float rhs) const {	// 연산자 오버로딩
	return Vector2(x / rhs, y / rhs);
}
float Vector2::operator*(const Vector2 rhs) const {	// 연산자 오버로딩
	return x * rhs.x + y * rhs.y;
}

/*-----실행결과-----
2, 3
-1, 4
3, -1
3.2, 4.8
3.2, 4.8
10
*/
```
