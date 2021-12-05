# 시간 복잡도(Time Complexity)

### 시간 복잡도(Time Complexity)란?

시간 복잡도란 어떠한 연산을 실행할 때 연산 횟수에 비해 시간이 얼마나 걸리는지 나타내는 것이다.<br>
효율적인 방법으로 문제해결을 할 때 시간복잡도도 항상 고려대상에 포함되어야 한다.

시간복잡도는 Big-O(빅-오), Big-Ω(빅-오메가), Big-θ(빅-세타) 표기법이 있는데,<br>
Big-O는 최악, Big-Ω는 최선, Big-θ는 평균에 대해 나타내는 표기법이다.

문제해결시 최악에 대해 고민하는것이 중요하므로 Big-O 표기법을 많이 사용한다.

<br>

## Big-O 표기법의 종류

### O(1)

시간복잡도 O(1) 은 constant complexity 라고도 하며, 입력값이 증가하더라도 시간이 늘어나지 않는다.

즉 입력값의 크기가 증가해도 바로 출력값을 얻을 수 있다.

![image](https://user-images.githubusercontent.com/62639722/144744827-0d690292-5cc9-4e27-8159-b1c579dd649b.png)

__O(1)__ 의 예시
```javascript
//arr의 크기가 아무리 커도 시간복잡도가 증가하지 않는다.
function funcOne(arr){
  return arr[1];
}
```

<br>

### O(n)
