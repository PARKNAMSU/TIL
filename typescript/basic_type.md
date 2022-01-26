# Typescript 기본타입

### String

문자열 타입은 string 키워드를 사용한다.

```typescript
let str:string = 'hihi'
```

<br>

### Number

숫자 타입은 number 를 사용한다.

```typescript
let num:number = 1234
```

<br>

### Boolean

진위여부 값은 boolean을 사용한다.

```typescript
let isTrue:boolean = true
```

<br>

### Array

배열은 `type[]` 형태로 지정하거나 제네릭을 사용하여 `Array<type>` 으로 지정할 수 있다.

```typescript
let arr1:number[] = [1,2,3]

//제네릭 사용
let arr2:Array<number> = [1,2,3]
```

<br>

### Tuple

튜플은 값이 고정되어 있고 각 요소마다 타입이 지정되어있는 자료형을 말한다.

```typescript
let arr:[boolean,string,number] = [true,'hi',10]
```

<br>

### Enum

이넘은 특정값들의 집합을 의미한다.

```typescript
enum MyEnum {
    A,
    B,
    C,
  }
  //index 로 접근 시 B라는 이름을 출력
  console.log(TEST[0]);
  
  //값을 설정해 놓지 않고 이름으로 접근 시 차례대로 0부터 1씩 증가한다
  //123 출력
  console.log(`${TEST.A} ${TEST.B} ${TEST.C}`)
```

이넘의 각 요소의 값 또는 인덱스를 지정할 수 있다.

```typescript
enum MyEnum {
    A = 2,
    B,
    C,
  }
  // 첫 요소 A 의 인덱스를 2로 지정했으므로 A를 출력
  console.log(TEST[2]);
  
  //A를 2로 지정했으므로 2부터 1씩 증가
  //234 출력
  console.log(`${TEST.A} ${TEST.B} ${TEST.C}`)
```

<br>

### Any

any 타입은 모든 값에 사용될 수 있다.

```typescript
let a:any = [1,2,3];
let b:any = {
  a:1,
  b:2,
  c:3
}
```

### Void

void 타입의 변수에는 undefind 와 null 값만 할당이 가능하고, 함수의 반환형에 void 를 지정하면 반환값이 없다.

```typescript
let none:void = null;

function helloWorld:void (){
  console.log('Hello World');
}
```

<br>

### Never

함수 끝에 도달하지 않는 함수를 말한다.

```typescript
function loop(): never {
  while (true) {

  }
}
```

## 참조
[typescript 핸드북](https://joshua1988.github.io/ts/guide/basic-types.html#void)
