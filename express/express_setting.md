# express 개발환경 구축

<br>

### 프로젝트 폴더
터미널에서 프로젝트를 생성할 폴더를 생성하고 폴더 경로로 이동한다.
```
$ mkdir [프로젝트 폴더명]
$ cd [프로젝트 폴더 경로]
```

<br>

### 프로젝트 폴더 초기화
init 명령어로 package.json 파일을 생성한다. 만약 자동으로 설정하고 싶으면 뒤에 -y를 추가한다.
```
$ npm init
$ npm init -y
```

<br>

### express 설치
npm install 을 이용하여 express를 설치한다. <br> package.json에 종속 항목으로 추가할 경우 --save를 추가하고, 추가하지 않을경우 생략한다.
```
$ npm install express
$ npm install express --save
```

<br>

참조<br>
[express 공식문서](https://expressjs.com/ko/starter/installing.html)
