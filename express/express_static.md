# Express 정적 파일 제공

### express.static
express에서 제공하는 미들웨어 함수 express.static 을 이용하면 정적파일 경로를 서버에 저장해 놓을 수 있다.

### server
```javascript
//app.static을 이용하여 현재디렉토리/js 의 경로를 /js로 지정
app.use('/js',express.static(__dirname+'/js'))
```

### html
```html
<!-- 현재 디렉토리/js/app.js의 파일을 지정해놓은 static 경로를 이용하여 http://localhost:3000/js/app.js로 가져옴.-->
<script src="http://localhost:3000/js/app.js"></script>
```

<br>참조<br>
[express 공식문서](https://expressjs.com/ko/starter/static-files.html)
