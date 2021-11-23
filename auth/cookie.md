# Cookie

### Cookie란 ?
cookie란 서버에서 클라이언트에 데이터를 저장하는 방법 중 하나이다.<br>

cookie는 서버가 원하면 cookie를 이용하여 클라이언트에서 데이터를 가져올 수 있다는 특징을 가지고 있다.<br>

하지만 데이터를 저장하고 특정 조건을 만족해야지 데이터를 서버로 가져올 수 있고,
이러한 조건들을 __쿠키옵션__ 으로 나타낼 수 있다.

<br>

### Cookie Options

#### Domain
쿠키에서의 도메인은 포트, 서브 도메인, 세부 경로를 포함하지 않는다.
죽, _http://www.localhost.com:3000/users_ 의 Domain은 localhost.com 이 된다.<br>

Domain 옵션을 설정하면 클라이언트에서 요청 시 서버에 등록한 Domain 옵션과 같아야 쿠키를 전송할 수 있다.

<br>

#### Path
Path는 서버가 라우팅 할 때 사용하는 경로이다.
즉, _http://www.localhost.com:3000/users_ 의 Path는 /users 가 된다.<br>

Path요청은 Path요청을 만족하면 추가 경로가 더 있어도 조건을 만족한다.<br>

즉, Path가 /users이면 /users/login 도 만족한다.

<br>

#### MaxAge / Expires
쿠키의 유효 기간을 설정해준다.<br>

MaxAge는 쿠키가 생성된 시점부터 얼마나 지속되는지 설정하고, Expires는 쿠키가 유효할때까지의 날짜, 시간을 설정해 준다.

<br>
  
#### Secure
Secure은 boolean 값으로 지정해 주는데, true인 경우 https환경의 서버에만 쿠키를 전송할 수 있다.

<br>

#### HttpOnly
HttpOnly를 true 로 설정하면 javascript에서는 쿠키에 접근을 못하고 통신을 통해서만 접근이 가능하다.
이 옵션이 false 일 경우 javascript에서 쿠키 접근이 가능하므로 __XSS__ 공격에 취약해 진다.

<br>

#### SameSite

SameSite에는 cross-origin 관련하여 아래와 같은 설정이 있다.
* Lax : Cross-Origin 요청을 받는 경우 GET 메서드에 대해서만 쿠키를 전송할 수 있다.
* Strict : Cross-Origin 에서는 쿠키를 전송할 수 없다.
* None : 항상 쿠키를 보내줄 수 있다. 하지만 Secure 옵션이 true 여야한다.

<br>

### Cookie 사용법

npm install로 cookie-parser를 설치한 후 import 하여 app.use를 이용해 cookie 사용한다.
```javascript
const express = require('express');
const cookieParser = require('cookie-parser');
const app = express();

app.use(cookieParser());
```
