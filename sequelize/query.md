# Sequelize Query

### attribute

attribute를 이용하여 테이블의 일부 컬럼만 가져올 수 있다.
```javascript
Model.findAll({
  //Model과 sync된 테이블에서 a, b 컬럼만 가져온다.
  attribute:['a','b']
});
```

중첩 배열을 이용해 컬럼을 가져올 때 컬럼의 이름을 바꿀 수 있다.
```javascript
Model.findAll({
  //b컬럼의 이름을 c로 변경
  attribute:['a',['b','ㅊ']]
});
```

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

exclude 옵션을 사용하면 include와는 반대로 전체 컬럼에서 해당 컬럼을 제외하고 가져올 수 있다.
```javascript
Model.findAll({
  attribute:{
    //전체 컬럼에서 a 컬럼만 제외
    exclude:['a']
  }
});
```