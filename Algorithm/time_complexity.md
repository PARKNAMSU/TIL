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

시간복잡도 O(n)은 linear complexity 라고도 하며 입력값 증가에 따라 같은비율로 증가한다.

예를들면 입력값이 1이면 1초가 걸리는 문제라면, 100이라면 100초가 된다.

![image](https://user-images.githubusercontent.com/62639722/144744946-f427a1ea-1c59-4dd8-9aec-abe1cd87c158.png)

__O(n)의 예시__
```javascript
//arr의 길이만큼 반복(즉 arr가 증가하면 시간도 같은비율로 증가)
function funcTwo(arr){
  let max = 0;
  for(let i=0; i<arr.length; i++){
    if(arr[i] > max)
      max = arr[i];
  }
  return max;
}
```

<br>

### O(log n)

시간복잡도 O(log n)은 logarithmic complexity 라고도 하며, 입력값이 증가할수록 시간 증가율이 하락한다.

![image](https://user-images.githubusercontent.com/62639722/144745166-e00ee6ee-8d47-451d-9d4e-bf5f6e06ab3b.png)
