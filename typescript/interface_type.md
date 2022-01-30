# Interface

## Interface 란?

인터페이스의 정의는 상호 간에 정의한 약속 혹은 규칙이다.  
타입 스크립트에서는 아래의 범주에 대해 약속을 정의할 수 있다.

* 객체의 속성과 속성의 타입
* 함수의 파리미터와 반환 타입
* 배열과 객체 접근 방식
* 클래스

<br>

## Interface 적용

`name` 이라는 string 값과 `age` 라는 number 타입의 프로퍼티를 가지는 객체를 다음과 같이 정의할 수 있다.

```typescript
interface Player {
  name:string;
  age:number
}

// User타입을 사용하기로 약속하였기 때문에 name 과 age 는 필수로 입력되어야 한다.
// name 과 age 가 포함되어 있으므로 추가된 속성인 team 이 있어도 상관없다.
let player1:Player = {
  name:'heungmin son',
  age:29,
  team:'tottenham'
}
```

<br>

## 옵션 속성

옵션 속성을 사용한 프로퍼티는 필수로 사용하지 않아도 된다.  
옵션 속성은 `property?:type` 형태로 사용된다.

```typescript
interface Player{
  name:string;
  age:number;
  team?:string
}

//team 속성은 옵션 속성이므로 사용하지 않아도 된다.
let player1:Player = {
  name:'heungmin son',
  age:29,
}
```

<br>

## 읽기전용 속성

읽기전용 속성은 객체를 처음 선언할때만 값을 할당할 수 있고 그이후로는 값 변경을 할 수 없고 오로지 호출만 가능하다.  
읽기전용 속성은 프로퍼티 앞에 `readonly` 속성을 입력한다.

```typescript
interface Player{
  name:string;
  age:number;
  team?:string;
  readonly nationality:string
}

let player1:Player = {
  name:'heungmin son',
  age:29,
  nationality:'Republic of Korea'
}

// readonly 속성이므로 에러 발생
player1.nationality = 'Japan'
```

<br>

## 읽기전용 배열

`ReadonlyArray<T>` 타입을 지정하고 배열은 한번 선언하면 배열의 값 수정, 삭제, 변경을 할 수 없다.

```typescript
let arr: ReadonlyArray<number> = ['a','b','c'];

// 아래의 코드들은 모두 배열을 변경하는 것이므로 모두 에러 발생
arr.push('e');

arr.splice(0,1);

arr[1] = 'f';
```

<br>

## 함수 타입

인터페이스는 함수 타입도 정의할 수 있다.

```typescript
interface Method{
  (arg1:string,arg2:string):string;
}

let myMethod:Method = 
  function(arg1:string,arg2:string):string{
    return arg1 + arg2;
  }
```

<br>

## 클래스 타입

클래스 뒤에 implements 를 사용하여 인터페이스를 구현할 수 있다.

```typescript
interface Car{
  company:string;
  name:string;
  price:number;
  drive():void;
}

class Avante implements Car{
  company:'Hyundai';
  name:'Avante';
  price:20000000;
  drive(){
    console.log(this.name +' stare drive')
  };
} 
```

<br>

## 인터페이스의 확장

extends 예약어를 이용하여 인터페이스들 끼리 확장할 수 있다.

```
interface Player{
  name:string;
  age:number;
}

interface FootBallPlayer extends Player{
  position:string
}

// Player 를 상속받았기 때문에 name , age 프로퍼티가 있다.
let player1:FootBallPlayer ={
  name:'kante',
  age:29,
  position:'Midfielder'
}
```

## 하이브리드 타입

자바스크립트의 유연성을 살려서 하이브리드 타입을 만들 수 있다.  
아래는 함수이면서 객체 타입을 정의할 수 있는 하이브리드 타입이다.

```
interface Hybrid{
  (arg1:string):string;
  name:string;
  age:number;
}

function myHybrid():Hybrid{
  let val = (function(arg1:string):string { console.log(arg1 + arg1) } ) as Hybrid;
  val.name = 'park';
  val.age = 23
  
  return val
}

let myVal = myHybrid();

// hihi 출력
myVal('hi');
//park : 23 출력
console.log(`${myVal.name} : ${myVal.age}`)
```

<br>

## 참조

[typescript 핸드북](https://joshua1988.github.io/ts/guide/interfaces.html)

