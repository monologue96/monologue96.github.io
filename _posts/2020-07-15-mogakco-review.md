---  
layout: post  
title: "[Dev] 2. 텍스트 관련 태그들"  
subtitle: "2020 모각코 07-15 개인별 결과"  
categories: dev  
tags: 2020-Summer-Mogakco Web HTML  
comments: true  
<!--header-img: img/review/review-book-automate-tasks-1.png-->
---

## 개인별 결과
### ● 학습내용 정리
>**텍스트를 덩어리로 묶어주는 태그**

>>**&lt;hn&gt; 태그 - 제목 표시** : h는 heading의 줄임말. n은 제목 크기를 나타내는 숫자(1~6). 숫자가 작을수록 큰 제목  

```html
<h1>제목</h1>
<h2>제목</h2>
<h3>제목</h3>
<h4>제목</h4>
<h5>제목</h5>
<h6>제목</h6>  
```
<h1>제목</h1>
<h2>제목</h2>
<h3>제목</h3>
<h4>제목</h4>
<h5>제목</h5>
<h6>제목</h6>  
<br>

>>**&lt;p&gt; 태그 - 단락 만들기** : p는 paragraph의 줄임말. 텍스트 줄이 창의 너비보다 길어질 경우 줄이 자동으로 바뀜.

```html
<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
<p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
```

<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p> <p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
<br>

>>**&lt;br&gt; 태그 - 줄바꿈** : br은 break의 줄임말. 줄을 바꿀 위치에 사용.

```html
줄<br>바꿈<br>다시바꿈
```
줄<br>바꿈<br>다시바꿈
<br>

>>**&lt;hr&gt; 태그 - 수평줄 추가** : hr은 horizontal의 줄임말. 수평 가로선을 삽입함

```html
단락1<hr>단락2<hr>단락3
```
단락1<hr>단락2<hr>단락3
<br>

>**텍스트를 한 줄로 표시하는 태그**

>>**&lt;strong&gt; 태그, &lt;b&gt; 태그 - 굵게 표시** : 중요한 내용에 굵게 표시. 다만 b 태그는 단순히 웹브라우저에서 굵게 표시하고 싶을 때만, strong 태그는 실제로 해당 부분이 문서에서 중요한 내용이라는 의미를 부여하고 싶을 때 사용

```html
<strong>굵게표시(중요하다는 의미 부여)</strong>
<b>굵게표시(단순 표시를 위함)</b>
```
<strong>굵게표시(중요하다는 의미 부여)</strong>
<b>굵게표시(단순 표시를 위함)</b>  
<br>

>>**&lt;span&gt; 태그 - 줄바꿈 없이 영역 묶기** : 텍스트 단락 안에서 일부 텍스트만 묶어 스타일을 적용할 때 사용

```html
<p>Lorem ipsum dolor sit amet, <span style="color:blue;">consectetur adipiscing elit</span>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
<p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
```
<p>Lorem ipsum dolor sit amet, <span style="color:blue;">consectetur adipiscing elit</span>, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
<p>Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
<br>

>**목록을 만드는 태그**

>>**&lt;ul&gt; 태그, &lt;li&gt; 태그 - 순서 없는 목록 만들기** : ul(unordered list)태그는 순서가 없는 목록을 만들 때 사용, li(list item)태그는 각 항목 표시에 사용

```html
<ul>
  <li>항목</li>
  <li>항목</li>
</ul>
```
<ul>
  <li>항목</li>
  <li>항목</li>
</ul>
<br>

>>**&lt;ol&gt; 태그, &lt;li&gt; 태그 - 순서 있는 목록 만들기** : ol(ordered list)태그는 순서가 있는 목록을 만들 때 사용, li(list item)태그는 각 항목 표시에 사용

```html
<ol>
  <li>항목1</li>
  <li>항목2</li>
</ol>

<!--항목 앞에 순서 표기 형태는 type 속성으로 설정. 기본값은 숫자-->
<ol type="A">
  <li>항목1</li>
  <li>항목2</li>
</ol>

<ol type="i">
  <li>항목1</li>
  <li>항목2</li>
</ol>

<ol>
  <li>항목1
    <!--</li>태그를 생략할 수 있고, 항목 안에 목록을 넣을 수도 있음-->
    <ol type="a">
      <li>내용
      <li>내용
    </ol>
  <li>항목2
</ol>
```
<ol>
  <li>항목1</li>
  <li>항목2</li>
</ol>
<ol type="A"><!--항목 앞에 순서 표기 형태는 type 속성으로 설정-->
  <li>항목1</li>
  <li>항목2</li>
</ol>
<ol type="i">
  <li>항목1</li>
  <li>항목2</li>
</ol>
<ol>
  <li>항목1
    <ol type="a"><!--</li>태그를 생략할 수 있고, 항목 안에 목록을 넣을 수도 있음-->
      <li>내용
      <li>내용
    </ol>
  <li>항목2
</ol>
<br>

>>**&lt;table&gt;, &lt;tr&gt;, &lt;td&gt;, &lt;th&gt;태그 - 기본적인 표 만들기**

```html
<table>
  <tr>
  <!--rowspan 속성의 값으로 세로로 합칠 셀 개수를 설정-->
    <th> 제목 셀 </th>
    <td  rowspan="2"> 1행 2열 <br>rowspan="2" </td>
    <td> 1행 3열 </td>
  </tr>
  <tr>
    <th> 제목 셀 </th>
    <td> 2행 3열 </td>   
  </tr>
  <tr>
    <th> 제목 셀 </th>
    <!--colspan 속성의 값으로 가로로 합칠 셀 개수를 설정-->
    <td colspan="2"> 3행 2열 colspan="2"</td>
  </tr>
</table>
```
<table>
  <tr>
  <!--rowspan 속성의 값으로 세로로 합칠 셀 개수를 설정-->
    <th> 제목 셀 </th>
    <td  rowspan="2"> 1행 2열 <br>rowspan="2" </td>
    <td> 1행 3열 </td>
  </tr>
  <tr>
    <th> 제목 셀 </th>
    <td> 2행 3열 </td>   
  </tr>
  <tr>
    <th> 제목 셀 </th>
    <!--colspan 속성의 값으로 가로로 합칠 셀 개수를 설정-->
    <td colspan="2"> 3행 2열 colspan="2"</td>
  </tr>
</table>

```html
<table>
  <tr>
    <th>이름</th>
    <td></td>
    <th>연락처</th>
    <td></td>
  </tr>
  <tr>
    <th> 제목 셀 </th>
    <td> 2행 3열 </td>   
  </tr>
  <tr>
    <th> 제목 셀 </th>
    <!--colspan 속성의 값으로 가로로 합칠 셀 개수를 설정-->
    <td colspan="2"> 3행 2열 colspan="2"</td>
  </tr>
</table>
```
<table>
  <tr>
    <th>이름</th>
    <td></td>
    <th>연락처</th>
    <td></td>
  </tr>
  <tr>
    <th>주소</th>
    <td colspan="3"></td>   
  </tr>
  <tr>
  <th>자기소개</th>
  <td colspan="3"></td>  
  </tr>
</table>
<br>

>>**&lt;caption&gt;, &lt;figcaption&gt; 태그 - 표 제목 붙이기**
```html
<table>
<!--caption 태그는 table 태그 바로 뒤-->
<!-- 제목이 표 위쪽 중앙에 표시된다 -->
  <caption>
    <strong>인적사항</strong>
    <p>인적사항 입력</p>
  </caption>
  <tr>
    <th>이름</th>
    <td></td>
    <th>연락처</th>
    <td></td>
  </tr>
  <tr>
    <th>주소</th>
    <td colspan="3"></td>   
  </tr>
  <tr>
  <th>자기소개</th>
  <td colspan="3"></td>  
  </tr>
</table>
```

<table>
<!--caption 태그는 table 태그 바로 뒤-->
<!-- 제목이 표 위쪽 중앙에 표시된다 -->
  <caption>
    <strong>인적사항</strong>
    <p>인적사항 입력</p>
  </caption>
  <tr>
    <th>이름</th>
    <td></td>
    <th>연락처</th>
    <td></td>
  </tr>
  <tr>
    <th>주소</th>
    <td colspan="3"></td>   
  </tr>
  <tr>
  <th>자기소개</th>
  <td colspan="3"></td>  
  </tr>
</table>
<br>

```html
<!--figcaption 태그는 설명글을 붙이고 싶은 대상을 figure 태그로 감싼 후
figcaption 태그를 이용해 제목이나 설명글을 입력한다.
caption 태그와 달리 중앙에 정렬되지 않는다.-->
<!-- 제목이 표 위쪽 중앙에 표시된다 -->
<figure>
  <figcaption>
  <p><u>인적사항</u> 입력</p>
  </figcaption>
  <table>
    <tr>
      <th>이름</th>
      <td></td>
      <th>연락처</th>
      <td></td>
    </tr>
    <tr>
      <th>주소</th>
      <td colspan="3"></td>   
    </tr>
    <tr>
    <th>자기소개</th>
    <td colspan="3"></td>  
    </tr>
  </table>
</figure>
```

<!--figcaption 태그는 설명글을 붙이고 싶은 대상을 figure 태그로 감싼 후
figcaption 태그를 이용해 제목이나 설명글을 입력한다.
caption 태그와 달리 중앙에 정렬되지 않는다.-->
<!-- 제목이 표 위쪽 중앙에 표시된다 -->
<figure>
  <figcaption>
  <p><u>인적사항</u> 입력</p>
  </figcaption>
  <table>
    <tr>
      <th>이름</th>
      <td></td>
      <th>연락처</th>
      <td></td>
    </tr>
    <tr>
      <th>주소</th>
      <td colspan="3"></td>   
    </tr>
    <tr>
    <th>자기소개</th>
    <td colspan="3"></td>  
    </tr>
  </table>
</figure>
<br>

>>**&lt;thead&gt;, &lt;tbody&gt;, &lt;tfoot&gt; 태그 - 표 구조 정의**
```html
<table>
  <caption>XX마을 학교현황</caption>
  <!--표의 제목 부분 -->
  <thead>
    <tr>
      <th>구분</th>
      <th>학교수</th>
      <th>학급수</th>
    </tr>
  </thead>
  <!--표의 본문 부분 -->
  <tbody>
    <tr>
      <th>초등학교</th>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>중학교</th>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>고등학교</th>
      <td>2</td>
      <td>2</td>
    </tr>
  </tbody>
  <!--표의 요약 부분 -->
  <tfoot>
  <tr>
    <th>합계</th>
    <td>5</td>
    <td>8</td>
  </tr>
  </tfoot>
</table>
```

<table>
  <caption>XX마을 학교현황</caption>
  <!--표의 제목 부분 -->
  <thead>
    <tr>
      <th>구분</th>
      <th>학교수</th>
      <th>학급수</th>
    </tr>
  </thead>
  <!--표의 본문 부분 -->
  <tbody>
    <tr>
      <th>초등학교</th>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>중학교</th>
      <td>1</td>
      <td>3</td>
    </tr>
    <tr>
      <th>고등학교</th>
      <td>2</td>
      <td>2</td>
    </tr>
  </tbody>
  <!--표의 요약 부분 -->
  <tfoot>
  <tr>
    <th>합계</th>
    <td>5</td>
    <td>8</td>
  </tr>
  </tfoot>
</table>
<br>

### ● 소스코드  
[https://github.com/monologue96/2020-Mogakco/blob/master/HTML5-CSS3/01/first.html](https://github.com/monologue96/2020-Mogakco/blob/master/HTML5-CSS3/01/first.html "소스코드")    
```html
<!DOCTYPE html><!--현재 문서가 HTML5로 작성된 웹 문서임을 나타낸다.  <!doctype>은 태그는 아니다-->
<html lang="ko">
    <!-- 웹 문서의 시작을 알리는 태그.
    <html>부터 </html>까지의 소스를 읽어 HTML 문법에 맞게 브라우저에 표시한다
    속성 lang을 사용하여 문서에서 사용할 언어를 지정할 수 있다-->

    <!-- lang 속성으로 언어를 지정하는 이유는 검색 엔진에서 특정 언어로 제한하여 검색할 때
    그 대상이 될 수 있기 때문이다.-->
<head>
    <!--웹브라우저가 웹문서를 해석하기 위해 필요한 정보들이 입력된 부분.
    문서에서 사용할 외부 파일들도 이곳에서 링크한다.
    문서 제목을 제외한 나머지는 화면에 표시되지 않는다.-->

    <meta charset="UTF-8">
        <!--인코딩 방법 지정-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <!--모바일 기기 고려-->
    <meta name="keywords" content="html5, 웹표준">
        <!--해당 문서의 키워드-->
    <meta name="description" content="html5를 통해 웹 표준 공부하기">
        <!--해당 문서의 설명-->
    <meta name="author" content="monologue96">
        <!--문서 소유자/제작자-->
    <title>내가 처음 만드는 HTML 문서</title>
        <!--문서의 제목-->
</head>
<body><!--웹 문서의 내용이 입력되는 구간. 실제로 웹브라우저 화면에 표시됨-->
    <h1>시간이란...</h1>
        <!--제목을 표시하는 태그-->
    <p>내일 죽을 것처럼 오늘을 살고<br>
        <!--<p> 태그는 단락을 표시-->
        <!--<br> 태그를 사용하면 줄바꿈-->
    영원히 살 것처럼 내일을 꿈꾸어라</p>
    <img src="images/first.jpg">
</body>
</html><!--웹 문서가 끝났다-->
```
<br>  

>**내가 작성한 웹문서를 다른 사람도 볼 수 있게 하기**  

다른 사람들이 웹브라우저를 통해 내가 작성한 웹 문서를 볼 수 있게 하려면, 작성한 웹 문서를 서버 컴퓨터로 업로드해야 한다. **내 컴퓨터(클라이언트)에서 웹 문서를 작성하여 서버에 업로드(upload)하면, 다른 사람의 컴퓨터(클라이언트)는 정해진 도메인 주소를 통해 서버에 접근하여 서버로부터 웹 문서를 다운로드(download)받아 웹브라우저를 통해 확인할 수 있다.**

클라이언트와 서버 컴퓨터 간에 업로드와 다운로드를 통해 파일을 주고 받을 수 있게 하는 것을 '**파일 전송 프로토콜(File Transfer Protocol; FTP)**'이라고 한다.

개인이 웹 서버를 운영할 수도 있지만 일반적으로 그것이 쉽지 않기 때문에 '웹 호스팅 서비스'를 이용하여 웹호스트의 서버 일부를 사용할 수 있다.

오늘 작성한 first.html 파일을 Github에 업로드하였는데, 내가 작성한 웹 문서를 Github의 서버에 업로드하였으므로 Github 역시 웹 호스팅 서비스를 제공한다고 볼 수 있다. 작성한 웹문서를 다른 유저가 확인하고 싶다면, 아래의 도메인 주소를 통해 first.html 파일이 업로드되어 있는 Github 서버에 접근하여 first.html 파일을 서버로부터 다운로드받아 웹브라우저를 통해 확인할 수 있다.  
[https://monologue96.github.io/2020-Mogakco/HTML5-CSS3/01/first.html](https://monologue96.github.io/2020-Mogakco/HTML5-CSS3/01/first.html)

<br>

### ● 회고  
1. HTML이 웹 표준을 만족시키는 웹문서를 만들기 위한 기본 언어임을 알게 되었다.
2. HTML 문서가 &lt;!doctype&gt;, &lt;html&gt;, &lt;head&gt;, &lt;body&gt; 네 가지 기본 요소로 구성된다는 것을 알게 되었다.
3. &lt;title&gt;, &lt;body&gt;, &lt;h1&gt;, &lt;p&gt;, &lt;img&gt; 태그의 의미와 사용법을 알게 되었다.
4. 웹사이트에 접근하여 웹사이트의 내용을 화면을 통해 확인하는 과정을 이해하였다.
5. 내가 작성한 웹문서를 인터넷에 연결된 다른 컴퓨터에서 볼 수 있게 하는 방법을 이해하였다.
