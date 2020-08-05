---  
layout: post  
title: "[Dev] 알고리즘 기초 1 - 자료구조 1 (3) - 연습문제"  
subtitle: "[Dev] 알고리즘 기초 1 - 자료구조 1 (3) - 연습문제"  
categories: dev  
tags: Algorithm C++ Stack Baekjoon 백준 백준알고리즘  
comments: true  
---  

■ **코드플러스 '알고리즘 기초 1/2' 강좌의 '자료구조 1 - 연습' 강의에서의 연습문제를 풀이하였다.**

<br>

**PC 환경에 최적화되어 있는 포스트입니다.<br>모바일 환경에서 소스코드가 잘려 보일 경우 '소스코드(github)' 링크를 확인해 주세요.**

---

>**단어 뒤집기 2**<br>
[백준알고리즘 문제 17413](https://www.acmicpc.net/problem/17413 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja17413.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <stack>
#include <string>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);

	string str;
	getline(cin, str);	// getline(읽어올 입력 스트림, 저장할 문자열 변수)
	str += '\n';
	stack<char> s;	// 스택
	bool valid = true;		// 현재 문자가 스택에 입력될 수 있는 문자인지 여부(< > 안의 문자는 false)

	for (char ch : str) {
		if (ch == '>') {
			valid = true;
			cout << ch;
			continue;
		}

		if (!valid) {
			cout << ch;
		}
		else {
			if (ch == ' ' || ch == '<' || ch == '\n') {
				while (!s.empty()) {
					cout << s.top();
					s.pop();
				}
				if (ch == '<') {
					valid = false;
				}
				cout << ch;
			}
			else {
				s.push(ch);
			}
		}

	}

	return 0;
}
```
<br>

>**쇠막대기**<br>
[백준알고리즘 문제 10799](https://www.acmicpc.net/problem/10799 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja10799.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <stack>
#include <string>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);

	string str;
	getline(cin, str);
	str += '\n';

	stack<int> s;	// 괄호 인덱스 스택
	int ans = 0;
	int index = 1;	// 괄호의 인덱스(1부터 시작)

	for (char ch : str) {
		if (ch == '(') {
			s.push(index);
			index++;
		}
		else if (ch == ')' && (index - s.top() == 1)) {	// 레이저
			s.pop();
			ans += s.size();	// s.size()개의 조각이 생김
		}
		else if (ch == ')' && (index - s.top() != 1)) {	// 쇠막대기의 오른쪽 끝
			s.pop();
			ans += 1;	// 1개의 조각이 생김
		}
		if (ch == '\n') {
			break;
		}
	}// 문자열 끝에 도달

	cout << ans;
	return 0;
}
```
<br>

>**오큰수**<br>
[백준알고리즘 문제 17298](https://www.acmicpc.net/problem/17298 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja17298.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <stack>
#include <vector>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);

	int n;
	cin >> n;
	vector<int> a(n);	// 입력
	vector<int> ans(n);	// 답

	for (int i = 0; i < n; i++) {
		cin >> a[i];
	}

	stack<int> s;
	s.push(0);	// 첫번째 숫자는 오큰수를 아직 찾을 수 없으므로 스택에 넣음

	for (int i = 1; i < n; i++) {

		while (!s.empty() && a[s.top()] < a[i]) {
			// 스택이 비어 있지 않고
			// 스택의 맨 위 인덱스가 가리키는 숫자 a[s.top()] 보다 i번째 숫자가 더 크면
			// i번째 숫자는 a[s.top()]의 오큰수이다.
			// 이것을 스택이 비거나, 스택에 남아 있는 숫자 중 i번째 숫자보다 큰 수가 나올때까지 반복한다.
			ans[s.top()] = a[i];
			s.pop();
		}
		// 스택이 비거나, 스택에 남아 있는 숫자 중 i번째 숫자보다 큰 수가 나온 경우
		// 인덱스 i를 스택에 넣는다.
		s.push(i);

	}
	// 이 시점에서 스택에 남아있는 인덱스들은 오큰수가 없는 인덱스이다.
	while (!s.empty()) {
		ans[s.top()] = -1;	// 이들의 답은 -1
		s.pop();
	}

	for (int a : ans) {
		cout << a << " ";	// 답 출력
	}

	return 0;
}
```
<br>

>**오등큰수**<br>
[백준알고리즘 문제 17299](https://www.acmicpc.net/problem/17299 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja17299.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <stack>
#include <vector>
using namespace std;

int freq[1000001];

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);

	int n;
	cin >> n;
	vector<int> a(n);	// 입력
	vector<int> ans(n);	// 답

	for (int i = 0; i < n; i++) {
		cin >> a[i];
		freq[a[i]] += 1;
	}

	stack<int> s;
	s.push(0);	// 첫번째 숫자는 오등큰수를 아직 찾을 수 없으므로 스택에 넣음

	for (int i = 1; i < n; i++) {

		while (!s.empty() && freq[a[s.top()]] < freq[a[i]]) {
			// 스택이 비어 있지 않고
			// 스택의 맨 위 인덱스가 가리키는 숫자 a[s.top()]의 등장횟수보다 i번째 숫자의 등장횟수가 더 크면
			// i번째 숫자는 a[s.top()]의 오등큰수이다.
			// 이것을 스택이 비거나, 스택에 남아 있는 숫자 중 i번째 숫자보다 등장횟수가 큰 수가 나올때까지 반복한다.
			ans[s.top()] = a[i];
			s.pop();
		}
		// 스택이 비거나, 스택에 남아 있는 숫자 중 i번째 숫자보다 등장횟수가 큰 수가 나온 경우
		// 인덱스 i를 스택에 넣는다.
		s.push(i);

	}
	// 이 시점에서 스택에 남아있는 인덱스들은 오등큰수가 없는 인덱스이다.
	while (!s.empty()) {
		ans[s.top()] = -1;	// 이들의 답은 -1
		s.pop();
	}

	for (int a : ans) {
		cout << a << " ";	// 답 출력
	}

	return 0;
}
```
<br>
