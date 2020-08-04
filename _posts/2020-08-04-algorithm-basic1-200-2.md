---  
layout: post  
title: "[Dev] 알고리즘 기초 1 - 자료구조 1 (2) - 스택"  
subtitle: "[Dev] 알고리즘 기초 1 - 자료구조 1 (2) - 스택"  
categories: dev  
tags: Algorithm C++ Stack Baekjoon 백준  
comments: true  
---  

■ **코드플러스 '알고리즘 기초 1/2' 강좌의 '자료구조 1' 강의 수강 후 스택과 관련 있는 연습문제 5문제 중 나머지 2문제를 풀이하였다.**

<br>

**PC 환경에 최적화되어 있는 포스트입니다.<br>모바일 환경에서 소스코드가 잘려 보일 경우 '소스코드(github)' 링크를 확인해 주세요.**

---

>**스택 수열**<br>
[백준알고리즘 문제 1874](https://www.acmicpc.net/problem/1874 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1874.cpp "소스코드(깃허브)")  

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

	int num = 0;	// 스택에 넣을 값 변수
	stack<int> s;
	string result;
	bool v = true;	// 스택 수열 가능/불가능 여부(초기값 true)

	int n;
	cin >> n;
	// 스택 비어 있음
	for (int i = 0; i < n; i++) {	// push 반복횟수 = n
		s.push(++num);
		result += "+\n";
	}
	s.pop();
	result += "-\n";
	test_num--;

	while (test_num--) {
		int n;
		cin >> n;
		if ((!s.empty() && n >= s.top() && v == true) || (s.empty() && v == true)) {
			int rep = n - num;
			for (int i = 0; i < rep; i++) {
				// push 반복횟수(고정시키기 위해 rep 변수 사용) = n - num
				s.push(++num);
				result += "+\n";
			}
			s.pop();
			result += "-\n";
		}
		else if (!s.empty() && n < s.top() && v == true) {
			// 스택 수열 생성 불가능 : 스택 맨 위 숫자가 n보다 크므로
			// n을 스택에서 바로 빼낼 수 없다 -> n보다 위에 있는 숫자가 pop되므로 NO 출력
			result = "NO";
			v = false;
		}
	}

	std::cout << result;
	return 0;
}
```
<br>

>**에디터**<br>
[백준알고리즘 문제 1406](https://www.acmicpc.net/problem/1406 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1406.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <stack>
#include <string>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);
	cout.tie(nullptr);

	string str;
	cin >> str;

	int test_num;
	cin >> test_num;
	cin.ignore();

	stack<char> ls;	// 커서 왼쪽 문자열을 담는 스택
	stack<char> rs;	// 커서 오른쪽 문자열을 담는 스택

	for (int i = 0; i < str.length(); i++) {
		ls.push(str.at(i));
	}

	while (test_num--) {
		string cmd;
		cin >> cmd;

		// 예시 문자열 : algori|thm (|는 커서)
		// right stack의 top : i
		// left stack의 top : t

		if (cmd == "L" && !ls.empty()) {
			rs.push(ls.top());
			ls.pop();
		}

		if (cmd == "D" && !rs.empty()) {
			ls.push(rs.top());
			rs.pop();
		}

		if (cmd == "B" && !ls.empty()) {
			ls.pop();
		}

		if (cmd == "P") {
			char add;
			cin >> add;
			ls.push(add);
		}
	}

	// 왼쪽 스택에 들어있는 문자들을 차례로 pop하여 오른쪽 스택에 push
	// 오른쪽 스택을 차례로 pop하여 최종 문자열 출력
	while (!ls.empty()) {
		rs.push(ls.top());
		ls.pop();
	}
	while (!rs.empty()) {
		cout << rs.top();
		rs.pop();
	}

	return 0;
}
```
<br>
