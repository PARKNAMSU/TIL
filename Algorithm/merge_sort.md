# 병합 정렬(Merge Sort)

### 병합 정렬(Merge Sort)이란?
병합 정렬은 퀵 정렬과 같이 하나의 문제를 두개의 작은 문제로 나누어 해결하는 '분할 정복'을 사용하는 알고리즘 이다.<br>
퀵 정렬은 피벗값을 기준으로 큰값과 작은값을 나누는 반면, 병합 정렬은 정확히 반으로 나누어 정렬한 후 합치는 방식의 알고리즘 이다.<br>

### 병합정렬의 진행과정
<img width="1126" alt="스크린샷 2021-11-03 오후 9 41 31" src="https://user-images.githubusercontent.com/62639722/140061884-68b5721b-462c-40b8-a35d-a07eb6ae29bd.png">
병합정렬은 일단 절반씩 최소단위까지 나누어 왼쪽에서부터 병합하며 정렬을 하는 진행과정을 가지고 있다.<br>

### example
```javascript


//임시로 정렬하기 위한 임시 배열
let temp = [];

/*
    병합 정렬
    arr: 정렬할 array
    start: 시작값
    end: 마지막값
    merge: 정렬을 위한 콜백함수
*/
function mergeSort(arr,start,end,
    
    /* 정렬을 위한 콜백함수 
        start: 첫번째 인덱스
        mid: 배열 분할을 위한 중간값
        end: 마지막 인덱스
    */
    merge = (arr,start,mid,end) => {
    
    // 첫번째 ~ mid값 까지 분할을 위한 인덱스
    let left = start;
    // mid+1 ~ 마지막 까지 분할을 위한 인덱스
    let right = mid+1;
    // 임시 정렬을 위한 k
    let k = start;
    
    /*
        왼쪽 분할 배열 left 가 mid(중간값) 보다 커지거나 
        오룬쪽 분할 배열 right가 end 보다 커지면 종료
    */
    while(left <= mid && right <= end){
        //정렬을 위한 임시배열 temp에 left 가 right 값보다 크면 left를 임시배열의 k번째에 삽입하고 left다음값을 찾기위해 left를 1증가시킴(반대의경우는 right)
        temp[k] = arr[left] <= arr[right] ? arr[left++]:arr[right++];
        //다음값 정렬을 위해 k를 1증가
        k++;
    }

    /*  
        left가 mid보다 크다는 것은 left는 모두 정렬했지만 right에 값이 남아있다는 것이므로
        현재의 right부터 end 까지 값을 temp에 삽입    
    */
    if(left > mid){
        for(let i = right; i <= end; i++)
            temp[k++] = arr[i];
    }
    /*
        반대의 경우 left에 값이 남아있는 것이므로
        현재 left부터 mid 까지 값을 temp에 삽입
    */
    else{
        for(let i = left; i<= mid; i++)
            temp[k++] = arr[i];
    }

    // temp에 정렬된 값들을 arr에 삽입하여 arr의 현재의 start부터 end까지의 값들을 정렬시킴
    for(let i = start; i<= end; i++)
        arr[i] = temp[i];
}){

    /* 
        start가 end와 같거나 커지면 데이터가 1개밖에 없어
        정렬할 필요가 없으므로 실행시키지 않음
    */
    if(start < end){

        // 배열을 반으로 나누기 위해 start+end를 2로 나눔
        let mid = Math.floor((start + end) / 2);
        // start ~ mid 까지 분할
        mergeSort(arr,start,mid);
        // mid+1 ~ end 까지 분할
        mergeSort(arr,mid+1,end);
        // 콜백함수 merge를 사용하여 정렬
        merge(arr,start,mid,end);
    }
}
let myArr = [10,2,1,5,3,4,7,6,9,8];
mergeSort(myArr,0,myArr.length-1);
console.log(myArr);
```
<br>

### 병합 정렬(Merge Sort)의 시간복잡도
병합 정렬은 퀵 정렬과 마찬가지로 N(logN)의 시간복잡도를 가지고 있지만,<br>
퀵 정렬은 최악의 경우 시간복잡도가 N(N^2) 가 되는 반면, 병합정렬은 최악의 경우에도 N(logN)을 보장한다.

<br>참조<br>
[안경잡이 개발자](https://m.blog.naver.com/PostView.naver?blogId=ndb796&logNo=221227934987&navType=by)
