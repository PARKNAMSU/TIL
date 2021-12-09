# Router

### Router 사용

라우터는 express 4.x 부터 추가된 것으로, 기존 express app 에서 몇가지 기능이 추가되었다.

라우터는 app.use를 이용해 미니 어플리케이션처럼 사용할 수 있다.

```javascript
const express = require('express');
const app = express();
//express.Router() 를 이용하여 생성
const router = express.Router();

// 이 경로로 들어올려면 http://[ip address]:4000/router/ 를 통해 들어올  수 있다.
router.get('/',(req,res) => {
    res.send("Use Router")
});

// /router 경로를 통해서만 router 에서 설정한 경로로 이동할 수 있다.
app.use('/router',router);


// 이 경로로 들어올려면 http://[ip address]:4000/ 를 통해 들어올 수 있다.
app.get('/',(req,res) => {
  res.send("Use App");
});

app.listen(4000);
```

### Router.all()

Router.all() 메서드는 모든 HTTP 메서드에서 접근할 수 있다.

```
// GET,POST,HEAD 등 모든 HTTP메서드에서 접근 가능하다.
router.all('/all',(req,res) => {
    res.send('Use All Method');
});
```

### Router.param()

Router.param() 메서드는 restful API 방식으로 요청을 할때 자원에 이름을 첫번째 인자로 주어<br>
해당 자원의 restful API 요청이 들어요면 param의 2번째 인자인 콜백함수에 먼저 들어오게 된다.

param의 매개변수는 _req, res, next, val(자원의 데이터)_ 4개로 구성되어 있다.

```
// http://[ip address]:4000/router/user/[id] 의 요청이 들어오면 콜백함수가 실행된다.
router.param('id', function (req, res, next, val) {
    console.log(`throw this param 
                    value: ${val}`);
    next();
});

// param의 콜백함수가 실행된 후 메서드의 콜백함수가 실행된다.
router.get('/user/:id',(req,res) => {
    res.send('get Id');
});
```
