# express의 기본적인 라우팅
### express import 
require를 이용하여 express를 import 한다.
```javascript
const express = require('express');
```

<br>

### app 생성
express를 이용해 app을 생성한다.
```javascript
const app = express();
```

<br>

### port 설정
port를 설정한다
```javascript
const port = 3000;
```

<br>

### 라우팅
특정 엔드포인트에 대한 클라이언트 요청에 응답하기 위해 http 메소드와 경로를 설정하여 라우팅한다.
<br>
#### http메소드의 종류
1.GET : url의 query string 을 받아서 해당 정보를 검색하기 위해 사용됨
2.POST : request body 를 통해 폼 입력을 처리하기 위해 사용됨
3.HEAD : GET과 유사하나 요청 시 헤더 정보 이외에 어떠한 데이터도 보내지 않음
4.DELETE : 특정 리소스를 삭제하기 위해 사용됨
5.PUT : 특정 리소스를 request body에 들어있는 값으로 생성하거나 이미 특정 리소스가 있는경우 값을 변경한다.
6.OPTIONS : 해당 메소드를 통해 시스템에서 지원되는 메소드 종류를 확인할 수 있다.
```javascript
// GET 메소드와 경로 '/index' 사용
// 1번째인자 : 경로    2번째 인자 : 핸들러 (request,response[,next]) 요청, 응답, next(다음 실행, 옵션)
// response.send()로 response 데이터 전달
app.get('/index',function(req,res){
  res.send("It is a Index Page ");
})
```
