# Express의 미들웨어

### Express 미들웨어 구성
express에서 미들웨어 함수의 인자는 request , response 그리고 다음 요청을 처리하기 위한 next 를 가지고 있다.<br><br>

미들웨어 함수의 작업을 다 끝내고 마지막에 next()를 사용하여 다음 요청을 처리하지 않으면 요청은 정지된 채로 방치된다.

<br>

```javascript
// 미들웨어는 request, response, next 로 구성되어 있다.
function myMiddleware(req,res,next){
  console.log('Middleware Start');
  
  //next를 반드시 사용해야 다음 요청을 실행할 수 있다.
  next();
}
```

<br>

### 미들웨어 사용

미들웨어는 app의 use() 나 Method 요청에 인자로 전달하여 사용할 수 있다.

<br>

```javascirpt
const express = require('express');

const app = express();

function myMiddleware(req,res,next){
  console.log('Middleware Start');
  
  //request의 requestTime 프로퍼티를 생성
  req.requestTime = Date.now();
  next();
}

// 생성한 미들웨어를 인자로 전달
app.use(myMiddleware);


app.get('/',(req,res) => {
  // 미들웨어에서 생성한 request 프로퍼티를 사용할 수 있음
   console.log(`Request time is ${req.requestTime}`);
   
   res.send(req.requestTime);
});

app.listen(5000);

```

<br>참조<br>

[express 공식문서](https://expressjs.com/ko/guide/writing-middleware.html)
