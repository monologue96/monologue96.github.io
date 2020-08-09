---  
layout: post  
title: "[Dev] 알고리즘 기초 1 - 수학 1 - 연습문제"  
subtitle: "[Dev] 알고리즘 기초 1 - 수학 1 - 연습문제"   
categories: dev  
tags: Algorithm C++ Baekjoon 소수 최소공배수 최대공약수 골드바흐 백준 백준알고리즘  
comments: true  
---  

■ **코드플러스 '알고리즘 기초 1/2' 강좌의 '수학 1 - 연습' 강의에서의 문제들을 풀이하였다.**

<br>

**PC 환경에 최적화되어 있는 포스트입니다.<br>모바일 환경에서 소스코드가 잘려 보일 경우 '소스코드(github)' 링크를 확인해 주세요.<br>백준 온라인 저지 monologue96 페이지에서도 확인하실 수 있습니다.**<br>

[&gt;&gt; 백준 온라인 저지 monologue96 페이지](https://www.acmicpc.net/user/monologue96 "백준 온라인 저지 monologue96 페이지"){: target="_blank"}

---

>**GCD 합**<br>
[백준알고리즘 문제 9613](https://www.acmicpc.net/problem/9613 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja9613.cpp "소스코드(깃허브)"){: target="_blank"}  

```c++
#include <iostream>
using namespace std;

// 유클리드 호제법으로 구하는 최대공약수(GCD)
int gcd(int a, int b) {
	if (b == 0) {
		return a;
	}
	else {
		return gcd(b, a % b);
	}

}

int a[1000001];

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);
	cout.tie(nullptr);

	int testN;
	cin >> testN;

	while (testN--) {
		int n;
		long long sum = 0;
		cin >> n;

		for (int i = 0; i < n; i++) {
			cin >> a[i];
		}
		for (int i = 0; i < n-1; i++) {
			for (int j = i+1; j < n; j++) {
				sum += gcd(a[i], a[j]);
			}
		}
		cout << sum << '\n';
	}

	return 0;
}
```
<br>

>**숨바꼭질 6**<br>
[백준알고리즘 문제 17087](https://www.acmicpc.net/problem/17087 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja17087.cpp "소스코드(깃허브)"){: target="_blank"}  

```c++
#include <iostream>
using namespace std;

// 유클리드 호제법으로 구하는 최대공약수(GCD)
int gcd(int a, int b) {
	if (b == 0) {
		return a;
	}
	else {
		return gcd(b, a % b);
	}
}

int a[100001];

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);
	cout.tie(nullptr);

	int n;
	long long s;
	cin >> n >> s;

	for (int i = 0; i < n; i++) {
		cin >> a[i];
		a[i] = abs(s - a[i]);
	}

	int ans = a[0];
	for (int i = 1; i < n; i++) {
		ans = gcd(ans, a[i]);
	}
	// 예시: 6 12 4 8
	// gcd(6, 12) = 6 -> gcd(6, 4) = 2 -> gcd(2, 8) = 2
	// ans = 2

	cout << ans << '\n';
	return 0;
}
```
<br>

>**2진수 8진수**<br>
[백준알고리즘 문제 1373](https://www.acmicpc.net/problem/1373 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1373.cpp "소스코드(깃허브)"){: target="_blank"}  

```c++
#include <iostream>
#include <string>
using namespace std;

int main() {
	string s;
	cin >> s;
	int n = s.size();
	if (n % 3 == 1) {	// 뒤에서부터 3자리씩 끊었을 때 1자리 남음
		cout << s[0];
	}
	else if (n % 3 == 2) {	// 뒤에서부터 3자리씩 끊었을 때 2자리 남음
		cout << (s[0] - '0') * 2 + (s[1] - '0');
	}
	for (int i = n % 3; i < n; i+=3) {
		cout << (s[i] - '0') * 4 + (s[i + 1] - '0') * 2 + (s[i + 2] - '0');
	}
	cout << '\n';
	return 0;
}
```
<br>

>**8진수 2진수**<br>
[백준알고리즘 문제 1212](https://www.acmicpc.net/problem/1212 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1212.cpp "소스코드(깃허브)"){: target="_blank"}  

```c++
#include <iostream>
#include <string>
using namespace std;

int main() {
	string s;
	string ans = "";
	cin >> s;
	int n = s.size();

	// 0부터 7까지에 대한 각각의 2진수를 string 배열에 저장하여 출력하는 방법도 있으나
	// 여기서는 8진수를 2진수로 변환하는 과정을 포함하였다.
	// 미리 2진수들을 배열에 저장하면 시간은 훨씬 적게 걸린다.
	for (int i = 0; i < n; i++) {
		int a = s[i] - '0';
		int r[3];
		// 8진수 a를 2진수로 변환하는 과정
		for (int i = 0; i < 3; i++) {
			r[i] = a % 2;	// a를 2로 나눈 나머지를 저장
			a = a / 2;		// a를 2로 나눈 몫이 a가 된다
		}
		// 나머지를 거꾸로 쓴다
		ans += to_string(r[2]);
		ans += to_string(r[1]);
		ans += to_string(r[0]);
	}

	if (ans[0] == '0') {
		if (ans[1] == '0') {
			cout << ans.substr(2);
		}
		else {
			cout << ans.substr(1);
		}
	}
	else {
		cout << ans;
	}

	return 0;
}
```
<br>

>**-2진수**<br>
[백준알고리즘 문제 2089](https://www.acmicpc.net/problem/2089 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja2089.cpp "소스코드(깃허브)"){: target="_blank"}  

```c++
#include <iostream>
#include <string>
using namespace std;

void nbin(int n) {
	if (n == 0) {
		return;
	}
	if (n % 2 == 0) {
		nbin(-(n / 2));
		cout << 0;
	}
	else {	// 나머지는 음수일 수 없다.
		if (n > 0) {	// 양수 나눗셈
			nbin(-(n / 2));
		}
		else {	// 음수 나눗셈
			nbin((-n + 1) / 2);	// ex. n=-13이면 몫=7 나머지 1
		}
		cout << 1;
	}
}

int main() {
	ios_base::sync_with_stdio(false);
	cout.tie(nullptr);
	cin.tie(nullptr);

	int n;
	string ans = "";
	cin >> n;

	if (n == 0) {
		cout << 0 << '\n';
	}
	else {
		nbin(n);
	}

	return 0;
}
```
<br>

>**골드바흐 파티션**<br>
[백준알고리즘 문제 17103](https://www.acmicpc.net/problem/17103 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja17103.cpp "소스코드(깃허브)"){: target="_blank"}  

```c++
#include <iostream>
using namespace std;

bool a[1000001];

int main() {
	a[0] = a[1] = true;
	for (int i = 2; i < 1000001; i++) {
		if (a[i] == false) {
			for (int j = i * 2; j < 1000001; j += i) {
				a[j] = true;
			}
		}
	}

	int t, n;
	cin >> t;

	while (t--) {
		int ans = 0;
		cin >> n;
		for (int i = 2; i <= n/2; i++) {
			// 순서만 바뀐 경우는 1개로 간주하기 위해 i <= n/2

			if (a[i] == false && a[n - i] == false) {
				ans++;
			}
		}
		cout << ans << '\n';
	}
}
```
<br>
