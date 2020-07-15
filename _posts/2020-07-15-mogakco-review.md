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
      <li>내용</li>
    </ol>
  </li>
  <li>항목2</li>
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

### ● 회고  
1. 텍스트, 목록과 관련된 태그를 이해하고 사용할 수 있게 되었다.
2. HTML 태그를 사용하여 표를 만들 수 있게 되었다.
