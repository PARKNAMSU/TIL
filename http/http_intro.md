# HTTP의 개요

## HTTP란?

* html, css 같은 문서들을 가져올 수 있는 어플리케이션 레벨 프로토콜
* 웹에서 이루어 지는 모든 데이터 교환의 시초
* 클라이언트 - 서버 프로토콜
* TCP, 혹은 암호화된 TCP연결인 TSL 을 통해 전송됨

🔎 **클라이언트 서버 프로토콜이란?**
> 수신자(보통 클라이언트) 측에 의해 요청이 초기화 되는 프로토콜을 클라이언트 - 서버 프로토콜 이라고 하고,
> <br>
> 클라이언트와 서버는 개별적인 메세지 교환으로 통신하고 클라이언트에 의해 전송되는 메세지를 요청(request),<br> 서버에서 응답으로 전송되는 메세지를 응답(response) 이라고 한다.

<br>

## HTTP 기반 시스템의 구성요소

HTTP 기반 시스템의 구성요소는 크게 사용자 에이전트인 클라이언트, 프록시, 웹 서버로 구성되어 있다.  
물론 클라이언트와 웹 서버 사이에는 좀 더 많은 요소들이 있지만 웹의 계층적 설계 덕분에 다른 요소들은 네트워크와 전송 계층에 숨겨져 있다.

<br>

### 클라이언트

* 클라이언트는 사용자 에이전트 이다.

🔎 **사용자 에이전트란?**
>  사용자를 대신하여 동작하는 모든 도구이고 이 역할은 주로 브라우저에 의해 수행된다.

* 클라이언트인 브라우저에서 항상 서버에 요청을 보낸다.
* 브라우저는 HTTP 요청 내에서 지시 사항들을 변환하고 HTTP 응답을 해석하여 사용자에게 명확한 응답을 표시한다.


### 웹 서버

* 서버는 클라이언트의 요청에 대한 문서를 제공한다.
* 서버는 논리적으로는 단일 머신이다.
* 하지만 서버는 반드시 단일 머신일 필요는 없고 한 머신에 여러개의 서버가 존재할 수 있다.


### 프록시

웹 브라우저와 서버 사이에서는 수많은 컴퓨터와 머신이 HTTP 메시지를 이어 받고 전달하는데, 이중에 어플리케이션 계층에 존재하는 것을 프록시 라고 한다.  
프록시의 다양한 기능들은 다음과 같다.

* 메모리에 캐싱 기능
* 바이러스 백신 스캔, 유해컨텐츠 차단 등 필터링 기능
* 여러 서버들이 서로 다른 요청을 처리하도록 허용하는 로드 밸런싱
* 인증을 통한 리소스 접근제어
* 이력 정보 저장하는 로깅

<br>

## 참조
[MDN 공식문서](https://developer.mozilla.org/ko/docs/Web/HTTP/Overview)
