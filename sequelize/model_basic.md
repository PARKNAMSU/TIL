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
    firstName:DataTypes.STRING,
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
