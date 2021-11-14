# HTTP 모듈

### HTTP 모듈
nodeJS의 내장 모듈에는 http를 통해 데이터를 전송할 수 있는 http 모듈이 있다.

### HTTP SERVER 생성
http 모듈은 __createServer__ 를 사용해 서버의 포트를 수신하여 요청을 받고 응답을 전달할 수 있다.

```javascript
const http = require('http');

//createServer 메서드로 서버 생성
http.createServer((req,res) => {
  //write로 응답할 데이터 추가
  res.write('get request and send response!!');
  //end로 종료후 전송
  res.end();
}).listen(5000);
```

<br>

### HTTP Header 추가

응답에 http header를 추가하여 전송할 수 있다.

```javascript
const http = require('http');

http.createServer((req,res) => {
  //header 에 content-type 추가
  res.writeHead(200,{'Content-Type':'text/html'});
  res.write('get request and send response!!');
  //end로 종료후 전송
  res.end();
}).listen(5000);
```

<br>

### Query String 읽기

request.url을 통해 url의 포트 뒤의 query 문자열과 경로를 가져온다.

```javascript
const http = require('http');

http.createServer((req,res) => {
  //req.url에 경로 및 쿼리 문자열이 담겨있음
  let url = req.url;
  console.log(url);
  res.writeHead(200,{'Content-Type':'text/html'});
  res.write('get request and send response!!');
  res.end();
}).listen(5000);
```

<br>

### Query String 분할
url 모듈을 사용하면 query string 을 분할하여 사용할 수 있다.

```javascript
const http = require('http');
const url = require('url');

// 'http://localhost@5000/test?name=park&age=25' 로 요청
http.createServer((req,res) => {
  // query string을 분할  
  let url = url.parse(req.url,true).query;
  
  res.writeHead(200,{'Content-Type':'text/html'});
  res.write(`name : ${url.name} age : ${url.age}`);
  res.end();
}).listen(5000);
```
