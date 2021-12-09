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
})

app.listen(4000);
```
