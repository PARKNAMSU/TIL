# Express 미들웨어 사용

### 미들웨어에서 수행하는 task 와 미들웨어의 유형
미들웨어에서 수행할 수 있는  task의 종류는 다음과 같다.
* 미들웨어 내의 코드를 실행
* 요청(request), 응답(response) 의 object의 변경을 수행
* request-response cycle을 종료
* stack 내의 그 다음 middleware function을 실행

<br>

미들웨어 사용 시 req-res 주기가 종료되지 않을 시 next()를 이용하여 다음 middleware function을 종료하지 않으면 요청은 정지된 채로 방치된다.

<br>

미들웨어의 유형은 다음과 같다.
* application level middleware
* router level middleware
* error handling middleware
* built-in middleware
* third-party middleware

<br>

### Application Level MiddleWare
application level middleware는 app object에 미들웨어를 바인드하는 것을 의미한다.

```javascript
let express = require('express');
let app = express();

//app object에 미들웨어 bind
app.use(function(req,res,next){
  req.requestTime = Date.now();
  console.log(`request time : ${req.requestTime}`)
})

app.get('/',function(req,res){
  res.send(req.requestTime);
});
```

<br>

### Router Level MiddleWare
router level middleware는 app object 가 아닌 express.Router() 에 bind 된다.

```javascript
let express = require('express');

let router = express.Router();

//router 에 bind
router.use(function(req,res,next){
  req.requestTime = Date.now();
  console.log(`request time : ${req.requestTime}`)
})

router.get('/',function(req,res){
  res.send(req.requestTime);
});
```

<br>

### Error-Handling MiddleWare
error handling middleware 는 인자가 err, req, res ,next로 구성되어 있어서 error를 받을 수 있다.
 
```javascript

app.use(function(err,req,res,next){
  //err stack 출력
  console.log(err.stack)
  
  res.status(500).send('some error');
})
```

<br>

### Built-In MiddleWare
built-in middleware는 express에서 기본적으로 제공해주는 미들웨어이다.<br>
ex) express.static();

### Third-Party MiddleWare

npm install을 통해 설치한 노드 모듈 MiddleWare를 의미한다.
<br>
[third-party middleware 참조](https://expressjs.com/ko/resources/middleware.html)

<br><br>
참조<br>
[express 공식 문서](https://expressjs.com/ko/resources/middleware.html)
