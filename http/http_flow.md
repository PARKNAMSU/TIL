# HTTP 의 흐름

HTTP는 다음과 같은 흐름을 가지고 있다.

## TCP 연결 오픈

TCP 연결을 열어서 요청을 보내거나 응답을 받는데 사용한다.  
클라이언트는 새 연결을 열거나 기존의 연결을 재사용 할 수 있고, 서버에 대한 여러 TCP연결을 열 수 있다.

<br>

## HTTP 메세지 전송

HTTP/2 이전의 HTTP 프로토콜의 메세지는 사람이 읽을 수 있는 문자로 되어있습니다.  
HTTP/2 에서의 메세지는 메세지가 프레임 속으로 캡슐화 되어있습니다.

**HTTP/2 이전의 프로토콜 에서의 HTTP 메세지 예시**

```
GET / HTTP/1.1
Host: test.org
Accept-Language: en
```

<br>

## 서버에서 전송된 응답 받기

서버에서 응답을 받습니다.

**서버 응답 예시**

```
HTTP/1.1 200 OK
Date: Sat, 09 Oct 2010 14:28:02 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
ETag: "51142bc1-7449-479b075b2891b"
Accept-Ranges: bytes
Content-Length: 29769
Content-Type: text/html

<!DOCTYPE html... (here comes the 29769 bytes of the requested web page)
```

<br>

## TCP 연결 닫기

TCP연결을 닫거나 다른 요청을 위해 재사용합니다.

<br>

## 참조

[MDN 공식문서](https://developer.mozilla.org/ko/docs/Web/HTTP/Overview)
