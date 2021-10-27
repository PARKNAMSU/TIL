# 선택정렬(Selection Sort)
### 선택 정렬이란?
선택 정렬이란 어떠한 숫자들의 집합인 배열이 있을 때 가장 작은(혹은 큰) 숫자를 앞으로 보내서 정렬을 하는 정렬 알고리즘이다.

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
