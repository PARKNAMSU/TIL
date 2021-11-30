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
            id: find.id, 
            name: find.name,
            age: find.age
        },
        // 비밀키 전달 
        SECRET_KEY,
        // 옵션 설정 
        {
            expiresIn: '10m', // 만료시간 10분
            issuer: 'provider', // 토큰 발급자 설정
        });
        
        //쿠키에 refreshToken 생성
        await res.cookie('refreshToken', jwt.sign(find, SECRET_KEY), {
            maxAge: 60 * 60 * 1000,
            httpOnly: true,
            secure: true,
            path: '/',
            sameSite: 'none'
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

<br>

### 전달받은 Access Token 이용하여 인증
클라이언트에서 전달받은 토큰이 유효한지 jwt.verify 메서드로 확인한다.

```javascript
app.post('/auth', (req, res) => {
    try {
        // 요청헤더 authorization 에 담긴 토큰이 유효한 토큰인지 검증
        let token = jwt.verify(req.headers.authorization, SECRET_KEY);
        //인증 성공
        res.status(200).send({
            data:{
                id: token.id, 
                name: token.name,
                age: token.age
            },
            message:'유효한 토큰입니다.'
        })
    }
    // 인증 실패
    catch (error) {
        // 유효시간이 초과된 경우
        if (error.name === 'TokenExpiredError') {
            res.status(419).json({
                message: '토큰이 만료되었습니다.'
            });
        }
        // 토큰의 비밀키가 일치하지 않는 경우
        if (error.name === 'JsonWebTokenError') {
            res.status(401).json({
                message: '유효하지 않은 토큰입니다.'
            });
        }
    }
});
```

<br>

### 토큰 재발급
access 토큰이 만료되었을 경우 refresh토큰을 이용하여 재발급 받습니다.

```javascript
app.post('/refresh', (req, res) => {
    let refToken = req.cookies['refreshToken'];
    if (refToken === undefined) {
        res.status(400).send({ data: null, message: '토큰이 전달되지 않았습니다.' });
    } else if (refToken === 'invalidtoken') {
        res.status(400).send({ data: null, message: '유효하지 않은 토큰입니다.' });
    } else {
        let data = jwt.verify(refToken, SECRET_KEY);
        res.status(200).send({
            accessToken:
                jwt.sign({
                    type: 'JWT', // token type이 Jwt 임을 명시
                    /* 인코딩할 데이터(default인코더는 SHA256) */
                    id: data.id,
                    name: data.name,
                    age: data.age
                },
                    // 비밀키 전달 
                    SECRET_KEY,
                    // 옵션 설정 
                    {
                        expiresIn: '10m', // 만료시간 15분
                        issuer: 'provider', // 토큰 발급자 설정
                    }
                ),
            message: 'ok'
        });
    }
});
```

<br>

### 전체 코드

```javascript
const express = require('express');
const app = express();
const port = 5000;
const dummy = require('./dummy/data');
const SECRET_KEY = 'secret';
const jwt = require('jsonwebtoken');

/*
    jwt login 구현
*/
app.post('/login/:id', async (req, res) => {
    let id = req.params.id;
    let pass = req.body;

    let find = dummy.find(item => {
        return item.id === id && item.password === pass;
    });

    if (find) {
        let token = jwt.sign({
            type: 'JWT', // token type이 Jwt 임을 명시
            /* 인코딩할 데이터(default인코더는 SHA256) */
            id: find.id,
            name: find.name,
            age: find.age
        },
            // 비밀키 전달 
            SECRET_KEY,
            // 옵션 설정 
            {
                expiresIn: '10m', // 만료시간 15분
                issuer: 'provider', // 토큰 발급자 설정
            }
        );
        //쿠키에 refreshToken 생성
        await res.cookie('refreshToken', jwt.sign(find, SECRET_KEY), {
            maxAge: 60 * 60 * 1000,
            httpOnly: true,
            secure: true,
            path: '/',
            sameSite: 'none'
        });

        res.status(200).send({
            data: {
                accesstoken: token
            },
            message: 'ok'
        })
    } else {
        res.status(400).send({
            message: 'invalid id or password'
        });
    }
});


app.post('/auth', (req, res) => {
    try {
        // 요청헤더 authorization 에 담긴 토큰이 유효한 토큰인지 검증
        let token = jwt.verify(req.headers.authorization, SECRET_KEY);
        res.status(200).send({
            data: {
                id: token.id,
                name: token.name,
                age: token.age
            },
            message: '유효한 토큰입니다.'
        })
    }
    // 인증 실패
    catch (error) {
        // 유효시간이 초과된 경우
        if (error.name === 'TokenExpiredError') {
            res.status(419).json({
                error: 'TokenExpiredError',
                message: '토큰이 만료되었습니다.'
            });
        }
        // 토큰의 비밀키가 일치하지 않는 경우
        if (error.name === 'JsonWebTokenError') {
            res.status(401).json({
                error: 'JsonWebTokenError',
                message: '유효하지 않은 토큰입니다.'
            });
        }
    }
});

app.post('/refresh', (req, res) => {
    let refToken = req.cookies['refreshToken'];
    if (refToken === undefined) {
        res.status(400).send({ data: null, message: '토큰이 전달되지 않았습니다.' });
    } else if (refToken === 'invalidtoken') {
        res.status(400).send({ data: null, message: '유효하지 않은 토큰입니다.' });
    } else {
        let data = jwt.verify(refToken, SECRET_KEY);
        res.status(200).send({
            accessToken:
                jwt.sign({
                    type: 'JWT', // token type이 Jwt 임을 명시
                    /* 인코딩할 데이터(default인코더는 SHA256) */
                    id: data.id,
                    name: data.name,
                    age: data.age
                },
                    // 비밀키 전달 
                    SECRET_KEY,
                    // 옵션 설정 
                    {
                        expiresIn: '10m', // 만료시간 15분
                        issuer: 'provider', // 토큰 발급자 설정
                    }
                ),
            message: 'ok'
        });
    }
});

app.listen(port, () => console.log('127.0.0.1:' + port + " start!!"));
```




