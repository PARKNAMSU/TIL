# TypeScript

### 📚 TypeScript 란?

타입 스크립트(TypeScript) 는 자바 스크립트(JavaScript)를 확장하여 자바 스크립트(JavaScript) 에 타입을 부여한 프로그래밍 언어이다.

타입 스크립트(TypeScript) 는 자바스크립트와 달리 브라우저나 NodeJs 환경에서 실행 시 컴파일 과정을 거쳐야 한다.

### 📚 TypeScript를 사용하는 이유

타입스크립트를 사용해야 하는 첫번째 이유는 _에러를 사전에 방지할 수 있다._

2개의 정수 타입의 매개변수를 받아서 두 매가변수의 합을 구하는 함수가 있다고 가정해 보자.

자바스크립트에서는 만약 매개변수가 정수의 타입이 아니라 문자열이 들어올 경우 아래와 같은 결과를 보여준다.

```javascript
function sumNumber(a,b){
  return a + b;
}

// err 가 발생하는 게 아닌 문자열 '1020' 을 반환
console.log(sumNumber('10','20'));

```

하지만 매개변수에 타입을 지정해 주면 문자열이 들어올 경우 에러를 발생시켜준다.

```typescript
function sumNumber(a:number,b:number){
  return a + b;
}

// 에러 발생
console.log(sumNumber('10','20'));
```
<br>

두번째는 _큰규모의 프로젝트 협업 또는 유지보수_ 시에 이점이 있다.

큰 규모의 프로젝트를 진행하거나 어떠한 프로젝트를 유지보수 할 경우에는 때로 다른 개발자의 코드를 살펴봐야 할 필요가 있다.

이 경우에 미리 타입을 명시적으로 지정해 주면 코드를 더욱 쉽게 이해할 수 있고 이는 협업을 통한 생산성을 증대시킬 수 있다.

## 참조

[typescript 공식문서](https://www.typescriptlang.org/ko/docs/handbook/intro.html)

[타입스크립트 핸드북](https://joshua1988.github.io/ts/why-ts.html#%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%9E%80)
