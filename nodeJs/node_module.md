# NodeJS 모듈
### NodeJS 모듈이란?
NodeJS의 모듈이란 라이브러리와 같이 응용 프로그램에서 사용되는 기능들의 집합이다.

<br>

### 내장모듈
nodeJs에 내장되어있는 모듈들을 사용할 수 있다.

<br>

[nodeJs 내장모듈(w3school)](https://www.w3schools.com/nodejs/ref_modules.asp)

<br>

### 모듈사용
모듈을 사용하려면 require를 이용해 모듈을 요청해야 한다.
```javascript
//http모듈 사용하기 위해 요청
const http = require('http');
```

<br>

### custom 모듈 생성 및 사용
__exports__ 키워드를 사용해 파일 외부에서 속성과 메서드를 사용할 수 있도록 한다.

```javascript
// myLog.js 파일
// 이름과 컨텐츠를 받아 로그를 리턴하는 함수 생성하고 exports
exports.myLog(name,content){
  let result = `Time: ${Date()}
    User: ${name}
    Content: ${content}`
  return result;
}
```

<br>

외부 파일에서 require로 myLog를 요청한다.

```javascript
//뒤에 js는 생략
const log = require('./myLog')

function objMsg(user,content){
  let msgObj = {
    user,
    content,
    log:log.myLog(user,conent)
  }
  return msgObj
}

```

<br>

참조 : [w3school](https://www.w3schools.com/nodejs/nodejs_modules.asp)
