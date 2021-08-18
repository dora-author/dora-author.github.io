---
layout: post
title: "[TW] 마크다운 사용법"
excerpt: 
tags:
  - Markdown
category: Technical Writing
date: 2021-08-14
comments: true
---

## Markdown 사용법  👍

**Markdown**은 많은 기술 전문가가 기술 문서를 만들고 편집하는 데 사용하는 가벼운 마크업 언어입니다. Markdown을 사용하면 일반 텍스트 편집기(예: vi 또는 Emacs)에서 텍스트를 작성하고 헤더, 볼드체, 글머리 기호 등을 생성하기 위해 특수 문자를 삽입합니다. 다음은 Markdown 형식의 간단한 사용법과 예에 관한 내용입니다. 

<br>

### 단어 표현

  | **How to use**                 | **How to look**  |
  | :----------------------------- | :--------------- |
  | \_기울임\_ or </br> \*기울임\* | _기울임_         |
  | \*\*굵게\*\*                   | **굵게**         |
  | \*\*\*굵고기울임\*\*\*         | ***굵고기울임*** |
  | \~\~취소선\~\~                 | ~~취소선~~       |
  | \`인라인코드\`                 | `인라인코드`     |

> ℹ️ **_NOTE_** 
<br> 테이블 칸 안에서 줄바꿈을 할 경우, `</br>`을 줄바꿈할 단어 앞에 기입하여 한 줄로 작성한다.
<br> Ex) b를 a 다음줄에 오도록 하려면 `a </br> b` 를 한 칸에 한 줄로 작성한다.


<br>

### 인용구 및 블락

- 인용구: 작성할 텍스트 앞에 `>`을 기입하면 해당 텍스트 전체가 회색으로 구분되는 인용구가 된다. <br>
  
  **How to use** <br>
  \> 안녕하세요

  **How to look**
  > 안녕하세요

> ℹ️ **_NOTE_** <br>
  `>` 다음줄에 `>>`, 그 다음 줄에 `>>>`를 기입하면 여러 계층의 인용구로 작성할 수 있다. <br>

- 코드 블락: 코드를 일반 문장과 구분하기 위해 블락으로 표현. 예시나 구분이 필요한 내용을 블락으로 묶을 때도 사용한다. <br>
  
  **How to use** <br>
  해당 문장의 앞 줄과 다음 줄에 ` ``` ` 혹은 `~~~`을 기입한다. <br>

  \`\`\` <br>
  안녕하세요 <br>
  \`\`\`

  **How to look**
  ```
  안녕하세요
  ```
  
  > ℹ️ **_NOTE_** 
  <br> 코드 문법을 적용하기 위해 앞 줄에 ` ``` ` 와 해당 언어 종류를 같이 기입한다.
  <br> Ex)  앞 줄에 ` ```c ` 와 같이 기입하면 해당 문법에 대한 색상이 적용된다.
  > ```c 
  > int val = 10; // C문법 적용함
  > printf(%s,"Hello, World!");
  > ```

<br>

### 제목 수준

- 큰제목: 텍스트 밑에 `=====` 기입
  
  **How to use**
  ```
  큰제목
  ======
  ```

  **How to look**

  큰제목
  ======

- 작은 제목: 텍스트 밑에 `-----` 기입
  
  **How to use**
  ```
  작은제목
  -------
  ```
  **How to look**

  작은제목
  --------

- `#`을 사용하여 다양한 수준으로 표현: 1단계부터 6단계까지 지원
  
  **How to use**
  ```
  # 1단계 //가장 큰제목
  ```
  ```
  ##### 5단계 //5번째로 큰제목
  ```
  **How to look**

  # 1단계

  ##### 5단계 

<br>

### 리스트

- Unordered
  
  **How to use**
  ```
  * Item 1
  * Item 2
    * Item 2a
    * Item 2b
  ```
  **How to look**  
  * Item 1
  * Item 2
    * Item 2a
    * Item 2b

- Ordered
  
  **How to use**
  ```
  1. Item 1 //첫 줄은 무조건 1부터 시작
  1. Item 2 //번호를 순서대로 안써도 2로 인식함
  1. Item 3 //번호를 순서대로 안써도 3으로 인식함
     1. Item 3a //앞 줄 대비 세 칸 띄우고 1부터 시작
     3. Item 3b //번호를 순서대로 안써도 2로 인식함
  ```
  **How to look**
  1. Item 1
  1. Item 2
  2. Item 3
     1. Item 3a
     3. Item 3b

<br>

### 링크 

  |             | **How to use**                                                               | **How to look**                   |
  | :---------- | :--------------------------------------------------------------------------- | :-------------------------------- |
  | url 링크    | \<http://github.com\>                                                        | <http://github.com>               |
  | 참조 링크   | 검색엔진은 [Google][1] 이 있다. </br> [1]: http://google.com “구글”          | 검색엔진은 google이 있다.         |
  | 인라인 링크 | [url 대신 표현 단어](url 주소) </br> Ex) `[Google](http://google.com"구글")` | [Google](http://google.com"구글") |
  | 내부 링크   | [표현할 단어](#작성한 본문 내 제목) </br> Ex) `[링크](#링크)`                | [링크](#링크)                     |
 
<br>

### 이미지 삽입

  **How to use**
   
  `![이미지 이름](이미지 주소)`

   Ex) `![markdown_logo](https://raw.github.com/dcurtis/markdown-mark/master/png/208x128.png)`

  **How to look**
  
  ![markdown_logo](https://raw.github.com/dcurtis/markdown-mark/master/png/208x128.png)


<br>

### 테이블

  **How to use**
  ~~~ 
  | First Header | Second Header  |       Third Header |
  | :----------- | :------------: | -----------------: |
  | 왼쪽맞춤     |   가운데맞춤   |         오른쪽맞춤 |
  | Second row   |    **Cell**    |             *Cell* |
  | Third row    | Cell that span | across two columns |
  ~~~ 

  **How to look**

  | First Header |           Second Header            | Third Header |
  | :----------- | :--------------------------------: | -----------: |
  | 왼쪽맞춤     |             가운데맞춤             |   오른쪽맞춤 |
  | Second row   |              **Cell**              |       *Cell* |
  | Third row    | Cell that spans across two columns |              |

<br>

### 단락 구분

같은 제목 내에서도 구분할 내용에 대하여
내용 앞줄 혹은 뒷 줄에 \*\*\* or --- or \_\_\_ or --- 를 사용하여 수평선을 표현

  **How to use**

  ```
  ***
  이 단락의 내용을 앞 내용과 구분
  ```

  **How to look**

  ***
  이 단락의 내용을 앞 내용과 구분

<br>

### 접어두기 표시

  **How to use**

  ```
  <details markdown="1">
  <summary>상세 내용 확인</summary> 
  div 에 markdown attribute를 1 로 
  하는 이유는 div 안에서
  markdown 을 사용하기 위해서입니다.
  </details>
  ```

  **How to look**
  
  <details markdown="1">
  <summary>상세 내용 확인</summary> 
  div 에 markdown attribute를 1 로 
  하는 이유는 div 안에서
  markdown 을 사용하기 위해서입니다.
  </details>

<br>

### 작업 목록

  **How to use**

  ```
  - [x] #739
  - [ ] Add delight to the experience when all tasks are complete
  - [ ] Open a followup issue
  ```
  
  **How to look**

  - [x] #739
  - [ ] Add delight to the experience when all tasks are complete
  - [ ] Open a followup issue

<br>

### 컨벤션 규칙

작성 내용 중 독자가 참고해야할 메모, 정보, 주의 사항에 대하여 다음과 같이 표기한다.

  **How to use**
  
  ```
  > ℹ️ **_NOTE_** <br>
  This is note content.

  > ⚠️ **_Warning_** <br>
  This is a warning content.
  ```

  **How to look**

  > ℹ️ **_NOTE_** <br>
    This is note content.

  > ⚠️ **_Warning_** <br>
    This is a warning content.


