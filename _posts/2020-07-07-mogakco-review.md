---  
layout: post  
title: "[알고리즘] 백준 알고리즘 1193 - 분수찾기"  
subtitle: ""  
categories: dev  
tags: Algorithm Baekjun Java  
comments: true  
<!--header-img: img/review/review-book-automate-tasks-1.png-->
---  
## 개인별 목표  
백준 알고리즘 1193 문제풀고 풀이 남기기  
Source : [https://www.acmicpc.net/problem/1193](https://www.acmicpc.net/problem/1193 "문제 Source")  

## 개인별 결과
### ● 문제 풀이  
우선 문제에서 말한 지그재그 순서를 그림의 화살표로 나타내면 다음과 같다.  
![img1](https://monologue96.github.io/assets/img/dev/algorithm/07-07-image1.png)

우선 위 그림에서 노란색 직사각형으로 그려놓은 **'대각선' 부분을 왼쪽 상단부터 Level 1,2,3,...** 라 하자.  
문제에서 말한 순서대로 **각 분수가 어느 level 에 속하는지 아래에 표로 나타내 보자.**  
![img2](https://monologue96.github.io/assets/img/dev/algorithm/07-07-image2.png)  

표에서 **노란색 음영 부분은 각 레벨의 첫 번째 번호이고, 이를 level_firstnum 이라 하자.  
level_firstnum은 1,2,4,7,11,16... 의 계차수열 형태**로 나타난다.  

위 표를 통해 우선 level_firstnum 에 해당하는 분수에서 규칙을 찾을 수 있다.  
**level 이 홀수일 경우, 해당 level의 첫 번째 분수는 'level / 1' 로 표현되고, level 이 짝수일 경우, 해당 level의 첫 번째 분수가 '1 / level' 로 표현된다.**

이번엔 각 level 에 해당하는 분수들에서 규칙을 찾아보자.  
**level 이 홀수일 경우, 해당 level에서 번호가 증가할수록 분자가 1씩 감소하고, 분모는 1씩 증가한다.  
level 이 짝수일 경우, 해당 level에서 번호가 증가할수록 분자가 1씩 증가하고, 분모는 1씩 감소한다.**

그렇다면 **예를 하나 들어서, 9번 분수는 어떻게 3/2 로 표현되는지 유추해보자.**  
9번 분수의 level : 4 (짝수), level_firstnum(9번 분수가 속하는 level의 첫 번째 번호) : 7  
9번 분수의 분자 : 1 + (9 - level_firstnum) = 1+(9-7) = 3  
9번 분수의 분모 : level - (9 - level_firstnum) = 4-(9-7) = 2  

이번에는 **level이 홀수인 14번 분수를 유추해보자.**  
14번 분수의 level : 5 (홀수), level_firstnum(14번 분수가 속하는 level의 첫 번째 번호) : 11  
14번 분수의 분자 : level - (14 - level_firstnum) = 5-(14-11) = 2  
14번 분수의 분모 : 1 + (14-level_firstnum) = 1+(14-11) = 4  

**홀수 level 의 분수와 짝수 level의 분수의 분자, 분모 규칙이 서로 반대인 것을 확인할 수 있다.**  

정리하면, **N번째 분수의 표현은  
level 이 짝수일 때  
분자 : 1 + (N - level_firstnum)  
분모 : level - (N-level_firstnum)**  

**level 이 홀수일 때  
분자 : level - (N-level_firstnum)  
분모 : 1 + (N - level_firstnum)**  

### ● 소스코드  
[https://github.com/monologue96/2020-Mogakco/blob/master/2020-07-07-Baekjun-1193.java](https://github.com/monologue96/2020-Mogakco/blob/master/2020-07-07-Baekjun-1193.java "소스코드")  

### ● 실행 결과  
입력: 9  
출력: 3/2  

입력: 14  
출력: 2/4  

입력: 1  
출력: 1/1  

입력: 45  
출력: 1/9  

입력: 36800  
출력: 57/215  

### ● 회고  
원래 2020 모각코를 통해 알고리즘+웹프로그래밍 공부를 하기로 했다.  
알고리즘 강좌와 웹프로그래밍 교재 준비가 아직 안 되어서 백준 알고리즘 문제 하나를 골라서 풀어 보았다.  
앞으로 들을 알고리즘 강좌를 위한 워밍업으로 생각하고 다음 회차에는 본격적으로 알고리즘과 웹프로그래밍 공부 내용을 기록할 것이다.  
