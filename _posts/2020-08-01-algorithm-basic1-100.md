---  
layout: post  
title: "[Dev] 알고리즘 기초 1 - 알고리즘 시작"  
subtitle: "[Dev] 알고리즘 기초 1 - 알고리즘 시작"  
categories: dev  
tags: Algorithm C++   
comments: true  
---  

■ **코드플러스 '알고리즘 기초 1/2' 강좌의 '알고리즘 시작' 강의 수강 후 연습문제를 풀이하였다.**

<br>

**PC 환경에 최적화되어 있는 포스트입니다.<br>모바일 환경에서 소스코드가 잘려 보일 경우 '소스코드(github)' 링크를 확인해 주세요.**

---

>**Hello World**<br>
[백준알고리즘 문제 2557](https://www.acmicpc.net/problem/2557 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja2557.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main(){
	ios_base::sync_with_stdio(false);
	cout.tie(NULL);

	cout << "Hello World!";
}
```
<br>

>**A+B**<br>
[백준알고리즘 문제 1000](https://www.acmicpc.net/problem/1000 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1000.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cout.tie(NULL);
	cin.tie(NULL);

	int a, b;

	cin >> a >> b;

	cout << a + b;
}
```
<br>

>**A+B - 3**<br>
[백준알고리즘 문제 10950](https://www.acmicpc.net/problem/10950 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja10950.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cout.tie(NULL);
	cin.tie(NULL);

	int n, a, b;
	cin >> n;
	for (int i = 0; i < n; i++) {
		cin >> a >> b;
		cout << a + b << endl;
	}
}
```
<br>

>**A+B - 4**<br>
[백준알고리즘 문제 10951](https://www.acmicpc.net/problem/10951 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja10951.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cout.tie(NULL);
	cin.tie(NULL);

	int a, b;
	while(cin >> a >> b) {
		cout << a + b << endl;
	}
}
```
<br>

>**A+B - 5**<br>
[백준알고리즘 문제 10952](https://www.acmicpc.net/problem/10952 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja10952.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cout.tie(NULL);
	cin.tie(NULL);

	int a, b;
	while (cin >> a >> b && (a != 0) && (b != 0)) {
		cout << a + b << endl;
	}
}
```
<br>

>**A+B - 6**<br>
[백준알고리즘 문제 10953](https://www.acmicpc.net/problem/10953 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja10953.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cout.tie(NULL);
	cin.tie(NULL);

	int n, a, b;
	char c;

	cin >> n;
	for (int i = 0; i < n; i++) {
		cin >> a >> c >> b;
		cout << a + b << endl;
	}
}
```
<br>

>**A+B - 7**<br>
[백준알고리즘 문제 11021](https://www.acmicpc.net/problem/11021 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja11021.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cout.tie(NULL);
	cin.tie(NULL);

	int n, a, b;

	cin >> n;
	for (int i = 1; i < n+1; i++) {
		cin >> a >> b;
		cout << "Case #" << i << ": " << a + b << endl;
	}
}
```
<br>

>**A+B - 8**<br>
[백준알고리즘 문제 11022](https://www.acmicpc.net/problem/11022 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja11022.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cout.tie(NULL);
	cin.tie(NULL);

	int n, a, b;

	cin >> n;
	for (int i = 1; i < n + 1; i++) {
		cin >> a >> b;
		cout << "Case #" << i << ": " << a << " + " << b << " = " << a + b << endl;
	}
}
```
<br>
