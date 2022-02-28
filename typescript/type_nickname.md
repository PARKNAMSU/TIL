# Type NickName

<br>

## 타입 별칭이란?

타입 별칭은 특정 타입이나 인터페이스를 참조하는 변수를 말한다.

#### 간단한 타입에 대한 타입 별칭

```typescript
type Name = string;

let name:Name = 'Park';
```

<br>

#### Interface Level에 대한 타입 별칭
```typescript
type User = {
  name:string;
  age:number
}
```

<br>

#### Generic 사용
```typescript
type MyType<T> = {
  dynamicType:T
}
```

<br>

## 참조

[typescript 핸드북](https://joshua1988.github.io/ts/guide/type-alias.html#%ED%83%80%EC%9E%85-%EB%B3%84%EC%B9%AD-type-aliases)
