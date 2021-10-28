# 버블정렬(Bubble Sort)

### 버블정렬(Bubble Sort)란?
버블정렬이란 옆에있는 값과 비교하여 더 작은(혹은 큰) 값을 앞으로 보내는 정렬 방법이다.<br>
버블정렬도 선택정렬과 같이 매우 직관적인 정렬 방법이나, 계속해서 값을 변경해 줘야 하므로 가장 비효율적인 정렬 방법이다.

<br>

### example
```javascript
function bubbleSort(arr){
    
    for(let i=0; i<arr.length;i++){
        //1은 첫 사이클 시 outOfIndex 방지하기 위해 빼줌
        //한번 사이클이 돌때마다 가장 큰 값은 맨 뒤로 이동하므로 이미 비교된 값은 계산할 필요 없으므로 i를 빼줌
        for(let j=0;j<arr.length-1-i;j++){ 

            if(arr[j] > arr[j+1]){ //다음 인덱스의 값이 현재 인덱스의 값보다 작다면 두개의 위치를 변경해줌
                let temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp;
            }
            
        }
    }
    return arr;
}
```

<br>

###  버블정렬의 시간복잡도
버블정렬의 시간복잡도는 선택정렬과 마찬가지로 N의 2제곱으로, O(N^2) 이다.
