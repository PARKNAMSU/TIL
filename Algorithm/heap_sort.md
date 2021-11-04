# 힙 정렬(Heap Sort)

### 힙 정렬(Heap Sort) 이란?
힙 정렬이란 **힙 트리구조** 를 이용하여 정렬하는 알고리즘 이다.

### 힙(Heap) 과 이진 트리(Binary Tree)
힙(Heap) 이 무엇인지 알려면 먼저 이진 트리(Binary Tree)가 무엇인지 알이야 한다.<br><br>

* 이진 트리

이진 트리란 모든 노드의 자식 노드가 2개 이하인 트리구조를 말한다.

<img width="712" alt="스크린샷 2021-11-04 오후 9 57 13" src="https://user-images.githubusercontent.com/62639722/140317389-30b190c9-9ea8-4d32-9fc9-4bbccd680f9a.png">

위와같이 모든 노드는 자식을 2개를 초과하여 가질 수 없다.<br><br>

* 완전 이진 트리

완전 이진 트리는 최 상단의 root 노드부터 시작하여 왼쪽, 오른쪽으로 차근차근 데이터가 들어가는 형태의 노드이다.

<br><br>

* 힙

힙은 최소값이나 최대값을 빠르게 찾기 위해서 완전 이진트리를 기반으로 사용하는 트리 이다.<br>
힙에는 **최대힙** 과 **최소힙** 이 있는데 최대힙은 부모 노드가 자식 노드보다 큰 구조의 힙이다.<br>
힙정렬을 사용하기 위해서는 **힙 생성 알고리즘(Heapify Algorithm)** 을 사용하여 주어진 데이터들이 힙 구조를 가지도록 해주어야 한다.

* 힙 생성 알고리즘

힙 생성 알고리즘은 어떠한 특정 노드의 자식 중 더 큰 자식이 자신보다 클 시 그 자식노드와 자신을 바꾸는 방법의 알고리즘이다.<br>

<img width="438" alt="스크린샷 2021-11-04 오후 10 15 34" src="https://user-images.githubusercontent.com/62639722/140319963-0dfc30c4-4e00-48c1-ad66-da4c94126f32.png">

위 그림을 보면 부모노드 2가 자식노드 3보다 작으므로 힙 구조가 아닌 상태이므로 힙 생성(heapify)을 위해 3 과 2를 변경해 준다.<br><br>

<img width="506" alt="스크린샷 2021-11-04 오후 10 16 46" src="https://user-images.githubusercontent.com/62639722/140320160-5a2d5c73-4700-4e6c-bf67-c6fc04461efc.png">
이제 모든 부모노드가 자식노드보다 크므로 힙 구조를 가지고 있다

<br><br>

이러한 힙구조를 가지게 되면 root 노드는 모든 값중 가장 큰값이 된다.<br>
이때 root 노드를 배열의 가장 마지막으로 옮겨 정렬을 하고 정렬된 인덱스를 제외한 부분의 배열을 다시 힙 생성 알고리즘을 통해 힙 구조를 구성하는 과정을 반복한다.
<br><br>

이러한 과정을 거치면서 데이터를 정렬하는 것이 힙 정렬 이다.

<br><br>

### example

```javascript
function heapSort(arr,max = arr.length){ // arr와 정렬된 노드를 제외한 인덱스

    //더이상 정렬할 노드가 없으면 리턴
    if(max === 1)
        return arr;

    //자신의 부모노드보다 큰 노드들을 부모노드와 변경하며 heapify 실행
    for(let i = 1; i<max; i++){
        //reaf: 부모와 비교할 자식노드
        let reaf = i;
        //비교할 부모가 root일때까지 반복
        while(reaf !== 0){
            // (reaf-1) / 2 의 계산식으로 부모노드를 찾음
            let root = Math.floor( (reaf-1) / 2 );
            if(arr[reaf] > arr[root]){
                let temp = arr[reaf];
                arr[reaf] = arr[root];
                arr[root] = temp;
            }
            reaf = root;
        }
    }

    /*
        heapify가 완료된 상태는 arr의 가장 처음 인덱스에 가장 큰값이 들어가 있는 상태이므로
        최상단 root노드를 정렬이 되지않은 인덱스 중 가장 마지막 인덱스로 이동하며 오름차순 정렬
    */
    let temp = arr[0];
    arr[0] = arr[max-1];
    arr[max-1] = temp;

    //정렬된 마지막 인덱스를 제외하고 재귀실행으로 다시 heapify 실행
    return heapSort(arr,max-1);
}

let arr = [5,2,1,3,6,10,9,8,4];
console.log(heapSort(arr));
```

<br><br>

### 힙 정렬의 시간복잡도
힙 생성(heapify) 를 한번 실행할 때마다 O(logN)의 시간복잡도가 발생한다.<br>
이 과정을 N번 거치므로 힙 정렬의 전체 시간복잡도는 **O(N * logN)** 이다.

<br><br>
참조<br>

[안경잡이 개발자](https://m.blog.naver.com/PostView.naver?blogId=ndb796&logNo=221228342808&navType=by)
    
    
    
    
