# Enum

## Enum 이란?

이넘은 특정한 타입의 값들의 집합을 의미한다.  
타입 스크립트에서는 문자형 이넘과 숫자형 이넘을 지원한다.

<br>

## 숫자형 Enum

숫자형 이넘을 사용할 때 값을 초기화 해 주지 않으면 초기값이 0부터 시작해서 1씩 증가한다.  
이넘값을 사용할 때는 객체의 프로퍼티를 불러올 때 처럼 사용하면 된다.

```typescript
enum MyNum{
  ONE,
  TWO,
  THREE
}

// 0 1 2
console.log(`${MyNum.ONE} ${MyNum.TWO} ${MyNum.THREE}`);
```

값 초기화를 해줄 시 그 값부터 1씩 증가한다.

```typescript
enum MyNum{
  ONE = 1,
  TWO,
  THREE
}

// 1 2 3
console.log(`${MyNum.ONE} ${MyNum.TWO} ${MyNum.THREE}`);
```

<br>

## 문자형 Enum

문자형 이넘을 사용할 때는 모든 값을 초기화 해야 한다.

```typescript
enum MyStr{
  ONE = 'one',
  TWO = 'two',
  THREE = 'three'
}

// one two three
console.log(`${MyNum.ONE} ${MyNum.TWO} ${MyNum.THREE}`);
```

<br>

## 복합 Enum

문자열과 숫자를 복합하여 이넘에 사용할 수 있지만 이넘에는 같은 타입을 사용하는 것이 좋다.


```typescript
// 사용 할 수는 있지만 권장하지 않는다.
enum MyEnum{
  ONE = 1,
  TWO = 'two',
  THREE = 'three'
}

// 1 two three
console.log(`${MyNum.ONE} ${MyNum.TWO} ${MyNum.THREE}`);
```

<br>

## 컴파일 시점 Enum

런타임 시점에 Enum은 실제 객체이지만 컴파일 시점에서는 아니므로 keyof 사용 시 typeof를 함께 사용해 주어야 한다.

```typescript
enum UserType {
  TEMP,USER,ADMIN
}

// 'TEMP' | 'USER' | 'ADMIN';
type LogLevelStrings = keyof typeof UserType
```

<br>

## 참조

[typescript 핸드북](https://joshua1988.github.io/ts/guide/enums.html)
