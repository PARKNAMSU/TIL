# Typescript 함수

<br>

## 함수의 기본적인 타입 선언

함수에 타입을 지정해 줄 때는 매개변수의 타입과 함수의 반환값을 지정해 줘야 한다.

```typescript
// number 타입 a, b 를 매개변수로 받고 두 매개변수를 더한 값인 number 타입을 반환
function plus(a:number, b:number):number {
  return a + b;
}
```

<br>

## 함수의 인자

typescript 는 기본적으로 모든 인자를 필수값으로 인식하므로 인자를 필수값으로 지정하고 싶지 않을 때는 매개변수 뒤에 `?` 를 작성하고, 
어떠한 매개변수의 기본값을 설정하고 싶으면 ES6 문법과 같이 `arg = 'some value'` 로 할당한다.

```typescript
// a는 필수로 전달받아야 하지만 b는 전달받을 필요가 없다.
function addStr(a:string, b?:string):string {
  return b ? a + b : a;
}

// b의 기본값을 10으로 초기화 한다.
fucntion plus(a:number, b = 10):number {
  return a + b;
}
```

<br>

## 참조
[Typescript 핸드북](https://joshua1988.github.io/ts/guide/functions.html#this)
