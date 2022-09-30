---
layout: post
title: "[Network] 도메인에 HTTPS 적용하기"
excerpt: CloudFlare에서 제공하는 범용 SSL 인증서를 이용하여 내 도메인에 HTTPS 적용하기
tags:
  - Network
  - Domain
  - HTTPS
  - SSL
category: TechJourney
date: 2022-09-18
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
          <th>SSL(Secure Socket Layer)</th>
          <td>보안 소켓 계층. 넷스케이프사에서 개발한 인터넷 보안 프로토콜로 웹사이트와 브라우저 사이에 전송되는 데이터를 암호화하여 인터넷 연결을 보호하는 표준 기술.</td>
          <td><a href="#ssl-소개">SSL 소개</a></td>
        </tr>
        <tr>
          <th>TLS(Transport Layer Security)</th>
          <td>전송 계층 보안. SSL(보안 소켓 계층) 기술이 표준화되면서 Transport Layer Security(TLS)으로 이름이 바뀜.</td>
          <td><a href="#tls와-ssl-차이">TLS와 SSL 차이</a></td>
        </tr>
        <tr>
          <th>DDOS(Distributed Denial of Service)</th>
          <td>서비스 거부 공격. 사이트 또는 네트워크 리소스 사용이 불가능하도록 악성 트래픽을 대량으로 보내는 공격.</td>
          <td> </td>
        </tr>
      </tbody>
 </table>
</div>

<br>

## Table of Contents
{:.no_toc}

* TOC 
{:toc}

---

## Intro
지난 블로그, [커스텀 도메인 적용기](https://dora-author.me/tech%20journey/network-customdomain)에 이어, 도메인에 HTTPS 프로토콜을 적용하는 방법에 관하여 설명하고자 한다. <br>

커스텀 도메인을 적용 후 발생하였던 HTTPS 연결 문제를 해결하고자 조사 결과, DNS 서비스 업체인 [CloudFlare](https://www.cloudflare.com/ko-kr/)에서 제공하는 [무료 SSL/TLS](https://www.cloudflare.com/ko-kr/ssl/) 기능을 사용하여 내 커스텀 도메인에 HTTPS 프로토콜을 적용해볼 수 있었다. <br>
HTTPS 적용 전, 내 웹사이트 URL 주소창에는 `⚠️주의 요함`이 나타났지만, HTTPS 적용 성공 이후에는 안전한 자물쇠 표시를 확인할 수 있었다.

  ![https](/img/tech/ssl-https.png)
  <p align="left">
  [그림 1. HTTPS 연결 설정이 완료된 URL 주소창]</p>

본 블로그에서는 내 도메인에 HTTPS를 적용하기 위한 기술로 SSL에 대한 소개부터 CloudFlare에서 제공하는 범용 SSL 인증서를 이용하여 도메인에 HTTPS를 적용하는 방법, HTTPS 연결을 위한 추가 설정 방법, 그리고 적용 이후 발생한 에러 해결 방법에 대하여 설명한다. 

<BR>

## SSL 소개 
Secure Socket Layer and Transport Layer Security(SSL)은 컴퓨터 네트워크에 통신 보안을 제공하기 위해 설계된 암호화 규약이다.<br>
SSL은 인터넷과 같이 TCP/IP 네트워크를 사용하는 통신에 적용되며, 브라우저(사용자의 컴퓨터)와 웹사이트(서버)) 간에 전송되는 데이터를 암호화하여 인터넷 연결을 보호하는 표준 기술이다. <br>
따라서 SSL을 적용하면 두 컴퓨터 시스템 간 데이터 통신 과정에서 종단 간 암호화(End to End Encryption)와 데이터 무결성을 확보함으로써 개인 정보나 금융 데이터와 같은 민감한 정보가 노출되거나 도용되는 것을 방지할 수 있다. <br>

### TLS와 SSL 차이
Transport Layer Security(TLS)는 SSL 기술이 표준화되면서 SSL 3.0을 기반으로 개발된 보다 향상되고 안전한 버전의 암호화 프로토콜이다. <br> 
보안 인증서를 SSL 인증서로 부르는 경우와 같이, SSL이 보다 일반적인 용어이지만 [TLS 1.3](https://namu.wiki/w/TLS#s-1.3.5)로 버전 업그레이드를 통한 업계 전반에 TLS 용어 사용이 늘어나면서, SSL/TLS 용어가 절충안으로 보인다. <Br>

### 통신 계층
SSL은 OSI 7계층에서 전송 계층(Transport Layer)과 응용 계층(Application Layer) 사이에 위치해 있다. <br>
내 컴퓨터의 웹 브라우저로 서버의 웹사이트에 접속한다고 했을 때, 서버로부터 전달 받은 데이터 패킷이 내 컴퓨터 시스템의 전송 계층 단까지 오면 SSL은 이 패킷의 암호를 해독하여 응용 계층으로 전달함으로써, 해당 HTTP 메시지를 웹 브라우저로 보여줄 수 있다.

![SSL](/img/tech/ssl-7layer2.png)
<p align="center">
  [그림 2. OSI 모델에서 SSL의 위치]
</p>

### 동작 방식
SSL은 '보안 인증서'로 동작함으로써 인터넷 연결을 암호화하고 보호한다. <br>
내 휴대폰에 나만이 풀 수 있는 보안 코드가 적용된 인증서를 설치하여 은행이나 민원 관련 서비스를 이용할 수 있는 것과 같다.<br>
SSL 인증서는 암호화키 혹은 공개키(public Key)를 적용한 '비대칭 암호화 방식'으로 동작한다. 비대칭 암호화는 어떤 문자를 A로 암호화하면 B로만 해독할 수 있는 방식이다.<br>
SSL 인증서를 통한 암호화 통신 과정은 아래와 같다. <br>

![SSL](/img/tech/ssl-transaction.png)
<p align="center">
  [그림 3. SSL 암호화 통신 과정]
</p>

  1] 클라이언트가 서버에 접속한다.

  2] 서버가 SSL 인증서를 제공한다.

  3] 클라이언트가 서버가 제공한 보안인증서의 유효성을 파악한다.
    최상위 발급 기관과 통신하여 유효성을 확인한다. (최상위 발급기관은 운영체제 또는 웹브라우저에 미리 정의되어 있다.)

  <div class="highlight2">
    <p> 서버에서 제공한 인증서가 유효하지 않다면 클라이언트는 검증 오류로 인해 아래 화면과 같이 통신을 중단한다.</p>
    <img src="/img/tech/ssl-notransaction.png" alt="ssl-notransaction" height="150" width="100">
  </div>
  
  4] SSL 인증서가 유효하면 클라이언트는 인증서에 쓰여져 있는 공개 암호화키 A를 이용하여 클라이언트 자신의 공개 암호화키 C를 암호화하여 서버로 전송한다.

  5] 서버는 전송된 암호화 구문을 자신이 가지고 있는 해독키(개인 비밀키) B를 이용하여 해독한다.

  6] 해독한 메시지가 유효한 요청이고 클라이언트의 공개 암호화키 C를 포함하고 있다면 서버는 암호화키 C를 이용하여 잘 받았다는 메시지를 암호화해서 응답한다.

  7] 클라이언트는 서버로부터 전달된 응답 메시지를 자신이 가지고 있는 해독키(개인 비밀키) D를 통해서 해독한다. 서버의 응답 메시지가 유효하다면 클라이언트는 다시 A 를 이용해 암호화해서 메시지를 보내고, 서버는 암호화키 C를 통해 암호화해서 메시지를 보낸다. <br>
  즉, 클라언트에서 A로 암호화된 메시지는 서버에서는 B로만 해독이 가능하고, 서버에서 C로 암호화된 메시지는 클라이언트에서는 D로만 해독이 가능하므로 종단 간 암호화(End to End Encryption) 통신이 성립된 것이다. 

  <div class="highlight2">
    <a href="https://namu.wiki/w/%EC%A2%85%EB%8B%A8%EA%B0%84%20%EC%95%94%ED%98%B8%ED%99%94">종단 간 암호화(End to End Encryption)</a>는 메시지를 보내는 곳부터 받는 곳까지의 모든 과정에서 암호화된 상태로 전송하는 방식으로, 메시지 전송 중에는 해독키가 없어 메시지 해석이 불가하므로, 중간 패킷 감청으로터 안전하다.
  </div>
<br>

위와 같은 과정을 'SSL 핸드쉐이크(SSL Hadnshake)'라고 부른다. 즉, 브라우저와 서버 간의 암호화된 데이터를 교환하기 위한 일련의 협상 과정을 의미하며, 이 과정을 통해 웹사이트(서버)와 브라우저(사용자 컴퓨터) 간에 암호화된 연결을 수립할 수 있다. <br>

SSL 인증서를 통한 SSL 핸드쉐이크 과정은 웹사이트에 방문하는 즉시 순간적으로 이루어지기 때문에 방문자(사용자 컴퓨터)측에서는 보이지 않지만, 암호화 통신이 성공하면 웹사이트 URL 창에 'HTTPS'로 표시되어 '현재 안전한 연결 상태'임을 확인할 수 있다. <br>

##  CloudFlare를 이용한 HTTPS 적용하기

<br>

### CloudFlare 특징

### 무료 SSL 서비스 사용하기(설정 순서)

  1. 클라우드 가입 및 웹사이트 추가
  2. DNS 변경
  3. 레코드 설정
     "Proxied" and "DNS Only" 차이
  4. https 연결 설정

### 성능 개선을 위한 추가 설정(캐시 관련)

## 에러 해결


