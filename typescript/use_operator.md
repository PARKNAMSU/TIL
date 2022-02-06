# 연산자를 이용한 타입

## Union Type

유니온 타입은 `|` 를 이용하여 사용하고 자바스크립트의 `||`  과 같은 'or' 연산자 타입이다

```typescript
// 유니온 타입을 사용하여 string 또는 number 타입을 지정할 수 있다.
let a: string | number = 10;

a = 'ten';

```

<br>

## Intersection Type

인터섹션 타입은 여러타입을 모두 만족하는 하나의 타입을 의미한다. 즉 타입들의 합집합을 의미

```
interface User{
  name:string,
  age:number
}
interface Student{
  name:string,
  school:string
}

/* 
  StudentInfomation 타입은 다음과 같은 타입으로 설정됨
  
  {
    name:string,
    age:number,
    school:string
  }

*/
type StudentInfomation = User & Student;
```

<br>

## Union Type Interface 적용 시 주의점

Union Type 을 Interface 에 적용 시에는 두 인터페이스 들의 교집합인 프로퍼티만 사용이 가능하다.  교집합이 아닌 타입을 사용 시 오류가 발생

```
interface User{
  name:string,
  age:number
}
interface Student{
  name:string,
  school:string
}

function test(user: User | Student){
  console.log(user.age);
}

let user: User = { name:'park' , age:19 };

//age 속성은 User 와 Student 의 교집합이 아니므로 오류 발생
test(user);
```

<br>

## 참조

[typescript 핸드북](https://joshua1988.github.io/ts/guide/operator.html#union-type%EC%9D%84-%EC%93%B8-%EB%95%8C-%EC%A3%BC%EC%9D%98%ED%95%A0-%EC%A0%90)
