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
    lastName:DataTypes.STRING,
        cash:{
        type:DataTypes.INTEGER,
        defaultValue:0
    }
},{ 
    sequelize,
    modelName:'User',
    tableName:'user'
});
```

<br>

### Instace Create
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

<br>
__create__ 를 이용하여 위 두 작업을 동시에 할 수 있음

```javascript
let steve = User.create({
    email:'llee@gmail.com',
    password:'1234',
    firstName:'wood',
    lastName:'steve'
});
```

<br>
인스턴스에는 데이터 정보 말고 다양한 프로퍼티들이 있는데, __instance.toJSON()__ 을 이용하면 인스턴스 데이터의 정보만 볼 수 있음

```javascript
let log = steve.toJSON();
```

<br>

### Instance Update

Instance의 프로퍼티를 직접 변경 혹은 __.set__을 이용하여 변경 후 save

```javascript
let steve = User.create({
    email:'llee@gmail.com',
    password:'1234',
    firstName:'wood',
    lastName:'steve'
});

steve.firstName = 'kim';

//set을 이용하면 한번에 여러 정보 설정
steve.set({
        firstName:'kim',
        lastName:'wayne'
});

steve.save()
```

<br>
__update__를 이용하면 위 두작업을 한번에 할 수 있음

```javascript
let steve = await User.create({
    email:'llee@gmail.com',
    password:'1234',
    firstName:'wood',
    lastName:'steve'
});

await steve.update({
        firstName:'kim',
        lastName:'wayne'
})
```


<br>

### Instance 일부만 저장

save시 fields 속성을 이용하여 일부 컬럼만 db에 저장할 수 있다.

```javascript
//build 이용하여 steve 인스턴스 생성
let steve = await User.create({
    email:'llee@gmail.com',
    password:'1234',
    firstName:'wood',
    lastName:'steve'
});

steve.password = '5678';
steve.firstName = 'lee'

// fields 속성에 값으로 변경하고 싶은 column 만 배열 형태로 전달.
await steve.save({
        fields:['firstName']
});
```

<br>

### Instace Increament
__increament__를 이용하여 Instance의 값을 증가시킬 수 있다.

```javascript
//cash의 값이 5로 설정되는것이 아닌 5가 증가한다.
await steve.increament('cash',{by:5});
```

<br>

참조 : [sequelize 공식문서](https://sequelize.org/master/manual/model-instances.html)
