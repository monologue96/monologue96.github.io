---  
layout: post  
title: "[Dev] 알고리즘 기초 1 - DP 1 (1)"  
subtitle: "[Dev] 알고리즘 기초 1 - DP 1 (1)"   
categories: dev  
tags: Algorithm C++ Baekjoon DP 다이나믹프로그래밍 재귀 반복  
comments: true  
---  

■ **코드플러스 '알고리즘 기초 1/2' 강좌의 '다이나믹 프로그래밍 1' 강의에서의 문제들(1,2,3 더하기까지) 풀이하였다.**

<br>

**PC 환경에 최적화되어 있는 포스트입니다.<br>모바일 환경에서 소스코드가 잘려 보일 경우 '소스코드(github)' 링크를 확인해 주세요.<br>백준 온라인 저지 monologue96 페이지에서도 확인하실 수 있습니다.**<br>

[&gt;&gt; 백준 온라인 저지 monologue96 페이지](https://www.acmicpc.net/user/monologue96 "백준 온라인 저지 monologue96 페이지"){: target="_blank"}

---

>**1로 만들기**<br>
[백준알고리즘 문제 1463](https://www.acmicpc.net/problem/1463 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja1463.cpp "소스코드(깃허브)"){: target="_blank"}  

```c++
#include <iostream>
using namespace std;

int d[1000001];

// 점화식: d[n] = min(d[n-1], d[n/2], d[n/3]) + 1
int cal(int n) {
	if (n == 1) return 0;
	if (d[n] > 0) return d[n];
	d[n] = cal(n - 1) + 1;
	if (n % 2 == 0) {
		int temp = cal(n / 2) + 1;
		if (d[n] > temp) d[n] = temp;
	}
	if (n % 3 == 0) {
		int temp = cal(n / 3) + 1;
		if (d[n] > temp) d[n] = temp;
	}
	return d[n];
}

int main() {
	int n;
	cin >> n;
	cout << cal(n);
}
```
<br>

>**2 x n 타일링**<br>
[백준알고리즘 문제 11726](https://www.acmicpc.net/problem/11726 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja11726.cpp "소스코드(깃허브)"){: target="_blank"}  

![img1](https://github.com/monologue96/monologue96.github.io/blob/master/assets/img/dev/algorithm/note4_1.jpg)

```c++
#include <iostream>
using namespace std;

int d[1001];

int cal(int n) {
	if (d[n] > 0) return d[n];	// memorization

	// 2x2까지는 답이 n과 같다.
	if (n <= 2) {
		d[n] = n;
		return n;
	}
	// d[n] : 2xn 크기의 직사각형을 타일로 채우는 방법의 수
	// 2x(n-1) 직사각형에 1x2 타일을 붙여 2xn 직사각형을 만들 수 있다.
	// 2x(n-2) 직사각형에 2x1 타일 2개를 붙여 2xn 직사각형을 만들 수 있다.
	// 따라서 점화식은 d[n] = d[n-1] + d[n-2];

	// 재귀 중간에 오버플로우가 발생할 수 있기 때문에
	// 계산할 때마다 10007을 나누어 준다.
	// 계산 중에 %10007을 하는 것과 마지막에 %10007을 하는 것의 결과가 같다.
	d[n] = (cal(n - 1) + cal(n - 2)) % 10007;
	return d[n];
}

int main() {
	int n;
	cin >> n;
	cout << cal(n);
	// cout << cal(n) % 10007 라고 하면
	// n이 큰 수일때 cal(n)의 값이 이미 수많은 오버플로우를 거쳐서 나온 틀린 값이 되어 답도 틀리게 된다.
}
```
<br>

>**2 x n 타일링 2**<br>
[백준알고리즘 문제 11727](https://www.acmicpc.net/problem/11727 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja11727.cpp "소스코드(깃허브)"){: target="_blank"}  

```c++
#include <iostream>
using namespace std;

int d[1001];

int cal(int n) {
	if (d[n] > 0) return d[n];	// memorization

	// d[n] : 2xn 크기의 직사각형을 타일로 채우는 방법의 수
	// 2x(n-1) 직사각형에 1x2 타일을 붙여 2xn 직사각형을 만들 수 있다.
	// 2x(n-2) 직사각형에 2x1 타일 2개를 붙여 2xn 직사각형을 만들 수 있다.
	// 2x(n-2) 직사각형에 2x2 타일 1개를 붙여 2xn 직사각형을 만들 수 있다.
	// 따라서 점화식은 d[n] = d[n-1] + 2*d[n-2];

	// 재귀 중간에 오버플로우가 발생할 수 있기 때문에
	// 계산할 때마다 10007을 나누어 준다.
	// 계산 중에 %10007을 하는 것과 마지막에 %10007을 하는 것의 결과가 같다.
	d[n] = (cal(n - 1) + (2*cal(n - 2))) % 10007;
	return d[n];
}

int main() {
	d[0] = 0;
	d[1] = 1;
	d[2] = 3;

	int n;
	cin >> n;
	cout << cal(n);
	// cout << cal(n) % 10007 라고 하면
	// n이 큰 수일때 cal(n)의 값이 이미 수많은 오버플로우를 거쳐서 나온 틀린 값이 되어 답도 틀리게 된다.
}
```
<br>

>**1, 2, 3 더하기**<br>
[백준알고리즘 문제 9095](https://www.acmicpc.net/problem/9095 "문제"){: target="_blank"}<br>
[소스코드(github)](https://github.com/monologue96/baekjoon_algorithm_practice/blob/master/Algorithm_basic_1_practice/Algorithm_basic_1_practice/bja9095.cpp "소스코드(깃허브)"){: target="_blank"}  

![img1](https://github.com/monologue96/monologue96.github.io/blob/master/assets/img/dev/algorithm/note4_2.jpg)

```c++
#include <iostream>
using namespace std;

int d[11];

int cal(int n) {
	if (d[n] > 0) return d[n];
	if (n - 1 >= 0)
		d[n] += cal(n - 1);
	if (n - 2 >= 0)
		d[n] += cal(n - 2);
	if (n - 3 >= 0)
		d[n] += cal(n - 3);
	return d[n];
}

int main() {
	d[0] = 1;
	int t, n;
	cin >> t;
	while (t--) {
		cin >> n;
		cout << cal(n) << '\n';
	}
}
```
<br>
