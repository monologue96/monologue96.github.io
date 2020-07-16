---  
layout: post  
title: "[Dev] 3. 이미지와 하이퍼링크"  
subtitle: "2020 모각코 07-16 개인별 결과"  
categories: dev  
tags: 2020-Summer-Mogakco Web HTML  
comments: true  
<!--header-img: img/review/review-book-automate-tasks-1.png-->
---

## 개인별 결과
### ● 학습내용 정리
>**웹문서에 이미지 삽입하기 : &lt;img&gt;, &lt;figure&gt;, &lt;figcaption&gt; 태그**  

```html
<img src="이미지 경로" 속성="값">

<!-- 인터넷에 연결된 다른 컴퓨터에서 이미지가 보이려면 이미지 파일을 서버에 업로드해야 한다 -->
```
- alt 속성 : 이미지를 설명하는 대체 텍스트. 화면 낭독기가 인식하여 설명을 읽도록 하거나, 이미지가 표시되지 않는 상황에서 이미지 설명을 표시하여 어떤 이미지가 사용되는지 짐작할 수 있게 한다. 사용법은 alt=" "
- width, height 속성 : 이미지 크기 조정을 위한 속성
- Chapter2 에서  &lt;figure&gt;, &lt;figcaption&gt; 태그를 사용하여 표 제목을 표시한 것과 같은 방법으로, 이미지에도 설명(캡션)을 추가할 수 있다.  

```html
<figure>
  <img src="https://github.com/monologue96/2020-Mogakco/blob/master/HTML5-CSS3/03/images/prod.jpg?raw=true" alt="예멘 모카 마타리">
  <figcaption>예멘 모카 마타리(Yemen Mocha Mattari)</figcaption>
</figure>
```
<figure>
  <img src="https://github.com/monologue96/2020-Mogakco/blob/master/HTML5-CSS3/03/images/prod.jpg?raw=true" alt="예멘 모카 마타리">
  <figcaption>예멘 모카 마타리(Yemen Mocha Mattari)</figcaption>
</figure>
<br>
.

>**링크 만들기 : &lt;a&gt; 태그와 href 속성**  

```html
텍스트 링크 : <a href="링크할 주소" 속성="값"> 텍스트 </a>
이미지 링크 : <a href="링크할 주소" 속성="값"><img src="이미지 경로"> </a>
target 속성에서 _blank 값을 지정하면 링크 내용이 새 창 또는 새 탭에서 열린다.
<iframe> 태그를 사용하면 현재 문서 안에 다른 문서의 내용을 표시할 수 있다.

앵커(anchor) : 웹문서가 너무 길 경우 한 페이지 안에서 문서의 특정 위치로 이동할 수 있도록 하는 기능
-> 이동을 원하는 부분의 태그에 id="아이디명" 속성이 추가되어 있어야 한다.

<태그 id="앵커 이름"> 내용 </태그>
<a href="#앵커 이름"> 내용 </a>
```
```html
<h3 id="link_ex">텍스트 링크 만들기</h3><!--밑의 앵커 예시코드에서 사용할 id 추가 -->
<a href="http://www.easyspub.com" target="_blank">이지스퍼블리싱 홈페이지</a>
<h3>이미지 링크 만들기</h3>
<a href="http://www.easyspub.com">
	<img src="https://github.com/monologue96/2020-Mogakco/blob/master/HTML5-CSS3/03/images/easyspub.jpg?raw=true" alt="이지스퍼블리싱 홈페이지로 가기">
</a>
```

<h3 id="link_ex">텍스트 링크 만들기</h3><!--밑의 앵커 예시코드에서 사용할 id 추가 -->
<a href="http://www.easyspub.com" target="_blank">이지스퍼블리싱 홈페이지</a>
<h3>이미지 링크 만들기</h3>
<a href="http://www.easyspub.com">
	<img src="https://github.com/monologue96/2020-Mogakco/blob/master/HTML5-CSS3/03/images/easyspub.jpg?raw=true" alt="이지스퍼블리싱 홈페이지로 가기">
</a>
<br>  
.

```html
<iframe src="https://github.com/monologue96" width="600" height="400"></iframe>
```
<iframe src="https://github.com/monologue96" width="600" height="400"></iframe>
<br>
.

```html
<a href="#link_ex">텍스트 및 이미지 링크 예제로 돌아가기</a>
```
<a href="#link_ex">텍스트 및 이미지 링크 예제로 돌아가기</a>
<br>
.

### ● 회고  
1. HTML을 사용하여 웹 문서에 이미지를 표시하는 방법을 알게 되었다.
2. '웹'의 핵심 기능은 단언컨대 서로 다른 웹문서끼리 연결할 수 있는 '링크' 기능이라고 할 수 있다. 이번 시간에 텍스트와 이미지에 링크를 추가하여 다른 웹 페이지로 이동하는 방법을 학습함으로써 고립된 웹문서가 아닌 넓은 세계로 확장될 수 있는 웹문서를 만들 수 있게 되었다.
