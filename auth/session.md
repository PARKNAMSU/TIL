# Session

### Session이란?

Session이란 방문자의정보 예를들면 로그인시 유저정보 등을 클라이언트가 아닌 서버에 저장하는 방법이다.<br>

로그인이 성공하면 서버가 해당 사용자가 인증을해야 접근할 수 있는 자원을 사용하기 위해 인증을 했음을 알고 있어야 하고,
매번 로그인하여 인증을 진행할 필요 없이 세션에 해당 사용자를 저장하여 인증되었음을 서버에서 알 수 있다.<br>

세션이 등록되면 서버는 클라이언트에 인증을 확인할 세션 아이디를 전달하는데, 이 세션아이디를 쿠키에 저장한다.

<br>

### 세션 사용
express-session 모듈을 사용하여 세션을 사용 및 관리할 수 있다.

[express-session GitHub](https://github.com/expressjs/session#reqsession)

<br>

npm install 을 이용해 express-session을 설치한다.

```
npm i express-session
```

서버에 express-session을 require한 후 use를 이용해 사용한다.

```
const express = require('express');
const app = express();
const session = require('express-session');	// express-session

app.use(session({
  httpOnly: true,	//javascript 에서 session cookie 사용을 사용할 수 없도록 한다.
  secure: ture,	//https 서버 환경에서만 session 정보를 주고받도록 처리한다.
  secret: 'secret key',	//암호화하는 데 쓰일 키
  resave: false,	//세션을 언제나 저장할지 설정함
  saveUninitialized: true,	//세션이 저장되기 전 uninitialized 상태로 미리 만들어 저장
  cookie: {	//세션 쿠키 설정 (세션 관리 시 클라이언트에 보내는 쿠키)
    httpOnly: true,
    Secure: true,
    maxAge: 60000 
  }
}));
```


세션은 저장될 때 서버 메모리에 저장되는데, 이는 서버가 한번 내려가면 세션이 모두 초기화 되서 사라진다.<br>
그래서 세션을 따로 저장소에 따로 저장해야 하는데 실제 프로젝트 시에는 사용 데이터베이스에 따라 지원하는 모듈을 사용하면 된다. [session-store API](https://www.npmjs.com/package/express-session#compatible-session-stores) <br>

하지만 여기서는 데이터베이스를 사용하지 않으므로 session-file-store 모듈을 사용한다.
```
npm i session-file-store
```





