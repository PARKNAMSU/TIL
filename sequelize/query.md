# Sequelize Query

### attribute

```javascript
const { Sequelize, DataTypes, Model } = require('sequelize');
const Op = Sequelize.Op;
```

<br>

attribute를 이용하여 테이블의 일부 컬럼만 가져올 수 있다.

```javascript
Model.findAll({
  //Model과 sync된 테이블에서 a, b 컬럼만 가져온다.
  attribute:['a','b']
});
```

<br>

중첩 배열을 이용해 컬럼을 가져올 때 컬럼의 이름을 바꿀 수 있다.

```javascript
Model.findAll({
  //b컬럼의 이름을 c로 변경
  attribute:['a',['b','ㅊ']]
});
```

<br>

sequelize.fn 을 이용해 집계함수를 사용할 수 있다.(count, sum, max ...)

```javascript
Model.findAll({
  attribute:[[
    // 테이블의 a 컬럼의 row 개수를 가져옴
    sequelize.fn('COUNT',sequelize.col('a')),
    'count'
  ]]
});
```

<br>

attribute에 include 속성을 주어 include의 값으로 집계함수를 사용하면 모든컬럼과 집계함수를 가져올 수 있다.

```javascript
Model.findAll({
  attribute:{
    include:[[
      sequelize.fn('COUNT',sequelize.col('a')),
      'count'
    ]]
  }
});
```

<br>

exclude 옵션을 사용하면 include와는 반대로 전체 컬럼에서 해당 컬럼을 제외하고 가져올 수 있다.

```javascript
Model.findAll({
  attribute:{
    //전체 컬럼에서 a 컬럼만 제외
    exclude:['a']
  }
});
```

### Where

where 옵션을 사용하면 필터링해서 데이터를 가져올 수 있다.(sql where문과 같음)

User 모델과 user 테이블이 있다고 가정.

```javascript
// gender 컬럼이 male 인 데이터만 가져옴
User.findAll({
  where: {
    gender: 'male' 
  }
});
```

<br>

where 의 프로퍼티를 2개 이상을 주면 기본적으로 and 적용

```javascript
// gender가 male 이고 firstName이 park인 데이터만 가져옴
User.findAll({
  where: {
    gender: 'male',
    firstName: 'park'
  }
});
```

<br>

Op를 이용하면 or연산을 사용할 수 있다.

```javascript
// firstName 이 park 또는 gender 가 male 인 데이터
User.findAll({
  where: {
    [Op.or]:[
      firstName:'park',
      gender:'male'
    ]
  }
});

//firstName 이 park 또는 lee 인 데이터
User.findAll({
  where: {
    firstName:{
      [Op.or]:['park','lee']
    }
  }
});
```

<br>

[sequelize 공식문서](https://sequelize.org/v5/manual/querying.html#operators) 에서 다양한 연산자들을 확인할 수 있다.

### Limit/Offset

limit 프로퍼티는 데이터의 개수를 제한해 주고, offset 프로퍼티는 처음 몇개의 데이터를 제외하고 데이터를 가져온다.

```javascript
// 맨위의 데이터부터 5개의 데이터만 가져온다.
User.findAll({
  limit:5
});

//처음 5개의 데이터를 제외하고, 5개의 데이터만 가져온다.
User.findAll({
  limit:5,
  offset:5
});
```

### Order

order 프로퍼티는 sql문의 ORDER 처럼 특정 컬럼에 따라 데이터를 오름차순, 내림차순으로 정렬하여 나타낸다.

```
// age에 따라 내림차순으로 정렬
User.findAll({
  order:[
    ['age','DESC']
  ]
})
```
<br>

## 참조
[sequelize 공식문서](https://sequelize.org/v5/manual/querying.html)

