# Model Instance

sequelize 사용 위해 아래와 같이 설정
```javascript
const { Sequelize, DataTypes, Model } = require('sequelize');

let sequelize = new Sequelize('test', 'root', 'slek4173', {
        host: 'localhost',
        dialect:'mysql'
    });

class User extends Model {}

User.init({
    email:{
        type:DataTypes.STRING,
        primaryKey:true
    },
    password:{
        type:DataTypes.STRING,
        allowNull:false
    },
    firstName:DataTypes.STRING,
    lastName:DataTypes.STRING
},{ 
    sequelize,
    modelName:'User',
    tableName:'user'
});
```

### Model Create
Sequelize Model의 인스턴스를 만들 때 new 연산자가 아닌 __.build__ 를 이용하여 생성한다.<br>

생성한 인스턴스에 __.save()__ 를 이용하여 db에 저장한다.
```javascript
//build 이용하여 steve 인스턴스 생성
let steve = User.build({
    email:'llee@gmail.com',
    password:'1234',
    firstName:'wood',
    lastName:'steve'
});
// database에 저장(save 작업 하지 않을 시 db 저장 안됨)
await steve.save();
console.log(`${steve.lastName} was saved!!`);
```

__create__ 를 이용하여 위 두 작업을 동시에 할 수 있음

```javascript
let steve = User.create({
    email:'llee@gmail.com',
    password:'1234',
    firstName:'wood',
    lastName:'steve'
});
```




