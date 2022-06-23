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

<h2 style="color: #308cbc"> | 기술 용어 | </h2>

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
          <td><a href="#도메인 구매하기">도메인 구매하기</a></td>
        </tr>
        <tr>
          <th>DNS(Domain Name System or Server)</th>
          <td> TCP/IP 프로토콜 체계를 유지하기 위한 컨트롤 프로토콜. 도메인 주소를 IP 주소로 변환하는 역할을 한다.</td>
          <td> </td>
        </tr>
        <tr>
          <th>TLD (Top-Level Domain)</th>
          <td>도메인 계층 정보 중 루트 다음의 최상위 도메인으로  인터넷할당번호관리기관(Internet Assigned Numbers Authority, IANA) 산하의 국제인터넷주소관리기구(Internet Corporation for Assigned Names and Numbers, ICANN)에서 관리한다. 일반 최상위 도메인(gTLD)으로 com, net, org, gov, mil, edu을 인터넷 초장기부터 사용해왔다.</td>
          <td></td>
        </tr>
      </tbody>
 </table>
</div>

## Table of Contents
{:.no_toc}

* TOC 
{:toc}

---

## Intro
많은 분들이 GitHub에서 제공하는 GitHub Pages 웹 호스팅 서비스를 통해 개인 블로그를 운영하고 있다. 
GitHub Pages에서 기본으로 제공하는 도메인 주소는 `<username>.github.io`가 된다. 이번 포스트에서는 이러한 도메인 주소에 사용자가 원하는 커스텀 도메인과 HTTPS 프로토콜을 적용하는 방법을 알아보겠다.

### 도메인 주소 구조
도메인 주소는 root, top-level, second-level, third-level 순서의 계층 구조를 가지며, 각 계층 간의 경계를 `.`으로 표시한다. DNS는 이를 맨 뒤의 `.`(root)부터 시작하여 최하위 레벨까지 역으로 해석한다. 참고로 root는 `.`으로 표시하며 주소로 표현 시 생략한다.
예를 들어 `<username>.github.io` 도메인 주소의 경우, `io`가 TLD(Top Level Domain)에 해당하며 `github`, `username` 순서로 Second Level, Third Level Domain이 된다. 

### HTTPS
HTTPS(HyperText Transfer Protocol over Secure Socket Laye)는 HTTP에 SSL/TLS(Secure Socket Layer and Transport Layer Security) 기술이 적용된 프로토콜로 기본적인 인터넷 전송 프로토콜인 HTTP의 보안이 강화된 버전이라고 할 수 있다. 따라서 사용자 컴퓨터와 방문한 사이트 간에 전송되는 사용자 데이터의 무결성과 기밀성을 유지할 수 있어 전자 상거래와 같은 웹사이트를 안전한 비공개 온라인 환경에서 이용할 수 있다. 
현재 대부분의 기업의 웹사이트에서는 HTTPS를 의무적으로 사용하기 때문에 HTTP로 접속은 더 이상 지원하지 않는다.
참고로 구글에서는 2014년부터 HTTPS를 쓰도록 권고했고 2017년 1월 크롬 56버전부터 HTTP로 접속하는 사이트에 대해서는 '안전하지 않음'이라는 경고를 띄우기 시작했다. 

[관련 기사 #파리사 타브리즈](https://www.econovill.com/news/articleView.html?idxno=309031)

[![파리사 타브리즈](https://cdn.econovill.com/news/photo/201702/309031_141789_1952.jpg)](https://cdn.econovill.com/news/photo/201702/309031_141789_1952.jpg "파리사 타브리즈")

이러한 이유로 새로 생성한 커스텀 도메인에 대해서도 HTTPS로 접속이 가능해야 한다.

<br>

## 본론
기본 깃허브페이지 주소를 커스텀 도메인 주소로 바꾸기 위해 도메인 구입 및 DNS 서버 선택에 대한 과정과 최종 생성한 커스텀 도메인에 HTTS 접속이 가능하도록 SSL/TLS 인증을 적용하는 과정에 대하여 설명한다.

### 도메인 구매하기
커스텀 도메인을 생성하려면 우선 고유의 도메인이 필요하다. 본인이 원하는 고유의 도메인을 구매하여 커스텀 도메인 주소로 사용할 수 있다.
도메인은 DNS 서비스를 제공하는 도메인 업체를 통하여 구매할 수 있다. 업체마다 원하는 TLD에 따른 구매 비용이 다르고, DNS 관리 외에 웹사이트 호스팅, 마케팅 등 추가적으로 제공하는 유료형 서비스가 다르므로 메이저급 이상의 안정적인 업체 위주로 비교하여 선정해야 한다.
필자는 같은 TLD 기준으로 비용이 저렴하면서도 안정적으로 도메인을 관리할 수 있는 규모가 있는 업체를 조사한 결과 [GoDaddy](https://kr.godaddy.com/)를 선택하게 되었다.

아래와 같은 단계로 원하는 도메인을 구매하여 설정한다.

**Step 1.**  [GoDaddy](https://kr.godaddy.com/)에서 원하는 도메인의 Second-Level, Top-Level 순서로 입력하여 검색한다.

**Step 2.** 선택한 도메인을 최소 1년 계약 단위로 구매한다. 구매 시 계정 로그인이 필요하다.

<div class="highlight2">⚠️<span style="color:red"> <i><b>Warning</b></i></span> <br>
구매 후 1년 후 동일 도메인을 유지할지 확신이 없다면 <b>요금 청구서 관리</b>에서 자동 갱신 옵션을 끄길 바란다. 그 외 구매와 함께 유료 서비스가 자동 선택되었을 수도 있으니 결제 방법으로 등록된 본인의 카드 정보도 삭제하길 바란다. 필자는 도메인에 대한 자동 갱신 옵션은 꺼두었으나 구매 시 자동으로 설정된 유료 서비스가 30일 이후 자동 결제 및 유료로 전환되는 것을 확인하지 못해 번거로운 환불 과정을 거쳐야 했다.
</div>

**Step 3.** **내 제품 > DNS 관리 > DNS 레코드**에서 기존 깃허브페이지 주소를 구매한 도메인 주소로 매핑하기 위한 레코드를 등록한다.
크게 도메인 주소를 IP 주소로 매핑하는 A 레코드와 `www` 없이 해당 도메인 주소로 매핑되도록 CNAME 레코드를 등록한다.

실제 깃허브페이지의 서버 IP 주소 4개를 아래와 같이 A 레코드로 등록한다.
![godaddy arecord](/img/tech/a_record1.png)

이어서 내 깃허브페이지 주소에 대한 CNAME 레코드를 아래와 같이 등록한다.
![godaddy crecord](/img/tech/cname_record.png)

<div class="highlight2">ℹ️<span style="color:#247CFF"> <i><b>NOTE</b></i> </span> <br>
현재 GitHub Pages 주소를 구매한 도메인 주소로 바꾸기 위한 CNAME 레코드 등록은 해당 깃허브 저장소에서 진행해야 한다.
</div>

<br>

### 도메인 네임서버 선택하기
도메인을 구매하고 관련 레코드를 등록하였으면 내 도메인 정보를 저장하고 관리할 도메인 네임서버(DNS)를 연결해야 한다. 도메인 네임서버는 내 도메인에 접속하려고 하는 사용자에게 도메인에 매핑된 실제 IP 주소를 전달해주며, 도메인을 구매한 사이트에서 제공해준다.

구매한 GoDaddy 사이트의 **내 제품 > DNS 관리 > 네임서버**에서 기본으로 제공된 네임서버를 확인할 수 있으며, **사용자 지정 네임 서버 사용**에서 변경할 수 있다.

### GitHub Pages에 커스텀 도메인 설정하기
현재 블로그의 배포 환경은 GitHub 저장소의 GitHub Pages 에서 관리되고 있다. 
기존 GitHub Pages 주소 대신 새로운 도메인 주소로 바꾸려면 배포되고 있는 저장소의 브랜치에 CNAME 레코드를 등록해야 한다.
이 과정은 아래와 같이 해당 저장소의 **GitHub Pages > Custom domain**에서 구매한 도메인 주소를 `<SLD>.<TLD>` 형태로 저장하여 진행할 수 있다.

![githubcustomdomain](/img/tech/github_customdoamin.png)

### 적용 결과 '주의 요함'
여기까지 진행했으면 커스텀 도메인이 적용된 블로그 주소를 생성할 수 있을 줄 알았으나, 몇 시간 뒤 새로운 도메인 주소로 접속했을 때 크롬 브라우저 주소표시창에 'HTTPS가 사용되지 않았다' 는 상세 메시지와 함께 '주위 요함' 경고가 표시되었다.

<img src="/img/tech/nossl.png" alt="안전하지 않음">

<div class="highlight2">
이러한 경고는 내 사이트에 접속할 적마다 신뢰감이 없어보여 상당히 거슬리는게 마련이다.
다음 섹션에서는 이 부분을 해결하고자 
내 도메인 주소에 HTTPS 적용하는 방법에 대해 알아보겠다.
</div>

