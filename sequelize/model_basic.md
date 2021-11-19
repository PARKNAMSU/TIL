# Sequelize Model

### Sequelize Model의 개념
Sequelize에서 모델이란 데이터 베이스의 테이블을 추상화를 통해 나타낸 것을 말한다.<br>

모델은 데이터 베이스 테이블의 이름 및 column 등의 정보를 나타낸다.<br>

모델과 데이터 베이스의 이름이 반드시 같을 필요는 없다.

<br>

### Model Define
모델을 정의하는 방법에는 sequelize.define 과 Model 클래스 확장 두가지 방법이 있다.<br>

여기서는 Model 클래스 확장을 통해서 모델을 정의한다.
```javascript
const { Sequelize, DataTypes, Model } = require('sequelize');

let sequelize = new Sequelize('database', 'user', 'password', {
        host: 'localhost',
        dialect:'mysql'
    });

//Model을 상속받은 User 클래스 생성
class User extends Model {}

//User.init 을 통해 테이블 구조를 정의한다.
User.init({
  /*
    type과 제약조건 정의
    primaryKey를 정의하지 않을 시 자동으로 Auto Increament 되는 id 컬럼이 생성된다.
   */
    email:{
        type:DataTypes.STRING,
        primaryKey:true
    },
    password:{
        type:DataTypes.STRING,
        allowNull:false
    },
    firstName:{
        DataTypes.STRING,
        defaultValue:''
    },
    lastName:DataTypes.STRING
},{ 
    /*
      sequelize와 model이름, table이름을 전달한다.
      table이름을 전달하지 않을 시 테이블명은 model명과 같아진다.
    */
    sequelize,
    modelName:'User',
    tableName:'user'
});
```

### Model 동기화
Model.sync()를 통해 Model에서 정의한 내용을 데이터베이스에 테이블로 추가할 수 있다.<br>

sync 메서드는 아래와 같은 옵션을 가지고 있다.

* Model.sync({ force:true }) : 해당 모델의 테이블이 이미 존재하는 경우 테이블을 삭제하고 재생성한다.
* Model.sync({ alter:true }) : 해당 모델의 테이블이 이미 존재하는 경우 테이블의 상태를 확인하여 모델의 상태와 일치시킨다.

```
const setup = async () => {
    try {
        //User.sync()를 통해 데이터베이스에 User에서 정의한 테이블을 생성
        await User.sync({ force: true });
    }catch(err) {
        console.log(err);
    }
}
```

<br>

정의한 모든 모델을 db에 동기화 하기 위해서는 sequelize.sync()를 사용한다.
```
await sequelize.sync();
```

<br>

### Table 제거
Model.drop(); 을 사용하여 테이블을 제거할 수 있다.<br>

동기화와 마찬가지로 sequelize.drop()을 통해 해당 데이터 베이스 내 모든 테이블을 제거할 수 있다.

<br>

만약 특정 table만 제거하고 싶을 경우 match 옵션에 정규 표현식을 제공하여 해당 정규 표현식을 만족하는 테이블만 drop할 수 있다.
```javascript
//테이블 명이 _test 로 끝나는 테이블만 제거
sequelize.drop({match:/_test$/});
```

### DataTypes

equelize의 데이터 타입의 종류는 아래와 같다.

<br>

#### 문자열
```
DataTypes.STRING             // VARCHAR(255)
DataTypes.STRING(1234)       // VARCHAR(1234)
DataTypes.STRING.BINARY      // VARCHAR BINARY
DataTypes.TEXT               // TEXT
DataTypes.TEXT('tiny')       // TINYTEXT
```

#### Boolean
```
DataTypes.BOOLEAN            // TINYINT(1)
```

#### 숫자
```
DataTypes.INTEGER            // INTEGER
DataTypes.BIGINT             // BIGINT
DataTypes.BIGINT(11)         // BIGINT(11)

DataTypes.FLOAT              // FLOAT
DataTypes.FLOAT(11)          // FLOAT(11)
DataTypes.FLOAT(11, 10)      // FLOAT(11,10)

DataTypes.DOUBLE             // DOUBLE
DataTypes.DOUBLE(11)         // DOUBLE(11)
DataTypes.DOUBLE(11, 10)     // DOUBLE(11,10)

DataTypes.DECIMAL            // DECIMAL
DataTypes.DECIMAL(10, 2)     // DECIMAL(10,2)
```

#### 날짜
```
DataTypes.DATE       // DATETIME for mysql / sqlite, TIMESTAMP WITH TIME ZONE for postgres
DataTypes.DATE(6)    // DATETIME(6) for mysql 5.6.4+. Fractional seconds support with up to 6 digits of precision
DataTypes.DATEONLY   // DATE without time
```
