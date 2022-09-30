---
layout: post
title: "[TW] 마크다운 사용법"
excerpt: 마크다운 문법과 사용법에 관하여
tags:
  - Markdown
category: DocsasCode
date: 2021-08-14
comments: true
---

**<Table of Contents>**  
* TOC 
{:toc}

<Br>

## Intro
웹 콘텐츠에서 주로 쓰이는 Markdown을 사용하기 위한 문법 및 예시에 관한 내용이다. 

***

<br>

## Callout Convention 규칙
작성 내용 중 독자가 참고해야 할 노트(혹은 정보), 설정 팁, 주의사항 에 대하여 아래와 같이 표기한다.

### Html 링크 적용한 Convention 규칙 생성
각 callout용 html 파일을 블로그 프로젝트 내 `_includes` 폴더에 넣고 링크하는 방식으로 적용한다.

**- How to look**

{% include callout.html title=" **Note**" content="This is my callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="primary" %}

{% include callout_tip.html title=" **Tip**" content="This is my callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="success" %} 

{% include callout_warning.html title= " **Warning**" content="This is my **danger** type." type="danger" level=3 %}

<br>

### Markdown을 통한 Convention 규칙 생성
미리 정의한 callout용 html 파일 대신 마크다운 문법과 간략한 style tag를 적용해서 Convention 규칙을 만들 수 있다. <Br>
먼저 마크다운용 컨벤션 아이콘(ℹ️, ⚠️, ✅)을 사용하기 위한 `:emojisense:` 확장자를 설치한다.

**- How to use**
<pre>
  > ℹ️<span style="color:#247CFF">***NOTE*** </span> <br>
  > This is note content.
</pre>

<br>

**- How to look**

  > ℹ️<span style="color:#247CFF">***NOTE*** </span> <br>
  > This is note content.

<br>

## 강조 블록 표기 규칙

### 단락형 강조 구문

  <div class="highlight2">
  이건 어때요? <br>
  색상태그를 적용했습니다.
  </div>

### 문장형 강조 구문

  `이건 어때요? 문장을 backquote로 감싼 my code입니다.`

<br>

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
<br>

## 단어 표현

| How to use                    | How to look  |
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

## 인용구 블록

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

## 제목 수준

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
    {:.no_toc}

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

## 리스트

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

## 링크

|             | **How to use**                                                               | **How to look**             |
| :---------- | :--------------------------------------------------------------------------- | :-------------------------- |
| url 링크    | \<http://github.com>                                                         | http://github.com           |
| 참조 링크   | 검색엔진은 [Google][1] 이 있다. </br> [1]: http://google.com “구글”          | 검색엔진은 google이 있다.   |
| 인라인 링크 | [url 대신 표현 단어](url 주소) </br> Ex) `[Google](http://google.com"구글")` | [Google](http://google.com) |
| 내부 링크   | [표현할 단어](#작성한 본문 내 제목) </br> Ex) `[리스트로 가기](#리스트)`     | [리스트로 가기](#리스트)    |

<br>

## 이미지 삽입

**- How to use**

`![이미지 이름](이미지 주소)`

Ex) `![markdown_logo](https://raw.github.com/dcurtis/markdown-mark/master/png/208x128.png)`

<br>

**- How to look**

![markdown_logo](https://raw.github.com/dcurtis/markdown-mark/master/png/208x128.png)

<br>

## 테이블

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

## 단락 구분

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

## 접어두기 표시

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

## 작업 목록

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

