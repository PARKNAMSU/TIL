# HTTPS

### HTTPS Protocol
HTTPS(Hyper Text Transfer Protocol Secure Socket Layer)는 HTTP요청을 SSL, TSL 알고리즘을 이용하여 HTTP통신을 할때, 데이터를 암호화 하여 전송하는 프로토콜 이다.

> SSL / TLS 이란?

SSL(Secure Socket Layer)은 서버와 클라이언트 사이에 전송된 데이터를 암호화 하여 인터넷 연결 시 보안을 유지하는 기술이고,
TLS(Transport Layer Security)는 더 강력한 버전의 SSL이다.

<br>

### HTTPS 사설 인증서 발급

mkcert라는 프로그램을 이용하여 https 사설 인증서를 발급받아 웹 서버를 https 프로토콜로 구축할 수 있다.

<br>

#### mkcert 설치

homebrew를 이용해 mkcert를 설치한다.

```
brew install mkcert

# firefox를 사용할 경우 필요에 따라 설치
brew install nss
```

<br>

#### 로컬을 인증된 발급기관으로 등록

```
mkcert -install
```

<br>

#### 인증서 설치
프로젝트 폴더로 이동하여 인증서를 설치한다.

```
mkcert -key-file key.pem -cert-file cert.pem localhost 127.0.0.1 ::1
```

<br>

### HTTPS 서버 작성
https 모듈을 사용하여 https 프로토콜을 사용하는 서버를 생성한다.

```javascript
const express = require('express');
const https = require('https');
const fs = require('fs');

const app = express();

https.createServer(
  {
    key: fs.readFileSync(__dirname + '/key.pem', 'utf-8'),
    cert: fs.readFileSync(__dirname + '/cert.pem', 'utf-8'),
  },
  app
);
```

<br>

참조 : [codestate](https://codestates.com/)
