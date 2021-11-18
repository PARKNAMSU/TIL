# Sequelize 설치 및 세팅

### Sequelize란?

Sequelize란, Postgres, MySQL, MariaDB, SQLite등 SQL Server 의 Promise기반 Node.js ORM(Object Relational Mapping) 이다.

> ORM(Object Relational Mapping) 이란?

<br>

ORM은 객체 데이터 타입과 데이터베이스의 데이터 들을 자동으로 Mapping 시켜주는것을 말한다.

### Sequelize 설치
nodeJs 또는 express 프로젝트 폴더를 생성하고 npm install로 mysql2 또는 postgres등 사용할 db의 모듈을 설치한 후 npm install을 이용하여 Sequelize를 설치한다.

```
cd [폴더경로]
npm install -y
npm install --save express
npm install --save mysql2
npm install --save sequelize
```
<br>

### db연결
sequelize를 이용하여 db조작을 할 수 있게 db를 연동합니다.

```javascript
const { Sequelize } = require('sequelize');

/*
  arg1: database name
  arg2: user
  arg3: password
  arg4: {
    host,
    using database
  }
*/
let sequelize = new Sequelize('database', 'root', 'password', {
        host: 'localhost',
        dialect:'mysql'
    });
```

<br>

### db연결 확인
authenticate 메서드를 이용하여 db연결이 됬는지 확인합니다.
```javascript
const connectCk =  async () => {
    try {
        //db 연결
        await sequelize.authenticate();
        console.log("연결 성공!!");
    }catch(err) {
        console.log(err);
    }
}
```

<br>

### db연결 해제
close 메서드를 이용하여 db연결을 종료합니다.
```javascript
const disConnect = async () => {
    try {
        sequelize.close();
        console.log("연결 해제!!");
    }catch(err) {
        console.log(err)
    }
}
```

<br>

### 전체 코드
```javascript
const { Sequelize } = require('sequelize');

let sequelize = new Sequelize('test', 'root', 'slek4173', {
        host: 'localhost',
        dialect:'mysql'
    });

const connectCk =  async () => {
    try {
        //db 연결
        await sequelize.authenticate();
        console.log("연결 성공!!");
    }catch(err) {
        console.log(err);
    }
}

const disConnect = async () => {
    try {
        sequelize.close();
        console.log("연결 해제!!");
    }catch(err) {
        console.log(err)
    }
}
```

<br>

참조: [sequelize 공식문서](https://sequelize.org/master/manual/getting-started.html)
