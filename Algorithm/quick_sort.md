# 퀵 정렬(Quick Sort)
### 퀵 정렬 이란?
퀵 정렬은 하나의 큰 문제를 두개의 작은 문제로 분할하여 해결하는 '분할정복 알고리즘' 이다.
<br>
퀵정렬의 실행 순서는 다음과 같다.<br>

1. 특정한 기준값(pivot)을 설정한다. (보통은 첫번째 인덱스)
2. 기준값보다 큰 값을 왼쪽에서 부터 탐색하여 찾는다.
3. 기준값보다 작은 값을 오른쪽에서 부터 탐색하여 찾는다.
4. 큰값과 작은값의 위치를 변경하여 작은값을 왼쪽, 큰값을 오른쪽으로 이동시킨다.
5. 기준값을 기준으로 위의 작업이 끝나면 작은값중 가장오른쪽에 있는 값과 기준값의 위치를 변경한다.
6. 기준값을 기준으로 작은값과 큰값 2개의 문제로 나누어 다시 정렬을 실행한다.

### example
'''javascript

let arr = [1,10,9,2,3,5,4,8,7,6];

function quickSort(arr,start,end){ //정렬할 array, start index, end index
    if(start >= end) //start가 end보다 크거나 같으면 실행 취소
        return;

    //기준값 key    
    let key = start;
    //기준값보다 큰 값을 찾기위한 left index
    let left = start+1;
    //기준값보다 작은 값을 찾기위한 right index
    let right = end;

    //left가 right보다 커지면 종료(엇갈리는 상황이므로)
    while(left <= right){
        /*
            left 가 end보다 크거나 (기준값보다 큰값이 없거나) 
            기준값보다 큰 left의 값을 만나기 전까지 실행하여 기준보다 큰 값을 찾음
        */
        while(left <= end && arr[left] < arr[key])
            left++;
        /*
            right 가 start보다 작거나같아지거나(기준값보다 작은값이 없거나) 
            기준값보다 작은 right의 값을 만나기 전까지 실행하여 기준보다 작은값을 찾음
        */  
        while(right > start && arr[right] > arr[key])
            right--;
        
        /*
            left가 right보다 커졌다는 것은 엇갈린 상태이므로(현재 기준값 기준으로 정렬이 완료된 상태)
            기준값과 right(기준값 보다 작은값)를 변경.
        */
        if(left > right){
            let temp = arr[key];
            arr[key] = arr[right];
            arr[right] = temp;
        }
        /*
            left 가 right보다 작은 상태에서는 
            left(큰값) 와 right(작은값) 을 변경하여 작은값을 앞으로 이동
        */
        else{
            let temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;           
        }
    }
    /*
        기준값과 right를 변경했으므로 right를 기준으로 반으로 분할하여 재귀실행 
    */
    quickSort(arr,start,right-1);
    quickSort(arr,right+1,end);
}

quickSort(arr,0,arr.length-1);
console.log(arr);
'''
