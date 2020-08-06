---  
layout: post  
title: "[Dev] 알고리즘 기초 1 - 수학 1 (1)"  
subtitle: "[Dev] 알고리즘 기초 1 - 수학 1 (1)"   
categories: dev  
tags: Algorithm C++ Baekjoon 소수 GCD LCM 팩토리얼 백준 백준알고리즘  
comments: true  
---  

■ **코드플러스 '알고리즘 기초 1/2' 강좌의 '수학 1' 강의에서의 문제들을 풀이하였다.**

<br>

**PC 환경에 최적화되어 있는 포스트입니다.<br>모바일 환경에서 소스코드가 잘려 보일 경우 '소스코드(github)' 링크를 확인해 주세요.**

---

>**나머지**<br>
[백준알고리즘 문제 10430](https://www.acmicpc.net/problem/10430 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja10430.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);

	int a, b, c;
	cin >> a >> b >> c;

	cout << (a + b) % c << endl;
	cout << ((a % c) + (b % c)) % c << endl;
	// 이 둘은 같다.

	cout << (a * b) % c << endl;
	cout << ((a % c) * (b % c)) % c << endl;
	// 이 둘은 같다.
	return 0;
}
```
<br>

>**최대공약수와 최소공배수**<br>
[백준알고리즘 문제 2609](https://www.acmicpc.net/problem/2609 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja2609.cpp "소스코드(깃허브)")  

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
int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);

	int a, b;
	cin >> a >> b;

	cout << gcd(a, b) << endl;
	// 최소공배수 = (a * b) / 최대공약수
	cout << (a * b) / gcd(a, b) << endl;
	return 0;
}
```
<br>

>**최소공배수**<br>
[백준알고리즘 문제 1934](https://www.acmicpc.net/problem/1934 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1934.cpp "소스코드(깃허브)")  

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
int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);
	cout.tie(nullptr);

	int n;
	cin >> n;

	while (n--) {
		int a, b;
		cin >> a >> b;

		// 최소공배수 = (a * b) / 최대공약수
		cout << (a * b) / gcd(a, b) << endl;
	}

	return 0;
}
```
<br>

>**소수 찾기**<br>
[백준알고리즘 문제 1978](https://www.acmicpc.net/problem/1978 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1978.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <vector>
using namespace std;

// 소수 판별: n이 소수인가?
bool prime(int n) {
	if (n < 2) {
		return false;
	}
	// N이 소수가 아니라면, N = a * b (a <= b)
	// 두 수 a와 b의 차이가 가장 작은 경우는 a <= 루트 N, b >= 루트 N
	// 따라서 N이 소수가 되려면, 2보다 크거나 같고
	// 루트N 보다 작거나 같은 자연수로 나누어 떨어지면 안된다.(검사를 루트N까지만 해보면 된다)
	for (int i = 2; i * i <= n; i++) {
		if (n % i == 0) {
			return false;
		}
	}
	return true;
}

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);
	cout.tie(nullptr);

	int ans = 0;
	int n;
	cin >> n;

	vector<int> a(n);

	for (int i = 0; i < n; i++) {
		cin >> a[i];
		if (prime(a[i])) ans++;
	}

	cout << ans;

	return 0;
}
```
<br>

>**소수 구하기 (에라토스테네스의 체)**<br>
[백준알고리즘 문제 1929](https://www.acmicpc.net/problem/1929 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1929.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <vector>
using namespace std;

// 소수 판별: 1부터 N까지 범위 안에 들어가는 모든 소수 구하기
// 에라토스테네스의 체
// 1. 2부터 N까지 모든 수를 써놓는다.
// 2. 아직 지워지지 않은 수 중 가장 작은 수를 찾는다.
// 3. 그 수는 소수이다.
// 4. 이제 그 수의 배수를 모두 지운다.
// 1~4 과정을 반복한다.


const int MAX = 1000000;
bool check[MAX + 1];

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);
	cout.tie(nullptr);

	// 에라토스테네스의 체
	check[0] = check[1] = true;
	for (int i = 2; i * i <= MAX; i++) {
		if (check[i] == false) {
			for (int j = i + i; j <= MAX; j += i) {
				check[j] = true;	// 지워짐
			}
		}
	}

	int m, n;
	cin >> m >> n;
	for (int i = m; i <= n; i++) {
		if (check[i] == false) {
			cout << i << '\n';
		}
	}

	return 0;
}
```
<br>

>**골드바흐의 추측**<br>
[백준알고리즘 문제 6588](https://www.acmicpc.net/problem/6588 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja6588.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
#include <vector>
using namespace std;

const int MAX = 1000000;
bool check[MAX + 1];

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);
	cout.tie(nullptr);

	// 에라토스테네스의 체를 이용하여 소수가 아닌 것을 걸러낸다.
	check[0] = check[1] = true;
	for (int i = 2; i * i <= MAX; i++) {
		if (check[i] == false) {
			for (int j = i + i; j <= MAX; j += i) {
				check[j] = true;	// 지워짐
			}
		}
	}

	int n;
	while (cin >> n && n != 0) {
		for (int i = 2; i <= n; i++) {
			if (check[i] == false && check[n-i] == false) {
				cout << n << " = " << i << " + " << n-i << '\n';
				break;
			}
		}
	}


	return 0;
}
```
<br>

>**팩토리얼**<br>
[백준알고리즘 문제 10872](https://www.acmicpc.net/problem/10872 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja10872.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);

	int n;
	cin >> n;

	int ans = 1;

	while (n>0) {
		ans *= n;
		n--;
	}

	cout << ans;

	return 0;
}
```
<br>

>**팩토리얼 0의 개수**<br>
[백준알고리즘 문제 1676](https://www.acmicpc.net/problem/1676 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1676.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);

	int n;
	cin >> n;

	// 2의 배수의 개수가 5의 배수의 개수보다 항상 많다.
	// 따라서 5의 배수를 찾을때마다 0의 개수가 하나씩 늘어난다.
	// 문제에서 N<=500이므로 25의 배수, 125의 배수는 5가 각각 1번,2번씩 더 곱해진다.

	int ans = (n / 5);
	if (n >= 25) {
		ans += (n / 25);
	}
	if (n >= 125) {
		ans += (n / 125);
		// 25의 배수들을 찾아 ans++ 하였으므로
		// ans += 2가 아닌 ans++
	}
	cout << ans;

	return 0;
}
```
<br>

>**조합 0의 개수**<br>
[백준알고리즘 문제 2004](https://www.acmicpc.net/problem/2004 "문제")<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja2004.cpp "소스코드(깃허브)")  

```c++
#include <iostream>
using namespace std;

/*
조합 nCm의 0의 개수
nCm = n! / ((n-m)! m!)
n!, (n-m)!, m! 각각의 2, 5 개수를 구한다음
n!에서 구한 2, 5 개수에서 (n-m)!, m!에서 구한 2, 5 개수를 각각 뺀다
뺀 결과 2의 개수와 5의 개수 중 작은 값이 nCm의 0의 개수이다.
*/
int findTwo(int n) {
	int t = 0;
	for (long long i = 2; i <= 2000000000 && n >= i; i *= 2) {
		t += (n / i);
	}
	return t;
}
int findFive(int n) {
	int f = 0;
	for (long long i = 5; i <= 2000000000 && n >= i; i *= 5) {
		f += (n / i);
	}
	return f;
}
int main() {
	ios_base::sync_with_stdio(false);
	cin.tie(nullptr);

	int n, m, ans;
	cin >> n >> m;
	int t = 0, f = 0;	// 각각 2와 5의 개수

	t = findTwo(n) - findTwo(n - m) - findTwo(m);
	f = findFive(n) - findFive(n - m) - findFive(m);

	ans = (t < f) ? t : f;
	cout << ans;

	return 0;
}
```
<br>
