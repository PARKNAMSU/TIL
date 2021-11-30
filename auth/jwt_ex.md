# JWT 사용 예제

### 모듈 설치
JWT 토큰 사용을 위해 npm install 한다.

```
npm install jsonwebtoken
```

<br>

### 서버에서 JWT 토큰 사용
require를 이용해 설치한 모듈을 불러오고, 서버에서 인증을 위해 jwt 토큰을 사용한다.

```javascript
const jwt = require('jsonwebtoken');
const express = require('express');
const app = express();
cosnt port = 5000;
const SECRET_KEY = 'secret';

/*
  jwt 로그인 구현
*/
app.post('/login/:id',(req,res) => {
  //...
});
```

### Access Token 발급
클라이언트에서 전달받은 id와 password를 확인하여 jwt.sign으로 토큰을 받급한다.

<br>

db를 사용하지 않으므로 dummy데이터 만들어서 사용한다.(프로젝트 진행 시 database 사용)
```javascript
/*
  {
    id,
    password,
    name,
    age
  } 
  형태의 객체 데이터가 들어있는 배열 dummy data 생성
*/
let dummy = require('./dummy/data');

app.post('/login/:id', (req, res) => {
    let id = req.params.id;
    let pass = req.body;

    let find = dummy.find(item => {
        return item.id === id && item.password === pass;
    });

    if (find) {
        //jwt.sign을 이용하여 토큰 생성
        let token = jwt.sign({
            type: 'JWT', // token type이 Jwt 임을 명시
            /* 인코딩할 데이터(default인코더는 SHA256) */
            id: dummy.id, 
            name: dummy.name,
            age: dummy.age
        },
        // 비밀키 전달 
        SECRET_KEY,
        // 옵션 설정 
        {
            expiresIn: '10m', // 만료시간 10분
            issuer: 'provider', // 토큰 발급자 설정
        });

        res.status(200).send({
            data:{
                accesstoken:token
            },
            message:'ok'
        })
    }else{
        res.status(400).send({
            message:'invalid id or password'
        });
    }
});
```

