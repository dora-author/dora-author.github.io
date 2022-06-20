---
layout: post
title: "[Network] 커스텀 도메인 적용기"
excerpt: 커스텀 도메인 적용을 위한 기술 스터디
tags:
  - network
  - domain
category: Tech Journey
date: 2022-06-17
comments: true
---


<h2 style="color: #308cbc">  | 기술 용어 |  </h2>

<div>
 <table class>
      <thead>
        <tr>
          <th width="200">용어</th>
          <th>설명</th>
          <th width="150">연관 콘텐츠</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>도메인(Domain)</th>
          <td>인터넷에서 특정 사이트를 찾아가기 위한 의미있는 문자열로 구성된 주소. 숫자로 구성된 IP 주소 대신하여 사람이 인식하고 기억하기 쉬워 도메인 주소를 이용함.</td>
          <td><a href="#링크">Label</a></td>
        </tr>
        <tr>
          <th>TLD (Top-Level Domain)</th>
          <td>도메인 계층 정보 중 루트 다음의 최상위 도메인으로 IANA(Internet Assigned Numbers Authority)에서 정의한 6가지 유형이 있다.</td>
          <td> </td>
        </tr>
        <tr>
          <th>TLD (Top-Level Domain)</th>
          <td>도메인 계층 정보 중 루트 다음의 최상위 도메인으로 IANA(Internet Assigned Numbers Authority)에서 정의한 6가지 유형이 있다.</td>
          <td></td>
        </tr>
      </tbody>
 </table>
</div>

<br>

---

**<Table of Contents>**  
* TOC 
{:toc}

---
# 본론
ㅁㅇㄹ

## Intro
많은 분들이 깃허브페이지의 웹 호스팅 서비스를 통해 개인 블로그를 운영하고 있.다. 
깃허브 페이지 호스팅 시 기본적으로 제공되는 도메인 주소는 <`username`.github.io>가 된다. 이번 포스트에서는 이러한 도메인 주소에 사용자가 원하는 커스텀 도메인과 HTTPS 프로토콜을 적용하는 방법을 알아보겠다.

### 도메인 주소 구조
도메인 주소는 root, top-level, second-level, third-level 순서의 계층 구조를 가지며, 각 계층 간의 경계를 `.`으로 표시한다. DNS는 이를 맨 뒤의 .root부터 시작하여 최하위 레벨 계층까지 역으로 해석한다. 참고로 root는 `.`으로 표시하며 주소로 표현 시 생략한다.
예를 들어 <`username`.github.io> 도메인 주소의 경우, `io`가 TLD(Top-level Domain)에 해당하며 `github`, `username`이 각 Second-Level, Third Level Domain이 된다. 

### HTTPS
HTTPS(HyperText Transfer Protocol over Secure Socket Laye)는 HTTP에 SSL/TLS(Secure Socket Layer and Transport Layer Security) 기술이 적용된 프로토콜로 기본적인 인터넷 전송 프로토콜인 HTTP의 보안이 강화된 버전이라고 할 수 있다. 따라서 사용자 컴퓨터와 방문한 사이트 간에 전송되는 사용자 데이터의 무결성과 기밀성을 유지할 수 있어 전자 상거래와 같은 웹사이트를 안전한 비공개 온라인 환경에서 이용할 수 있다. 
현재 대부분의 기업 웹사이트에서는 HTTPS를 의무적으로 사용하기 때문에 HTTP로 접속은 더 이상 지원하지 않는다.
참고로 구글에서는 2014년부터 HTTPS를 쓰도록 권고했고 2017년 1월 크롬 56버전부터 HTTP로 접속하는 사이트에 대해서는 '안전하지 않음'이라는 경고를 띄우기 시작했다.

이러한 이유로 새로 생성한 커스텀 도메인에 대해서도 HTTPS로 접속이 가능해야 한다.

<br>

## 본론
기본 깃허브페이지 주소를 커스텀 도메인 주소로 바꾸기 위해 도메인 구입 및 DNS 서버 선택에 대한 과정과 최종 생성한 커스텀 도메인에 HTTS 접속이 가능하도록 SSL/TLS 인증을 적용하는 과정에 대하여 설명한다.

### 도메인 구매하기
커스텀 도메인을 생성하려면 우선 고유의 도메인이 필요하다. 본인이 원하는 고유의 도메인을 구매하여 커스텀 도메인 주소로 사용할 수 있다.
도메인은 DNS 서비스를 제공하는 도메인 업체를 통하여 구매할 수 있다. 업체마다 원하는 TLD에 따른 구매 비용이 다르고, DNS 관리 외에 웹사이트 호스팅, 마케팅 등 추가적으로 제공하는 유료형 서비스가 다르므로 메이저급 이상의 안정적인 업체 위주로 비교하여 선정해야 한다.
필자는 같은 TLD 기준으로 구매 비용이 저렴하면서도 안정적인 호스팅 환경을 제공하는 규모가 있는 업체를 조사한 결과 [GoDaddy](https://kr.godaddy.com/)를 선택하게 되었다.

아래와 같은 단계로 원하는 도메인을 검색해 구매한다.

**Step 1.**  [GoDaddy](https://kr.godaddy.com/)에서 원하는 도메인의 Second-Level, Top-Level 순서로 입력하여 검색한다.

**Step 2.** 선택한 도메인을 최소 1년 계약 단위로 구매한다. 구매 시 계정 로그인이 필요하다.

> ⚠️ <span style="color: red"> ***Warning*** </span> <br>
구매 후 1년 후 동일 도메인을 유지할지 확신이 없다면 **요금 청구서 관리**에서 자동 갱신 옵션을 끄길 바란다. 그 외 구매와 함께 유료 서비스가 자동 선택되었을 수도 있으니 아예 결제 방법으로 등록된 본인의 카드 정보도 삭제하길 바란다. 필자는 도메인에 대한 자동 갱신 옵션은 꺼두었으나 구매 시 자동으로 설정된 유료 서비스가 30일 이후 자동 결제 및 유료로 전환되는 것을 확인하지 못해 번거로운 환불 과정을 거쳐야 했다.

**Step 3.** 내 제품 > DNS 관리에서 기존 깃허브페이지 주소를 구매한 도메인 주소로 매핑하기 위한 레코드를 등록한다.
크게 도메인 주소를 IP주소로 매핑하는 A 레코드와 `www`없이도 해당 도메인 주소로 매핑되도록 CNAME 레코드를 등록한다.

실제 깃허브페이지 IP 주소 4개로 매핑하도록 A 레코드를 아래와 같이 등록한다.





DNS 서버 선택하기
TLS/SSL 적용하기

## Callout  연습

{% include note.html content="This is my note. All the content I type here is treated as a single  paragraph." %}
<br>

{% include callout.html title=" **Note**" content="This is my callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="primary" %}

{% include callout_tip.html title=" **Tip**" content="This is my callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="success" %} 

{% include callout_warning.html title= " **Warning**" content="This is my **danger** type." type="danger" level=3 %}

{% include callout.html type="danger" content="This is my **danger** type callout" %}
<br>

## 강조 블록 표기 규칙

### 단락형 강조 구문 (alert외 별도로)

> <div style= "background-color:#ededed; padding:10px"><span class="highlight">
> 이건 어때요? <br>
> 색상태그를 적용했습니다. </span></div>


### 문장형 강조 구문

`이건 어때요? 문장을 backquote로 감싼 my code입니다.`

## 코드 블록

```c
  int val = 10; // ```C 적용함  
  printf(%s,"Hello, World!"); 
```

```curl
  $ git clone https://github.com/swagger-api/swagger-ui.git 
```

```c
  <div style= "background-color:#444; padding:10px">
    int val = 10; // ```C 안에 <div> 블랙 바탕 색상 태크 적용 안됨  
    printf(%s,"Hello, World!"); 
  </div>
```


***

### 단어 표현


| How to use                    | How to look      |
| :---------------------------- | :--------------- |
| \_기울임\_ or <br> \*기울임\* | _기울임_         |
| \*\*굵게\*\*                  | **굵게**         |
| \*\*\*굵고기울임\*\*\*        | ***굵고기울임*** |
| \~\~취소선\~\~                | ~~취소선~~       |
| \<U>밑줄\</U>                 | <u>밑줄</u>      |
| \`인라인코드\`                | `인라인코드`     |

<br>

> ℹ️ <span style="color:#247CFF"> ***NOTE*** </span> <br>
> 테이블 칸 안에서 줄바꿈을 할 경우, `</br>`을 줄바꿈할 단어 앞에 기입하여 한 줄로 
> 작성한다. <br>
  Ex) b를 a 다음줄에 오도록 하려면 `a </br> b` 를 한 칸에 한 줄로 작성한다.



<br>

### 인용구 및 블락

-	인용구: 작성할 텍스트 앞에 `>`을 기입하면 해당 텍스트가 구분되는 인용구가 된다.<br>

    **- How to use**

    \> 안녕하세요

    <br>

    **- How to look**

    > 안녕하세요

<br>

> ℹ️ <span style="color:#247CFF"> ***NOTE*** </span> <br>
> `>` 다음줄에 `>>`, 그 다음 줄에 `>>>`를 기입하면 여러 계층의 인용구로 작성할 수 있다.

<br>

-	코드 블락: 코드를 일반 문장과 구분하기 위해 블락으로 표현. 예시나 구분이 필요한 내용을 블락으로 묶을 때도 사용한다.<br>

    **- How to use**

    해당 문장의 앞 줄과 다음 줄에 \`\`\` 혹은 `~~~`을 기입한다.
    <Br>

    \`\`\`
    <br> 안녕하세요.

    \`\`\`

    <br>

    **- How to look**

    ```
    안녕하세요.
    ```

    <br>

> ℹ️ <span style="color:#247CFF"> ***NOTE*** </span> <br>
> 코드 문법을 적용하기 위해 첫 줄에 \`\`\`와 해당 언어 종류를 같이 기입한다.<br>
> Ex) 첫줄을 \`\`\`c 와 같이 기입하면 해당 문법에 대한 색상이 적용된다.
> 
>   ```c 
>    int val = 10; // C문법 적용함
>    printf(%s,"Hello, World!");
>  ```  

<br>

### 제목 수준

-	큰제목: 텍스트 밑에 `=====` 기입<br>

    **- How to use**

    ```
    큰제목
    ======
    ```

    <br>

    **- How to look**

    큰제목
    ======
    {:.no_toc}

<Br>

- 작은 제목: 텍스트 밑에 `-----` 기입 <Br>

    **- How to use**

    ```
     작은제목
     -------
    ```
    <br>

    **- How to look**

  작은 제목
  ---------
  {:.no_toc}

<br>

- `#`을 사용하여 다양한 수준으로 표현: 1단계부터 6단계까지 지원

    **- How to use**
    ```
    # 1단계 //가장 큰제목
    ##### 5단계 //5번째로 큰제목
    ```

    <br>

    **- How to look**

    # 1단계
    ##### 5단계

<br>

### 리스트

-	Unordered <br>  
    **- How to use**

    ```
	  -	Item 1
	  -	Item 2
	    -	Item 2a
	    -	Item 2b
    ```
    <Br>

    **- How to look**

    * Item 1
    * Item 2
      * Item 2a
      * Item 2b

<Br>

-	Ordered <br>
    **- How to use**

    ```
	  1. Item 1 //첫 줄은 무조건 1부터 시작
	  2. Item 2 //번호를 순서대로 안써도 2로 인식함
	  3. Item 3 //번호를 순서대로 안써도 3으로 인식함
		  1. Item 3a //앞 줄 대비 세 칸 띄우고 1부터 시작
		  2. Item 3b //번호를 순서대로 안써도 2로 인식함
    ```
    <Br>

    **- How to look**

    1. Item 1
    2. Item 2
    3. Item 3
       1. Item 3a
       2. Item 3b

<br>

### 링크

|             | **How to use**                                                               | **How to look**             |
| :---------- | :--------------------------------------------------------------------------- | :-------------------------- |
| url 링크    | \<http://github.com>                                                         | http://github.com           |
| 참조 링크   | 검색엔진은 [Google][1] 이 있다. </br> [1]: http://google.com “구글”          | 검색엔진은 google이 있다.   |
| 인라인 링크 | [url 대신 표현 단어](url 주소) </br> Ex) `[Google](http://google.com"구글")` | [Google](http://google.com) |
| 내부 링크   | [표현할 단어](#작성한 본문 내 제목) </br> Ex) `[리스트로 가기](#리스트)`     | [리스트로 가기](#리스트)    |

<br>

### 이미지 삽입

**- How to use**

`![이미지 이름](이미지 주소)`

Ex) `![markdown_logo](https://raw.github.com/dcurtis/markdown-mark/master/png/208x128.png)`

<br>

**- How to look**

![markdown_logo](https://raw.github.com/dcurtis/markdown-mark/master/png/208x128.png)

<br>

### 테이블

**- How to use**
<pre> 
    | First Header | Second Header  |       Third Header |
    | :----------- | :------------: | -----------------: |
    | 왼쪽맞춤     |   가운데맞춤   |         오른쪽맞춤 |
    | Second row   |    **Cell**    |             *Cell* |
    | Third row    | Cell that span | across two columns |
    
</pre>
  

<br>

**- How to look**

| First Header | Second Header  |       Third Header |
| :----------- | :------------: | -----------------: |
| 왼쪽맞춤     |   가운데맞춤   |         오른쪽맞춤 |
| Second row   |    **Cell**    |             *Cell* |
| Third row    | Cell that span | across two columns |

<br>

### 단락 구분

같은 제목 내에서도 구분할 내용에 대하여 내용 앞줄 혹은 뒷 줄에 `***` or `---` or `___` or `---` 를 사용하여 수평선을 표현

**- How to use**

<pre>

  ***
  이 단락의 내용을 앞 내용과 구분

</pre>

<Br>

**- How to look**

---
이 단락의 내용을 앞 내용과 구분

<br>

### 접어두기 표시

**- How to use**

<pre>
  <summary\>상세 내용 확인</summary>
    <details markdown="1"
      div 에 markdown attribute를 1 로
      하는 이유는 div 안에서 markdown 을 사용하기 위해서입니다.
</pre>

<br>

**- How to look**

<summary>상세 내용 확인</summary>
<details markdown="1">
 <pre> div 에 markdown attribute를 1 로 하는 이유는 div 안에서 markdown을 사용하기 위해서입니다.</pre></details>

<br>

### 작업 목록

**- How to use**

<pre>
  - [x] #739
  - [ ] Add delight to the experience when all tasks are complete
  - [ ] Open a followup issue
</pre>

<br>

**- How to look**

-	[x] #739
-	[ ] Add delight to the experience when all tasks are complete
-	[ ] Open a followup issue

<br>

### 컨벤션 규칙
작성 내용 중 독자가 참고해야할 메모, 주의 사항, 팁스에 대하여 다음과 같이 표기한다.

**- How to use**

<pre>
  > ℹ️ `<span style="color:#247CFF">` ***NOTE*** `</span>`
  > This is note content.
</pre>
