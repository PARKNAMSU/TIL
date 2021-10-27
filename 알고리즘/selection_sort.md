# 선택정렬(Selection Sort)
### 선택 정렬이란?
선택 정렬이란 어떠한 숫자들의 집합인 배열이 있을 때 가장 작은(혹은 큰) 숫자를 앞으로 보내서 정렬을 하는 정렬 알고리즘이다.
선택정렬은 가장 원시적이고 기초적인 알고리즘이다.

### example
```javascript
function selectionSort(arr){
    //맨 앞으로 보낼 요소와 인덱스를 위한 변수
    let min,idx;
    for(let i=0 ; i<arr.length; i++){
        
        //최소값과 그 인덱스를 현재 가장 앞에있는 값으로 변경
        min = arr[i];
        idx = i;
        for(let j=i; j<arr.length; j++){
            //배열을 돌면서 가장 앞에있는 값보다 더 작은 값을 min, 그 인덱스를 idx에 저장
            if(min > arr[j]){ 
                min = arr[j];
                idx = j;
            }
        }
        //한 사이클이 끝난 후 가장작은값을 맨 앞으로 이동
        let temp = arr[i];
        arr[i] = arr[idx];
        arr[idx] = temp;

    }
    return arr;
}
```

### 선택정렬의 시간복잡도
선택정렬은 데이터가 N개가 있을 경우 N의 2제곱만큼 연산을 수행해야 한다.
이를 O(N^2) 로 표현할 수 있다.

[참조: 안경잡이 개발자](https://m.blog.naver.com/PostView.naver?blogId=ndb796&logNo=221226800661&navType=by)
