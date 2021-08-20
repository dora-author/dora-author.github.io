---
layout: post
title: "Google Technical Writing Pe-Class One"
excerpt: 
tags:
  - Google Technical Writing
category: Training
date: 2021-06-24
comments: true
---


## 내용 요약  
Google Developers Site에 [Technical Writing Course for Engineers](https://developers.google.com/tech-writing?hl=en) 가 개설되어 있다. 
영문으로 기술 문서를 작성할 때 실제로 도움될만한 팁이 많아 공유하고자 한다. 
크게 Pre-Class(이론), In-Class(실습) 두가지 세션이 있는데 [Pre-Class for Students](https://developers.google.com/tech-writing/overview?hl=en)의 One, Two 주요 내용을 요약했다.
(번역 유)
- - -

## Pre-Class One

### 주요 알아야 할 것   

  - 주요 영문법
  - 용어(Terminology) 사용
  - 대명사를 명확화 
  - 수동태를 능동태로 변환  
  - 문장을 명확하고 간결하게 작성하기
  - 불릿 리스트와 숫자 리스트의 차이 이해하기
  - 단락 작성법
  - 문서 시작의 Key Point
  - 독자가 이미 아는것과 알아야 할것을 결정
  - 마크다운 역량 개발
  - 쉼표, 괄호, 콜론, 대시 및 세미콜론의 적절한 사용

<br>

### 영문법
문법은 이 과정에서 설명하는 것보다 훨씬 더 복잡하지만, 간략히 품사를 중점적으로 설명한다.

  - 형용사는 명사를 수식
  - 부사는 동사를 수식
  - 전치사는 두 가지 사이의 관계를 지정 
  
    e.g. The C Programming Language **by** Kernighan and Richie remains popular
  

  > ⭐ Note: `under` is usually a preposition, `under` can also serve as an adverb or adjective depending on context

<br>

### 용어의 사용 👍
  
  - **새롭거나 생소한 용어**에 대하여
    - 이미 그 용어가 존재한다면 정의가 잘되어 있는 설명으로 [링크](https~)한다.
    - 문서에서 처음 소개하는 용어라면 그 용어를 정의한다. 문서에서 정의할 용어가 많다면 **용어집**으로 분류하여 작성한다.
  
  - **일관성**있는 용어 사용
    - 함수 중간에 변수 이름을 변경하면 코드가 컴파일되지 않듯이, 문서 중간에 용어를 변경하면 사용자의 머리에서 저자의 개념이 정립되지 않는다. 따라서 한번 용어 이름을 정했으면 변경하면 안된다.
    - 용어명이 길다면 해당 용어의 축약명을 같이 지정한다. 이후 문서 전체에서 해당 축약명을 사용할 수 있다.
  
  - **약어**의 적절한 사용
    - 전체 용어를 굵게 표시 후 두문자(약어)를 괄호안에 기입하여 굵게 표시.
    이후 해당 약어를 계속 사용할 수 있다.
    <br> Ex) ~ **Telekinetic Tactile Network**(**TTN**) ~ how to order **TTN** replacement parts </br>
    - 전체 용어와 해당 약어를 동일 문서에서 순환하면 안된다.

<br>

### 대명사의 명확화
대부분 대명사를 피하고 명사를 재사용해야 하나, 다음의 가이드대로 대명사를 사용하면 유용할 수 있다.

  - **명사를 소개한 후**에만 대명사를 사용하기
  - 대명사는 가능한 해당 명사와 가깝게 배치하기- **5 단어 이상** 명사로부터 떨어진 경우, 대명사 대신 명사를 반복하는게 좋다.
  - 명사와 대명사 사이 두 번째 명사를 사용하면 대명사 대신 명사를 재사용하기

<br>

### 능동태 vs. 수동태
테크니컬 라이팅에서 대부분의 문장은 **능동태**로 작성되어야 한다고 한다.
<br>일반적으로 능동태 문장이 더 명확하게 전달되므로 수동태로 작성된 문장도 능동태로 바꾸는게 좋다.

  - 능동태와 수동태의 공식 차이
    - 능동태: `주어 + 동사 + 목적어`
    - 수동태: `목적어 + 동사 + 주어`
  
  - 수동태 문장은 가끔식 주어가 생략되기도 한다. 이렇게 되면 독자를 주어를 추측해야 하므로 명확성이 낮아진다. 기술 문서에서 좋은 문장은 독자가 '누가 누구에게 무엇을 하는지'를 파악하도록 해야 한다.
  
  - 명령형 동사로 시작되는 명령문은 일반적으로 능동태이다. 명령문은 주어(you)를 함축하므로, 주어 생략이 가능한다. 

  - 능동태의 이점
    - **직관적**이다. 독자는 수동태도 능동태로 변환해서 해석하므로 바로 능동태를 쓰는 것이 독자가 받아들이는데 더 효율적이다.
    - 능동태 문장이 일반적으로 수동태 문장보다 짧다. 이는 저자 관점에서도 효울적이다.

<br>

### 명확한 문장

테크니컬 라이터는 명확성을 추구해야 하며, 명확성은 다른 규칙보다 가장 우선한다. 
<br> 명확한 문장을 만들기 위한 몇가지 방법은 다음과 같다.

  -  **효과적인 동사**를 선택: 테크니컬 라이팅에서 효과적인 동사란 그 문장을 잘 표현하기에 가장 적합한 동사라 할 수   
     있다.동사는 문장에서 가장 중요한 부분이므로 적합한 동사를 선택한다면, 나머지 문장은 그 자체로 전달될 수 있다.
    
      - 독자의 참여를 유도하고 교육시키기 위해, 정확하고 강력하며 구체적인 동사를 선택하고 다음과 같이 부정확하거나, 약하거나, 일반적인 동사는 지양해라.

      | **Weak Verb**                                         | **Strong Verb**                                    |
      | :---------------------------------------------------- | :------------------------------------------------- |
      | The error **occurs** when clicking the Submit button. | Clicking the Submit button **triggers** the error. |
      | This error message **happens** when ~                 | The system generates this error message when ~     |
      | We **are** very careful to ensure ~                   | We carefully **ensure** ~                          |

  - `there is`나 `there are`를 지양해라.
    
      - `there is`나 `there are` 대신 문장 끝에 있는 실제 의미있는 주어와 동사를 앞으로 옮기면 문장이 더 명확해진다.
      <br> Ex) ``There are`` two disturbing facts about Perl you should know.
          --> ``You should know`` two disturbing facts about Perl.
      
      - 새로운 주어와 동사를 만드는게 번거로워서 `there is`나 `there are`를 쓰는 경우가 많다. `there is`나 `there are` 대신 의미있는 주어를 만들면 넣으면 문장이 더 명확해진다.
      <br> Ex) ``There is`` no guarantee that the updates will be received in sequential order.
           --> ``Clients`` might not receive the updates in sequential order.``
   
<br>

### 간결한 문장

프로그래밍과 테크니컬 라이팅은 다음과 같은 이유로 간결성을 추구한다.

  - 짧은 코드/문서는 해석하기 쉽다. 빨리 읽을 수 있다.
  - 짧은 코드/문서는 유지보수 하기 쉽다
  - 추가적인 코드/문장은 실패 포인트를 제공한다.

#### 한 문장에는 하나의 아이디어

프로그램애서 하나의 statement(명령문)가 단일 작업을 처리하듯이, TW에서 하나의 문장은 단일 아이디어를 수행해야 한다.

  - 하나의 긴 문장은 일련의 단일 아이디어 문장으로 나눈다.
  - 지나치게 긴 문장은 짧은 문장으로 변환하나, 너무 많이 수정하지 않는다.

#### 긴 문장을 목록으로 변환

접속사로 이어지나 긴 문장은 글머리 기호(불릿 or 숫자)의 리스트로 재구조화합니다. 

#### 불필요한 단어를 제거하나거나 줄인다.

  Ex) An input value greater than 100 **causes the triggering of** logging.
  <br> --> An input value greater than 100 **triggers** logging.

  Ex) This design document **provides a detailed description of** Project Frambus.
  <br> --> This design document **describes** Project Frambus.

The following table suggests **concise replacements** for a few wordy expression

  | **Wordy**                 | **Concise** |
  | :------------------------ | :---------- |
  | at this point in time     | now         |
  | determine the location of | find        |
  | is able to                | can         |

#### 종속절 줄이기

`한 문장 = 한 주제` 공식을 염두하여 종속절이 하나의 주제를 확장한 내용이 아닌 별도의 주제를 다룬다면 별도의 문장으로 나누어라.

#### `that`과 `which`의 구별

  - 미국에서는 문장에서 필수적이지 않은 절에는 `which`, 필수적인 절에는 `that`을 사용한다.
  <br> Ex) Python is an interpreted language, **which** Guido van Rossum invented(nonessential)
  <br> Ex) Fortran is perfect for mathematical calculations **that** don't involve linear algebra(essential).

  - 종속절 시작하기에 앞서 멈춤이 필요하면 `which`를 사용하고, 멈춤이 필요 없이 이어지는 절에서는 `that`을 사용해라
  - `which` 앞에 쉼표(,)를 넣고, `that` 앞에 쉼표를 넣지 마십시오.

<br>

### 리스트와 표

좋은 리스트는 기술적 혼란을 질서있게 바꿀 수 있다.

다음은 테크니컬 라이팅에서 주로 쓰이는 리스트 타입이다.
  - bulleted lists
  - embedded listsI have been to Vetnam 

#### 올바른 타입의 리스트 선택하기

  - bulleted lists vs. numbered lists
    <br> 순서가 없는(순서를 바꿔도 내용 변경이 없는) 항목에는 `bulleted list`, 순서가 있는(순서를 바꾸면 내용 변경이 있는) 항목에는`numbered list`를 사용한다.

  - embedded lists: 
    - `run-in list`라 부르는 `embedded list`는 문장 내 열거형 항목으로 존재한다.<br>
    Ex) The llamacatcher API enables callers to **create and query llamas, analyze alpacas, delete vicugnas, and track dromedaries**. (4개 항목의 `embedded list`)

    - 일반적으로 `embedded list`는 기술 정보를 표시하는 데 좋은 방법은 아니므로 `bulleted list` 혹은 `numbered list`로 변환한다. 
    <br> Ex) The llamacatcher API enables callers to do the following:
    
      - Create and query llamas.
      -  Analyze alpacas.
      - Delete vicugnas.
      - Track dromedaries.

#### 리스트 항목을 병렬로 유지하기

효과적인 목록은 병렬입니다. 병렬 목록의 모든 항목은 '함께 속해있는 것'처럼 보인다.
<br> 즉 병렬 목록 항목은 다음 조건에 대하여 모두 공통성을 갖는다.

 - 문법
 - 범주
 - 대/소문자
 - 구두점

다음 리스트는 모든 항목이 복수 명사(문법),먹을 수 있는(범주), 소문자(대/소문자, 마침표가 없음(구두점)에서 모두 공통적이므로 병렬이다.

  - carrots
  - potatoes
  - cabbages

다음 리스트는 모든 항목이 대문자로 시작하고 구두점이 있는 문장이므로 병렬이다.
  - Carrots contain lots of Vitamin A.
  - Potatoes taste delicious.
  - Cabbages provide oodles of Vitamin K.  

반대로, 비병렬 리스트는 최소한 한 개 항목이라도 위 조건 중 최소한 한 개 이상 공통성을 갖지 않는다.

다음 리스트는 최소 한 개 항목이 네 가지 조건에 대해 모두 비병렬적이다.
  - carrots
  - potatoes
  - The summer light obscures all memories of winter.(문법, 범주, 대/소문자, 구두점)


#### 명령형 동사로 `numbered list` 시작하기

명령형 동사는 `open` 혹은 `start`와 같이 명령형이다.

병렬 `numbered list`의 모든 항목은 다음과 명령형 동사로 시작한다.

  1. Download the Frambus app from Google Play or iTunes.
  2. Configure the Frambus app's settings.
  3. Start the Frambus app.

다음 `numbered list` 중 두 개는 명령형 동사로 시작하지만 하나는 그렇지 않으므로 비병렬형이다. 병렬형으로 유지해야 한다.

  1. Instantiate the Froobus class.
  2. Invoke the Froobus.Salmonella() method.
  3. The process stalls.

<br>

### 단락 작성법

결합력 있는 단락은 만드는 몇 가지 지침 사항

#### 멋진 시작 문장 쓰기

시작 문장은 모든 단락애서 가장 중요하다. 바쁜 독자는 첫 문장에는 집중하고 다음 문장을 건너뛰기도 한다.

- 좋은 시작 문장은 단락의 중심점을 만든다.
- 결함이 있는 시작 문장은 독자를 잘못된 방향으로 보낸다.

  **Exercise**
  다음의 시작 문장은 단락이 피타고라스 정리에 초점을 맞출 것을 암시하기 때문에 결함이 있다. 사실, 단락의 초점은 실제로 클러스터링 알고리즘이다. 

  ```
  The Pythagorean Theorem states that the sum of the squares of both legs of a right triangle is equal to the square of the hypotenuse. The k-means clustering algorithm relies on the Pythagorean Theorem to measure distances. By contrast, the k-median clustering algorithm relies on the Manhattan Distance.
  ```
  다음의 시작 문장 더 효과적일 것이다.
  ```
  Different clustering algorithms measure distances differently.
  ```

<br>

### 문서 구성의 Key Point

#### 문서의 범위를 명시하기
 
- 좋은 문서는 그의 범의를 정의하며 시작한다.
  ```
  Ex) This document describes the overall design of Project Frambus.
  ```

- 더 좋은 문서는 독자가 문서에 다룰 것으로 예상할 수 있는 비범위 주제를 추가 정의한다.
  ```
  Ex) This document does not describe the design for the related technology, Project Froobus.
  ```
- 범위 및 비범위 설명은 독자뿐만 아니라 작성자에게도 도움이 된다. 쓰는 동안 문서의 내용이 범위 설명에서 벗어나면 문서의 초점을 다 맞주거나 범위 설명을 수정해야 한다. 

- 처음 초안을 검토할 때 범위 설명을 층족하는데 도움이 되지 않는 섹션을 삭제한다.
  

#### 독자를 명시하기
 
- 좋은 문서는 독자를 명시적으로 정의한다.
  
  ```
  Ex) I wrote this document for the test engineers supporting Project Frambus.
  ```
- 독자의 정의는 사전 조건 지식이나 경험을 지정할 수 있다.
  
  ```
  Ex) This document assumes that you understand matrix multiplication and how to brew a really good cup of tea.
  ```

#### 핵심 포인트를 미리 설정하기

- 문서를 검토할 때 시작 부분에서 독자의 필수 질문에 답하는지 확인해라.
- 전문 작가는 독자가 2 페이지를 읽을 확률을 높이기 위해 1 페이지에 상당한 에너지를 쏳는다.

#### 독자를 위해 작성하기

문서를 구성하기 위한 방법으로 독자를 정의한다.

- 독자를 정의하기: 다음의 질문은 문서에서 포함해야 할 것이 무엇인지 결정하도록 돕는다.
  - 대상 독자는 누구인지
  - 문서를 읽기 전 독자가 알고 있어야 할 것은 무엇인지
  - 문서를 읽은 후 독자가 알아야 할 것 혹은 할 수 있는 것은 무엇인지

- 독자의 필요 사항에 대하여 구성하기: 독자가 문서를 읽고 알아야 할 것, 할 수 있는 것을 문서에서 제공할 수 있도록 구성

#### 주제를 섹션으로 쪼개기

모듈식 코드가 읽기, 이해, 유지 관리 및 재사용에 더 쉽듯이 문서를 모듈식으로 만드는 것도 동일한 이점을 제공한다.

<br>

### Markdown  👍

**Markdown**은 많은 기술 전문가가 기술 문서를 만들고 편집하는 데 사용하는 가벼운 마크업 언어이다. Markdown을 사용하면 일반 텍스트 편집기(예: vi 또는 Emacs)에서 텍스트를 작성하고 헤더, 볼드체, 글머리 기호 등을 생성하기 위해 특수 문자를 삽입한다. 
<br>자세한 Markdown 문법은 이 블로그에서 별도로 정리한 [[TW] 마크다운 사용법](https://dora-author.github.io/markdown-usage)를 참조.

