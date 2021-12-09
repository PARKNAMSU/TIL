# 오류 처리

### 오류처리 미들웨어

오류처리 미들웨어는 다른 미들웨어들과 다르게 _err, req, res, next_ 4개의 인자를 가지고 있다.

```javascript
// /err 요청을 보낼때 오류가 발생하면 이 미들웨어로 들어옴
app.use('/err',(err,req,res,next) => {
  console.log(req.body);
  res.status(500).send({
    err
  });
})
```

오류가 발생하더라도 next를 통해 다음 로직을 실행할 수 있다.

```javascript
app.use('/err',(err,req,res,next) => {
  console.log(err);
  if(req.body.errStop === 'y')
    res.status(400).send({err});
  else{
    req.errHappend = true;
    next()
  }  
});
```

next에 err를 전달하면 html 파일로 오류 내용이 전달된다.

```javascript
app.use('/err',(err,req,res,next) => {
  console.log(err);
  next(err);
});
```

결과

![image](https://user-images.githubusercontent.com/62639722/145347409-a6da9b40-7354-4be8-a23e-85a578c38b20.png)

## 참조
[express 공식문서](https://expressjs.com/ko/guide/error-handling.html)
