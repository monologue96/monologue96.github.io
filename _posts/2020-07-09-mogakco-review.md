---  
layout: post  
title: "[Dev] 1. HTML 기본 다지기"  
subtitle: "2020 모각코 07-09 개인별 결과"  
categories: dev  
tags: 2020-Summer-Mogakco Web HTML  
comments: true  
<!--header-img: img/review/review-book-automate-tasks-1.png-->
---

## 개인별 결과
### ● 학습내용 정리
>**HTML**

**HTML(HyperText Markup Language)** : HyperText(웹 사이트에서 링크를 클릭해 다른 문서나 사이트로 즉시 이동할 수 있는 기능)를 Markup(tag를 사용하여 문서의  제목, 본문, 사진, 링크 등을 표시하는 것)하는 언어. 웹에서 자유롭게 오갈 수 있는 웹 문서를 만드는 언어.

사용자의 브라우저에 상관없이 쉽게 웹사이트를 볼 수 있게 하기 위해서는 웹 표준(웹사이트를 만들때 지켜야 하는 약속들)을 지킨 웹문서를 만들어야 한다. **HTML을 사용하면 웹 표준을 지킨 문서를 만들 수 있다.**

또한, HTML5(대부분의 웹 브라우저가 지원하는 현재 HTML의 표준안. HTML이라고 부른다)는 **애플리케이션 화면 디자인의 기초**이며, **웹사이트를 원하는 형태로 수정하고 싶을 때** HTML과 CSS 소스를 이해하고 있어야 한다.  
<br>

>**front-end와 back-end**

- **front-end** : 브라우저를 통해 화면에 보여줄 웹사이트의 내용(ex. 회원가입 화면)
- **back-end** : 웹사이트에 표시할 데이터, 사용자 정보 등을 저장하고 관리하는 부분(ex. 사용자가 회원가입 화면에서 정보를 입력하고 '가입하기' 버튼을 눌렀을 때 입력한 정보들은 백엔드 서버에 저장 및 관리된다)
- **HTML5은 front-end 기술이다.**  
<br>  

>**HTML 기본 문서 구조: &lt;!doctype&gt;, &lt;html&gt;, &lt;head&gt;, &lt;body&gt;**


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
https://monologue96.github.io/2020-Mogakco/HTML5-CSS3/01/first.html
<br>

### ● 회고  
1. HTML이 웹 표준을 만족시키는 웹문서를 만들기 위한 기본 언어임을 알게 되었다.
2. HTML 문서가 &lt;!doctype&gt;, &lt;html&gt;, &lt;head&gt;, &lt;body&gt; 네 가지 기본 요소로 구성된다는 것을 알게 되었다.
3. &lt;title&gt;, &lt;body&gt;, &lt;h1&gt;, &lt;p&gt;, &lt;img&gt; 태그의 의미와 사용법을 알게 되었다.
4. 웹사이트에 접근하여 웹사이트의 내용을 화면을 통해 확인하는 과정을 이해하였다.
5. 내가 작성한 웹문서를 인터넷에 연결된 다른 컴퓨터에서 볼 수 있게 하는 방법을 이해하였다.
