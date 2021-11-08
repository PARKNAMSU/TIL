# 계수 정렬(Counting Sort)

### 계수 정렬(Counting Sort) 알고리즘 이란?
계수 정렬(Counting Sort) 알고리즘 이란 '범위' 가 정해져 있다는 가정하에 가장 빠른 알고리즘이다.<br>

예를들어 숫자의 범위가 1~8 이라는 범위가 정해져 있으면 각각의 수를 counting 하여서 빠르게 정렬을 수행할 수 있다.

### example
```javascript
function countSort(arr,range){

    //카운트를 위한 배열을 범위만큼 생성
    let count = new Array(range+1).fill(0);
    
    //정렬할 배열 생성
    let answer = [];
    
    //배열을 순회하며 해당하는 숫자의 인덱스의 값을 추가함
    for(let i=0; i<arr.length; i++){
        count[arr[i]]++;
    }
    
    //카운트한 숫자를 작은수 부터 answer에 담음
    count.forEach((item,idx) => {
        if(item !== 0)
            for(let i=0; i<item; i++)
                answer.push(idx);
    });

    return answer;
}
```

### 계수 정렬(Counting Sort)의 시간복잡도
계수 정렬의 시간복잡도는 O(N)으로 앞의 알고리즘보다 훨씬 빠르다.<br>
하지만 계수 정렬은 범위가 정해져 있을때만 사용이 가능하다.<br>

참조<br>

[안경잡이 개발자](https://m.blog.naver.com/PostView.naver?blogId=ndb796&logNo=221228361368&navType=by)
