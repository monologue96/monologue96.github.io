---  
layout: post  
title: "[Dev] 알고리즘 기초 1 - 자료구조 1 (1) - 스택"  
subtitle: "[Dev] 알고리즘 기초 1 - 자료구조 1 (1) - 스택"  
categories: dev  
tags: Algorithm C++ Stack Baekjoon 백준  
comments: true  
---  

■ **코드플러스 '알고리즘 기초 1/2' 강좌의 '자료구조 1' 강의 수강 후 스택과 관련 있는 연습문제 5문제 중 3문제를 우선 풀이하였다.**

<br>

**PC 환경에 최적화되어 있는 포스트입니다.<br>모바일 환경에서 소스코드가 잘려 보일 경우 '소스코드(github)' 링크를 확인해 주세요.**

---

>**스택 구현**<br>
[백준알고리즘 문제 10828](https://www.acmicpc.net/problem/10828 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja10828.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

struct Stack {
	int data[10000];
	int size;
	Stack() {
		size = 0;
	}
	void push(int num) {
		data[size] = num;
		size += 1;
	}
	bool empty() {
		if (size == 0)
			return true;
		else
			return false;
	}
	int pop() {
		if (empty()) {
			return -1;
		}
		else {
			size -= 1;
			return data[size];
		}
	}
	int top() {
		if (empty()) {
			return -1;
		}
		else {
			return data[size - 1];
		}
	}
};

int main() {
	ios_base::sync_with_stdio(false);
	cout.tie(NULL);
	cin.tie(NULL);

	int n;
	cin >> n;

	Stack s;

	while (n--) {
		string cmd;
		cin >> cmd;
		if (cmd == "push") {
			int num;
			cin >> num;
			s.push(num);
		}
		else if (cmd == "top") {
			cout << (s.empty() ? -1 : s.top()) << '\n';
		}
		else if (cmd == "size") {
			cout << s.size << '\n';
		}
		else if (cmd == "empty") {
			cout << s.empty() << '\n';
		}
		else if (cmd == "pop") {
			cout << (s.empty() ? -1 : s.pop()) << '\n';
		}
	}

	return 0;

}
```
<br>

>**단어 뒤집기**<br>
[백준알고리즘 문제 9093](https://www.acmicpc.net/problem/9093 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja9093.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <stack>
#include <string>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);
	int test_num;
	cin >> test_num;
	cin.ignore();
	// cin 은 변수에 '\n'을 담지 않고 입력버퍼에 남겨둔다.
	// getline은 '\n'을 변수에 담는다.
	// 따라서 cin이 남겨둔 '\n'을 getline이 변수에 담지 않도록
	// 맨 앞의 문자 하나를 지우는 cin.ignore()를 사용하여 '\n'을 제거한다.

	while (test_num--) {
		string str;
		getline(cin, str);	// getline(읽어올 입력 스트림, 저장할 문자열 변수)
		str += '\n';
		stack<char> s;	// 스택
		for (char ch : str) {
			// 공백이나 엔터를 만날 때까지 push
			// 공백이나 엔터를 만나면 하나의 단어를 스택에 넣은 것이므로
			// 스택을 비운다.
			if (ch == ' ' || ch == '\n') {
				while (!s.empty()) {
					cout << s.top();
					s.pop();
				}
				cout << ch;
			}else {
				s.push(ch);
			}
		}
	}
	return 0;
}
```
<br>

>**괄호**<br>
[백준알고리즘 문제 9012](https://www.acmicpc.net/problem/9012 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja9012.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <stack>
#include <string>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);
	int test_num;
	cin >> test_num;
	cin.ignore();

	while (test_num--) {
		string str;
		getline(cin, str);
		str += '\n';
		stack<char> s;	// 여는괄호를 넣을 스택
		bool isVPS = true;
		for (char ch : str) {
			if (ch == '(') {
				s.push(ch);	// 여는괄호이면 스택에 push
			}
			else if (ch == ')' && !s.empty()) {
				s.pop();	// 닫는 괄호를 만날 때마다 스택의 맨 위 여는 괄호를 pop
			}
			else if (ch == ')' && s.empty()) {
				// "())" 과 같이 짝이 없는 닫는 괄호가 남는 경우 VPS(valid parenthesis string)가 아님
				isVPS = false;
			}
			if (ch == '\n') {
				break;
			}
		}// 문자열 끝에 도달
		if (!s.empty()) {	// "(()"와 같이 여는 괄호가 스택에 남는 경우 VPS가 아님
			isVPS = false;
		}

		if (isVPS)
			cout << "YES" << endl;
		else
			cout << "NO" << endl;
	}
	return 0;
}
```
<br>
