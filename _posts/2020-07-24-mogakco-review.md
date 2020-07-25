---  
layout: post  
title: "[Dev] 알고리즘 준비학습 - C++ 기초 학습 (1)"  
subtitle: "2020 모각코 07-24 개인별 결과"  
categories: dev  
tags: 2020-Summer-Mogakco Algorithm C++   
comments: true  
<!--header-img: img/review/review-book-automate-tasks-1.png-->
---
**오늘 활동목표 : 인프런 C++ 강좌 수강(49강~53강)**  
**&gt;&gt; 소스코드**
>입출력
```c++
#include <iostream>
#include <string>

using namespace std;

int main() {
	string name;

	cout << "이름 입력 : ";
	cin >> name;

	string message = "안녕하세요, " + name + "님.";
	cout << message << endl;

}
/*-----실행결과------
이름 입력 : monologue96
안녕하세요, monologue96님.
*/
```
<br>

>변수, 레퍼런스 변수

```c++
#include <iostream>

using namespace std;

int main() {
	int a(10);
	int b(a + 5);

	cout << "a = " << a << endl;	// a = 10
	cout << "b = " << b << endl;	// b = 15

	//------------------------------------------
	// 범위 기반 for문

	int arr[10] = { 3,1,4,1,5,9,2,6,5,3 };

	for (int n : arr) {
		cout << n << ' ';
	}
	cout << endl;

	for (int& n : arr) {
		n++;
	}

	for (int n : arr) {
		cout << n << ' ';
	}
	cout << endl;
	//--------------------------------------------
	// 범위 기반 for문을 사용하여 이차원 배열 출력
	int arr_d[2][3] = { {1,2,3}, {4,5,6} };

	for (int(&ln)[3] : arr_d) {
		for (int& col : ln) {
			cout << col << ' ';
		}
		cout << endl;
	}


}

/*-------실행결과-------
a = 10
b = 15
3 1 4 1 5 9 2 6 5 3
4 2 5 2 6 10 3 7 6 4
1 2 3
4 5 6
*/
```
<br>

>함수 선언과 사용

```c++
#include <iostream>

// overload(다중정의)
void swap(int &a, int &b) {
	int tmp = a;
	a = b;
	b = tmp;
}
void swap(double &a, double &b) {
	double tmp = a;
	a = b;
	b = tmp;
}
void swap(int* (&a), int* (&b)) {
	int *tmp = a;
	a = b;
	b = tmp;
}

int main() {
	int a = 20, b = 30;
	double da = 2.222, db = 3.333;
	int *pa = &a, *pb = &b;

	swap(a, b);
	swap(da, db);
	swap(pa, pb);

	std::cout << "a : " << a << std::endl;
	std::cout << "b : " << b << std::endl;

	std::cout << "da : " << da << std::endl;
	std::cout << "db : " << db << std::endl;

	std::cout << "*pa : " << *pa << std::endl;
	std::cout << "*pb : " << *pb << std::endl;
}
/*-------실행결과-------
a : 30
b : 20
da : 3.333
db : 2.222
*pa : 20
*pb : 30
*/
```


### ● 회고  
1. 입출력, 변수 선언 및 초기화(C에서처럼 =도 가능), 함수의 다중정의에 관해 학습하였다.
